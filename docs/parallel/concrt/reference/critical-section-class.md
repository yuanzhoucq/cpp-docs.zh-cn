---
title: critical_section 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6be352c936401ddae6dc3dd825280096e06a7be
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163915"
---
# <a name="criticalsection-class"></a>critical_section 类

明确感知并发运行时的不可重入互斥。

## <a name="syntax"></a>语法

```
class critical_section;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`native_handle_type`|对 `critical_section` 对象的引用。|

### <a name="public-classes"></a>公共类

|名称|描述|
|----------|-----------------|
|[critical_section:: scoped_lock 类](#critical_section__scoped_lock_class)|有关的异常安全的 RAII 包装`critical_section`对象。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[critical_section](#ctor)|构造新的关键部分。|
|[~ critical_section 析构函数](#dtor)|销毁关键部分。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[lock](#lock)|获取此临界区。|
|[native_handle](#native_handle)|返回平台特定本机句柄，如果存在。|
|[try_lock](#try_lock)|尝试获取锁，而不会阻塞。|
|[try_lock_for](#try_lock_for)|尝试在不将锁阻塞特定毫秒数的情况下获取锁。|
|[unlock](#unlock)|解除锁定关键部分。|

## <a name="remarks"></a>备注

有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`critical_section`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> critical_section

构造新的关键部分。

```
critical_section();
```

##  <a name="dtor"></a> ~critical_section

销毁关键部分。

```
~critical_section();
```

### <a name="remarks"></a>备注

应在析构函数运行时不再持有锁。 允许关键节锁析构仍保留会导致未定义的行为。

##  <a name="lock"></a> 锁

获取此临界区。

```
void lock();
```

### <a name="remarks"></a>备注

它通常是更安全，以利用[scoped_lock](#critical_section__scoped_lock_class)构造来获取和释放`critical_section`引发异常的对象安全的方式。

如果锁已由调用的上下文中，保留[improper_lock](improper-lock-class.md)将引发异常。

##  <a name="native_handle"></a> native_handle

返回平台特定本机句柄，如果存在。

```
native_handle_type native_handle();
```

### <a name="return-value"></a>返回值

对关键部分的引用。

### <a name="remarks"></a>备注

一个`critical_section`对象不是与 Windows 操作系统的平台特定本机句相关联。 该方法只需返回到对象本身的引用。

##  <a name="critical_section__scoped_lock_class"></a>  critical_section:: scoped_lock 类

有关的异常安全的 RAII 包装`critical_section`对象。

```
class scoped_lock;
```

##  <a name="critical_section__scoped_lock_ctor"></a> scoped_lock::scoped_lock

构造`scoped_lock`对象，并获取`critical_section`传入的对象`_Critical_section`参数。 如果由另一个线程持有关键节，将阻止此调用。

```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>参数

*_Critical_section*<br/>
若要锁定关键部分。

##  <a name="critical_section__scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock

销毁`scoped_lock`对象并释放其构造函数中提供的关键部分。

```
~scoped_lock();
```

##  <a name="try_lock"></a> try_lock

尝试获取锁，而不会阻塞。

```
bool try_lock();
```

### <a name="return-value"></a>返回值

如果已获取锁，则这 **，则返回 true**; 否则为值**false**。

##  <a name="try_lock_for"></a> try_lock_for

尝试在不将锁阻塞特定毫秒数的情况下获取锁。

```
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>参数

*超时) (_t*<br/>
超时前要等待的毫秒数。

### <a name="return-value"></a>返回值

如果已获取锁，则这 **，则返回 true**; 否则为值**false**。

##  <a name="unlock"></a> 解锁

解除锁定关键部分。

```
void unlock();
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[reader_writer_lock 类](reader-writer-lock-class.md)
