---
title: CComTearOffObject 类
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: fd35b1e9e69c97402dd1ec357fd25fa1dcd5dd49
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259412"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject 类

此类实现分离式接口。

## <a name="syntax"></a>语法

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>参数

*基本*<br/>
分离式类，派生自`CComTearOffObjectBase`和希望分离式对象以支持接口。

ATL 在两个阶段中实现其分离式接口 —`CComTearOffObjectBase`方法处理引用计数并`QueryInterface`，而`CComTearOffObject`实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|构造函数。|
|[CComTearOffObject::~CComTearOffObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|递增引用计数为`CComTearOffObject`对象。|
|[CComTearOffObject::QueryInterface](#queryinterface)|返回一个指向所请求的接口分离式类或所有者类上。|
|[CComTearOffObject::Release](#release)|递减引用计数为`CComTearOffObject`对象，并销毁它。|

### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase 方法

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|构造函数。|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase 数据成员

|||
|-|-|
|[m_pOwner](#m_powner)|一个指向`CComObject`所有者类派生。|

## <a name="remarks"></a>备注

`CComTearOffObject` 作为一个单独的对象，该接口查询时，仅实例化来实现分离式接口。 拖曳时将删除其引用计数变为零。 通常情况下，生成很少使用，因为主要对象的所有实例中，使用分离式节省 vtable 指针的接口的分离式接口。

应派生类实现分离式从`CComTearOffObjectBase`和从希望分离式对象以支持任何接口。 `CComTearOffObjectBase` 在所有者类和线程模型上模板化。 在所有者类是对象的为其分离式正在实现的类。 如果不指定线程模型，则使用默认线程模型。

分离式类，应创建 COM 映射。 当分离式实例化 ATL 时，它将创建`CComTearOffObject<CYourTearOffClass>`或`CComCachedTearOffObject<CYourTearOffClass>`。

例如，在寻呼机示例中，`CBeeper2`类是分开的类和`CBeeper`类是在所有者类：

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComTearOffObject`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="addref"></a>  CComTearOffObject::AddRef

递增引用计数的`CComTearOffObject`由一个对象。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

一个值，可能是有用的诊断和测试。

##  <a name="ccomtearoffobject"></a>  CComTearOffObject::CComTearOffObject

构造函数。

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
[in]将转换为指向指针的指针`CComObject<Owner>`对象。

### <a name="remarks"></a>备注

所有者的引用计数加一。

##  <a name="dtor"></a>  CComTearOffObject:: ~ CComTearOffObject

析构函数。

```
~CComTearOffObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源，而该模块的调用 FinalRelease，并减少锁定计数。

##  <a name="ccomtearoffobjectbase"></a>  CComTearOffObject::CComTearOffObjectBase

构造函数。

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>备注

初始化[m_pOwner](#m_powner)为 NULL 的成员。

##  <a name="m_powner"></a>  CComTearOffObject::m_pOwner

一个指向[CComObject](../../atl/reference/ccomobject-class.md)对象派生自*所有者*。

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>参数

*Owner*<br/>
[in]为其分离式正在实现的类。

### <a name="remarks"></a>备注

在构造期间，该指针被初始化为 NULL。

##  <a name="queryinterface"></a>  CComTearOffObject::QueryInterface

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]所请求的接口的 IID。

*ppvObject*<br/>
[out]通过标识的接口指针的指针*iid*，或如果找不到该接口，则为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

首先为您分离式的类上的接口的的查询。 如果接口不存在，所有者对象上的接口的查询。 如果所请求的接口是`IUnknown`，返回`IUnknown`的所有者。

##  <a name="release"></a>  CComTearOffObject::Release

引用计数按 1 递减，引用计数为零，如果删除`CComTearOffObject`。

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>返回值

在非调试版本中，始终返回零。 在调试版本中返回一个值，可能是有用的诊断或测试。

## <a name="see-also"></a>请参阅

[CComCachedTearOffObject 类](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
