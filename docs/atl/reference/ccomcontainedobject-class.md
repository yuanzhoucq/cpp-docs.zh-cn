---
title: CComContainedObject 类
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: 289174fbfc61b0bbca65233fe24d93537627e17d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492568"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject 类

此类实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)通过将委派给所有者对象`IUnknown`。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>参数

*基本*<br/>
您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|构造函数。 初始化所有者对象的成员指针`IUnknown`。|
|[CComContainedObject:: ~ CComContainedObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|递增所有者对象的引用计数。|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|检索所有者对象`IUnknown`。|
|[CComContainedObject::QueryInterface](#queryinterface)|检索在所有者对象上请求的接口指针。|
|[CComContainedObject::Release](#release)|递减引用计数在所有者对象上。|

## <a name="remarks"></a>备注

使用 ATL`CComContainedObject`类中[CComAggObject](../../atl/reference/ccomaggobject-class.md)， [CComPolyObject](../../atl/reference/ccompolyobject-class.md)，并且[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)。 `CComContainedObject` 实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)通过将委派给所有者对象`IUnknown`。 （所有者为外部对象的聚合或为其创建分离式接口的对象）。`CComContainedObject`调用`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，并`OuterRelease`、 通过所有继承`Base`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComContainedObject`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="addref"></a>  CComContainedObject::AddRef

递增所有者对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可能是有用的诊断或测试一个值。

##  <a name="ccomcontainedobject"></a>  CComContainedObject::CComContainedObject

构造函数。

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
[in]所有者对象`IUnknown`。

### <a name="remarks"></a>备注

集`m_pOuterUnknown`成员指针 (通过继承`Base`类) 向*pv*。

##  <a name="dtor"></a>  CComContainedObject:: ~ CComContainedObject

析构函数。

```
~CComContainedObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

##  <a name="getcontrollingunknown"></a>  CComContainedObject::GetControllingUnknown

返回`m_pOuterUnknown`成员指针 (通过继承*Base*类)，它持有所有者对象`IUnknown`。

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>返回值

所有者对象`IUnknown`。

### <a name="remarks"></a>备注

此方法可能是虚拟如果`Base`已声明[DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown)宏。

##  <a name="queryinterface"></a>  CComContainedObject::QueryInterface

检索在所有者对象上请求的接口指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]所请求的接口的标识符。

*ppvObject*<br/>
[out]通过标识的接口指针的指针*iid*。 如果该对象不支持此接口， *ppvObject*设置为 NULL。

*pp*<br/>
[out]由类型标识的接口指针的指针`Q`。 如果该对象不支持此接口， *pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="release"></a>  CComContainedObject::Release

递减引用计数在所有者对象上。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试版本中，`Release`返回一个值，可能是有用的诊断或测试。 在非调试版本中，`Release`始终返回 0。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
