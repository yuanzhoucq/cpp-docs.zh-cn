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
ms.openlocfilehash: cb0dc440fc0e79e0023b5fbd6e4ca2345d031d3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327368"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection 类

此类提供了获取和释放关键节对象的所有权的方法。

## <a name="syntax"></a>语法

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComSafe 删除关键部分：：CcomSafe删除关键部分](#ccomsafedeletecriticalsection)|构造函数。|
|[CComSafe 删除关键部分：：_CcomSafe删除关键部分](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComSafe 删除关键部分：：Init](#init)|创建并初始化关键截面对象。|
|[CComSafe 删除关键部分：：锁定](#lock)|获取关键部分对象的所有权。|
|[CComSafe 删除关键部分：：术语](#term)|释放关键部分对象使用的系统资源。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_bInitialized](#m_binitialized)|标记内部`CRITICAL_SECTION`对象是否已初始化。|

## <a name="remarks"></a>备注

`CComSafeDeleteCriticalSection`派生自类[CCom临界节](../../atl/reference/ccomcriticalsection-class.md)。 然而，`CComSafeDeleteCriticalSection`通过[CCom临界部分](../../atl/reference/ccomcriticalsection-class.md)提供了额外的安全机制。

当实例`CComSafeDeleteCriticalSection`超出范围或从内存中显式删除时，如果基础关键部分对象仍然有效，则会自动清理该对象。 此外，如果基础关键节对象尚未分配或已经从内存中释放[，CComSafeDelete关键节：术语](#term)方法将正常退出。

有关关键部分帮助器类的详细信息，请参阅[CCom临界节](../../atl/reference/ccomcriticalsection-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CCom临界部分](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>要求

**标题：** atlcore.h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a>CComSafe 删除关键部分：：CcomSafe删除关键部分

构造函数。

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>备注

将[m_bInitialized](#m_binitialized)数据成员设置为 FALSE。

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a>CComSafe 删除关键部分：：_CcomSafe删除关键部分

析构函数。

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>备注

如果m_bInitialized数据`CRITICAL_SECTION`成员设置为 TRUE，[m_bInitialized](#m_binitialized)则从内存中释放内部对象。

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a>CComSafe 删除关键部分：：Init

调用[Init](/visualstudio/debugger/init)的基类实现，如果成功[，m_bInitialized](#m_binitialized)将设置为 TRUE。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>返回值

返回[CCom临界节的结果：：Init](../../atl/reference/ccomcriticalsection-class.md#init)。

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a>CComSafe 删除关键部分：：锁定

调用[Lock](ccomcriticalsection-class.md#lock)的基类实现。

```
HRESULT Lock();
```

### <a name="return-value"></a>返回值

返回[CCom临界节的结果：锁定](../../atl/reference/ccomcriticalsection-class.md#lock)。

### <a name="remarks"></a>备注

此方法假定[m_bInitialized](#m_binitialized)数据成员在输入时设置为 TRUE。 如果未满足此条件，则在调试生成中生成断言。

有关函数行为的详细信息，请参阅[CCom临界节：：锁定](../../atl/reference/ccomcriticalsection-class.md#lock)。

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a>CComSafe 删除关键部分：：m_bInitialized

标记内部`CRITICAL_SECTION`对象是否已初始化。

```
bool m_bInitialized;
```

### <a name="remarks"></a>备注

数据`m_bInitialized`成员用于跟踪与`CRITICAL_SECTION`[CComSafeDelete关键节](../../atl/reference/ccomsafedeletecriticalsection-class.md)类关联的基础对象的有效性。 如果未将此`CRITICAL_SECTION`标志设置为 TRUE，则不会尝试从内存中释放基础对象。

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a>CComSafe 删除关键部分：：术语

调用[CCom临界节的基本类实现：：](../../atl/reference/ccomcriticalsection-class.md#term)如果内部`CRITICAL_SECTION`对象有效，则术语。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>返回值

返回[CCom临界节的结果：：术语](../../atl/reference/ccomcriticalsection-class.md#term)，或者S_OK如果[m_bInitialized](#m_binitialized)在输入时设置为 FALSE。

### <a name="remarks"></a>备注

即使内部`CRITICAL_SECTION`对象无效，也是安全的调用此方法。 如果[m_bInitialized](#m_binitialized)数据成员设置为 TRUE，则此类的析构函数将调用此方法。

## <a name="see-also"></a>另请参阅

[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
