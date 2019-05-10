---
title: CComPolyObject 类
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: a8dbbc06d35d2606cc76e89cc555ba7f8577daa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246252"
---
# <a name="ccompolyobject-class"></a>CComPolyObject 类

此类实现`IUnknown`聚合或非聚合对象。

## <a name="syntax"></a>语法

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>参数

*包含*<br/>
您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持任何其他接口也一样。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|构造函数。|
|[CComPolyObject::~CComPolyObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|递增对象的引用计数。|
|[CComPolyObject::CreateInstance](#createinstance)|（静态）可以创建一个新**CComPolyObject <** `contained` **>** 对象而不需要的开销[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。|
|[CComPolyObject::FinalConstruct](#finalconstruct)|执行的最终初始化`m_contained`。|
|[CComPolyObject::FinalRelease](#finalrelease)|执行的最后一个析构`m_contained`。|
|[CComPolyObject::QueryInterface](#queryinterface)|检索指向所请求的接口的指针。|
|[CComPolyObject::Release](#release)|递减对象的引用计数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|委托`IUnknown`调用到未知的外部，如果对象聚合或`IUnknown`如果对象未聚合的对象。|

## <a name="remarks"></a>备注

`CComPolyObject` 实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)聚合或非聚合对象。

实例时`CComPolyObject`创建的外部值检查未知。 如果值为 NULL，`IUnknown`为非聚合对象实现。 如果未知的外部不为 NULL，`IUnknown`为聚合对象实现。

使用的优点`CComPolyObject`避免同时[CComAggObject](../../atl/reference/ccomaggobject-class.md)并[CComObject](../../atl/reference/ccomobject-class.md)处理聚合和非聚合的情况下在模块中。 单个`CComPolyObject`对象将处理这两种情况。 这意味着你的模块中存在的 vtable 只有一个副本和函数的一个副本。 如果你 vtable 很大，这可以显著减少模块大小。 但是，如果你 vtable 很小，则使用`CComPolyObject`可能导致稍大模块大小，因为它不优化聚合或非聚合对象，因为`CComAggObject`和`CComObject`。

如果在对象的类定义中指定 DECLARE_POLY_AGGREGATABLE 宏`CComPolyObject`将用于创建您的对象。 如果使用 ATL 项目向导来创建完全控制或 Internet 资源管理器控件，将自动声明 DECLARE_POLY_AGGREGATABLE。

如果聚合，`CComPolyObject`对象都有其自身`IUnknown`、 独立于外部对象的`IUnknown`，并维护其自身的引用计数。 `CComPolyObject` 使用[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)委派给未知的外部。

有关聚合的详细信息，请参阅文章[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="addref"></a>  CComPolyObject::AddRef

递增该对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可能是有用的诊断或测试一个值。

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

构造函数。

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
[in]未知的外部聚合，或如果为 NULL 的对象是否为指针的对象，如果对象不聚合。

### <a name="remarks"></a>备注

初始化`CComContainedObject`数据成员[m_contained](#m_contained)，和模块的锁计数递增。

析构函数递减模块锁计数。

##  <a name="dtor"></a>  CComPolyObject:: ~ CComPolyObject

析构函数。

```
~CComPolyObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源，调用[FinalRelease](#finalrelease)，并减少模块锁计数。

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

可以创建一个新**CComPolyObject <** `contained` **>** 对象而不需要的开销[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>参数

*pp*<br/>
[out]一个指向**CComPolyObject <** `contained` **>** 指针。 如果`CreateInstance`就会失败， *pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

返回的对象的引用计数为零，因此请调用`AddRef`立即，然后使用`Release`来完成后释放的对象指针上的引用。

如果不需要直接访问对象，但仍想要创建新的对象而不需要的开销`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)相反。

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

调用对象构造的最后阶段，此方法对中执行任何最终初始化[m_contained](#m_contained)数据成员。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease

调用对象析构期间，此方法释放[m_contained](#m_contained)数据成员。

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComPolyObject::m_contained

一个[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)从您的类派生的对象。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>参数

*包含*<br/>
[in]您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持任何其他接口也一样。

### <a name="remarks"></a>备注

`IUnknown` 通过调用`m_contained`对象进行了聚合，或到委派到未知的外部`IUnknown`此对象，如果对象不聚合。

##  <a name="queryinterface"></a>  CComPolyObject::QueryInterface

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>参数

*Q*<br/>
COM 接口。

*iid*<br/>
[in]所请求的接口的标识符。

*ppvObject*<br/>
[out]通过标识的接口指针的指针*iid*。 如果该对象不支持此接口， *ppvObject*设置为 NULL。

*pp*<br/>
[out]指向由标识的接口的指针`__uuidof(Q)`。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

对于聚合对象，如果所请求的接口是`IUnknown`，`QueryInterface`返回一个指向聚合对象的自己`IUnknown`和递增引用计数。 否则，此方法为通过接口会询问`CComContainedObject`数据成员[m_contained](#m_contained)。

##  <a name="release"></a>  CComPolyObject::Release

递减引用计数对象上。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试版本中，`Release`返回一个值，可能是有用的诊断或测试。 在非调试版本中，`Release`始终返回 0。

## <a name="see-also"></a>请参阅

[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[类概述](../../atl/atl-class-overview.md)
