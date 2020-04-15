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
ms.openlocfilehash: de7528d3972991c233ee4b9037f609b89d0f7434
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327312"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject 类

此类实现分机接口。

## <a name="syntax"></a>语法

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>参数

*基地*<br/>
您的拆解类，派生自`CComTearOffObjectBase`您希望拆解对象支持的接口。

ATL分两个阶段实现其分管接口 -`CComTearOffObjectBase`该方法处理引用计数和`QueryInterface`，同时`CComTearOffObject`实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComTEARoff 对象：CComtearoff 对象](#ccomtearoffobject)|构造函数。|
|[CComTEARoff 对象：*CComtearoff 对象](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComTearoff 对象：：添加参考](#addref)|增加`CComTearOffObject`对象的引用计数。|
|[CComtearoff 对象：：查询接口](#queryinterface)|返回指向拆解类或所有者类上请求接口的指针。|
|[CComTearOff 对象：：发布](#release)|取消`CComTearOffObject`对象的引用计数并销毁它。|

### <a name="ccomtearoffobjectbase-methods"></a>CComTEAROff对象基础方法

|||
|-|-|
|[CComTEAROff 对象库](#ccomtearoffobjectbase)|构造函数。|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTEAROff 对象基础数据成员

|||
|-|-|
|[m_pOwner](#m_powner)|指向从所有者类`CComObject`派生的指针。|

## <a name="remarks"></a>备注

`CComTearOffObject`实现拆解接口作为单独的对象，仅在查询该接口时实例化。 当其引用计数变为零时，将删除拆解。 通常，为很少使用的接口构建分机接口，因为使用分泪将 vtable 指针保存在主对象的所有实例中。

应派生实现撕掉的类，`CComTearOffObjectBase`并从希望拆解对象支持哪个接口派生。 `CComTearOffObjectBase`在所有者类和线程模型上模板化。 所有者类是正在为其实现撕掉的对象的类。 如果不指定线程模型，则使用默认线程模型。

应为拆解类创建 COM 映射。 当 ATL 实例化撕裂时，它将创建`CComTearOffObject<CYourTearOffClass>`或`CComCachedTearOffObject<CYourTearOffClass>`。

例如，在 BEEPER 示例中，`CBeeper2`类是撕掉类，`CBeeper`类是所有者类：

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComTearOffObject`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomtearoffobjectaddref"></a><a name="addref"></a>CComTearoff 对象：：添加参考

将`CComTearOffObject`对象的引用计数增加一个。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>返回值

可用于诊断和测试的值。

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="ccomtearoffobject"></a>CComTEARoff 对象：CComtearoff 对象

构造函数。

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
[在]将转换为指向对象的指针的`CComObject<Owner>`指针。

### <a name="remarks"></a>备注

将所有者的引用计数增加一个。

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="dtor"></a>CComTEARoff 对象：*CComtearoff 对象

析构函数。

```
~CComTearOffObject();
```

### <a name="remarks"></a>备注

释放所有分配的资源，调用 FinalRelease，并递减模块锁计数。

## <a name="ccomtearoffobjectccomtearoffobjectbase"></a><a name="ccomtearoffobjectbase"></a>CComTEARoff 对象：CComtearoff 对象库

构造函数。

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>备注

将[m_pOwner](#m_powner)成员初始化为 NULL。

## <a name="ccomtearoffobjectm_powner"></a><a name="m_powner"></a>CComTearoff 对象：：m_pOwner

指向从*所有者*派生的[CComObject](../../atl/reference/ccomobject-class.md)对象的指针。

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>参数

*所有者*<br/>
[在]正在为其实现撕扯的类。

### <a name="remarks"></a>备注

指针在构造期间初始化为 NULL。

## <a name="ccomtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComtearoff 对象：：查询接口

检索指向所请求的接口的指针。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]请求的接口的 IID。

*ppvObject*<br/>
[出]指向*iid*标识的接口指针，如果找不到接口，则指向 NULL 的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

首先查询拆解类上的接口。 如果接口不存在，则查询所有者对象上的接口。 如果请求的接口为`IUnknown`，则`IUnknown`返回所有者。

## <a name="ccomtearoffobjectrelease"></a><a name="release"></a>CComTearOff 对象：：发布

将引用计数除以 1，如果引用计数为零，则删除 。 `CComTearOffObject`

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>返回值

在非调试生成中，始终返回零。 在调试生成中，返回可用于诊断或测试的值。

## <a name="see-also"></a>另请参阅

[CComCachedTearOffObject 类](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
