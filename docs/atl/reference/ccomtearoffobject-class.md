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
ms.openlocfilehash: 0d27a6fa3c0070cd32c78971a7544327c51d4393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496917"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject 类

此类实现一个脱离接口。

## <a name="syntax"></a>语法

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>参数

*基座*<br/>
从`CComTearOffObjectBase`派生的类, 以及要使其支持您的脱离对象的接口。

ATL 在两个阶段内实现`CComTearOffObjectBase`其脱离接口: 方法会处理引用计数和`QueryInterface`, 同时`CComTearOffObject`实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|构造函数。|
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|递增`CComTearOffObject`对象的引用计数。|
|[CComTearOffObject::QueryInterface](#queryinterface)|返回一个指针, 该指针指向您的脱离类或所有者类上所请求的接口。|
|[CComTearOffObject::Release](#release)|递减`CComTearOffObject`对象的引用计数, 并将其销毁。|

### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase 方法

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|构造函数。|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase 数据成员

|||
|-|-|
|[m_pOwner](#m_powner)|指向`CComObject`派生自所有者类的指针。|

## <a name="remarks"></a>备注

`CComTearOffObject`将独立的接口实现为单独的对象, 该对象仅在查询该接口时进行实例化。 在引用计数变为零时, 将删除该删除。 通常, 你为很少使用的接口生成了一个脱离接口, 因为使用脱离会将 vtable 指针保存在主对象的所有实例中。

你应从任何需要你的脱离对象支持的`CComTearOffObjectBase`接口派生出实现脱离的类。 `CComTearOffObjectBase`所有者类和线程模型上的模板化。 所有者类是要为其实现撕的对象的类。 如果未指定线程模型, 则使用默认线程模型。

应为您的脱离类创建一个 COM 映射。 当 ATL 实例化撕时, 它将创建`CComTearOffObject<CYourTearOffClass>`或。 `CComCachedTearOffObject<CYourTearOffClass>`

例如, 在 BEEPER 示例中, `CBeeper2`类是脱离类`CBeeper` , 类是所有者类:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComTearOffObject`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="addref"></a>CComTearOffObject:: AddRef

将`CComTearOffObject`对象的引用计数递增1。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可能对诊断和测试有用的值。

##  <a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject

构造函数。

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>参数

*pv*<br/>
中将转换为指向`CComObject<Owner>`对象的指针的指针。

### <a name="remarks"></a>备注

将所有者的引用计数递增1。

##  <a name="dtor"></a>CComTearOffObject:: ~ CComTearOffObject

析构函数。

```
~CComTearOffObject();
```

### <a name="remarks"></a>备注

释放所有已分配的资源, 调用 FinalRelease, 并递减模块锁计数。

##  <a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase

构造函数。

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>备注

将[m_pOwner](#m_powner)成员初始化为 NULL。

##  <a name="m_powner"></a>  CComTearOffObject::m_pOwner

指向从*所有者*派生的[CComObject](../../atl/reference/ccomobject-class.md)对象的指针。

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>参数

*Owner*<br/>
中正在实现其脱离的类。

### <a name="remarks"></a>备注

在构造过程中, 指针初始化为 NULL。

##  <a name="queryinterface"></a>CComTearOffObject:: QueryInterface

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*iid*<br/>
中所请求的接口的 IID。

*ppvObject*<br/>
弄指向由*iid*标识的接口指针的指针; 如果找不到接口, 则为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

首先查询脱离类的接口。 如果接口不存在, 则对所有者对象上的接口进行查询。 如果请求的接口为`IUnknown`, 则`IUnknown`返回所有者的。

##  <a name="release"></a>CComTearOffObject:: Release

将引用计数减一, 如果引用计数为零, 则删除`CComTearOffObject`。

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>返回值

在非调试版本中, 始终返回零。 在调试版本中, 将返回一个值, 该值对于诊断或测试可能很有用。

## <a name="see-also"></a>请参阅

[CComCachedTearOffObject 类](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
