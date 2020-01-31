---
title: CComSafeDeleteCriticalSection 类
ms.date: 11/04/2016
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
ms.openlocfilehash: da83bc5d0c2ebb79aee07f30069144368169fc26
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821644"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection 类

此类提供用于获取和释放关键节对象的所有权的方法。

## <a name="syntax"></a>语法

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|构造函数。|
|[CComSafeDeleteCriticalSection：： ~ CComSafeDeleteCriticalSection](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|Name|描述|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|创建并初始化一个临界区对象。|
|[CComSafeDeleteCriticalSection::Lock](#lock)|获取临界区对象的所有权。|
|[CComSafeDeleteCriticalSection::Term](#term)|释放由临界区对象使用的系统资源。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_bInitialized](#m_binitialized)|标记内部 `CRITICAL_SECTION` 对象是否已初始化。|

## <a name="remarks"></a>备注

`CComSafeDeleteCriticalSection` 派生自类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 但是，`CComSafeDeleteCriticalSection` 通过[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)提供其他安全机制。

当 `CComSafeDeleteCriticalSection` 的实例超出范围或从内存中显式删除时，将自动清除基础临界区对象（如果它仍有效）。 此外，如果基础临界区对象尚未分配或已从内存中释放，则[CComSafeDeleteCriticalSection：： Term](#term)方法将正常退出。

有关关键部分帮助器类的详细信息，请参阅[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 。

## <a name="inheritance-hierarchy"></a>繼承階層

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>需求

**标头：** atlcore

##  <a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

构造函数。

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>备注

将[m_bInitialized](#m_binitialized)数据成员设置为 FALSE。

##  <a name="dtor"></a>CComSafeDeleteCriticalSection：： ~ CComSafeDeleteCriticalSection

析构函数。

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>备注

如果[m_bInitialized](#m_binitialized)数据成员设置为 TRUE，则从内存中释放内部 `CRITICAL_SECTION` 对象。

##  <a name="init"></a>CComSafeDeleteCriticalSection：： Init

调用[Init](/visualstudio/debugger/init)的基类实现，如果成功，则将[M_BINITIALIZED](#m_binitialized)设置为 TRUE。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>返回值

返回[CComCriticalSection：： Init](../../atl/reference/ccomcriticalsection-class.md#init)的结果。

##  <a name="lock"></a>CComSafeDeleteCriticalSection：： Lock

调用[锁](ccomcriticalsection-class.md#lock)的基类实现。

```
HRESULT Lock();
```

### <a name="return-value"></a>返回值

返回[CComCriticalSection：： Lock](../../atl/reference/ccomcriticalsection-class.md#lock)的结果。

### <a name="remarks"></a>备注

此方法假定在输入时将[m_bInitialized](#m_binitialized)数据成员设置为 TRUE。 如果不满足此条件，则会在调试版本中生成断言。

有关函数行为的详细信息，请参阅[CComCriticalSection：： Lock](../../atl/reference/ccomcriticalsection-class.md#lock)。

##  <a name="m_binitialized"></a>CComSafeDeleteCriticalSection：： m_bInitialized

标记内部 `CRITICAL_SECTION` 对象是否已初始化。

```
bool m_bInitialized;
```

### <a name="remarks"></a>备注

`m_bInitialized` 数据成员用于跟踪与[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)类关联的基础 `CRITICAL_SECTION` 对象的有效性。 如果此标志未设置为 TRUE，则将不会尝试从内存中释放基础 `CRITICAL_SECTION` 对象。

##  <a name="term"></a>CComSafeDeleteCriticalSection：： Term

如果内部 `CRITICAL_SECTION` 对象有效，将调用[CComCriticalSection：： Term](../../atl/reference/ccomcriticalsection-class.md#term)的基类实现。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>返回值

返回[CComCriticalSection：： Term](../../atl/reference/ccomcriticalsection-class.md#term)的结果，如果在输入时将[M_BINITIALIZED](#m_binitialized)设置为 FALSE，则返回 S_OK。

### <a name="remarks"></a>备注

即使内部 `CRITICAL_SECTION` 对象无效，也可以安全地调用此方法。 如果[m_bInitialized](#m_binitialized)数据成员设置为 TRUE，则此类的析构函数将调用此方法。

## <a name="see-also"></a>另请参阅

[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
