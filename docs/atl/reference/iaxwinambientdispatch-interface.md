---
title: IAxWinAmbientDispatch 接口 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5bb644e43a5dd5085c53d0428f892cccd424fc1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766680"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch 接口

此接口提供了用于指定承载的控件或容器的特征的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|`AllowContextMenu`属性指定是否允许所承载的控件以显示其自己的上下文菜单。|
|[get_AllowShowUI](#get_allowshowui)|`AllowShowUI`属性指定是否允许所承载的控件以显示其自己的用户界面。|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|`AllowWindowlessActivation`属性指定容器是否允许无窗口激活。|
|[get_BackColor](#get_backcolor)|`BackColor`属性指定的容器的环境背景色。|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` 为环境属性，若要了解是否它是默认控件的控件。|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|`DocHostDoubleClickFlags`属性指定应执行一次双击响应的操作。|
|[get_DocHostFlags](#get_dochostflags)|`DocHostFlags`属性指定该主机对象的用户界面功能。|
|[get_Font](#get_font)|`Font`属性指定的容器的环境的字体。|
|[get_ForeColor](#get_forecolor)|`ForeColor`属性指定的容器的环境前景色。|
|[get_LocaleID](#get_localeid)|`LocaleID`属性指定的容器的环境的区域设置 ID。|
|[get_MessageReflect](#get_messagereflect)|`MessageReflect`环境属性指定是否在容器将反映到所承载的控件的消息。|
|[get_OptionKeyPath](#get_optionkeypath)|`OptionKeyPath`属性指定对用户设置的注册表项路径。|
|[get_ShowGrabHandles](#get_showgrabhandles)|`ShowGrabHandles`环境属性允许要找出是否它应绘制本身使用随取即行句柄的控件。|
|[get_ShowHatching](#get_showhatching)|`ShowHatching`环境属性允许要找出是否它应绘制阴影线本身的控件。|
|[get_UserMode](#get_usermode)|`UserMode`属性指定的容器的环境的用户模式。|
|[put_AllowContextMenu](#put_allowcontextmenu)|`AllowContextMenu`属性指定是否允许所承载的控件以显示其自己的上下文菜单。|
|[put_AllowShowUI](#put_allowshowui)|`AllowShowUI`属性指定是否允许所承载的控件以显示其自己的用户界面。|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|`AllowWindowlessActivation`属性指定容器是否允许无窗口激活。|
|[put_BackColor](#put_backcolor)|`BackColor`属性指定的容器的环境背景色。|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` 为环境属性，若要了解是否它是默认控件的控件。|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|`DocHostDoubleClickFlags`属性指定应执行一次双击响应的操作。|
|[put_DocHostFlags](#put_dochostflags)|`DocHostFlags`属性指定该主机对象的用户界面功能。|
|[put_Font](#put_font)|`Font`属性指定的容器的环境的字体。|
|[put_ForeColor](#put_forecolor)|`ForeColor`属性指定的容器的环境前景色。|
|[put_LocaleID](#put_localeid)|`LocaleID`属性指定的容器的环境的区域设置 ID。|
|[put_MessageReflect](#put_messagereflect)|`MessageReflect`环境属性指定是否在容器将反映到所承载的控件的消息。|
|[put_OptionKeyPath](#put_optionkeypath)|`OptionKeyPath`属性指定对用户设置的注册表项路径。|
|[put_UserMode](#put_usermode)|`UserMode`属性指定的容器的环境的用户模式。|

## <a name="remarks"></a>备注

此接口由 ATL 的 ActiveX 控件承载对象公开。 将可用的环境属性设置为所承载的控件或指定容器的行为的其他方面此接口上调用的方法。 若要通过所提供的属性来对补充`IAxWinAmbientDispatch`，使用[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)。

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)会尝试加载有关类型信息`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`从类型库包含的代码。

如果要链接到 ATL90.dll， **AXHost**将从类型库 DLL 中加载的类型信息。

请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)的更多详细信息。

## <a name="requirements"></a>要求

此接口的定义有多种形式下, 表中所示。

|定义类型|文件|
|---------------------|----------|
|IDL|atliface.idl|
|类型库|ATL.dll|
|C++|atliface.h （也包括在 ATLBase.h）|

##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu

`AllowContextMenu`属性指定是否允许所承载的控件以显示其自己的上下文菜单。

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>参数

*pbAllowContextMenu*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_TRUE。

##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI

`AllowShowUI`属性指定是否允许所承载的控件以显示其自己的用户界面。

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>参数

*pbAllowShowUI*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_FALSE。

##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation

`AllowWindowlessActivation`属性指定容器是否允许无窗口激活。

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>参数

*pbAllowWindowless*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_TRUE。

##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor

`BackColor`属性指定的容器的环境背景色。

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>参数

*pclrBackground*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用 COLOR_BTNFACE 或 COLOR_WINDOW 作为此属性 （具体取决于主机窗口的父级是否为一个对话框） 的默认值。

##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault` 为环境属性，若要了解是否它是默认控件的控件。

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>参数

*pbDisplayAsDefault*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_FALSE。

##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`属性指定应执行一次双击响应的操作。

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>参数

*pdwDocHostDoubleClickFlags*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用 DOCHOSTUIDBLCLK_DEFAULT 作为此属性的默认值。

##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags

`DocHostFlags`属性指定该主机对象的用户界面功能。

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>参数

*pdwDocHostFlags*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用 DOCHOSTUIFLAG_NO3DBORDER 作为此属性的默认值。

##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font

`Font`属性指定的容器的环境的字体。

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>参数

*pFont*  
[out]地址`IFontDisp`用来接收此属性的当前值的接口指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用的默认 GUI 字体或系统字体作为此属性的默认值。

##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor

`ForeColor`属性指定的容器的环境前景色。

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>参数

*pclrForeground*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值作为系统窗口文本颜色。

##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID

`LocaleID`属性指定的容器的环境的区域设置 ID。

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>参数

*plcidLocaleID*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值作为用户的默认区域设置。

可以使用此方法发现环境 LocalID，也就是说，该程序的 LocaleID 控件正在使用中。 一旦知道 LocaleID，可以从资源文件或附属 DLL，依此类推调用代码以加载特定于区域设置的隐藏式字幕，错误消息文本。

##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect

`MessageReflect`环境属性指定是否在容器将反映到所承载的控件的消息。

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>参数

*pbMessageReflect*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_TRUE。

##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath

`OptionKeyPath`属性指定对用户设置的注册表项路径。

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>参数

*pbstrOptionKeyPath*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles

`ShowGrabHandles`环境属性允许要找出是否它应绘制本身使用随取即行句柄的控件。

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>参数

*pbShowGrabHandles*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现始终返回此属性的值为 VARIANT_FALSE。

##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching

`ShowHatching`环境属性允许要找出是否它应绘制阴影线本身的控件。

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>参数

*pbShowHatching*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现始终返回此属性的值为 VARIANT_FALSE。

##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode

`UserMode`属性指定的容器的环境的用户模式。

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>参数

*pbUserMode*  
[out]要接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_TRUE。

##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu

`AllowContextMenu`属性指定是否允许所承载的控件以显示其自己的上下文菜单。

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>参数

*bAllowContextMenu*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_TRUE。

##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI

`AllowShowUI`属性指定是否允许所承载的控件以显示其自己的用户界面。

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>参数

*bAllowShowUI*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_FALSE。

##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation

`AllowWindowlessActivation`属性指定容器是否允许无窗口激活。

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>参数

*bAllowWindowless*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_TRUE。

##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor

`BackColor`属性指定的容器的环境背景色。

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>参数

*clrBackground*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用 COLOR_BTNFACE 或 COLOR_WINDOW 作为此属性 （具体取决于主机窗口的父级是否为一个对话框） 的默认值。

##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault` 为环境属性，若要了解是否它是默认控件的控件。

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>参数

*bDisplayAsDefault*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_FALSE。

##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`属性指定应执行一次双击响应的操作。

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>参数

*dwDocHostDoubleClickFlags*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用 DOCHOSTUIDBLCLK_DEFAULT 作为此属性的默认值。

##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags

`DocHostFlags`属性指定该主机对象的用户界面功能。

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>参数

*dwDocHostFlags*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用 DOCHOSTUIFLAG_NO3DBORDER 作为此属性的默认值。

##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font

`Font`属性指定的容器的环境的字体。

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>参数

*pFont*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用的默认 GUI 字体或系统字体作为此属性的默认值。

##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor

`ForeColor`属性指定的容器的环境前景色。

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>参数

*clrForeground*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值作为系统窗口文本颜色。

##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID

`LocaleID`属性指定的容器的环境的区域设置 ID。

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>参数

*lcidLocaleID*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值作为用户的默认区域设置。

##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect

`MessageReflect`环境属性指定是否在容器将反映到所承载的控件的消息。

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>参数

*bMessageReflect*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_TRUE。

##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath

`OptionKeyPath`属性指定对用户设置的注册表项路径。

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>参数

*bstrOptionKeyPath*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode

`UserMode`属性指定的容器的环境的用户模式。

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>参数

*bUserMode*  
[in]此属性的新值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用此属性的默认值为 VARIANT_TRUE。

## <a name="see-also"></a>请参阅

[IAxWinAmbientDispatchEx 接口](../../atl/reference/iaxwinambientdispatchex-interface.md)   
[IAxWinHostWindow 接口](../../atl/reference/iaxwinhostwindow-interface.md)   
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

