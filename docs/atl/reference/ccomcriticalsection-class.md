---
title: CComCriticalSection 类
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: ee4ce32ed4ae04bc3b390af5cf104b8a0af599f8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497277"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection 类

此类提供用于获取和释放关键节对象的所有权的方法。

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
|[CComCriticalSection::Init](#init)|创建并初始化一个临界区对象。|
|[CComCriticalSection::Lock](#lock)|获取临界区对象的所有权。|
|[CComCriticalSection::Term](#term)|释放由临界区对象使用的系统资源。|
|[CComCriticalSection::Unlock](#unlock)|释放临界区对象的所有权。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|一个 CRITICAL_SECTION 对象。|

## <a name="remarks"></a>备注

`CComCriticalSection`类似于类[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), 不同之处在于必须显式初始化并释放临界区。

通常, 使用`CComCriticalSection` [CriticalSection](ccommultithreadmodel-class.md#criticalsection)的**typedef**名称。 当使用`CComCriticalSection` [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)时, 此名称引用。

请参阅[CComCritSecLock 类](../../atl/reference/ccomcritseclock-class.md), 以了解使用此类比直接调用`Lock`和`Unlock`直接的方法更安全。

## <a name="requirements"></a>要求

**标头:** atlcore

##  <a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection

构造函数。

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>备注

将[m_sec](#m_sec)数据成员设置为 NULL。

##  <a name="init"></a>CComCriticalSection:: Init

调用 Win32 函数[InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), 该函数初始化[m_sec](#m_sec)数据成员中包含的临界区对象。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK; 如果失败, 则返回 E_OUTOFMEMORY 或 E_FAIL。

##  <a name="lock"></a>CComCriticalSection:: Lock

调用 Win32 函数[EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), 该函数将等待, 直到线程可以获得[m_sec](#m_sec)数据成员中包含的临界区对象的所有权。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK; 如果失败, 则返回 E_OUTOFMEMORY 或 E_FAIL。

### <a name="remarks"></a>备注

必须首先使用对[Init](#init)方法的调用初始化临界区对象。 当受保护的代码执行完毕后, 线程必须调用[Unlock](#unlock)以释放关键部分的所有权。

##  <a name="m_sec"></a>CComCriticalSection::m_sec

包含由所有`CComCriticalSection`方法使用的临界区对象。

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>CComCriticalSection:: Term

调用 Win32 函数[DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), 该函数释放[m_sec](#m_sec)数据成员中包含的临界区对象所使用的所有资源。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

调用`Term`后, 关键部分将无法再用于同步。

##  <a name="unlock"></a>CComCriticalSection:: Unlock

调用 Win32 函数[LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), 该函数释放[m_sec](#m_sec)数据成员中包含的临界区对象的所有权。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

若要首先获取所有权, 线程必须调用[Lock](#lock)方法。 对`Lock`的每个调用都需要对`Unlock`的调用, 以释放关键部分的所有权。

## <a name="see-also"></a>请参阅

[CComFakeCriticalSection 类](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock 类](../../atl/reference/ccomcritseclock-class.md)
