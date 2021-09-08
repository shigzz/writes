## 存储类型定义

> 四类文件
>
> 1. Manifest
> 2. Journal
> 3. Table
> 4. Temp

### interface

* syncer

* reader

  > io.ReadSeeker
  >
  > io.ReaderAt
  >
  > io.Closer

* writer

  > io.WriteCloser
  >
  > syncer

* locker

* **storage**

  >Lock
  >
  >Log
  >
  >SetMeta
  >
  >GetMeta
  >
  >List
  >
  >Open
  >
  >Create
  >
  >Remove
  >
  >Close

### fileStorage -> storage

> path
>
> logw
>
> logSize
>
> buf