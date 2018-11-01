---
title: CComCritSecLock 类
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: e0f68f48867510c270c7c69e325a796f274198d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606994"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock 类

此类提供用于锁定和解锁关键部分对象的方法。

## <a name="syntax"></a>语法

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>参数

*TLock*<br/>
要锁定和解锁的对象。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|构造函数。|
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|调用此方法以锁定关键部分对象。|
|[CComCritSecLock::Unlock](#unlock)|调用此方法以解除对锁定关键部分对象。|

## <a name="remarks"></a>备注

此类用于锁定和解锁对象比以更安全方式与[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)或[CComAutoCriticalSection 类](../../atl/reference/ccomautocriticalsection-class.md)。

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock

构造函数。

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>参数

*cs*<br/>
关键部分对象中。

*bInitialLock*<br/>
初始的锁定状态： **，则返回 true**锁定的方法。

### <a name="remarks"></a>备注

初始化关键部分对象。

##  <a name="dtor"></a>  CComCritSecLock:: ~ CComCritSecLock

析构函数。

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>备注

解除锁定关键部分对象。

##  <a name="lock"></a>  CComCritSecLock::Lock

调用此方法以锁定关键部分对象。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>返回值

如果对象已成功锁定，则为 S_OK 或错误的 HRESULT 返回失败。

### <a name="remarks"></a>备注

如果对象已锁定，在调试版本中将会出错断言。

##  <a name="unlock"></a>  CComCritSecLock::Unlock

调用此方法以解除对锁定关键部分对象。

```
void Unlock() throw();
```

### <a name="remarks"></a>备注

如果该对象已被解锁，断言错误会在调试版本中。

## <a name="see-also"></a>请参阅

[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection 类](../../atl/reference/ccomautocriticalsection-class.md)
