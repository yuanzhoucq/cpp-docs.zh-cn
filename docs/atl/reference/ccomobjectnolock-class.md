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
ms.openlocfilehash: c190f495e284e98b27a6c6dc2099a8dfc4b1693d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327619"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock 类

类实现`IUnknown`非聚合对象，但不增加构造函数中的模块锁计数。

## <a name="syntax"></a>语法

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>参数

*基地*<br/>
类派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx，](../../atl/reference/ccomobjectrootex-class.md)以及来自要支持的对象的任何其他接口。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComobject 无锁：：Ccomobject 无锁](#ccomobjectnolock)|构造函数。|
|[CComobject 无锁：：*CComobject 无锁](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComObjectnoLock：：添加参考](#addref)|增加对象上的引用计数。|
|[CComObject 无锁定：：查询接口](#queryinterface)|返回指向请求的接口的指针。|
|[CComObjectnoLock：：发布](#release)|对对象进行引用计数的取消。|

## <a name="remarks"></a>备注

`CComObjectNoLock`与[CComObject](../../atl/reference/ccomobject-class.md)类似，因为它为非聚合对象实现了[I未知](/windows/win32/api/unknwn/nn-unknwn-iunknown);但是，`CComObjectNoLock`不会增加构造函数中的模块锁计数。

ATL`CComObjectNoLock`在内部用于一流工厂。 通常，您不会直接使用此类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomobjectnolockaddref"></a><a name="addref"></a>CComObjectnoLock：：添加参考

增加对象上的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可用于诊断或测试的值。

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a>CComobject 无锁：：Ccomobject 无锁

构造函数。 与[CComObject 不同](../../atl/reference/ccomobject-class.md)，不增加模块锁计数。

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>参数

<em>void\*</em><br/>
[在]不使用此未命名的参数。 它与其他`CComXXXObjectXXX`构造函数的对称性存在。

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a>CComobject 无锁：：*CComobject 无锁

析构函数。

```
~CComObjectNoLock();
```

### <a name="remarks"></a>备注

释放所有分配的资源，并调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

## <a name="ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a>CComObject 无锁定：：查询接口

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]要请求的接口的标识符。

*ppvObject*<br/>
[出]指向*iid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppvObject*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ccomobjectnolockrelease"></a><a name="release"></a>CComObjectnoLock：：发布

对对象进行引用计数的取消。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试生成中`Release`，返回可用于诊断或测试的值。 在非调试生成中，`Release`始终返回 0。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
