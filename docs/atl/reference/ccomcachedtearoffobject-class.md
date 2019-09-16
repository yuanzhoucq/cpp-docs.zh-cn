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
ms.openlocfilehash: d993a349d38342bda30a83dfdbe25577953799b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497538"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject 类

此类为拆卸接口实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。

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

*独立*<br/>
从`CComTearOffObjectBase`派生的类，以及要使其支持您的脱离对象的接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|构造函数。|
|[CComCachedTearOffObject：： ~ CComCachedTearOffObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|递增`CComCachedTearOffObject`对象的引用计数。|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|`m_contained::FinalConstruct`调用（脱离类的方法）。|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|`m_contained::FinalRelease`调用（脱离类的方法）。|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|返回指向`IUnknown` `CComCachedTearOffObject`对象的的指针，或返回到脱离类（类`contained`）上请求的接口的指针。|
|[CComCachedTearOffObject::Release](#release)|递减`CComCachedTearOffObject`对象的引用计数，并在引用计数为0时将其销毁。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|派生`CComContainedObject`自脱离类（类`contained`）的对象。|

## <a name="remarks"></a>备注

`CComCachedTearOffObject`为脱离接口实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。 此类与的`CComTearOffObject`不同之`CComCachedTearOffObject`处在于， `IUnknown`它具有其自己的独立于`IUnknown`所有者对象的（所有者是要为其创建撕的对象）。 `CComCachedTearOffObject`在其`IUnknown`引用计数为零时，维护其自己的引用计数，并删除自身。 但是，如果查询其任何脱离接口，所有者对象的`IUnknown`引用计数将递增。

如果实现了分离的`CComCachedTearOffObject` 对象已经实例化，并再次查询了脱离接口，则重用相同的对象。`CComCachedTearOffObject` 与此相反，如果通过所有者对象再次查询由实现`CComTearOffObject`的脱离接口，则会实例化另一个`CComTearOffObject` 。

所有者`FinalRelease`类必须`Release` 在为`IUnknown`缓存的中实现并调用，这将减少其引用计数。`CComCachedTearOffObject` 这将导致`CComCachedTearOffObject` `FinalRelease`调用，并删除删除。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="addref"></a>CComCachedTearOffObject：： AddRef

将`CComCachedTearOffObject`对象的引用计数递增1。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可能对诊断和测试有用的值。

##  <a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject

构造函数。

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
中指向`IUnknown` 的`CComCachedTearOffObject`的指针。

### <a name="remarks"></a>备注

初始化`CComContainedObject`成员 [m_contained](#m_contained)。

##  <a name="dtor"></a>CComCachedTearOffObject：： ~ CComCachedTearOffObject

析构函数。

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源，并调用[FinalRelease](#finalrelease)。

##  <a name="finalconstruct"></a>CComCachedTearOffObject：： FinalConstruct

要`m_contained::FinalConstruct`创建`CComContainedObject` >的< 调用，该`contained`对象用于访问由你的撕开类实现的接口。 `m_contained`

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

`m_contained::FinalRelease` `CComContainedObject`调用（> 对象）< 。 `m_contained` `contained`

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComCachedTearOffObject::m_contained

一个派生自你的[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)类的对象。

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>参数

*独立*<br/>
中从`CComTearOffObjectBase`派生的类，以及要使其支持您的脱离对象的接口。

### <a name="remarks"></a>备注

方法`m_contained`继承用于通过缓存的撕出对象的`QueryInterface`、 `FinalConstruct`和`FinalRelease`来访问你的脱离类中的脱离接口。

##  <a name="queryinterface"></a>CComCachedTearOffObject：： QueryInterface

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*iid*<br/>
中所请求的接口的 GUID。

*ppvObject*<br/>
弄指向由*iid*标识的接口指针的指针; 如果找不到接口，则为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果请求的接口为`IUnknown`，则返回一个指向自身`CComCachedTearOffObject` `IUnknown`的指针并递增引用计数。 否则，使用从`CComObjectRootEx`继承的[InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)方法在您的脱离类上查询接口。

##  <a name="release"></a>CComCachedTearOffObject：： Release

将引用计数递减1，如果引用计数为0，则删除`CComCachedTearOffObject`对象。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在非调试版本中，始终返回0。 在调试版本中，将返回一个值，该值对于诊断或测试可能很有用。

## <a name="see-also"></a>请参阅

[CComTearOffObject 类](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
