---
title: CComCo类
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: 11e724a982f3a2f404473dbdd34d848842cc8e14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320823"
---
# <a name="ccomcoclass-class"></a>CComCo类

此类提供用于创建类实例和获取其属性的方法。

## <a name="syntax"></a>语法

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`CComCoClass`。

*pclsid*<br/>
指向对象的 CLSID 的指针。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComCoClass：创建实例](#createinstance)|（静态）为接口创建类和查询的实例。|
|[CComCoClass：错误](#error)|（静态）将丰富的错误信息返回给客户端。|
|[CComCoClass：获取对象CLSID](#getobjectclsid)|（静态）返回对象的类标识符。|
|[CComCoClass：：获取对象描述](#getobjectdescription)|（静态）覆盖以返回对象的说明。|

## <a name="remarks"></a>备注

`CComCoClass`提供了检索对象的 CLSID、设置错误信息和创建类实例的方法。 在对象映射中注册的任何类都应派生自`CComCoClass`。

`CComCoClass`还定义了对象的默认类工厂和聚合模型。 `CComCoClass`使用以下两个宏：

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)声明类工厂为[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)。

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)声明可以聚合对象。

您可以通过在类定义中指定另一个宏来覆盖这些默认值中的任何一个。 例如，要使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)而不是`CComClassFactory`，请指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomcoclasscreateinstance"></a><a name="createinstance"></a>CComCoClass：创建实例

使用这些`CreateInstance`函数创建 COM 对象的实例，并在不使用 COM API 的情况下检索接口指针。

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>参数

*Q*<br/>
应通过*pp*返回的 COM 接口。

*朋克外*<br/>
[在]聚合的外部未知或控制未知。

*Pp*<br/>
[出]如果创建成功，接收请求的接口指针的指针变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。 有关可能的返回值的说明，请参阅 Windows SDK 中的[CoCreateInstance。](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)

### <a name="remarks"></a>备注

使用此函数的第一个重载来创建典型对象;当您需要聚合正在创建的对象时，请使用第二个重载。

实现所需 COM 对象的 ATL 类（即用作[CComCoClass](../../atl/reference/ccomcoclass-class.md)的第一个模板参数的类）必须与调用代码位于同一项目中。 COM 对象的创建由为此 ATL 类注册的类工厂执行。

这些函数可用于创建通过使用[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)宏阻止外部可创建的对象。 它们在您希望出于效率原因避免 COM API 的情况下也很有用。

请注意，接口*Q*必须具有与其关联的 IID，可以使用[__uuidof](../../cpp/uuidof-operator.md)运算符检索。

### <a name="example"></a>示例

在下面的示例中，`CDocument`是从实现接口`CComCoClass`的向导生成的 ATL 类派生的。 `IDocument` 类在对象映射中注册了OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO宏，因此客户端无法使用[CoCreate实例](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)创建文档实例。 `CApplication`CoClass 在其自己的 COM 接口中提供方法以创建文档类的实例。 下面的代码显示了使用从`CreateInstance``CComCoClass`基类继承的成员创建文档类实例的简便性。

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

## <a name="ccomcoclasserror"></a><a name="error"></a>CComCoClass：错误

此静态函数设置`IErrorInfo`接口以向客户端提供错误信息。

```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>参数

*lpszDesc*<br/>
[在]描述错误的字符串。 的`Error`Unicode 版本指定*lpszDesc*的类型为 LPCOLESTR;ANSI 版本指定 LPCSTR 的类型。

*Iid*<br/>
[在]如果错误由操作系统定义，则定义错误的接口的 IID 或GUID_NULL（默认值）。

*hRes*<br/>
[在]要返回给调用方的 HRESULT。 默认值为 0。 有关*hRe 的更多*详细信息，请参阅备注。

*nID*<br/>
[在]存储错误描述字符串的资源标识符。 此值应介于 0x0200 和 0xFF 之间（包括）。 在调试生成中，如果*nID*不索引有效字符串，则会产生**ASSERT。** 在发布版本中，错误描述字符串将设置为"未知错误"。

*dwHelpID*<br/>
[在]错误的帮助上下文标识符。

*lpszHelp文件*<br/>
[在]描述错误的帮助文件的路径和名称。

*hInst*<br/>
[在]资源的句柄。 默认情况下，此参数是`_AtlModule::GetResourceInstance` `_AtlModule` [，CAtlModule](../../atl/reference/catlmodule-class.md)的全局实例就是 。

### <a name="return-value"></a>返回值

标准 HRESULT 值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

要调用`Error`，对象必须实现`ISupportErrorInfo Interface`接口。

如果*hRes*参数是非零，则`Error`返回*hRes*的值。 如果*hRes*为零，则`Error`返回的前四个版本DISP_E_EXCEPTION。 最后两个版本返回宏**MAKE_HRESULT的结果（1、FACILITY_ITF、nID** *nID* **）。**

## <a name="ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a>CComCoClass：获取对象CLSID

提供了检索对象的 CLSID 的一致方法。

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>返回值

对象的类标识符。

## <a name="ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a>CComCoClass：：获取对象描述

此静态函数检索类对象的文本说明。

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>返回值

类对象的描述。

### <a name="remarks"></a>备注

默认实现返回 NULL。 您可以使用[DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description)宏重写此方法。 例如：

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`由`IComponentRegistrar::GetComponents`调用 。 `IComponentRegistrar`是一个自动化接口，允许您在 DLL 中注册和取消注册单个组件。 使用 ATL 项目向导创建组件注册器对象时，向导将自动实现`IComponentRegistrar`接口。 `IComponentRegistrar`通常用于 Microsoft 事务服务器。

有关 ATL 项目向导的详细信息，请参阅创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)的文章。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
