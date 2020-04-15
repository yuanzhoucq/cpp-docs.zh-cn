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
ms.openlocfilehash: 13b44387f3e9489090ec31345fe4347ff5f205ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376244"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock 类

具有仅限本地旋转的基于编写器首选队列的读取器-编写器锁。 锁授予对编写器的先进先出 (FIFO) 访问权限，并在出现编写器持续负载的情况下停止读取器。

## <a name="syntax"></a>语法

```cpp
class reader_writer_lock;
```

## <a name="members"></a>成员

### <a name="public-classes"></a>公共类

|名称|说明|
|----------|-----------------|
|[reader_writer_lock::scoped_lock 类](#scoped_lock_class)|可用于作为编写器获取`reader_writer_lock`锁对象的异常安全 RAII 包装器。|
|[reader_writer_lock::scoped_lock_read 类](#scoped_lock_read_class)|可用于获取`reader_writer_lock`锁定对象作为读取器的异常安全 RAII 包装器。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[reader_writer_lock](#ctor)|构造新的 `reader_writer_lock` 对象。|
|[*reader_writer_lock析构函数](#dtor)|销毁`reader_writer_lock`对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[锁](#lock)|以编写器身份获取读取器-写入器锁。|
|[lock_read](#lock_read)|获取读写器锁作为读取器。 如果有作者，活跃的读者必须等待，直到他们完成。 读取器只需注册对锁的兴趣，然后等待编写器释放它。|
|[try_lock](#try_lock)|尝试获取读取器-写入器锁作为编写器而不阻塞。|
|[try_lock_read](#try_lock_read)|尝试获取读取器-写入器锁作为读取器而不阻塞。|
|[解 锁](#unlock)|根据锁定者、读取器或编写器来解锁读取器-写入器锁。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`reader_writer_lock`

## <a name="requirements"></a>要求

**标题：** concrt.h

**命名空间：** 并发

## <a name="lock"></a><a name="lock"></a>锁

以编写器身份获取读取器-写入器锁。

```cpp
void lock();
```

### <a name="remarks"></a>备注

利用[scoped_lock](#scoped_lock_class)构造以异常安全的方式获取和释放`reader_writer_lock`对象作为编写器通常更安全。

在编写器尝试获取锁后，在编写器成功获取和释放该锁之前任何将来的读取器都将阻塞。 这个锁偏向于作家，在不断的作家负载下，读者可能饿死。

编写器被链接，以便退出锁的编写器释放行下一个写入器。

如果调用上下文已持有锁，将引发[improper_lock](improper-lock-class.md)异常。

## <a name="lock_read"></a><a name="lock_read"></a>lock_read

获取读写器锁作为读取器。 如果有作者，活跃的读者必须等待，直到他们完成。 读取器只需注册对锁的兴趣，然后等待编写器释放它。

```cpp
void lock_read();
```

### <a name="remarks"></a>备注

利用[scoped_lock_read](#scoped_lock_read_class)构造以异常安全的方式获取和释放`reader_writer_lock`对象作为读取器通常更安全。

如果有写入器等待锁，读取器将等待，直到所有行的写入器都获取并释放锁。 这个锁偏向于作家，在不断的作家负载下，读者可能饿死。

## <a name="reader_writer_lock"></a><a name="ctor"></a>reader_writer_lock

构造新的 `reader_writer_lock` 对象。

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a>*reader_writer_lock

销毁`reader_writer_lock`对象。

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>备注

当析构函数运行时，预计锁不再被持有。 允许读取器编写器锁在锁仍持有时析构会导致未定义的行为。

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a>reader_writer_lock：：scoped_lock类

可用于作为编写器获取`reader_writer_lock`锁对象的异常安全 RAII 包装器。

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a>scoped_lock：scoped_lock

构造`scoped_lock`对象并获取作为编写器在`reader_writer_lock`参数中`_Reader_writer_lock`传递的对象。 如果锁由另一个线程持有，此调用将阻止。

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>参数

*_Reader_writer_lock*<br/>
作为`reader_writer_lock`编写器获取的对象。

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a>scoped_lock：~scoped_lock

销毁`reader_writer_lock`对象并释放其构造函数中提供的锁。

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a>reader_writer_lock：：scoped_lock_read类

可用于获取`reader_writer_lock`锁定对象作为读取器的异常安全 RAII 包装器。

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a>scoped_lock_read：scoped_lock_read

构造`scoped_lock_read`对象并获取作为读取器在`reader_writer_lock`参数中`_Reader_writer_lock`传递的对象。 如果锁被另一个线程作为编写器持有，或者存在挂起的写入器，则此调用将阻止。

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>参数

*_Reader_writer_lock*<br/>
作为`reader_writer_lock`读取器获取的对象。

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock：：：scoped_lock_read：*scoped_lock_read析构器

销毁`scoped_lock_read`对象并释放其构造函数中提供的锁。

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

尝试获取读取器-写入器锁作为编写器而不阻塞。

### <a name="syntax"></a>语法

```cpp
bool try_lock();
```

### <a name="return-value"></a>返回值

如果获取了锁，则值**为 true**;否则，该值**为 false**。

## <a name="try_lock_read"></a><a name="try_lock_read"></a>try_lock_read

尝试获取读取器-写入器锁作为读取器而不阻塞。

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>返回值

如果获取了锁，则值**为 true**;否则，该值**为 false**。

## <a name="unlock"></a><a name="unlock"></a>解 锁

根据锁定者、读取器或编写器来解锁读取器-写入器锁。

```cpp
void unlock();
```

### <a name="remarks"></a>备注

如果有写入器等待锁，锁的释放将始终按 FIFO 顺序转到下一个写入器。 这个锁偏向于作家，在不断的作家负载下，读者可能饿死。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[critical_section 类](critical-section-class.md)
