---
title: IPerPropertyBrowsingImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
dev_langs:
- C++
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8fc5cc44eeb06c5afec23b6a0a094c14987c599
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096088"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl 类

此类实现`IUnknown`和允许客户端访问对象的属性页中的信息。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IPerPropertyBrowsingImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|检索描述某一给定的属性的字符串。|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|检索与给定的属性可接受的值相对应的字符串数组。|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|检索包含由给定 DISPID 标识属性的值的变量。 使用从检索的字符串名称关联的 DISPID 是`GetPredefinedStrings`。 ATL 实现返回 E_NOTIMPL。|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|检索与给定属性相关联的属性页的 CLSID。|

## <a name="remarks"></a>备注

[IPerPropertyBrowsing](/windows/desktop/api/ocidl/nn-ocidl-iperpropertybrowsing)接口允许客户端访问对象的属性页中的信息。 类`IPerPropertyBrowsingImpl`提供默认实现此接口并实现`IUnknown`信息发送给转储调试中的设备生成。

> [!NOTE]
>  如果使用的 Microsoft Access 作为容器应用程序，您必须派生您的类从`IPerPropertyBrowsingImpl`。 否则，访问不会加载您的控件。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="getdisplaystring"></a>  IPerPropertyBrowsingImpl::GetDisplayString

检索描述某一给定的属性的字符串。

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>备注

请参阅[IPerPropertyBrowsing::GetDisplayString](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) Windows SDK 中。

##  <a name="getpredefinedstrings"></a>  IPerPropertyBrowsingImpl::GetPredefinedStrings

填充每个数组具有零个项目。

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>返回值

ATL 的实现[GetPredefinedValue](#getpredefinedvalue)返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IPerPropertyBrowsing::GetPredefinedStrings](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) Windows SDK 中。

##  <a name="getpredefinedvalue"></a>  IPerPropertyBrowsingImpl::GetPredefinedValue

检索包含由给定 DISPID 标识属性的值的变量。 使用从检索的字符串名称关联的 DISPID 是`GetPredefinedStrings`。

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

ATL 的实现[GetPredefinedStrings](#getpredefinedstrings)检索没有相应的字符串。

请参阅[IPerPropertyBrowsing::GetPredefinedValue](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) Windows SDK 中。

##  <a name="mappropertytopage"></a>  IPerPropertyBrowsingImpl::MapPropertyToPage

检索与指定的属性关联的属性页的 CLSID。

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射来获取此信息。

请参阅[IPerPropertyBrowsing::MapPropertyToPage](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) Windows SDK 中。

## <a name="see-also"></a>请参阅

[IPropertyPageImpl 类](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
