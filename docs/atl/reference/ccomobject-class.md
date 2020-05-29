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
ms.openlocfilehash: de6ffb45fe5c6f73ab656d5c6185b70d9f5edd38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327643"
---
# <a name="ccomobject-class"></a>CComObject 类

类实现`IUnknown`非聚合对象。

## <a name="syntax"></a>语法

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>参数

*基地*<br/>
类派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx，](../../atl/reference/ccomobjectrootex-class.md)以及来自要支持的对象的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComObject：CComObject](#ccomobject)|构造函数。|
|[CCom对象：*CCom对象](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComObject：addRef](#addref)|增加对象上的引用计数。|
|[CComObject：创建实例](#createinstance)|（静态）创建新`CComObject`对象。|
|[CComObject：查询接口](#queryinterface)|检索指向所请求的接口的指针。|
|[CComObject：发布](#release)|对对象进行引用计数的取消。|

## <a name="remarks"></a>备注

`CComObject`实现非聚合对象的[I 未知。](/windows/win32/api/unknwn/nn-unknwn-iunknown) 但是，对`QueryInterface`的`AddRef`调用`Release`将委派给`CComObjectRootEx`。

有关使用`CComObject`的详细信息，请参阅[ATL COM 对象的基础](../../atl/fundamentals-of-atl-com-objects.md)文章。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComObject`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomobjectaddref"></a><a name="addref"></a>CComObject：addRef

增加对象上的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

此函数返回对象上新的增量引用计数。 此值可用于诊断或测试。

## <a name="ccomobjectccomobject"></a><a name="ccomobject"></a>CComObject：CComObject

构造函数增加模块锁计数。

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>参数

<em>void\*</em><br/>
[在]不使用此未命名的参数。 它与其他`CComXXXObjectXXX`构造函数的对称性存在。

### <a name="remarks"></a>备注

析构函数将其递减。

如果使用新`CComObject`运算符成功构造派生对象，则初始**new**引用计数为 0。 要将引用计数设置为正确的值 （1），请调用[AddRef](#addref)函数。

## <a name="ccomobjectccomobject"></a><a name="dtor"></a>CCom对象：*CCom对象

析构函数。

```
CComObject();
```

### <a name="remarks"></a>备注

释放所有分配的资源，调用[FinalRelease，](ccomobjectrootex-class.md#finalrelease)并递减模块锁计数。

## <a name="ccomobjectcreateinstance"></a><a name="createinstance"></a>CComObject：创建实例

此静态函数允许您创建一个新的**CComObject<**`Base`**>** 对象，而无需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的开销。

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>参数

*Pp*<br/>
[出]指向**CComObject 的指针<**`Base`**>** 指针。 如果`CreateInstance`不成功 *，pp*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

返回的对象的引用计数为零，因此立即调用`AddRef`，然后在完成后使用`Release`释放对象指针上的引用。

如果不需要直接访问该对象，但仍希望创建一个没有开销的新对象`CoCreateInstance`，请使用[CComCoClass：：：createInstance。](../../atl/reference/ccomcoclass-class.md#createinstance)

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

## <a name="ccomobjectqueryinterface"></a><a name="queryinterface"></a>CComObject：查询接口

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

## <a name="ccomobjectrelease"></a><a name="release"></a>CComObject：发布

对对象进行引用计数的取消。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

此函数返回对象上的新递减引用计数。 在调试生成中，返回值可用于诊断或测试。 在非调试生成中，`Release`始终返回 0。

## <a name="see-also"></a>另请参阅

[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[类概述](../../atl/atl-class-overview.md)
