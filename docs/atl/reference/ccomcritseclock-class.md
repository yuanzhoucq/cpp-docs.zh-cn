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
ms.openlocfilehash: 24d141c5b0ec703feadcd7db96da33f9de940dda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327954"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock 类

此类提供锁定和解锁关键截面对象的方法。

## <a name="syntax"></a>语法

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>参数

*TLock*<br/>
要锁定和解锁的对象。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComCritSecLock：CComCritSecLock](#ctor)|构造函数。|
|[CComCritSecLock：*CComCritSecLock](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComCritSecLock：锁定](#lock)|调用此方法以锁定关键截面对象。|
|[CComCritSecLock：解锁](#unlock)|调用此方法以解锁关键截面对象。|

## <a name="remarks"></a>备注

使用此类以比[CCom临界节类](../../atl/reference/ccomcriticalsection-class.md)或[CComAuto临界节类](../../atl/reference/ccomautocriticalsection-class.md)更安全的方式锁定和解锁对象。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock：CComCritSecLock

构造函数。

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>参数

*cs*<br/>
关键截面对象。

*b 初始锁定*<br/>
初始锁定状态 **：true**表示锁定。

### <a name="remarks"></a>备注

初始化关键截面对象。

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock：*CComCritSecLock

析构函数。

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>备注

解锁关键截面对象。

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock：锁定

调用此方法以锁定关键截面对象。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>返回值

如果对象已成功锁定，则返回S_OK，或者失败时出现 HRESULT 错误。

### <a name="remarks"></a>备注

如果对象已锁定，则调试生成中将发生 ASSERT 错误。

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock：解锁

调用此方法以解锁关键截面对象。

```
void Unlock() throw();
```

### <a name="remarks"></a>备注

如果对象已解锁，则调试生成中将发生 ASSERT 错误。

## <a name="see-also"></a>另请参阅

[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection 类](../../atl/reference/ccomautocriticalsection-class.md)
