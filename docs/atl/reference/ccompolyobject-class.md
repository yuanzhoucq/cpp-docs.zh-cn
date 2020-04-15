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
ms.openlocfilehash: e30afef455db5f83afca8ff9e515f39f015c3b8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327561"
---
# <a name="ccompolyobject-class"></a>CComPolyObject 类

类实现`IUnknown`聚合或非聚合对象。

## <a name="syntax"></a>语法

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>参数

*包含*<br/>
类派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx，](../../atl/reference/ccomobjectrootex-class.md)以及来自要支持的对象的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCom波利对象：CComPoly对象](#ccompolyobject)|构造函数。|
|[CCom波利对象：*CCom波利对象](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComPoly 对象：添加参考](#addref)|增加对象的引用计数。|
|[CComPoly 对象：创建实例](#createinstance)|（静态）允许您创建一个新的**CComPolyObject<**`contained`**>** 对象，而无需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的开销。|
|[CComPoly对象：最终构造](#finalconstruct)|执行`m_contained`的最后初始化。|
|[CComPoly对象：最终释放](#finalrelease)|对 执行`m_contained`的最后销毁。|
|[CComPoly对象：查询接口](#queryinterface)|检索指向所请求的接口的指针。|
|[CComPoly 对象：发布](#release)|取消对象的引用计数。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComPoly 对象：：m_contained](#m_contained)|委托`IUnknown`调用外部未知对象是聚合对象还是对象（`IUnknown`如果对象未聚合）。|

## <a name="remarks"></a>备注

`CComPolyObject`实现聚合或非聚合对象的[I 未知。](/windows/win32/api/unknwn/nn-unknwn-iunknown)

创建 的`CComPolyObject`实例时，将检查外部未知值。 如果为 NULL，`IUnknown`则为非聚合对象实现。 如果外部未知值不是 NULL，`IUnknown`则为聚合对象实现。

使用`CComPolyObject`的优点是避免在模块中同时使用[CComAggObject](../../atl/reference/ccomaggobject-class.md)和[CComObject](../../atl/reference/ccomobject-class.md)来处理聚合和非聚合情况。 单个`CComPolyObject`对象处理这两种情况。 这意味着模块中仅存在一个 vtable 副本和一个函数副本。 如果 vtable 很大，这可大幅减小模块大小。 但是，如果 vtable 很小，则`CComPolyObject`使用可能会导致模块大小稍大一些，因为它未针对聚合或非聚合对象进行优化，例如`CComAggObject`和`CComObject`。

如果在对象的类定义中指定了DECLARE_POLY_AGGREGATABLE宏，`CComPolyObject`则将用于创建对象。 如果您使用 ATL 项目向导创建完全控制或 Internet 资源管理器控件，将自动声明DECLARE_POLY_AGGREGATABLE。

如果聚合，则`CComPolyObject`对象具有其自己的`IUnknown`，与外部对象的分离`IUnknown`，并维护其自己的引用计数。 `CComPolyObject`使用[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)委托给外部未知对象。

有关聚合的详细信息，请参阅[ATL COM 对象的基础](../../atl/fundamentals-of-atl-com-objects.md)文章。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccompolyobjectaddref"></a><a name="addref"></a>CComPoly 对象：添加参考

增加对象上的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可用于诊断或测试的值。

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a>CCom波利对象：CComPoly对象

构造函数。

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
[在]如果要聚合对象，则指向外部未知指针;如果对象未聚合，则指向 NULL。

### <a name="remarks"></a>备注

初始化`CComContainedObject`数据成员[，m_contained，](#m_contained)并递增模块锁计数。

析构函数会声明模块锁计数。

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a>CCom波利对象：*CCom波利对象

析构函数。

```
~CComPolyObject();
```

### <a name="remarks"></a>备注

释放所有分配的资源，调用[FinalRelease，](#finalrelease)并递减模块锁计数。

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a>CComPoly 对象：创建实例

允许您创建一个新的**CComPolyObject<**`contained`**>** 对象，而无需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的开销。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>参数

*Pp*<br/>
[出]指向**CComPolyObject 的指针<**`contained`**>** 指针。 如果`CreateInstance`不成功 *，pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

返回的对象的引用计数为零，因此立即调用`AddRef`，然后在完成后使用`Release`释放对象指针上的引用。

如果不需要直接访问该对象，但仍希望创建一个没有开销的新对象`CoCreateInstance`，请使用[CComCoClass：：：createInstance。](../../atl/reference/ccomcoclass-class.md#createinstance)

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a>CComPoly对象：最终构造

在对象构造的最后阶段调用此方法对[m_contained](#m_contained)数据成员执行任何最终初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a>CComPoly对象：最终释放

在对象销毁期间调用此方法释放[m_contained](#m_contained)数据成员。

```
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a>CComPoly 对象：：m_contained

派生自类的[CComContainedObject 对象](../../atl/reference/ccomcontainedobject-class.md)。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>参数

*包含*<br/>
[在]类派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx，](../../atl/reference/ccomobjectrootex-class.md)以及来自要支持的对象的任何其他接口。

### <a name="remarks"></a>备注

`IUnknown`如果对象`m_contained`是聚合的，则通过调用委托给外部未知对象，如果对象未聚合`IUnknown`，则委托给此对象的调用。

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a>CComPoly对象：查询接口

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>参数

*Q*<br/>
COM 接口。

*Iid*<br/>
[在]要请求的接口的标识符。

*ppvObject*<br/>
[出]指向*iid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppvObject*设置为 NULL。

*Pp*<br/>
[出]指向 标识的接口的`__uuidof(Q)`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

对于聚合对象，如果请求的接口为`IUnknown`，`QueryInterface`则返回指向聚合对象自己的`IUnknown`指针，并递增引用计数。 否则，此方法通过`CComContainedObject`数据成员[m_contained](#m_contained)查询接口。

## <a name="ccompolyobjectrelease"></a><a name="release"></a>CComPoly 对象：发布

对对象进行引用计数的取消。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试生成中`Release`，返回可用于诊断或测试的值。 在非调试生成中`Release`，始终返回 0。

## <a name="see-also"></a>另请参阅

[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[类概述](../../atl/atl-class-overview.md)
