---
title: CComObject 类
ms.date: 11/04/2016
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
ms.openlocfilehash: 57c054915ce98dd8cff6bb772cdd40f4b0f2b768
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660468"
---
# <a name="ccomobject-class"></a>CComObject 类

此类实现`IUnknown`非聚合对象。

## <a name="syntax"></a>语法

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>参数

*基本*<br/>
您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持任何其他接口也一样。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|构造函数。|
|[CComObject::~CComObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComObject::AddRef](#addref)|递增该对象的引用计数。|
|[CComObject::CreateInstance](#createinstance)|（静态）创建一个新`CComObject`对象。|
|[CComObject::QueryInterface](#queryinterface)|检索指向所请求的接口的指针。|
|[CComObject::Release](#release)|递减引用计数对象上。|

## <a name="remarks"></a>备注

`CComObject` 实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)非聚合对象。 但是，调用`QueryInterface`， `AddRef`，并`Release`委派给`CComObjectRootEx`。

有关使用详细信息`CComObject`，请参阅文章[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComObject`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="addref"></a>  CComObject::AddRef

递增该对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

此函数返回的对象上的新递增的引用数。 此值可能可用于诊断或测试。

##  <a name="ccomobject"></a>  CComObject::CComObject

构造函数递增模块的锁计数。

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>参数

\*void<br/>
[in]未使用此未命名的参数。 存在与其他对称性`CComXXXObjectXXX`构造函数。

### <a name="remarks"></a>备注

析构函数递减它。

如果`CComObject`-已成功使用构造派生的对象**新**运算符，在初始引用计数为 0。 若要将引用计数设置为适当的值 (1)，请调用[AddRef](#addref)函数。

##  <a name="dtor"></a>  CComObject::~CComObject

析构函数。

```
CComObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源，调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)，并减少模块锁计数。

##  <a name="createinstance"></a>  CComObject::CreateInstance

此静态函数，可创建一个新**CComObject <** `Base` **>** 对象，而不需要的开销[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>参数

*pp*<br/>
[out]一个指向**CComObject <** `Base` **>** 指针。 如果`CreateInstance`就会失败， *pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

返回的对象的引用计数为零，因此请调用`AddRef`立即，然后使用`Release`来完成后释放的对象指针上的引用。

如果确实不需要通过直接访问对象，但仍想要创建新的对象而不需要的开销`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)相反。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

##  <a name="queryinterface"></a>  CComObject::QueryInterface

检索指向所请求的接口的指针。

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

##  <a name="release"></a>  CComObject::Release

递减引用计数对象上。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

此函数返回的对象上的新递减引用计数。 在调试版本中，返回值可能是有用的诊断或测试。 在非调试版本中，`Release`始终返回 0。

## <a name="see-also"></a>请参阅

[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[类概述](../../atl/atl-class-overview.md)
