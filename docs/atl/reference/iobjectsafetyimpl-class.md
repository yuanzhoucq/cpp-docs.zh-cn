---
title: IObjectSafetyImpl 类
ms.date: 11/04/2016
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
ms.openlocfilehash: 17a1b362f2cfe40be99c10298a780a6bf4f6419f
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503127"
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl 类

此类提供的默认实现`IObjectSafety`接口，以允许客户端来检索和设置对象的安全级别。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IObjectSafetyImpl`。

*dwSupportedSafety*<br/>
指定控件的受支持的安全选项。 可以是以下值之一：

- 由标识的接口 INTERFACESAFE_FOR_UNTRUSTED_CALLER [SetInterfaceSafetyOptions](#setinterfacesafetyoptions)参数`riid`应对安全执行脚本。

- 由标识的接口 INTERFACESAFE_FOR_UNTRUSTED_DATA`SetInterfaceSafetyOptions`参数`riid`应对安全不受信任数据的初始化过程。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|检索该对象支持的安全选项，以及当前为该对象设置安全选项。|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|使对象安全的初始化或脚本。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|存储对象的当前安全级别。|

## <a name="remarks"></a>备注

类`IObjectSafetyImpl`提供的默认实现`IObjectSafety`。 `IObjectSafety`接口允许客户端检索和设置对象的安全级别。 例如，web 浏览器可以调用`IObjectSafety::SetInterfaceSafetyOptions`控件设为可安全执行初始化或可安全执行脚本。

请注意，使用[IMPLEMENTED_CATEGORY](category-macros.md#implemented_category)宏 CATID_SafeForScripting 和 CATID_SafeForInitializing 组件类别与提供的指定组件的安全的替代方法。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="getinterfacesafetyoptions"></a>  IObjectSafetyImpl::GetInterfaceSafetyOptions

检索该对象支持的安全选项，以及当前为该对象设置安全选项。

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>备注

实现返回的对象的实现所支持的任何接口的相应值`IUnknown::QueryInterface`。

> [!IMPORTANT]
>  支持的任何对象`IObjectSafety`负责其自身的安全，并且它将委托的任何对象。 程序员必须考虑到帐户中用户的上下文中运行代码出现的问题、 跨站点脚本和执行适合区域检查。

请参阅[IObjectSafety::GetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\)) Windows SDK 中。

##  <a name="m_dwcurrentsafety"></a>  IObjectSafetyImpl::m_dwCurrentSafety

存储对象的当前安全级别。

```
DWORD m_dwCurrentSafety;
```

##  <a name="setinterfacesafetyoptions"></a>  IObjectSafetyImpl::SetInterfaceSafetyOptions

使对象安全的初始化或通过设置脚本编写[m_dwCurrentSafety](#m_dwcurrentsafety)成员添加到适当的值。

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>备注

实现不支持的对象的实现任何接口将返回 E_NOINTERFACE `IUnknown::QueryInterface`。

> [!IMPORTANT]
>  支持的任何对象`IObjectSafety`负责其自身的安全，并且它将委托的任何对象。 程序员必须考虑到帐户中用户的上下文中运行代码出现的问题、 跨站点脚本和执行适合区域检查。

请参阅[IObjectSafety::SetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\)) Windows SDK 中。

## <a name="see-also"></a>请参阅

[IObjectSafety 接口](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[类概述](../../atl/atl-class-overview.md)
