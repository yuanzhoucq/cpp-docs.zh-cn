---
title: CComObjectNoLock 类
ms.date: 11/04/2016
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
ms.openlocfilehash: 9253c7495f4d13ed6ce609988251d8abd09592ad
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497039"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock 类

此类实现`IUnknown`非聚合对象, 但不会在构造函数中递增模块锁计数。

## <a name="syntax"></a>语法

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>参数

*基座*<br/>
从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)派生的类, 以及要在对象上支持的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|构造函数。|
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|递增对象的引用计数。|
|[CComObjectNoLock::QueryInterface](#queryinterface)|返回一个指向所请求的接口的指针。|
|[CComObjectNoLock::Release](#release)|递减对象的引用计数。|

## <a name="remarks"></a>备注

`CComObjectNoLock`类似于[CComObject](../../atl/reference/ccomobject-class.md) , 因为它为非聚合对象实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ;但是, `CComObjectNoLock`不会在构造函数中递增模块锁计数。

ATL 在`CComObjectNoLock`内部为类工厂使用。 通常, 不会直接使用此类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="addref"></a>  CComObjectNoLock::AddRef

递增对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可能对诊断或测试有用的值。

##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock

构造函数。 与[CComObject](../../atl/reference/ccomobject-class.md)不同, 不会递增模块锁计数。

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>参数

\*void<br/>
中未使用此未命名参数。 它与其他`CComXXXObjectXXX`构造函数存在对称。

##  <a name="dtor"></a>  CComObjectNoLock::~CComObjectNoLock

析构函数。

```
~CComObjectNoLock();
```

### <a name="remarks"></a>备注

释放所有已分配的资源, 并调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*iid*<br/>
中所请求的接口的标识符。

*ppvObject*<br/>
弄指向由*iid*标识的接口指针的指针。 如果对象不支持此接口, 则将*ppvObject*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="release"></a>  CComObjectNoLock::Release

递减对象的引用计数。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试版本中`Release` , 将返回一个值, 该值对于诊断或测试可能很有用。 在非调试版本中, `Release`始终返回0。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
