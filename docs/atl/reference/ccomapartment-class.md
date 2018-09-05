---
title: CComApartment 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
dev_langs:
- C++
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39750bcb6b8852e692e52f163e83bb815ecebe97
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755432"
---
# <a name="ccomapartment-class"></a>CComApartment 类

此类提供用于管理线程放入池中 EXE 模块中的单元的支持。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CComApartment
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComApartment::Apartment](#apartment)|标记线程的起始地址。|
|[CComApartment::GetLockCount](#getlockcount)|返回线程的当前锁计数。|
|[CComApartment::Lock](#lock)|线程的锁计数递增。|
|[CComApartment::Unlock](#unlock)|线程的锁计数递减。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|包含线程的标识符。|
|[CComApartment::m_hThread](#m_hthread)|包含线程的句柄。|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|包含线程的当前锁计数。|

## <a name="remarks"></a>备注

`CComApartment` 可供[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)来管理线程放入池中 EXE 模块中的某个单元。 `CComApartment` 提供了方法的递增和递减锁计数在线程上。

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="apartment"></a>  CComApartment::Apartment

标记线程的起始地址。

```
DWORD Apartment();
```

### <a name="return-value"></a>返回值

始终为 0。

### <a name="remarks"></a>备注

过程中自动设置[CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init)。

##  <a name="ccomapartment"></a>  CComApartment::CComApartment

构造函数。

```
CComApartment();
```

### <a name="remarks"></a>备注

初始化`CComApartment`数据成员[m_nLockCnt](#m_nlockcnt)并[m_hThread](#m_hthread)。

##  <a name="getlockcount"></a>  CComApartment::GetLockCount

返回线程的当前锁计数。

```
LONG GetLockCount();
```

### <a name="return-value"></a>返回值

该线程的锁计数。

##  <a name="lock"></a>  CComApartment::Lock

线程的锁计数递增。

```
LONG Lock();
```

### <a name="return-value"></a>返回值

可能是有用的诊断或测试一个值。

### <a name="remarks"></a>备注

调用[CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)。

在线程上的锁计数用于统计目的。

##  <a name="m_dwthreadid"></a>  CComApartment::m_dwThreadID

包含线程的标识符。

```
DWORD m_dwThreadID;
```

##  <a name="m_hthread"></a>  CComApartment::m_hThread

包含线程的句柄。

```
HANDLE m_hThread;
```

##  <a name="m_nlockcnt"></a>  CComApartment::m_nLockCnt

包含线程的当前锁计数。

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>  CComApartment::Unlock

线程的锁计数递减。

```
LONG Unlock();
```

### <a name="return-value"></a>返回值

可能是有用的诊断或测试一个值。

### <a name="remarks"></a>备注

调用[CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock)。

在线程上的锁计数用于统计目的。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
