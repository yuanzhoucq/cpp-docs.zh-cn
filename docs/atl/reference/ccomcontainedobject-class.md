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
ms.openlocfilehash: c5e2fa64cc0938e632a37eac7dd1d6e9111c3d98
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497324"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject 类

此类通过委托给所有者对象的`IUnknown`来实现 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>参数

*基座*<br/>
从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)派生的类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|构造函数。 初始化指向所有者对象的`IUnknown`成员指针。|
|[CComContainedObject：： ~ CComContainedObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|递增所有者对象的引用计数。|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|检索所有者对象的`IUnknown`。|
|[CComContainedObject::QueryInterface](#queryinterface)|检索指向所有者对象上所请求的接口的指针。|
|[CComContainedObject::Release](#release)|递减所有者对象的引用计数。|

## <a name="remarks"></a>备注

ATL 在`CComContainedObject`类[CComAggObject](../../atl/reference/ccomaggobject-class.md)、 [CComPolyObject](../../atl/reference/ccompolyobject-class.md)和[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)中使用。 `CComContainedObject`通过委托给所有者对象的`IUnknown`来实现 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。 （所有者是聚合的外部对象或正在为其创建脱离接口的对象。）`CComContainedObject` 调用`CComObjectRootEx` 、`OuterRelease`和，它们都通过`Base`继承。 `OuterAddRef` `OuterQueryInterface`

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComContainedObject`

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="addref"></a>CComContainedObject：： AddRef

递增所有者对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可能对诊断或测试有用的值。

##  <a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject

构造函数。

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
中所有者对象的`IUnknown`。

### <a name="remarks"></a>备注

将成员指针（ `Base`通过类继承）设置为*pv。* `m_pOuterUnknown`

##  <a name="dtor"></a>CComContainedObject：： ~ CComContainedObject

析构函数。

```
~CComContainedObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

##  <a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown

返回保存所有者对象的`IUnknown` 成员指针（通过基类继承`m_pOuterUnknown` ）。

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>返回值

所有者对象的`IUnknown`。

### <a name="remarks"></a>备注

如果`Base`已声明[DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown)宏，则此方法可能是虚拟的。

##  <a name="queryinterface"></a>CComContainedObject：： QueryInterface

检索指向所有者对象上所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>参数

*iid*<br/>
中所请求的接口的标识符。

*ppvObject*<br/>
弄指向由*iid*标识的接口指针的指针。 如果对象不支持此接口，则将*ppvObject*设置为 NULL。

*pp*<br/>
弄指向由类型`Q`标识的接口指针的指针。 如果对象不支持此接口，则*pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="release"></a>CComContainedObject：： Release

递减所有者对象的引用计数。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试版本中`Release` ，将返回一个值，该值对于诊断或测试可能很有用。 在非调试版本中， `Release`始终返回0。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
