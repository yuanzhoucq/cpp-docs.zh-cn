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
ms.openlocfilehash: b9200c9c396fc16b6df3f4c2f4c66fb7976316d4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748167"
---
# <a name="ccomaggobject-class"></a>CComAggObject 类

此类实现聚合对象的[I 未知](/windows/win32/api/unknwn/nn-unknwn-iunknown)接口。 根据定义，聚合对象包含在外部对象中。 该`CComAggObject`类类似于[CComObject 类](../../atl/reference/ccomobject-class.md)，只不过它公开了外部客户端可直接访问的接口。

## <a name="syntax"></a>语法

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>参数

*包含*<br/>
类派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx，](../../atl/reference/ccomobjectrootex-class.md)以及来自要支持的对象的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComagg 对象：Ccomagg 对象](#ccomaggobject)|构造函数。|
|[CComAgg 对象：*CcomAgg 对象](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComAgg 对象：addRef](#addref)|增加聚合对象的引用计数。|
|[CComAgg 对象：：创建实例](#createinstance)|此静态函数允许您创建一个新的**CComAggObject<**`contained`**>** 对象，而无需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的开销。|
|[CComAgg 对象：最终构造](#finalconstruct)|执行`m_contained`的最后初始化。|
|[CComAgg 对象：最终发布](#finalrelease)|对 执行`m_contained`的最后销毁。|
|[CComAgg 对象：查询接口](#queryinterface)|检索指向所请求的接口的指针。|
|[CComAgg 对象：：发布](#release)|对聚合对象取消引用计数。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComAgg 对象：：m_contained](#m_contained)|委托`IUnknown`调用外部未知。|

## <a name="remarks"></a>备注

`CComAggObject`实现[聚合对象的 I 未知。](/windows/win32/api/unknwn/nn-unknwn-iunknown) `CComAggObject`有自己的`IUnknown`接口，独立于外部对象的`IUnknown`接口，并维护自己的引用计数。

有关聚合的详细信息，请参阅[ATL COM 对象的基础](../../atl/fundamentals-of-atl-com-objects.md)文章。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomaggobjectaddref"></a><a name="addref"></a>CComAgg 对象：addRef

增加聚合对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可用于诊断或测试的值。

## <a name="ccomaggobjectccomaggobject"></a><a name="ccomaggobject"></a>CComagg 对象：Ccomagg 对象

构造函数。

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
[在]外部未知。

### <a name="remarks"></a>备注

初始化`CComContainedObject`成员[，m_contained，](#m_contained)并递增模块锁计数。

析构函数会声明模块锁计数。

## <a name="ccomaggobjectccomaggobject"></a><a name="dtor"></a>CComAgg 对象：*CcomAgg 对象

析构函数。

```
~CComAggObject();
```

### <a name="remarks"></a>备注

释放所有分配的资源，调用[FinalRelease，](#finalrelease)并递减模块锁计数。

## <a name="ccomaggobjectcreateinstance"></a><a name="createinstance"></a>CComAgg 对象：：创建实例

此静态函数允许您创建一个新的**CComAggObject<**`contained`**>** 对象，而无需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的开销。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>参数

*Pp*<br/>
[出]指向**CComAggObject 的\<** 指针<em>包含</em>**>** 指针。 如果`CreateInstance`不成功 *，pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

返回的对象的引用计数为零，因此立即调用`AddRef`，然后在完成后使用`Release`释放对象指针上的引用。

如果不需要直接访问该对象，但仍希望创建一个没有开销的新对象`CoCreateInstance`，请使用[CComCoClass：：：createInstance。](../../atl/reference/ccomcoclass-class.md#createinstance)

## <a name="ccomaggobjectfinalconstruct"></a><a name="finalconstruct"></a>CComAgg 对象：最终构造

在对象构造的最后阶段调用此方法，对[m_contained](#m_contained)成员执行任何最终初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ccomaggobjectfinalrelease"></a><a name="finalrelease"></a>CComAgg 对象：最终发布

在对象销毁期间调用此方法释放[m_contained](#m_contained)成员。

```cpp
void FinalRelease();
```

## <a name="ccomaggobjectm_contained"></a><a name="m_contained"></a>CComAgg 对象：：m_contained

派生自类的[CComContainedObject 对象](../../atl/reference/ccomcontainedobject-class.md)。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>参数

*包含*<br/>
[在]类派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx，](../../atl/reference/ccomobjectrootex-class.md)以及来自要支持的对象的任何其他接口。

### <a name="remarks"></a>备注

所有`IUnknown`通过`m_contained`的呼叫都委托给外部未知。

## <a name="ccomaggobjectqueryinterface"></a><a name="queryinterface"></a>CComAgg 对象：查询接口

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]要请求的接口的标识符。

*ppvObject*<br/>
[出]指向*iid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppvObject*设置为 NULL。

*Pp*<br/>
[出]指向类型标识的接口指针`Q`的指针。 如果对象不支持此接口 *，pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

如果请求的接口为`IUnknown` `QueryInterface` ，则返回指向聚合对象自己的`IUnknown`指针，并递增引用计数。 否则，此方法通过`CComContainedObject`成员查询接口[，m_contained](#m_contained)。

## <a name="ccomaggobjectrelease"></a><a name="release"></a>CComAgg 对象：：发布

对聚合对象取消引用计数。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试生成中`Release`，返回可用于诊断或测试的值。 在非调试生成中，`Release`始终返回 0。

## <a name="see-also"></a>请参阅

[CComObject 类](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[类概述](../../atl/atl-class-overview.md)
