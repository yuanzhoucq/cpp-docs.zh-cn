---
title: CComObjectGlobal 类
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: ec3abd04ce72cce98dae72a1ed8cbb8d9fe72079
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267428"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal 类

此类管理模块包含的引用计数在`Base`对象。

## <a name="syntax"></a>语法

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>参数

*基本*<br/>
您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持任何其他接口也一样。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|构造函数。|
|[CComObjectGlobal::~CComObjectGlobal](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|实现全局`AddRef`。|
|[CComObjectGlobal::QueryInterface](#queryinterface)|实现全局`QueryInterface`。|
|[CComObjectGlobal::Release](#release)|实现全局`Release`。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|包含构造期间返回的 HRESULT`CComObjectGlobal`对象。|

## <a name="remarks"></a>备注

`CComObjectGlobal` 管理包含的模块的引用计数在`Base`对象。 `CComObjectGlobal` 可确保，只要不释放该模块，将不会删除您的对象。 在整个模块的引用计数变为零时，将仅删除您的对象。

例如，使用`CComObjectGlobal`，类工厂可以包含一个常见的全局对象，由所有客户端共享。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="addref"></a>  CComObjectGlobal::AddRef

将该对象的引用计数加 1。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

一个值，可能是有用的诊断和测试。

### <a name="remarks"></a>备注

默认情况下`AddRef`调用`_Module::Lock`，其中`_Module`是全局实例[CComModule](../../atl/reference/ccommodule-class.md)或从其派生的类。

##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal

构造函数。 调用`FinalConstruct`，然后设置[m_hResFinalConstruct](#m_hresfinalconstruct)到`HRESULT`返回`FinalConstruct`。

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>备注

如果您不派生从基类[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)，必须提供你自己`FinalConstruct`方法。 析构函数调用 `FinalRelease`。

##  <a name="dtor"></a>  CComObjectGlobal:: ~ CComObjectGlobal

析构函数。

```
CComObjectGlobal();
```

### <a name="remarks"></a>备注

释放所有已分配的资源并调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct

包含调用 HRESULT`FinalConstruct`的构造期间`CComObjectGlobal`对象。

```
HRESULT m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface

检索指向请求的接口指针的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]所请求的接口的 GUID。

*ppvObject*<br/>
[out]指向标识 iid，则为 NULL，如果找不到该接口的接口指针的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`QueryInterface` 仅处理 COM 映射表中的接口。

##  <a name="release"></a>  CComObjectGlobal::Release

引用的对象的计数按 1 递减。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试版本中，`Release`返回一个值，可能是有用的诊断和测试。 在非调试版本中，`Release`始终返回 0。

### <a name="remarks"></a>备注

默认情况下`Release`调用`_Module::Unlock`，其中`_Module`是全局实例[CComModule](../../atl/reference/ccommodule-class.md)或从其派生的类。

## <a name="see-also"></a>请参阅

[CComObjectStack 类](../../atl/reference/ccomobjectstack-class.md)<br/>
[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 类](../../atl/reference/ccomobject-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
