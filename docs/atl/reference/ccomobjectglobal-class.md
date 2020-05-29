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
ms.openlocfilehash: 9a784584179186cdf1e63c1ec43cad4d59391ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327627"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal 类

此类管理包含对象的`Base`模块上的引用计数。

## <a name="syntax"></a>语法

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>参数

*基地*<br/>
类派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx，](../../atl/reference/ccomobjectrootex-class.md)以及来自要支持的对象的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComObject 全球：CComObject 全球](#ccomobjectglobal)|构造函数。|
|[CComObject 全球：*CComObject 全球](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComObjectGlobal：：添加参考](#addref)|实现全局`AddRef`。|
|[CComObject 全局：：查询接口](#queryinterface)|实现全局`QueryInterface`。|
|[CComObject 全球：发布](#release)|实现全局`Release`。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComObjectGlobal：：m_hResFinalConstruct](#m_hresfinalconstruct)|包含在构建`CComObjectGlobal`对象期间返回的 HRESULT。|

## <a name="remarks"></a>备注

`CComObjectGlobal`管理包含对象的`Base`模块上的引用计数。 `CComObjectGlobal`确保只要不释放模块，您的对象就不会被删除。 仅当整个模块上的引用计数为零时，才会删除对象。

例如，使用`CComObjectGlobal`类工厂可以保存由其所有客户端共享的通用全局对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomobjectglobaladdref"></a><a name="addref"></a>CComObjectGlobal：：添加参考

将对象的引用计数增加 1。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可用于诊断和测试的值。

### <a name="remarks"></a>备注

默认情况下，`AddRef`调用`_Module::Lock`， `_Module` [CComModule](../../atl/reference/ccommodule-class.md)的全局实例或派生自它的类的位置。

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a>CComObject 全球：CComObject 全球

构造函数。 调用`FinalConstruct`，然后[m_hResFinalConstruct](#m_hresfinalconstruct)设置到`HRESULT`返回的`FinalConstruct`。

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>备注

如果您尚未从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)派生基类，则必须提供您自己的`FinalConstruct`方法。 析构函数调用 `FinalRelease`。

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a>CComObject 全球：*CComObject 全球

析构函数。

```
CComObjectGlobal();
```

### <a name="remarks"></a>备注

释放所有分配的资源，并调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

## <a name="ccomobjectglobalm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectGlobal：：m_hResFinalConstruct

包含在对象构造期间从调用`FinalConstruct`的`CComObjectGlobal`HRESULT。

```
HRESULT m_hResFinalConstruct;
```

## <a name="ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a>CComObject 全局：：查询接口

检索指向请求的接口指针的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]请求的接口的 GUID。

*ppvObject*<br/>
[出]指向 iid 标识的接口指针，如果未找到接口，则指向 NULL 的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

`QueryInterface` 仅处理 COM 映射表中的接口。

## <a name="ccomobjectglobalrelease"></a><a name="release"></a>CComObject 全球：发布

将对象的引用计数减少 1。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试生成中`Release`，返回可用于诊断和测试的值。 在非调试生成中，`Release`始终返回 0。

### <a name="remarks"></a>备注

默认情况下，`Release`调用`_Module::Unlock`， `_Module` [CComModule](../../atl/reference/ccommodule-class.md)的全局实例或派生自它的类的位置。

## <a name="see-also"></a>另请参阅

[CComObjectStack 类](../../atl/reference/ccomobjectstack-class.md)<br/>
[CComAggObject 类](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 类](../../atl/reference/ccomobject-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
