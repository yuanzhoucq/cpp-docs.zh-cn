---
title: CComObjectStack 类
ms.date: 11/04/2016
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
ms.openlocfilehash: 8c3fd56635da8b80c84f6151009586b7bd2b4341
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327576"
---
# <a name="ccomobjectstack-class"></a>CComObjectStack 类

此类创建一个临时 COM 对象，并为它提供`IUnknown`的骨骼实现。

## <a name="syntax"></a>语法

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>参数

*基地*<br/>
类派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx，](../../atl/reference/ccomobjectrootex-class.md)以及来自要支持的对象的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComObject 堆栈：CComObject堆栈](#ccomobjectstack)|构造函数。|
|[CComObject 堆栈：*CComObject堆栈](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComObjectStack：：添加参考](#addref)|返回零。 在调试模式下，调用`_ASSERTE`。|
|[CComObjectStack：：查询接口](#queryinterface)|返回E_NOINTERFACE。 在调试模式下，调用`_ASSERTE`。|
|[CComObjectStack：：发布](#release)|返回零。 在调试模式下，调用`_ASSERTE`。 ~|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComObjectStack：：m_hResFinalConstruct](#m_hresfinalconstruct)|包含在构建`CComObjectStack`对象期间返回的 HRESULT。|

## <a name="remarks"></a>备注

`CComObjectStack`用于创建临时 COM 对象，并提供 对象的属性`IUnknown`实现。 通常，对象用作一个函数中的局部变量（即推送到堆栈上）。 由于对象在函数完成时被销毁，因此不会执行引用计数以提高效率。

下面的示例演示如何创建函数中使用的 COM 对象：

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

临时对象`Tempobj`被推送到堆栈上，并在函数完成时自动消失。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComObjectStack`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomobjectstackaddref"></a><a name="addref"></a>CComObjectStack：：添加参考

返回零。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

返回零。

### <a name="remarks"></a>备注

在调试模式下，调用`_ASSERTE`。

## <a name="ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a>CComObject 堆栈：CComObject堆栈

构造函数。

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>备注

调用`FinalConstruct`，然后将[m_hResFinalConstruct](#m_hresfinalconstruct)设置到 返回的`FinalConstruct`HRESULT。 如果您尚未从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)派生基类，则必须提供您自己的`FinalConstruct`方法。 析构函数调用 `FinalRelease`。

## <a name="ccomobjectstackccomobjectstack"></a><a name="dtor"></a>CComObject 堆栈：*CComObject堆栈

析构函数。

```
CComObjectStack();
```

### <a name="remarks"></a>备注

释放所有分配的资源，并调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

## <a name="ccomobjectstackm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectStack：：m_hResFinalConstruct

包含在`FinalConstruct``CComObjectStack`对象构造期间从调用返回的 HRESULT。

```
HRESULT    m_hResFinalConstruct;
```

## <a name="ccomobjectstackqueryinterface"></a><a name="queryinterface"></a>CComObjectStack：：查询接口

返回E_NOINTERFACE。

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>返回值

返回E_NOINTERFACE。

### <a name="remarks"></a>备注

在调试模式下，调用`_ASSERTE`。

## <a name="ccomobjectstackrelease"></a><a name="release"></a>CComObjectStack：：发布

返回零。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

返回零。

### <a name="remarks"></a>备注

在调试模式下，调用`_ASSERTE`。

## <a name="see-also"></a>另请参阅

[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 类](../../atl/reference/ccomobject-class.md)<br/>
[CComObjectGlobal 类](../../atl/reference/ccomobjectglobal-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
