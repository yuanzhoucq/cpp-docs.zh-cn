---
title: CComCoClass 类
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
ms.openlocfilehash: 5b4e39fa4d93893d288bb8de03d8a71b671be087
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497400"
---
# <a name="ccomcoclass-class"></a>CComCoClass 类

此类提供用于创建类的实例并获取其属性的方法。

## <a name="syntax"></a>语法

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`CComCoClass`的类。

*pclsid*<br/>
指向对象的 CLSID 的指针。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComCoClass::CreateInstance](#createinstance)|静止创建类的实例并查询接口。|
|[CComCoClass::Error](#error)|静止向客户端返回丰富的错误信息。|
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|静止返回对象的类标识符。|
|[CComCoClass::GetObjectDescription](#getobjectdescription)|静止重写以返回对象的说明。|

## <a name="remarks"></a>备注

`CComCoClass`提供用于检索对象的 CLSID、设置错误信息以及创建类的实例的方法。 对象映射中注册的任何类都应派生自`CComCoClass`。

`CComCoClass`还定义对象的默认类工厂和聚合模型。 `CComCoClass`使用以下两个宏:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)声明要[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)的类工厂。

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)声明可以聚合您的对象。

您可以通过在类定义中指定另一个宏来重写这些默认值之一。 例如, 若要使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)而不`CComClassFactory`是, 请指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="createinstance"></a>CComCoClass:: CreateInstance

使用这些`CreateInstance`函数创建 com 对象的实例, 并在不使用 COM API 的情况下检索接口指针。

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>参数

*Q*<br/>
应通过*pp*返回的 COM 接口。

*punkOuter*<br/>
中外部未知或控制聚合的未知。

*pp*<br/>
弄如果创建成功, 则为接收请求的接口指针的指针变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。 有关可能的返回值的说明, 请参阅中的[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) Windows SDK。

### <a name="remarks"></a>备注

使用此函数的第一个重载来创建典型的对象;需要聚合正在创建的对象时, 请使用第二个重载。

实现必需 COM 对象 (即, 用作[CComCoClass](../../atl/reference/ccomcoclass-class.md)的第一个模板参数的类) 的 ATL 类必须与调用代码位于同一项目中。 COM 对象的创建由为此 ATL 类注册的类工厂来执行。

这些函数可用于创建已阻止使用[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)宏进行外部创建的对象。 对于出于效率原因而要避免 COM API 的情况, 它们也非常有用。

请注意, 接口*Q*必须具有与之关联的 IID, 可以使用[__uuidof](../../cpp/uuidof-operator.md)运算符来检索它。

### <a name="example"></a>示例

在下面的示例中`CDocument` , 是一个由向导生成的、派生`CComCoClass`自的 ATL `IDocument`类, 该类实现接口。 类在对象映射中使用 OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO 宏注册, 因此客户端无法使用[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)创建文档的实例。 `CApplication`是一个组件类, 它提供了一个方法, 用于创建该文档类的实例的一个 COM 接口。 下面的代码演示了如何轻松地使用`CreateInstance` `CComCoClass`从基类继承的成员创建 document 类的实例。

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

##  <a name="error"></a>CComCoClass:: Error

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
中描述错误的字符串。 的`Error` Unicode 版本指定*lpszDesc*的类型为 LPCOLESTR; ANSI 版本指定 LPCSTR 的类型。

*iid*<br/>
中定义错误的接口的 IID 或 GUID_NULL (默认值) (如果错误由操作系统定义)。

*hRes*<br/>
中要返回给调用方的 HRESULT。 默认值为 0。 有关*hRes*的更多详细信息, 请参阅 "备注"。

*nID*<br/>
中存储错误说明字符串的资源标识符。 此值应介于0x0200 和0xFFFF 之间, 包括在内。 在调试版本中, 如果*nID*未为有效字符串编制索引, 则会产生**断言**。 在发布版本中, 错误描述字符串将设置为 "未知错误"。

*dwHelpID*<br/>
中错误的帮助上下文标识符。

*lpszHelpFile*<br/>
中描述错误的帮助文件的路径和名称。

*hInst*<br/>
中资源的句柄。 默认情况下, 此参数`_AtlModule::GetResourceInstance`为, `_AtlModule`其中是[CAtlModule](../../atl/reference/catlmodule-class.md)的全局实例。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。 有关详细信息，请参阅“备注”。

### <a name="remarks"></a>备注

若要`Error`调用, 你的对象必须`ISupportErrorInfo Interface`实现接口。

如果*hRes*参数为非零值, `Error`则返回*hRes*的值。 如果*hRes*为零, 则`Error`返回 DISP_E_EXCEPTION 的前四个版本。 最后两个版本返回宏**MAKE_HRESULT (1, FACILITY_ITF,** *nID* **)** 的结果。

##  <a name="getobjectclsid"></a>CComCoClass:: GetObjectCLSID

提供了一种一致的方法来检索对象的 CLSID。

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>返回值

对象的类标识符。

##  <a name="getobjectdescription"></a>CComCoClass:: GetObjectDescription

此静态函数检索类对象的文本说明。

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>返回值

类对象的说明。

### <a name="remarks"></a>备注

默认实现返回 NULL。 可以用[DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description)宏重写此方法。 例如:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`由`IComponentRegistrar::GetComponents`调用。 `IComponentRegistrar`是一个自动化接口, 可用于注册和取消注册 DLL 中的单个组件。 使用 ATL 项目向导创建组件注册器对象时, 向导将自动实现`IComponentRegistrar`接口。 `IComponentRegistrar`通常由 Microsoft 事务服务器使用。

有关 ATL 项目向导的详细信息, 请参阅文章[创建 Atl 项目](../../atl/reference/creating-an-atl-project.md)。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
