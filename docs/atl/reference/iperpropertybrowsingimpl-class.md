---
title: IPerPropertyBrowsingImpl 类
ms.date: 11/04/2016
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
ms.openlocfilehash: f8fb80cc38e775b9b26afa033647faac694e968a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326517"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl 类

此类实现`IUnknown`并允许客户端访问对象的属性页中的信息。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

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

|名称|说明|
|----------|-----------------|
|[IPer属性浏览：：获取显示字符串](#getdisplaystring)|检索描述给定属性的字符串。|
|[IPerProperty 浏览：：获取预定义的字符串](#getpredefinedstrings)|检索与给定属性可以接受的值对应的字符串数组。|
|[IPerProperty 浏览：：获取预定义价值](#getpredefinedvalue)|检索包含给定 DISPID 标识的属性的值的 VARIANT。 DISPID 与从`GetPredefinedStrings`检索到的字符串名称相关联。 ATL 实现返回E_NOTIMPL。|
|[IPer属性浏览：：映射属性页](#mappropertytopage)|检索与给定属性关联的属性页的 CLSID。|

## <a name="remarks"></a>备注

[IPerProperty 浏览](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing)界面允许客户端访问对象属性页中的信息。 类`IPerPropertyBrowsingImpl`通过在调试生成中向转储设备发送`IUnknown`信息来提供此接口的默认实现和实现。

> [!NOTE]
> 如果使用 Microsoft Access 作为容器应用程序，则必须从`IPerPropertyBrowsingImpl`派生类。 否则，Access 将不会加载您的控件。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="iperpropertybrowsingimplgetdisplaystring"></a><a name="getdisplaystring"></a>IPer属性浏览：：获取显示字符串

检索描述给定属性的字符串。

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>备注

请参阅[IPer 属性浏览：：在](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring)Windows SDK 中获取显示字符串。

## <a name="iperpropertybrowsingimplgetpredefinedstrings"></a><a name="getpredefinedstrings"></a>IPerProperty 浏览：：获取预定义的字符串

用零项填充每个数组。

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>返回值

ATL 对[GetPreValue 的](#getpredefinedvalue)实现E_NOTIMPL回报。

### <a name="remarks"></a>备注

请参阅[IPer 属性浏览：：在](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings)Windows SDK 中获取预定义的字符串。

## <a name="iperpropertybrowsingimplgetpredefinedvalue"></a><a name="getpredefinedvalue"></a>IPerProperty 浏览：：获取预定义价值

检索包含给定 DISPID 标识的属性的值的 VARIANT。 DISPID 与从`GetPredefinedStrings`检索到的字符串名称相关联。

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

ATL 的[GetPre 定义字符串](#getpredefinedstrings)的实现不会检索相应的字符串。

请参阅[IPerProperty 浏览：：在](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue)Windows SDK 中获取预定义值。

## <a name="iperpropertybrowsingimplmappropertytopage"></a><a name="mappropertytopage"></a>IPer属性浏览：：映射属性页

检索与指定属性关联的属性页的 CLSID。

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射来获取此信息。

请参阅[IPer 属性浏览：：Windows SDK 中的映射属性到页面](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage)。

## <a name="see-also"></a>另请参阅

[IPropertyPageImpl 类](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
