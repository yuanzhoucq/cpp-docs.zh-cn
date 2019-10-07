---
title: CComAggObject 类
ms.date: 11/04/2016
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
ms.openlocfilehash: 8b05284104f9d2e5e7704bceaee6f8adf9a33aac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497660"
---
# <a name="ccomaggobject-class"></a>CComAggObject 类

此类为聚合的对象实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)接口。 按照定义，聚合对象包含在外部对象中。 类类似于[CComObject 类](../../atl/reference/ccomobject-class.md)，只不过它公开了可直接由外部客户端访问的接口。 `CComAggObject`

## <a name="syntax"></a>语法

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>参数

*独立*<br/>
从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)派生的类，以及要在对象上支持的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|构造函数。|
|[CComAggObject：： ~ CComAggObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|递增聚合对象上的引用计数。|
|[CComAggObject::CreateInstance](#createinstance)|此静态函数允许创建新的**CComAggObject <** `contained` **>** 对象，而不会产生[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)开销。|
|[CComAggObject::FinalConstruct](#finalconstruct)|执行的`m_contained`最终初始化。|
|[CComAggObject::FinalRelease](#finalrelease)|执行的`m_contained`最终析构。|
|[CComAggObject::QueryInterface](#queryinterface)|检索指向所请求的接口的指针。|
|[CComAggObject::Release](#release)|递减聚合对象上的引用计数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|将`IUnknown`调用委托给外部未知。|

## <a name="remarks"></a>备注

`CComAggObject`实现聚合对象的[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。 `CComAggObject`具有其自己`IUnknown`的接口，与外部对象的`IUnknown`接口分离，维护其自己的引用计数。

有关聚合的详细信息，请参阅[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="addref"></a>CComAggObject：： AddRef

递增聚合对象上的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可能对诊断或测试有用的值。

##  <a name="ccomaggobject"></a>CComAggObject：： CComAggObject

构造函数。

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
中外部未知。

### <a name="remarks"></a>备注

初始化`CComContainedObject`成员 [m_contained](#m_contained)，并递增模块锁计数。

析构函数递减模块锁计数。

##  <a name="dtor"></a>CComAggObject：： ~ CComAggObject

析构函数。

```
~CComAggObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源，调用[FinalRelease](#finalrelease)，并递减模块锁计数。

##  <a name="createinstance"></a>CComAggObject：： CreateInstance

此静态函数允许创建新的**CComAggObject <** `contained` **>** 对象，而不会产生[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)开销。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>参数

*pp*<br/>
弄指向**CComAggObject\<** 包含**的>** 指针的指针。 如果`CreateInstance`不成功，则*pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

返回的对象的引用计数为零，因此立即调用`AddRef` ，然后在完成`Release`后使用释放对象指针上的引用。

如果不需要直接访问对象，但仍想要创建一个不带开销的`CoCreateInstance`新对象，请改用[CComCoClass：： CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 。

##  <a name="finalconstruct"></a>CComAggObject：： FinalConstruct

在对象构造的最后阶段调用，此方法对[m_contained](#m_contained)成员执行任何最终初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="finalrelease"></a>CComAggObject：： FinalRelease

在对象销毁过程中调用，此方法将释放[m_contained](#m_contained)成员。

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComAggObject：： m_contained

派生自类的[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)对象。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>参数

*独立*<br/>
中从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)派生的类，以及要在对象上支持的任何其他接口。

### <a name="remarks"></a>备注

`IUnknown` 所有`m_contained`调用都委托给外部未知。

##  <a name="queryinterface"></a>CComAggObject：： QueryInterface

检索指向所请求的接口的指针。

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

### <a name="remarks"></a>备注

如果请求的接口为`IUnknown`， `QueryInterface`则返回一个指向聚合对象自身`IUnknown`的指针，并递增引用计数。 否则，此方法将`CComContainedObject`通过成员[m_contained](#m_contained)来查询接口。

##  <a name="release"></a>CComAggObject：： Release

递减聚合对象上的引用计数。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试版本中`Release` ，将返回一个值，该值对于诊断或测试可能很有用。 在非调试版本中， `Release`始终返回0。

## <a name="see-also"></a>请参阅

[CComObject 类](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[类概述](../../atl/atl-class-overview.md)
