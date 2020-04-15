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
ms.openlocfilehash: f3991d217fbc201bd428ed2522a5c4c25e074928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327970"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection 类

此类提供了获取和释放关键节对象的所有权的方法。

## <a name="syntax"></a>语法

```
class CComCriticalSection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCom临界部分：Ccom临界节](#ccomcriticalsection)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom临界部分：：Init](#init)|创建并初始化关键截面对象。|
|[CCom临界部分：锁](#lock)|获取关键部分对象的所有权。|
|[CCom临界部分：：学期](#term)|释放关键部分对象使用的系统资源。|
|[CCom临界部分：解锁](#unlock)|释放关键部分对象的所有权。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CCom临界部分：m_sec](#m_sec)|对象CRITICAL_SECTION。|

## <a name="remarks"></a>备注

`CComCriticalSection`类似于[CComAuto临界节](../../atl/reference/ccomautocriticalsection-class.md)类，只不过您必须显式初始化和释放关键部分。

通常，您可以通过`CComCriticalSection`**类型def**名称["临界节](ccommultithreadmodel-class.md#criticalsection)"使用。 此名称引用`CComCriticalSection`时，使用[CComMultiThreadModel。](../../atl/reference/ccommultithreadmodel-class.md)

有关使用此类比直接调用`Lock``Unlock`更安全的方法，请参阅[CComCritSecLock 类](../../atl/reference/ccomcritseclock-class.md)。

## <a name="requirements"></a>要求

**标题：** atlcore.h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a>CCom临界部分：Ccom临界节

构造函数。

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>备注

将[m_sec](#m_sec)数据成员设置为 NULL。

## <a name="ccomcriticalsectioninit"></a><a name="init"></a>CCom临界部分：：Init

调用 Win32 函数[初始化关键节](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)，它初始化[m_sec](#m_sec)数据成员中包含的关键部分对象。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>返回值

返回S_OK成功、E_OUTOFMEMORY或失败E_FAIL。

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a>CCom临界部分：锁

调用 Win32 函数[Enter关键节](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)，它等待线程可以取得[m_sec](#m_sec)数据成员中包含的关键部分对象的所有权。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>返回值

返回S_OK成功、E_OUTOFMEMORY或失败E_FAIL。

### <a name="remarks"></a>备注

关键节对象必须首先用调用[Init](#init)方法初始化。 当受保护的代码完成执行后，线程必须调用[Unlock](#unlock)以释放关键部分的所有权。

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a>CCom临界部分：m_sec

包含所有`CComCriticalSection`方法使用的关键节对象。

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a>CCom临界部分：：学期

调用 Win32 函数[Delete关键节](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)，它释放数据成员中包含的关键节对象使用的所有资源[m_sec。](#m_sec)

```
HRESULT Term() throw();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

调用`Term`后，关键部分不能再用于同步。

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a>CCom临界部分：解锁

调用 Win32 函数[Leave临界节](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)，它释放[m_sec](#m_sec)数据成员中包含的关键部分对象的所有权。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

要首先获得所有权，线程必须调用[Lock](#lock)方法。 每个调用`Lock`都需要相应的调用以`Unlock`释放关键部分的所有权。

## <a name="see-also"></a>另请参阅

[CComFakeCriticalSection 类](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock 类](../../atl/reference/ccomcritseclock-class.md)
