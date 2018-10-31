---
title: CComCriticalSection 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
dev_langs:
- C++
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ebabc2d200047acec458c4a29603cc6aee5a589
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076823"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection 类

此类提供方法用于获取并释放关键节对象的所有权。

## <a name="syntax"></a>语法

```
class CComCriticalSection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComCriticalSection::Init](#init)|创建并初始化关键部分对象。|
|[CComCriticalSection::Lock](#lock)|获取关键节对象的所有权。|
|[CComCriticalSection::Term](#term)|释放系统资源使用的关键部分对象。|
|[CComCriticalSection::Unlock](#unlock)|释放关键节对象的所有权。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|CRITICAL_SECTION 对象。|

## <a name="remarks"></a>备注

`CComCriticalSection` 类似于类[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)，只不过必须显式初始化并释放关键节。

通常情况下，使用`CComCriticalSection`通过**typedef**名称[CriticalSection](ccommultithreadmodel-class.md#criticalsection)。 此名称引用`CComCriticalSection`时[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)正在使用。

请参阅[CComCritSecLock 类](../../atl/reference/ccomcritseclock-class.md)以使用相对于调用此类更安全的方式`Lock`和`Unlock`直接。

## <a name="requirements"></a>要求

**标头：** atlcore.h

##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection

构造函数。

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>备注

集[m_sec](#m_sec)数据成员为 NULL。

##  <a name="init"></a>  CComCriticalSection::Init

调用 Win32 函数[InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection)，其中初始化中包含的关键部分对象[m_sec](#m_sec)数据成员。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>返回值

如果成功，E_OUTOFMEMORY 或 E_FAIL 失败时返回 S_OK。

##  <a name="lock"></a>  CComCriticalSection::Lock

调用 Win32 函数[EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection)，哪个等待线程可以获得中包含的关键部分对象的所有权[m_sec](#m_sec)数据成员。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>返回值

如果成功，E_OUTOFMEMORY 或 E_FAIL 失败时返回 S_OK。

### <a name="remarks"></a>备注

首先必须使用对的调用初始化关键部分对象[Init](#init)方法。 当受保护的代码执行完成后时，必须调用线程[解锁](#unlock)释放关键节的所有权。

##  <a name="m_sec"></a>  CComCriticalSection::m_sec

包含一个关键部分对象，由所有`CComCriticalSection`方法。

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>  CComCriticalSection::Term

调用 Win32 函数[DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection)，以释放使用中包含的关键部分对象的所有资源[m_sec](#m_sec)数据成员。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

一次`Term`已调用的关键部分不能再用于同步。

##  <a name="unlock"></a>  CComCriticalSection::Unlock

调用 Win32 函数[LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection)，该版本中包含的关键部分对象的所有权[m_sec](#m_sec)数据成员。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要首先获取所有权，线程必须调用[锁](#lock)方法。 每次调用`Lock`需要相应地调用`Unlock`释放关键节的所有权。

## <a name="see-also"></a>请参阅

[CComFakeCriticalSection 类](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock 类](../../atl/reference/ccomcritseclock-class.md)
