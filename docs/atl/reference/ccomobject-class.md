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
ms.openlocfilehash: a2051932413d8658eb7cedb67ed0eab2077b599d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497137"
---
# <a name="ccomobject-class"></a>CComObject 类

此类实现`IUnknown`非聚合对象。

## <a name="syntax"></a>语法

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>参数

*基座*<br/>
从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)派生的类, 以及要在对象上支持的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|构造函数。|
|[CComObject::~CComObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComObject::AddRef](#addref)|递增对象的引用计数。|
|[CComObject::CreateInstance](#createinstance)|静止创建新`CComObject`的对象。|
|[CComObject::QueryInterface](#queryinterface)|检索指向所请求的接口的指针。|
|[CComObject::Release](#release)|递减对象的引用计数。|

## <a name="remarks"></a>备注

`CComObject`为非聚合对象实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。 但是, 对`QueryInterface`、 `AddRef`和`Release`的调用将委托给`CComObjectRootEx`。

有关使用`CComObject`的详细信息, 请参阅[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComObject`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="addref"></a>  CComObject::AddRef

递增对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

此函数返回对象的新递增引用计数。 此值可能适用于诊断或测试。

##  <a name="ccomobject"></a>  CComObject::CComObject

构造函数递增模块锁计数。

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>参数

\*void<br/>
中未使用此未命名参数。 它与其他`CComXXXObjectXXX`构造函数存在对称。

### <a name="remarks"></a>备注

析构函数将其递减。

如果使用 new 运算符成功构造派生对象, 则初始引用计数为0。 `CComObject` 若要将引用计数设置为正确的值 (1), 请调用[AddRef](#addref)函数。

##  <a name="dtor"></a>  CComObject::~CComObject

析构函数。

```
CComObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源, 调用[FinalRelease](ccomobjectrootex-class.md#finalrelease), 并递减模块锁计数。

##  <a name="createinstance"></a>  CComObject::CreateInstance

此静态函数允许您创建新的**CComObject <** `Base` **>** 对象, 而不会产生[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)开销。

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>参数

*pp*<br/>
弄指向**CComObject <** `Base` **>** 指针的指针。 如果`CreateInstance`不成功, 则*pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

返回的对象的引用计数为零, 因此立即调用`AddRef` , 然后在完成`Release`后使用释放对象指针上的引用。

如果不需要直接访问对象, 但仍想要创建一个不带开销的`CoCreateInstance`新对象, 请改用[CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 。

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
中所请求的接口的标识符。

*ppvObject*<br/>
弄指向由*iid*标识的接口指针的指针。 如果对象不支持此接口, 则将*ppvObject*设置为 NULL。

*pp*<br/>
弄指向由类型`Q`标识的接口指针的指针。 如果对象不支持此接口, 则*pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="release"></a>CComObject:: Release

递减对象的引用计数。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

此函数返回对象上新减少的引用计数。 在调试版本中, 返回值对于诊断或测试可能很有用。 在非调试版本中, `Release`始终返回0。

## <a name="see-also"></a>请参阅

[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[类概述](../../atl/atl-class-overview.md)
