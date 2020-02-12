---
title: critical_section 类
ms.date: 11/04/2016
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
ms.openlocfilehash: aef3ae6100133374cb89098f118c447effafd840
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143090"
---
# <a name="critical_section-class"></a>critical_section 类

明确感知并发运行时的不可重入互斥。

## <a name="syntax"></a>语法

```cpp
class critical_section;
```

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`native_handle_type`|对 `critical_section` 对象的引用。|

### <a name="public-classes"></a>公共类

|名称|说明|
|----------|-----------------|
|[critical_section：： scoped_lock 类](#critical_section__scoped_lock_class)|`critical_section` 对象的异常安全 RAII 包装。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[critical_section](#ctor)|构造一个新的关键部分。|
|[~ critical_section 析构函数](#dtor)|销毁关键部分。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[lock](#lock)|获取此关键部分。|
|[native_handle](#native_handle)|返回一个特定于平台的本机句柄（如果存在）。|
|[try_lock](#try_lock)|尝试在不阻止的情况下获取锁。|
|[try_lock_for](#try_lock_for)|尝试在不将锁阻塞特定毫秒数的情况下获取锁。|
|[unlock](#unlock)|解锁关键部分。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`critical_section`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>critical_section

构造一个新的关键部分。

```cpp
critical_section();
```

## <a name="dtor"></a>~ critical_section

销毁关键部分。

```cpp
~critical_section();
```

### <a name="remarks"></a>备注

当析构函数运行时，应不再持有锁。 允许具有锁定的临界区销毁仍会导致未定义的行为。

## <a name="lock"></a>住

获取此关键部分。

```cpp
void lock();
```

### <a name="remarks"></a>备注

通常，使用[scoped_lock](#critical_section__scoped_lock_class)构造以异常安全的方式获取和释放 `critical_section` 对象通常更安全。

如果锁已由调用上下文持有，则会引发[improper_lock](improper-lock-class.md)异常。

## <a name="native_handle"></a>native_handle

返回一个特定于平台的本机句柄（如果存在）。

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>返回值

对临界区的引用。

### <a name="remarks"></a>备注

`critical_section` 对象不与 Windows 操作系统的特定于平台的本机句柄关联。 方法只返回对对象本身的引用。

## <a name="critical_section__scoped_lock_class"></a>critical_section：： scoped_lock 类

`critical_section` 对象的异常安全 RAII 包装。

```cpp
class scoped_lock;
```

## <a name="critical_section__scoped_lock_ctor"></a>scoped_lock：： scoped_lock

构造 `scoped_lock` 对象并获取 `_Critical_section` 参数中传递的 `critical_section` 对象。 如果由另一个线程持有临界区，则此调用将被阻止。

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>参数

*_Critical_section*<br/>
要锁定的临界区。

## <a name="critical_section__scoped_lock_dtor"></a>scoped_lock：： ~ scoped_lock

销毁 `scoped_lock` 对象并释放其构造函数中提供的关键部分。

```cpp
~scoped_lock();
```

## <a name="try_lock"></a>try_lock

尝试在不阻止的情况下获取锁。

```cpp
bool try_lock();
```

### <a name="return-value"></a>返回值

如果已获取锁，则值为**true**;否则，值**为 false**。

## <a name="try_lock_for"></a>try_lock_for

尝试在不将锁阻塞特定毫秒数的情况下获取锁。

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>参数

*_Timeout*<br/>
超时前要等待的毫秒数。

### <a name="return-value"></a>返回值

如果已获取锁，则值为**true**;否则，值**为 false**。

## <a name="unlock"></a>解锁

解锁关键部分。

```cpp
void unlock();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[reader_writer_lock 类](reader-writer-lock-class.md)
