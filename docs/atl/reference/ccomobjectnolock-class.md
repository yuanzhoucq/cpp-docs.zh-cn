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
ms.openlocfilehash: 85a5a71e330b8171a8e0e239d9afab43a6df1512
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467351"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock 类

此类实现`IUnknown`的非聚合的对象，但不会递增模块锁计数的构造函数中。

## <a name="syntax"></a>语法

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>参数

*基本*<br/>
您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持任何其他接口也一样。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|构造函数。|
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|递增该对象的引用计数。|
|[CComObjectNoLock::QueryInterface](#queryinterface)|返回一个指向所请求的接口。|
|[CComObjectNoLock::Release](#release)|递减引用计数对象上。|

## <a name="remarks"></a>备注

`CComObjectNoLock` 类似于[CComObject](../../atl/reference/ccomobject-class.md) ，其中实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)非聚合的对象; 但是，`CComObjectNoLock`没有构造函数中不递增模块锁计数。

使用 ATL`CComObjectNoLock`在内部的类工厂。 一般情况下，您不会直接使用此类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="addref"></a>  CComObjectNoLock::AddRef

递增该对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可能是有用的诊断或测试一个值。

##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock

构造函数。 与不同[CComObject](../../atl/reference/ccomobject-class.md)，不会递增模块的锁计数。

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>参数

\*void<br/>
[in]未使用此未命名的参数。 存在与其他对称性`CComXXXObjectXXX`构造函数。

##  <a name="dtor"></a>  CComObjectNoLock::~CComObjectNoLock

析构函数。

```
~CComObjectNoLock();
```

### <a name="remarks"></a>备注

释放所有已分配的资源并调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]所请求的接口的标识符。

*ppvObject*<br/>
[out]通过标识的接口指针的指针*iid*。 如果该对象不支持此接口， *ppvObject*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="release"></a>  CComObjectNoLock::Release

递减引用计数对象上。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试版本中，`Release`返回一个值，可能是有用的诊断或测试。 在非调试版本中，`Release`始终返回 0。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
