---
title: CComApartment 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
ms.openlocfilehash: 5f4c7fc356e61210e9b99bf9989b1bb3f0abc98a
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821670"
---
# <a name="ccomapartment-class"></a>CComApartment 类

此类提供对在线程池 EXE 模块中管理单元的支持。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CComApartment
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|构造函数。|

### <a name="public-methods"></a>公共方法

|Name|描述|
|----------|-----------------|
|[CComApartment::Apartment](#apartment)|标记线程的起始地址。|
|[CComApartment::GetLockCount](#getlockcount)|返回线程的当前锁计数。|
|[CComApartment::Lock](#lock)|递增线程的锁计数。|
|[CComApartment::Unlock](#unlock)|减小线程的锁计数。|

### <a name="public-data-members"></a>公共数据成员

|Name|描述|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|包含线程的标识符。|
|[CComApartment::m_hThread](#m_hthread)|包含线程的句柄。|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|包含线程的当前锁计数。|

## <a name="remarks"></a>备注

[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)使用 `CComApartment` 在线程池 EXE 模块中管理单元。 `CComApartment` 提供了用于递增和递减线程上的锁计数的方法。

## <a name="requirements"></a>需求

**标头：** atlbase。h

##  <a name="apartment"></a>CComApartment：：公寓

标记线程的起始地址。

```
DWORD Apartment();
```

### <a name="return-value"></a>返回值

始终为0。

### <a name="remarks"></a>备注

在[CComAutoThreadModule：： Init](../../atl/reference/ccomautothreadmodule-class.md#init)期间自动设置。

##  <a name="ccomapartment"></a>CComApartment::CComApartment

构造函数。

```
CComApartment();
```

### <a name="remarks"></a>备注

初始化[m_nLockCnt](#m_nlockcnt)和[m_hThread](#m_hthread)的 `CComApartment` 数据成员。

##  <a name="getlockcount"></a>  CComApartment::GetLockCount

返回线程的当前锁计数。

```
LONG GetLockCount();
```

### <a name="return-value"></a>返回值

线程的锁计数。

##  <a name="lock"></a>CComApartment：： Lock

递增线程的锁计数。

```
LONG Lock();
```

### <a name="return-value"></a>返回值

可能对诊断或测试有用的值。

### <a name="remarks"></a>备注

由[CComAutoThreadModule：： Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)调用。

线程上的锁计数用于统计目的。

##  <a name="m_dwthreadid"></a>  CComApartment::m_dwThreadID

包含线程的标识符。

```
DWORD m_dwThreadID;
```

##  <a name="m_hthread"></a>CComApartment：： m_hThread

包含线程的句柄。

```
HANDLE m_hThread;
```

##  <a name="m_nlockcnt"></a>CComApartment：： m_nLockCnt

包含线程的当前锁计数。

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>CComApartment：： Unlock

减小线程的锁计数。

```
LONG Unlock();
```

### <a name="return-value"></a>返回值

可能对诊断或测试有用的值。

### <a name="remarks"></a>备注

由[CComAutoThreadModule：： Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock)调用。

线程上的锁计数用于统计目的。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
