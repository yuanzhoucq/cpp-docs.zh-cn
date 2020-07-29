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
ms.openlocfilehash: fd2904f67d84db42d6b35aa4e505b063d6ea9a9f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224287"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock 类

此类提供用于锁定和解锁临界区对象的方法。

## <a name="syntax"></a>语法

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>参数

*TLock*<br/>
要锁定和解除锁定的对象。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|构造函数。|
|[CComCritSecLock：： ~ CComCritSecLock](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CComCritSecLock：： Lock](#lock)|调用此方法可锁定临界区对象。|
|[CComCritSecLock：： Unlock](#unlock)|调用此方法可以解锁临界区对象。|

## <a name="remarks"></a>备注

使用此类可通过比[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)或[CComAutoCriticalSection 类](../../atl/reference/ccomautocriticalsection-class.md)更安全的方式锁定和解除锁定对象。

## <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock::CComCritSecLock

构造函数。

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>参数

*站*<br/>
临界区对象。

*bInitialLock*<br/>
初始锁定状态： **`true`** 表示锁定。

### <a name="remarks"></a>备注

初始化临界区对象。

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock：： ~ CComCritSecLock

析构函数。

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>备注

解锁临界区对象。

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock：： Lock

调用此方法可锁定临界区对象。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>返回值

如果对象已成功锁定，则返回 S_OK; 否则，返回错误 HRESULT。

### <a name="remarks"></a>备注

如果对象已锁定，则会在调试版本中发生断言错误。

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock：： Unlock

调用此方法可以解锁临界区对象。

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>备注

如果已解除锁定对象，则会在调试版本中发生断言错误。

## <a name="see-also"></a>另请参阅

[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection 类](../../atl/reference/ccomautocriticalsection-class.md)
