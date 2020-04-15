---
title: CComClassFactorySingleton 类
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: ec860f7ef59b7d3289bf2e18fea0f0e064a7c8f9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320830"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton 类

此类派生自[CComClassFactory，](../../atl/reference/ccomclassfactory-class.md)并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造单个对象。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>参数

*T*<br/>
你的班级

`CComClassFactorySingleton`派生自[CComClassFactory，](../../atl/reference/ccomclassfactory-class.md)并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造单个对象。 对方法`CreateInstance`的每个调用都只是查询此对象作为接口指针。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComClass 工厂单一：：创建实例](#createinstance)|接口指针`m_spObj`的查询。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComClass工厂单顿：：m_spObj](#m_spobj)|由 构造的`CComClassFactorySingleton` [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象。|

## <a name="remarks"></a>备注

ATL 对象通常通过[CComCoClass](../../atl/reference/ccomcoclass-class.md)获得类工厂。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，它`CComClassFactory`声明为默认类工厂。 要使用`CComClassFactorySingleton`，请在对象的类定义中指定[DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)宏。 例如：

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClass 工厂](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a>CComClass 工厂单一：：创建实例

通过`QueryInterface`[m_spObj](#m_spobj)调用以检索接口指针。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>参数

*pUnkOuter*<br/>
[在]如果对象是作为聚合的一部分创建的，则*pUnkOuter*必须是外部未知对象。 否则 *，pUnkOuter*必须为 NULL。

*riid*<br/>
[在]请求接口的 IID。 如果*pUnkOuter*是非 NULL，*则 riid*必须为`IID_IUnknown`。

*普夫奥比*<br/>
[出]指向*riid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppvObj*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ccomclassfactorysingletonm_spobj"></a><a name="m_spobj"></a>CComClass工厂单顿：：m_spObj

由 构造的`CComClassFactorySingleton` [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象。

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>备注

[对 CreateInstance](#createinstance)方法的每个调用都只是查询此对象以作为接口指针。

请注意，当前`m_spObj`形式的与以前版本的 ATL`CComClassFactorySingleton`的工作方式相比，存在重大变化。 在以前的版本中，`CComClassFactorySingleton`对象是在服务器初始化期间与类工厂同时创建的。 在 Visual C++.NET 2003 及更高版本中，对象在第一个请求上被懒惰地创建。 此更改可能会导致依赖于早期初始化的程序中的错误。

## <a name="see-also"></a>另请参阅

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 类](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComclass 工厂自动线程类](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThread模型](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[类概述](../../atl/atl-class-overview.md)
