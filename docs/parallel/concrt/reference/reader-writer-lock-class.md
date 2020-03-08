---
title: reader_writer_lock 类
ms.date: 11/04/2016
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
ms.openlocfilehash: 1a7386e527b5327d928bfdcb3281c88666f1b106
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867155"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock 类

具有仅限本地旋转的基于编写器首选队列的读取器-编写器锁。 锁授予对编写器的先进先出 (FIFO) 访问权限，并在出现编写器持续负载的情况下停止读取器。

## <a name="syntax"></a>语法

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Members

### <a name="public-classes"></a>公共类

|名称|说明|
|----------|-----------------|
|[reader_writer_lock：： scoped_lock 类](#scoped_lock_class)|可用于获取作为编写器 `reader_writer_lock` 锁定对象的异常安全 RAII 包装。|
|[reader_writer_lock：： scoped_lock_read 类](#scoped_lock_read_class)|可用于获取 `reader_writer_lock` 锁定对象作为读取器的异常安全 RAII 包装。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[reader_writer_lock](#ctor)|构造新的 `reader_writer_lock` 对象。|
|[~ reader_writer_lock 析构函数](#dtor)|销毁 `reader_writer_lock` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[lock](#lock)|获取编写器的读取器-编写器锁。|
|[lock_read](#lock_read)|获取读取器-编写器锁作为读取器。 如果有编写器，则活动读取器必须等待，直到完成。 读取器只是在锁定中注册兴趣，并等待编写器释放它。|
|[try_lock](#try_lock)|尝试在不阻止的情况下获取读取器-编写器锁作为编写器。|
|[try_lock_read](#try_lock_read)|尝试在不阻止的情况下获取读取器-编写器锁作为读取器。|
|[unlock](#unlock)|基于锁定读取器、读取器或编写器锁定读取器-编写器锁。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`reader_writer_lock`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="lock"></a>住

获取编写器的读取器-编写器锁。

```cpp
void lock();
```

### <a name="remarks"></a>备注

通常，使用[scoped_lock](#scoped_lock_class)构造作为编写器以异常安全方式获取和释放 `reader_writer_lock` 对象是一种更安全的做法。

在编写器尝试获取锁后，在编写器成功获取和释放该锁之前任何将来的读取器都将阻塞。 此锁偏向写入器，可枯竭读取器连续加载编写器。

编写器相互链接，以便退出锁定的编写器会在行中释放下一个编写器。

如果锁已由调用上下文持有，则会引发[improper_lock](improper-lock-class.md)异常。

## <a name="lock_read"></a>lock_read

获取读取器-编写器锁作为读取器。 如果有编写器，则活动读取器必须等待，直到完成。 读取器只是在锁定中注册兴趣，并等待编写器释放它。

```cpp
void lock_read();
```

### <a name="remarks"></a>备注

通常，利用[scoped_lock_read](#scoped_lock_read_class)构造以异常安全方式获取和释放 `reader_writer_lock` 对象作为读取器通常更安全。

如果有编写器正在等待锁定，读取器将等待，直到所有编写器都已获取并释放该锁。 此锁偏向写入器，可枯竭读取器连续加载编写器。

## <a name="ctor"></a>reader_writer_lock

构造新的 `reader_writer_lock` 对象。

```cpp
reader_writer_lock();
```

## <a name="dtor"></a>~ reader_writer_lock

销毁 `reader_writer_lock` 的对象。

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>备注

当析构函数运行时，应不再持有锁。 允许读取器在持有锁的情况中锁定析构会导致未定义的行为。

## <a name="scoped_lock_class"></a>reader_writer_lock：： scoped_lock 类

可用于获取作为编写器 `reader_writer_lock` 锁定对象的异常安全 RAII 包装。

```cpp
class scoped_lock;
```

## <a name="scoped_lock_ctor"></a>scoped_lock：： scoped_lock

构造一个 `scoped_lock` 对象，并获取作为编写器传入 `_Reader_writer_lock` 参数的 `reader_writer_lock` 对象。 如果锁由另一个线程持有，则此调用将被阻止。

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>参数

*_Reader_writer_lock*<br/>
要作为编写器获取的 `reader_writer_lock` 对象。

## <a name="scoped_lock_dtor"></a>scoped_lock：： ~ scoped_lock

销毁 `reader_writer_lock` 对象并释放在其构造函数中提供的锁。

```cpp
~scoped_lock();
```

## <a name="scoped_lock_read_class"></a>reader_writer_lock：： scoped_lock_read 类

可用于获取 `reader_writer_lock` 锁定对象作为读取器的异常安全 RAII 包装。

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_read_ctor"></a>scoped_lock_read：： scoped_lock_read

构造一个 `scoped_lock_read` 对象，并获取作为读取器传入 `_Reader_writer_lock` 参数的 `reader_writer_lock` 对象。 如果锁由另一个线程持有，或者有挂起的编写器，则此调用将被阻止。

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>参数

*_Reader_writer_lock*<br/>
要作为读取器获取的 `reader_writer_lock` 对象。

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor"> reader_writer_lock：： scoped_lock_read：： ~ scoped_lock_read 析构函数

销毁 `scoped_lock_read` 对象并释放在其构造函数中提供的锁。

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a>try_lock

尝试在不阻止的情况下获取读取器-编写器锁作为编写器。

### <a name="syntax"></a>语法

```cpp
bool try_lock();
```

### <a name="return-value"></a>返回值

如果已获取锁，则值为**true**;否则，值**为 false**。

## <a name="try_lock_read"></a>try_lock_read

尝试在不阻止的情况下获取读取器-编写器锁作为读取器。

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>返回值

如果已获取锁，则值为**true**;否则，值**为 false**。

## <a name="unlock"></a>解锁

基于锁定读取器、读取器或编写器锁定读取器-编写器锁。

```cpp
void unlock();
```

### <a name="remarks"></a>备注

如果有编写器正在等待锁定，则该锁的版本将始终按 FIFO 顺序进入下一编写器。 此锁偏向写入器，可枯竭读取器连续加载编写器。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[critical_section 类](critical-section-class.md)
