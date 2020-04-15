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
ms.openlocfilehash: 6eee7585bc3c5587e106ab6b0cefb4b7129df59f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329651"
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl 类

此类提供接口的默认实现，`IObjectSafety`以允许客户端检索和设置对象的安全级别。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IObjectSafetyImpl`。

*dw支持安全*<br/>
指定控件的支持安全选项。 可以是以下值之一：

- INTERFACESAFE_FOR_UNTRUSTED_CALLER [SetInterface 安全选项](#setinterfacesafetyoptions)参数`riid`标识的接口应使脚本编写安全。

- INTERFACESAFE_FOR_UNTRUSTED_DATA 参数标识的`SetInterfaceSafetyOptions`接口`riid`应在初始化期间对不受信任的数据提供安全。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IObjectSafetyimpl：：获取接口安全选项](#getinterfacesafetyoptions)|检索对象支持的安全选项以及当前为对象设置的安全选项。|
|[IObjectSafetyimpl：：设置接口安全选项](#setinterfacesafetyoptions)|使对象安全进行初始化或脚本化。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[IObjectSafetyimpl：：m_dwCurrentSafety](#m_dwcurrentsafety)|存储对象的当前安全级别。|

## <a name="remarks"></a>备注

类`IObjectSafetyImpl`提供`IObjectSafety`的默认实现。 该`IObjectSafety`接口允许客户端检索和设置对象的安全级别。 例如，Web 浏览器可以调用`IObjectSafety::SetInterfaceSafetyOptions`以使控件安全用于初始化或脚本编写安全。

请注意，将[IMPLEMENTED_CATEGORY](category-macros.md#implemented_category)宏与CATID_SafeForScripting和CATID_SafeForInitializing组件类别一起使用提供了指定组件安全的替代方法。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a>IObjectSafetyimpl：：获取接口安全选项

检索对象支持的安全选项以及当前为对象设置的安全选项。

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>备注

实现返回对象实现 支持的任何接口的适当`IUnknown::QueryInterface`值。

> [!IMPORTANT]
> 支持`IObjectSafety`的任何对象都负责其自身的安全性及其委托的任何对象的安全性。 程序员必须考虑在用户上下文中运行代码、跨站点脚本和执行适当的区域检查所产生的问题。

请参阅[IObject 安全：获取](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\))Windows SDK 中的接口安全选项。

## <a name="iobjectsafetyimplm_dwcurrentsafety"></a><a name="m_dwcurrentsafety"></a>IObjectSafetyimpl：：m_dwCurrentSafety

存储对象的当前安全级别。

```
DWORD m_dwCurrentSafety;
```

## <a name="iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a>IObjectSafetyimpl：：设置接口安全选项

通过将[m_dwCurrentSafety](#m_dwcurrentsafety)成员设置为适当的值，使对象在初始化或脚本化方面安全。

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>备注

对于对象实现 不支持的任何接口，实现返回`IUnknown::QueryInterface`E_NOINTERFACE。

> [!IMPORTANT]
> 支持`IObjectSafety`的任何对象都负责其自身的安全性及其委托的任何对象的安全性。 程序员必须考虑在用户上下文中运行代码、跨站点脚本和执行适当的区域检查所产生的问题。

请参阅[IObject 安全：在](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\))Windows SDK 中设置接口安全选项。

## <a name="see-also"></a>另请参阅

[IObject安全接口](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[类概述](../../atl/atl-class-overview.md)
