---
title: IAxWinAmbientDispatch 接口
ms.date: 11/04/2016
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
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: 6a4f5322d957b1e978bd123db3b4796be6b300da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330013"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch 接口

此接口提供用于指定托管控件或容器特征的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|属性`AllowContextMenu`指定是否允许托管控件显示其自己的上下文菜单。|
|[get_AllowShowUI](#get_allowshowui)|该`AllowShowUI`属性指定是否允许托管控件显示其自己的用户界面。|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|属性`AllowWindowlessActivation`指定容器是否允许无窗口激活。|
|[get_BackColor](#get_backcolor)|属性`BackColor`指定容器的环境背景颜色。|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault`是一个环境属性，允许控件找出它是默认控件。|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|属性`DocHostDoubleClickFlags`指定响应双击而应执行的操作。|
|[get_DocHostFlags](#get_dochostflags)|该`DocHostFlags`属性指定主机对象的用户界面功能。|
|[get_Font](#get_font)|属性`Font`指定容器的环境字体。|
|[get_ForeColor](#get_forecolor)|属性`ForeColor`指定容器的环境前景颜色。|
|[get_LocaleID](#get_localeid)|属性`LocaleID`指定容器的环境区域设置 ID。|
|[get_MessageReflect](#get_messagereflect)|环境`MessageReflect`属性指定容器是否将消息反映到托管控件。|
|[get_OptionKeyPath](#get_optionkeypath)|该`OptionKeyPath`属性指定用户设置的注册表键路径。|
|[get_ShowGrabHandles](#get_showgrabhandles)|环境`ShowGrabHandles`属性允许控件找出是否应使用抓取手柄绘制自身。|
|[get_ShowHatching](#get_showhatching)|环境`ShowHatching`属性允许控件找出是否应绘制自身阴影。|
|[get_UserMode](#get_usermode)|该`UserMode`属性指定容器的环境用户模式。|
|[put_AllowContextMenu](#put_allowcontextmenu)|属性`AllowContextMenu`指定是否允许托管控件显示其自己的上下文菜单。|
|[put_AllowShowUI](#put_allowshowui)|该`AllowShowUI`属性指定是否允许托管控件显示其自己的用户界面。|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|属性`AllowWindowlessActivation`指定容器是否允许无窗口激活。|
|[put_BackColor](#put_backcolor)|属性`BackColor`指定容器的环境背景颜色。|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault`是一个环境属性，允许控件找出它是默认控件。|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|属性`DocHostDoubleClickFlags`指定响应双击而应执行的操作。|
|[put_DocHostFlags](#put_dochostflags)|该`DocHostFlags`属性指定主机对象的用户界面功能。|
|[put_Font](#put_font)|属性`Font`指定容器的环境字体。|
|[put_ForeColor](#put_forecolor)|属性`ForeColor`指定容器的环境前景颜色。|
|[put_LocaleID](#put_localeid)|属性`LocaleID`指定容器的环境区域设置 ID。|
|[put_MessageReflect](#put_messagereflect)|环境`MessageReflect`属性指定容器是否将消息反映到托管控件。|
|[put_OptionKeyPath](#put_optionkeypath)|该`OptionKeyPath`属性指定用户设置的注册表键路径。|
|[put_UserMode](#put_usermode)|该`UserMode`属性指定容器的环境用户模式。|

## <a name="remarks"></a>备注

此接口由 ATL 的 ActiveX 控件托管对象公开。 调用此接口上的方法以设置托管控件可用的环境属性或指定容器行为的其他方面。 要补充 提供`IAxWinAmbientDispatch`的属性，请使用[IAxWin 环境调度Ex](../../atl/reference/iaxwinambientdispatchex-interface.md)。

<xref:System.Windows.Forms.AxHost>将尝试加载有关`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`从包含代码的 typelib 的类型信息。

如果要链接到 ATL90.dll，AXHost 将从 DLL 中的 typelib 加载类型信息。 **AXHost**

有关详细信息[，请参阅使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

## <a name="requirements"></a>要求

此接口的定义有多种形式，如下表所示。

|定义类型|文件|
|---------------------|----------|
|Idl|atliface.idl|
|类型库|ATL.dll|
|C++|atliface.h （也包含在 ATLBase.h 中）|

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWin 环境调度：：get_AllowContextMenu

属性`AllowContextMenu`指定是否允许托管控件显示其自己的上下文菜单。

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>参数

*pbAllow 上下文菜单*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a>IAxWin 环境调度：：get_AllowShowUI

该`AllowShowUI`属性指定是否允许托管控件显示其自己的用户界面。

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>参数

*pbAllowShowUI*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_FALSE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWin 环境调度：：get_AllowWindowlessActivation

属性`AllowWindowlessActivation`指定容器是否允许无窗口激活。

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>参数

*pbAllow 无窗口*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a>IAxWin 环境调度：：get_BackColor

属性`BackColor`指定容器的环境背景颜色。

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>参数

*pclr背景*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用COLOR_BTNFACE或COLOR_WINDOW作为此属性的默认值（取决于主机窗口的父对象是否是对话框）。

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a>IAxWin 环境调度：：get_DisplayAsDefault

`DisplayAsDefault`是一个环境属性，允许控件找出它是默认控件。

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>参数

*pb 显示AsDefault*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_FALSE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWin 环境调度：：get_DocHostDoubleClickFlags

属性`DocHostDoubleClickFlags`指定响应双击而应执行的操作。

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>参数

*pdwDocHost双击标志*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用DOCHOSTUIDBLCLK_DEFAULT作为此属性的默认值。

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a>IAxWin 环境调度：：get_DocHostFlags

该`DocHostFlags`属性指定主机对象的用户界面功能。

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>参数

*pdwDocHostFlags*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用DOCHOSTUIFLAG_NO3DBORDER作为此属性的默认值。

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a>IAxWin 环境调度：：get_Font

属性`Font`指定容器的环境字体。

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
[出]用于接收此属性的`IFontDisp`当前值的接口指针的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用默认 GUI 字体或系统字体作为此属性的默认值。

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a>IAxWin 环境调度：：get_ForeColor

属性`ForeColor`指定容器的环境前景颜色。

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>参数

*pclr前景*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用系统窗口文本颜色作为此属性的默认值。

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a>IAxWin 环境调度：：get_LocaleID

属性`LocaleID`指定容器的环境区域设置 ID。

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>参数

*plcidLocaleID*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用用户的默认区域设置作为此属性的默认值。

使用此方法，您可以发现环境局部 ID，即控件正在使用的程序的 LocaleID。 了解区域设置ID后，可以调用代码从资源文件或附属 DLL 加载特定于区域设置的标题、错误消息文本等。

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a>IAxWin 环境调度：：get_MessageReflect

环境`MessageReflect`属性指定容器是否将消息反映到托管控件。

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>参数

*pbMessage 反射*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a>IAxWin 环境调度：：get_OptionKeyPath

该`OptionKeyPath`属性指定用户设置的注册表键路径。

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>参数

*pbstrOptionKeyPath*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWin 环境调度：：get_ShowGrabHandles

环境`ShowGrabHandles`属性允许控件找出是否应使用抓取手柄绘制自身。

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>参数

*pbShowGrabHandles*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现始终返回VARIANT_FALSE作为此属性的值。

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a>IAxWin 环境调度：：get_ShowHatching

环境`ShowHatching`属性允许控件找出是否应绘制自身阴影。

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>参数

*pbShowHatching*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现始终返回VARIANT_FALSE作为此属性的值。

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a>IAxWin 环境调度：：get_UserMode

该`UserMode`属性指定容器的环境用户模式。

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>参数

*pbUser 模式*<br/>
[出]用于接收此属性的当前值的变量的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxwin 环境调度：:put_允许上下文菜单

属性`AllowContextMenu`指定是否允许托管控件显示其自己的上下文菜单。

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>参数

*bAllowContext菜单*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a>IAxWin 环境调度：:put_允许ShowUI

该`AllowShowUI`属性指定是否允许托管控件显示其自己的用户界面。

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>参数

*bAllowShowUI*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_FALSE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxwin 环境调度：:put_允许无窗口激活

属性`AllowWindowlessActivation`指定容器是否允许无窗口激活。

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>参数

*bAllow 无窗口*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a>IAxWin 环境调度：:put_背面颜色

属性`BackColor`指定容器的环境背景颜色。

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>参数

*clrBackground*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用COLOR_BTNFACE或COLOR_WINDOW作为此属性的默认值（取决于主机窗口的父对象是否是对话框）。

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a>IAxWin 环境调度：:put_显示作为默认

`DisplayAsDefault`是一个环境属性，允许控件找出它是默认控件。

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>参数

*b 显示默认*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_FALSE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxwin 环境调度：:put_DocHost 双键单击标志

属性`DocHostDoubleClickFlags`指定响应双击而应执行的操作。

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>参数

*dwDocHost双击标志*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用DOCHOSTUIDBLCLK_DEFAULT作为此属性的默认值。

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a>IAxWin 环境调度：:put_DocHostFlags

该`DocHostFlags`属性指定主机对象的用户界面功能。

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>参数

*dwDocHostFlags*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用DOCHOSTUIFLAG_NO3DBORDER作为此属性的默认值。

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a>IAxWin 环境调度：:put_Font

属性`Font`指定容器的环境字体。

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用默认 GUI 字体或系统字体作为此属性的默认值。

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a>IAxWin 环境调度：:put_ForeColor

属性`ForeColor`指定容器的环境前景颜色。

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>参数

*clr前景*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用系统窗口文本颜色作为此属性的默认值。

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a>IAxWin 环境调度：:put_localeID

属性`LocaleID`指定容器的环境区域设置 ID。

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>参数

*lcidLocaleID*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用用户的默认区域设置作为此属性的默认值。

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a>IAxWin 环境调度：:put_消息反射

环境`MessageReflect`属性指定容器是否将消息反映到托管控件。

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>参数

*b消息反射*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a>IAxWin 环境调度：:put_选项关键路径

该`OptionKeyPath`属性指定用户设置的注册表键路径。

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>参数

*bstrOptionKeyPath*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a>IAxWin 环境调度：:put_用户模式

该`UserMode`属性指定容器的环境用户模式。

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>参数

*用户模式*<br/>
[在]此属性的新值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

ATL 主机对象实现使用VARIANT_TRUE作为此属性的默认值。

## <a name="see-also"></a>另请参阅

[IAxWinAmbientDispatchEx 接口](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow 接口](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAx 窗口：：查询主机](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
