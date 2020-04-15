---
title: CComCachedTearOffObject 类
ms.date: 11/04/2016
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
ms.openlocfilehash: 43f914a52666788fc0bf394d9d14830b28f5adc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321043"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject 类

此类实现["I未知"](/windows/win32/api/unknwn/nn-unknwn-iunknown)的拆解接口。

## <a name="syntax"></a>语法

```
template
<class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>参数

*包含*<br/>
您的拆解类，派生自`CComTearOffObjectBase`您希望拆解对象支持的接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComCachedTearoff对象：：CcomCachedTearoff对象](#ccomcachedtearoffobject)|构造函数。|
|[CComCachedTearoff对象：：_CcomCachedTearoff对象](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComCachedTearOff对象：：添加参考](#addref)|增加`CComCachedTearOffObject`对象的引用计数。|
|[CComCachedTearOff对象：：最终构造](#finalconstruct)|调用`m_contained::FinalConstruct`（分接类） 方法。|
|[CComCachedTearOff对象：：最终发布](#finalrelease)|调用`m_contained::FinalRelease`（分接类） 方法。|
|[CComCachedTearoff对象：：查询接口](#queryinterface)|返回指向`IUnknown``CComCachedTearOffObject`对象的 的指针，或指向拆解类（类`contained`）上的请求接口。|
|[CComCachedTearOff对象：：发布](#release)|取消`CComCachedTearOffObject`对象的引用计数，并在引用计数为 0 时将其销毁。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComCachedTearOff对象：：m_contained](#m_contained)|派生`CComContainedObject`自拆解类（类`contained`）的对象。|

## <a name="remarks"></a>备注

`CComCachedTearOffObject`实现[I 未知](/windows/win32/api/unknwn/nn-unknwn-iunknown)的拆解接口。 `CComTearOffObject`类不同于`CComCachedTearOffObject`具有其自己的`IUnknown`、独立于所有者对象的`IUnknown`（所有者是为其创建撕掉的对象）。 `CComCachedTearOffObject`在其引用计数为零后，`IUnknown`在其上维护自己的引用计数并删除自身。 但是，如果查询其任何拆解接口，所有者对象的引用计数`IUnknown`将递增。

如果实现`CComCachedTearOffObject`分泪的对象已实例化，并且再次查询拆解接口，则重用同一`CComCachedTearOffObject`对象。 相反，如果通过`CComTearOffObject`所有者对象再次查询由 实现的分出接口，则将实例化另一个。 `CComTearOffObject`

所有者类`FinalRelease`必须实现和调用`Release``IUnknown`的 缓存的`CComCachedTearOffObject`。，这将递减其引用计数。 这将导致调用`CComCachedTearOffObject`并`FinalRelease`删除撕裂。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomcachedtearoffobjectaddref"></a><a name="addref"></a>CComCachedTearOff对象：：添加参考

将`CComCachedTearOffObject`对象的引用计数增加 1。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可用于诊断和测试的值。

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="ccomcachedtearoffobject"></a>CComCachedTearoff对象：：CcomCachedTearoff对象

构造函数。

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
[在]指向 的`IUnknown`指针`CComCachedTearOffObject`。

### <a name="remarks"></a>备注

初始化`CComContainedObject`成员[，m_contained](#m_contained)。

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="dtor"></a>CComCachedTearoff对象：：_CcomCachedTearoff对象

析构函数。

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>备注

释放所有分配的资源，并调用[FinalRelease](#finalrelease)。

## <a name="ccomcachedtearoffobjectfinalconstruct"></a><a name="finalconstruct"></a>CComCachedTearOff对象：：最终构造

调用`m_contained::FinalConstruct`创建`m_contained`，`CComContainedObject`< `contained`用于访问撕裂类实现的接口>对象。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ccomcachedtearoffobjectfinalrelease"></a><a name="finalrelease"></a>CComCachedTearOff对象：：最终发布

调用`m_contained::FinalRelease`自由`m_contained`，>`CComContainedObject`< `contained`对象。

```
void FinalRelease();
```

## <a name="ccomcachedtearoffobjectm_contained"></a><a name="m_contained"></a>CComCachedTearOff对象：：m_contained

从拆解类派生的[CComContainedObject 对象](../../atl/reference/ccomcontainedobject-class.md)。

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>参数

*包含*<br/>
[在]您的拆解类，派生自`CComTearOffObjectBase`您希望拆解对象支持的接口。

### <a name="remarks"></a>备注

方法`m_contained`继承用于通过缓存的拆解对象的`QueryInterface`和`FinalConstruct`访问拆解类中的拆解接口。 `FinalRelease`

## <a name="ccomcachedtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComCachedTearoff对象：：查询接口

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]请求的接口的 GUID。

*ppvObject*<br/>
[出]指向*iid*标识的接口指针，如果找不到接口，则指向 NULL 的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

如果请求的接口为`IUnknown`，则返回指向`CComCachedTearOffObject`的 自己的`IUnknown`指针，并递增引用计数。 否则，使用 从`CComObjectRootEx`继承的内部[查询接口](ccomobjectrootex-class.md#internalqueryinterface)方法查询拆解类上的接口。

## <a name="ccomcachedtearoffobjectrelease"></a><a name="release"></a>CComCachedTearOff对象：：发布

将引用计数减为 1，如果引用计数为 0，则删除`CComCachedTearOffObject`对象。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在非调试生成中，始终返回 0。 在调试生成中，返回可用于诊断或测试的值。

## <a name="see-also"></a>另请参阅

[CComTearOffObject 类](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
