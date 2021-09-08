# LevelDB源码

## 数据结构

### Slice

```cpp
const char* data_; // const修饰，必须在构造函数中初始化
size_t size_;
```

### Status

``` cpp
const char* state_;
Status(Status&& rhs) noexcept : state_(rhs.state_) { rhs.state_ = nullptr; } // 右值构造函数
Status& operator=(Status&& rhs) noexcept; // 右值移动构造函数
```

### Iterator

### Cache

## 写日志

一个block大小32KB，32768bytes

一个record的一个header大小7bytes，checksum（4）+length（2）+type（1）

如果一个block剩下的大小小于7字节，则补零，从下一个block开始