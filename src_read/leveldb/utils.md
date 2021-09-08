# utils

## hash

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

Leveldb自己实现的一个内存分配器。

