# utils

## Hash

### murmur hash

“来自Wikipedia”

```
Murmur3_32(key, len, seed)
c1 <- 0xcc9e2d51
c2 <- 0x1b873593
r1 <- 15
r2 <- 13
m <- 5
n <- 0xe6546b64

hash <- seed

for each forByteChunk of key
		k <- forByteChunk
		
		k <- k * c1
		k <- (k << r1) OR (k >> 32-r1)
		k <- k * c2
		
		hash <- hash XOR k
		hash <- (hash << r2) OR (hash >> 32-r1)
		hash <- hash * m + n
		
with any remainingBytesInKey
		remainingBytes <- SwapEndianOrderOf(remainingBytesInKey)
		remainingBytes <- remianingBytes * c1
		remianingBytes <- (remianingBytes << r1) OR (remianingBytes >> 32-r1)
		remianingBytes <- remianingBytes * c2
		
		hash <- hash XOR remianingBytes

hash <- hash XOR len

hash <- hash XOR (hash >> 16)
hash <- hash * 0x85ebca6b
hash <- hash XOR (hash >> 13)
hash <- hash * 0xc2b2ae35
hash <- hash XOR (hash >> 16)
```

### hash in leveldb

murmurhash的一个简化版本实现。

```
given char* data, size n, seed
m <- 0x6a4a793
r <- 24
h <- seed ^ (n * m)
for each forbyteChunk of data
		w <- uint32(forByteChunk)
		h <- h + w
		h <- h * m
		h <- h ^ (h >> 16)
for each remainingbyteChunk of data
		h <- h + remaining byte
		h = h ^ (h >> r)
```

## Arena

leveldb自己实现的一个内存分配器。arena成员变量很简单：

```cpp
// Allocation state
char* alloc_ptr_;
size_t alloc_bytes_remaining_;

// Array of new[] allocated memory blocks
std::vector<char*> blocks_;

  // Total memory usage of the arena.
std::atomic<size_t> memory_usage_;
```

从变量命名和注释可以看出，这里`alloc_ptr_`指向分配后的字符串，`alloc_bytes_remaining_`表示剩余可以分配的内存大小，`blocks_`为数据块向量，`memory_usage_`表示总内存占用，注意，这里使用了原子变量，可能是出于并发问题的顾虑。

另外，arena还定义了两个私有函数：

```cpp
char* AllocateFallback(size_t bytes);
char* AllocateNewBlock(size_t block_bytes);
```

其中`AllocateNewBlock`申请`block_bytes`大小的字符串，加入`blocks_`向量中，修改`memory_usage_`的值，返回申请后的内存地址。

`AllocateFallback`函数稍微复杂些，首先它判断`bytes`是否大于`kBlockSize`的1/4（`kBlockSize`是定义的块大小，为4096），如果大于，为了避免产生碎片，直接为它分配一个新的block。反之，则代表一个新的大小为`kBlockSize`的块可以接受多个内存分配请求，通过移动`alloc_ptr_`以及设置`alloc_bytes_remaining_`的值实现。公有的Allocate函数需要配合`AllocateFallback`，实现小对象的分配。

```cpp
inline char* Arena::Allocate(size_t bytes) {
  assert(bytes > 0);
  if (bytes <= alloc_bytes_remaining_) {
    char* result = alloc_ptr_;
    alloc_ptr_ += bytes;
    alloc_bytes_remaining_ -= bytes;
    return result;
  }
  return AllocateFallback(bytes);
}

char* Arena::AllocateFallback(size_t bytes) {
  if (bytes > kBlockSize / 4) {
    char* result = AllocateNewBlock(bytes);
    return result;
  }

  alloc_ptr_ = AllocateNewBlock(kBlockSize);
  alloc_bytes_remaining_ = kBlockSize;

  char* result = alloc_ptr_;
  alloc_ptr_ += bytes;
  alloc_bytes_remaining_ -= bytes;
  return result;
}
```

最后一个公共函数`AllocateAligned`，在分配内存前，进行了一次内存对齐操作，分配策略则与之前类似，如果当前块的剩余容量大于对齐需求后需要的容量，就在当前块继续分配，反之新建一个块进行分配。

## BloomFilterPolicy

bloom过滤器，是虚基类FilterPolicy的一个实现。是一个通用的工具，所以放在了util中。

### FilterPolicy

位于include/leveldb中，是一个虚基类，定义了各种过滤策略。

```cpp
class LEVELDB_EXPORT FilterPolicy {
 public:
  virtual ~FilterPolicy();

  virtual const char* Name() const = 0; // 返回过滤器的名称

  virtual void CreateFilter(const Slice* keys, int n,
                            std::string* dst) const = 0; // 创建过滤器

  // 匹配判定
  virtual bool KeyMayMatch(const Slice& key, const Slice& filter) const = 0; 
};

```

### bloom

bloomFilter类有两个私有变量：

```cpp
  size_t bits_per_key_;
  size_t k_;
```

其中`bits_per_key`为创建的时候作为参数传入，`k_`为`bits_per_key`乘以0.69，因为0.69最接近ln(2)，至于为什么是ln(2)，暂时不清楚。最后根据`k_`的大小确定最终取值。

```cpp
k_ = static_cast<size_t>(bits_per_key * 0.69);  // 0.69 =~ ln(2)
if (k_ < 1) k_ = 1;
if (k_ > 30) k_ = 30;
```

// 未完

### coding

coding部分包含一系列编码解码的操作。

### Cache









