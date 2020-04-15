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
ms.openlocfilehash: 13141d27592f6f40ea7b0529c61baba2fe83a10a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321122"
---
# <a name="ccomapartment-class"></a>CComApartment 类

此类支持在线程池 EXE 模块中管理单元。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CComApartment
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCom公寓：CCom公寓](#ccomapartment)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom公寓：公寓](#apartment)|标记线程的起始地址。|
|[CCom公寓：：获取锁计数](#getlockcount)|返回线程的当前锁计数。|
|[CCom公寓：锁](#lock)|增加线程的锁计数。|
|[CCom公寓：解锁](#unlock)|撤销线程的锁计数。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CCom公寓：m_dwThreadID](#m_dwthreadid)|包含线程的标识符。|
|[CCom公寓：m_hThread](#m_hthread)|包含线程的句柄。|
|[CCom公寓：m_nLockCnt](#m_nlockcnt)|包含线程的当前锁计数。|

## <a name="remarks"></a>备注

`CComApartment`[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)用于管理线程池 EXE 模块中的单元。 `CComApartment`提供了在线程上增加和递减锁计数的方法。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomapartmentapartment"></a><a name="apartment"></a>CCom公寓：公寓

标记线程的起始地址。

```
DWORD Apartment();
```

### <a name="return-value"></a>返回值

始终为 0。

### <a name="remarks"></a>备注

[在 CComautoThread 模块期间自动设置：：init](../../atl/reference/ccomautothreadmodule-class.md#init)。

## <a name="ccomapartmentccomapartment"></a><a name="ccomapartment"></a>CCom公寓：CCom公寓

构造函数。

```
CComApartment();
```

### <a name="remarks"></a>备注

初始化`CComApartment`数据成员[m_nLockCnt](#m_nlockcnt)和[m_hThread。](#m_hthread)

## <a name="ccomapartmentgetlockcount"></a><a name="getlockcount"></a>CCom公寓：：获取锁计数

返回线程的当前锁计数。

```
LONG GetLockCount();
```

### <a name="return-value"></a>返回值

线程上的锁计数。

## <a name="ccomapartmentlock"></a><a name="lock"></a>CCom公寓：锁

增加线程的锁计数。

```
LONG Lock();
```

### <a name="return-value"></a>返回值

可用于诊断或测试的值。

### <a name="remarks"></a>备注

由[CComAutoThreadModule 调用：锁定](../../atl/reference/ccomautothreadmodule-class.md#lock)。

线程上的锁计数用于统计目的。

## <a name="ccomapartmentm_dwthreadid"></a><a name="m_dwthreadid"></a>CCom公寓：m_dwThreadID

包含线程的标识符。

```
DWORD m_dwThreadID;
```

## <a name="ccomapartmentm_hthread"></a><a name="m_hthread"></a>CCom公寓：m_hThread

包含线程的句柄。

```
HANDLE m_hThread;
```

## <a name="ccomapartmentm_nlockcnt"></a><a name="m_nlockcnt"></a>CCom公寓：m_nLockCnt

包含线程的当前锁计数。

```
LONG m_nLockCnt;
```

## <a name="ccomapartmentunlock"></a><a name="unlock"></a>CCom公寓：解锁

撤销线程的锁计数。

```
LONG Unlock();
```

### <a name="return-value"></a>返回值

可用于诊断或测试的值。

### <a name="remarks"></a>备注

由[CComAutoThreadModule 调用：解锁](../../atl/reference/ccomautothreadmodule-class.md#lock)。

线程上的锁计数用于统计目的。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
