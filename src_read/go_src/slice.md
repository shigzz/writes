# slice

代码位于`src/runtime/slice.go`中

## 基本结构

```go
type slice struct {
	array unsafe.Pointer
	len   int
	cap   int
}
```

