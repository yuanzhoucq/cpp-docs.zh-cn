---
title: CComContainedObject 类
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: 72ba27c3be6576621995ffb8c98995c6abc9324c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320785"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject 类

此类通过委派到所有者对象的`IUnknown`实现 I[未知。](/windows/win32/api/unknwn/nn-unknwn-iunknown)

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>参数

*基地*<br/>
您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCom包含对象：：Ccom包含对象](#ccomcontainedobject)|构造函数。 初始化指向所有者对象的成员指针`IUnknown`。|
|[CCom包含对象：*CCom包含对象](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom包含对象：：添加参考](#addref)|增加所有者对象的引用计数。|
|[CCom包含对象：获取控制未知](#getcontrollingunknown)|检索所有者对象的`IUnknown`。|
|[CCom包含对象：查询接口](#queryinterface)|检索指向所有者对象上请求的接口的指针。|
|[CCom包含对象：：发布](#release)|对所有者对象的引用计数进行声明。|

## <a name="remarks"></a>备注

ATL在`CComContainedObject`类[CComAggObject，CComPolyObject，](../../atl/reference/ccomaggobject-class.md)和[CComCachedTearOff对象](../../atl/reference/ccomcachedtearoffobject-class.md)中使用。 [CComPolyObject](../../atl/reference/ccompolyobject-class.md) `CComContainedObject`实现[I未知](/windows/win32/api/unknwn/nn-unknwn-iunknown)，通过委派到所有者对象的`IUnknown`。 （所有者是聚合的外部对象，或者是为其创建拆解接口的对象。`CComContainedObject`调用`CComObjectRootEx`的`OuterQueryInterface` `OuterAddRef`、和`OuterRelease`， 都`Base`通过 继承。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComContainedObject`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomcontainedobjectaddref"></a><a name="addref"></a>CCom包含对象：：添加参考

增加所有者对象的引用计数。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可用于诊断或测试的值。

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a>CCom包含对象：：Ccom包含对象

构造函数。

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
[在]所有者对象的`IUnknown`。

### <a name="remarks"></a>备注

将`m_pOuterUnknown`成员指针（通过`Base`类继承）设置为*pv*。

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a>CCom包含对象：*CCom包含对象

析构函数。

```
~CComContainedObject();
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a>CCom包含对象：获取控制未知

返回保存`m_pOuterUnknown`所有者对象的`IUnknown`的成员指针（通过*Base*类继承）

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>返回值

所有者对象的`IUnknown`。

### <a name="remarks"></a>备注

如果`Base`已声明[DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown)宏，则此方法可能是虚拟的。

## <a name="ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a>CCom包含对象：查询接口

检索指向所有者对象上请求的接口的指针。

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

## <a name="ccomcontainedobjectrelease"></a><a name="release"></a>CCom包含对象：：发布

对所有者对象的引用计数进行声明。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>返回值

在调试生成中`Release`，返回可用于诊断或测试的值。 在非调试生成中，`Release`始终返回 0。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
