---
title: "IAxWinAmbientDispatch 界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatch
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 2352b970c81f58d164fb47a6d7a4728c708d864a
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch 接口
此接口提供用于指定承载的控件或容器的特征的方法。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
interface IAxWinAmbientDispatch : IDispatch
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[get_AllowContextMenu](#get_allowcontextmenu)|**AllowContextMenu**属性指定是否允许所承载的控件以显示上下文菜单。|  
|[get_AllowShowUI](#get_allowshowui)|**AllowShowUI**属性指定是否允许所承载的控件来显示其自身用户界面。|  
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|**AllowWindowlessActivation**属性指定是否在容器上允许无窗口激活。|  
|[get_BackColor](#get_backcolor)|`BackColor`属性指定的容器的环境背景色。|  
|[get_DisplayAsDefault](#get_displayasdefault)|**DisplayAsDefault**是一个允许控件以查看它是否具有默认控件的环境属性。|  
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|**DocHostDoubleClickFlags**属性指定应发生以响应一次双击该操作。|  
|[get_DocHostFlags](#get_dochostflags)|**DocHostFlags**属性指定该主机对象的用户界面功能。|  
|[get_Font](#get_font)|**字体**属性指定的容器的环境的字体。|  
|[get_ForeColor](#get_forecolor)|`ForeColor`属性指定的容器的环境前景色。|  
|[get_LocaleID](#get_localeid)|**LocaleID**属性指定的容器的环境的区域设置 ID。|  
|[get_MessageReflect](#get_messagereflect)|**MessageReflect**环境属性指定是否在容器将反映到所承载的控件的消息。|  
|[get_OptionKeyPath](#get_optionkeypath)|**OptionKeyPath**属性指定为用户设置的注册表项路径。|  
|[get_ShowGrabHandles](#get_showgrabhandles)|**ShowGrabHandles**环境属性允许要查找是否它应自行绘制使用抓图句柄的控件。|  
|[get_ShowHatching](#get_showhatching)|**ShowHatching**环境属性允许要查找是否它应将自身影线绘制的控件。|  
|[get_UserMode](#get_usermode)|**UserMode**属性指定的容器的环境的用户模式。|  
|[put_AllowContextMenu](#put_allowcontextmenu)|**AllowContextMenu**属性指定是否允许所承载的控件以显示上下文菜单。|  
|[put_AllowShowUI](#put_allowshowui)|**AllowShowUI**属性指定是否允许所承载的控件来显示其自身用户界面。|  
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|**AllowWindowlessActivation**属性指定是否在容器上允许无窗口激活。|  
|[put_BackColor](#put_backcolor)|`BackColor`属性指定的容器的环境背景色。|  
|[put_DisplayAsDefault](#put_displayasdefault)|**DisplayAsDefault**是一个允许控件以查看它是否具有默认控件的环境属性。|  
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|**DocHostDoubleClickFlags**属性指定应发生以响应一次双击该操作。|  
|[put_DocHostFlags](#put_dochostflags)|**DocHostFlags**属性指定该主机对象的用户界面功能。|  
|[put_Font](#put_font)|**字体**属性指定的容器的环境的字体。|  
|[put_ForeColor](#put_forecolor)|`ForeColor`属性指定的容器的环境前景色。|  
|[put_LocaleID](#put_localeid)|**LocaleID**属性指定的容器的环境的区域设置 ID。|  
|[put_MessageReflect](#put_messagereflect)|**MessageReflect**环境属性指定是否在容器将反映到所承载的控件的消息。|  
|[put_OptionKeyPath](#put_optionkeypath)|**OptionKeyPath**属性指定为用户设置的注册表项路径。|  
|[put_UserMode](#put_usermode)|**UserMode**属性指定的容器的环境的用户模式。|  
  
## <a name="remarks"></a>备注  
 此接口由 ATL 的 ActiveX 控件承载对象公开。 将可用的环境属性设置为所承载的控件或指定容器的行为的其他方面此接口上调用的方法。 若要补充提供的属性`IAxWinAmbientDispatch`，使用[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)。  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)将尝试加载的类型信息有关`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`从类型库包含的代码。  
  
 如果要链接到 ATL90.dll， **AXHost**将从类型库 DLL 中加载的类型信息。  
  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)的更多详细信息。  
  
## <a name="requirements"></a>要求  
 此接口的定义有多种形式，如下面的表中所示。  
  
|定义类型|文件|  
|---------------------|----------|  
|IDL|atliface.idl|  
|类型库|ATL.dll|  
|C++|atliface.h （也包括在 ATLBase.h）|  
  
##  <a name="a-namegetallowcontextmenua--iaxwinambientdispatchgetallowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu  
 **AllowContextMenu**属性指定是否允许所承载的控件以显示上下文菜单。  
  
```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```  
  
### <a name="parameters"></a>参数  
 *pbAllowContextMenu*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="a-namegetallowshowuia--iaxwinambientdispatchgetallowshowui"></a><a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI  
 **AllowShowUI**属性指定是否允许所承载的控件来显示其自身用户界面。  
  
```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```  
  
### <a name="parameters"></a>参数  
 *pbAllowShowUI*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**VARIANT_FALSE**作为此属性的默认值。  
  
##  <a name="a-namegetallowwindowlessactivationa--iaxwinambientdispatchgetallowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation  
 **AllowWindowlessActivation**属性指定是否在容器上允许无窗口激活。  
  
```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```  
  
### <a name="parameters"></a>参数  
 *pbAllowWindowless*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="a-namegetbackcolora--iaxwinambientdispatchgetbackcolor"></a><a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor  
 `BackColor`属性指定的容器的环境背景色。  
  
```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```  
  
### <a name="parameters"></a>参数  
 *pclrBackground*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**COLOR_BTNFACE**或**COLOR_WINDOW**作为 （具体取决于是否宿主窗口的父级是一个对话框，或不） 此属性的默认值。  
  
##  <a name="a-namegetdisplayasdefaulta--iaxwinambientdispatchgetdisplayasdefault"></a><a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault  
 **DisplayAsDefault**是一个允许控件以查看它是否具有默认控件的环境属性。  
  
```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```  
  
### <a name="parameters"></a>参数  
 *pbDisplayAsDefault*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**VARIANT_FALSE**作为此属性的默认值。  
  
##  <a name="a-namegetdochostdoubleclickflagsa--iaxwinambientdispatchgetdochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags**属性指定应发生以响应一次双击该操作。  
  
```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>参数  
 *pdwDocHostDoubleClickFlags*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**DOCHOSTUIDBLCLK_DEFAULT**作为此属性的默认值。  
  
##  <a name="a-namegetdochostflagsa--iaxwinambientdispatchgetdochostflags"></a><a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags  
 **DocHostFlags**属性指定该主机对象的用户界面功能。  
  
```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```  
  
### <a name="parameters"></a>参数  
 *pdwDocHostFlags*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**DOCHOSTUIFLAG_NO3DBORDER**作为此属性的默认值。  
  
##  <a name="a-namegetfonta--iaxwinambientdispatchgetfont"></a><a name="get_font"></a>IAxWinAmbientDispatch::get_Font  
 **字体**属性指定的容器的环境的字体。  
  
```
STDMETHOD(get_Font)(IFontDisp** pFont);
```  
  
### <a name="parameters"></a>参数  
 `pFont`  
 [out]地址**IFontDisp**用来接收此属性的当前值的接口指针。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现此属性的默认值中用作默认 GUI 字体或系统字体。  
  
##  <a name="a-namegetforecolora--iaxwinambientdispatchgetforecolor"></a><a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor  
 `ForeColor`属性指定的容器的环境前景色。  
  
```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```  
  
### <a name="parameters"></a>参数  
 *pclrForeground*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用此属性的默认值作为系统窗口文本颜色。  
  
##  <a name="a-namegetlocaleida--iaxwinambientdispatchgetlocaleid"></a><a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID  
 **LocaleID**属性指定的容器的环境的区域设置 ID。  
  
```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```  
  
### <a name="parameters"></a>参数  
 *plcidLocaleID*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用此属性的默认值作为用户的默认区域设置。  
  
 使用此方法可以发现环境 LocalID，也就是说，该程序的 LocaleID 控件正在使用中。 一旦您知道 LocaleID，可以从资源文件或附属 DLL，依此类推调用代码来加载特定于区域设置标题的错误消息文本。  
  
##  <a name="a-namegetmessagereflecta--iaxwinambientdispatchgetmessagereflect"></a><a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect  
 **MessageReflect**环境属性指定是否在容器将反映到所承载的控件的消息。  
  
```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```  
  
### <a name="parameters"></a>参数  
 *pbMessageReflect*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="a-namegetoptionkeypatha--iaxwinambientdispatchgetoptionkeypath"></a><a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath  
 **OptionKeyPath**属性指定为用户设置的注册表项路径。  
  
```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```  
  
### <a name="parameters"></a>参数  
 *pbstrOptionKeyPath*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-namegetshowgrabhandlesa--iaxwinambientdispatchgetshowgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles  
 **ShowGrabHandles**环境属性允许要查找是否它应自行绘制使用抓图句柄的控件。  
  
```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```  
  
### <a name="parameters"></a>参数  
 *pbShowGrabHandles*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现始终返回**VARIANT_FALSE**作为此属性的值。  
  
##  <a name="a-namegetshowhatchinga--iaxwinambientdispatchgetshowhatching"></a><a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching  
 **ShowHatching**环境属性允许要查找是否它应将自身影线绘制的控件。  
  
```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```  
  
### <a name="parameters"></a>参数  
 *pbShowHatching*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 主机对象实现始终返回**VARIANT_FALSE**作为此属性的值。  
  
##  <a name="a-namegetusermodea--iaxwinambientdispatchgetusermode"></a><a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode  
 **UserMode**属性指定的容器的环境的用户模式。  
  
```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```  
  
### <a name="parameters"></a>参数  
 *pbUserMode*  
 [out]接收此属性的当前值的变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="a-nameputallowcontextmenua--iaxwinambientdispatchputallowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put_AllowContextMenu  
 **AllowContextMenu**属性指定是否允许所承载的控件以显示上下文菜单。  
  
```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```  
  
### <a name="parameters"></a>参数  
 *bAllowContextMenu*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="a-nameputallowshowuia--iaxwinambientdispatchputallowshowui"></a><a name="put_allowshowui"></a>IAxWinAmbientDispatch::put_AllowShowUI  
 **AllowShowUI**属性指定是否允许所承载的控件来显示其自身用户界面。  
  
```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```  
  
### <a name="parameters"></a>参数  
 *bAllowShowUI*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**VARIANT_FALSE**作为此属性的默认值。  
  
##  <a name="a-nameputallowwindowlessactivationa--iaxwinambientdispatchputallowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put_AllowWindowlessActivation  
 **AllowWindowlessActivation**属性指定是否在容器上允许无窗口激活。  
  
```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```  
  
### <a name="parameters"></a>参数  
 *bAllowWindowless*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="a-nameputbackcolora--iaxwinambientdispatchputbackcolor"></a><a name="put_backcolor"></a>IAxWinAmbientDispatch::put_BackColor  
 `BackColor`属性指定的容器的环境背景色。  
  
```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```  
  
### <a name="parameters"></a>参数  
 *clrBackground*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**COLOR_BTNFACE**或**COLOR_WINDOW**作为 （具体取决于是否宿主窗口的父级是一个对话框，或不） 此属性的默认值。  
  
##  <a name="a-nameputdisplayasdefaulta--iaxwinambientdispatchputdisplayasdefault"></a><a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put_DisplayAsDefault  
 **DisplayAsDefault**是一个允许控件以查看它是否具有默认控件的环境属性。  
  
```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```  
  
### <a name="parameters"></a>参数  
 `bDisplayAsDefault`  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**VARIANT_FALSE**作为此属性的默认值。  
  
##  <a name="a-nameputdochostdoubleclickflagsa--iaxwinambientdispatchputdochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags**属性指定应发生以响应一次双击该操作。  
  
```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>参数  
 *dwDocHostDoubleClickFlags*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**DOCHOSTUIDBLCLK_DEFAULT**作为此属性的默认值。  
  
##  <a name="a-nameputdochostflagsa--iaxwinambientdispatchputdochostflags"></a><a name="put_dochostflags"></a>IAxWinAmbientDispatch::put_DocHostFlags  
 **DocHostFlags**属性指定该主机对象的用户界面功能。  
  
```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```  
  
### <a name="parameters"></a>参数  
 *dwDocHostFlags*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用 ATL 宿主对象实现**DOCHOSTUIFLAG_NO3DBORDER**作为此属性的默认值。  
  
##  <a name="a-nameputfonta--iaxwinambientdispatchputfont"></a><a name="put_font"></a>IAxWinAmbientDispatch::put_Font  
 **字体**属性指定的容器的环境的字体。  
  
```
STDMETHOD(put_Font)(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>参数  
 `pFont`  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现此属性的默认值中用作默认 GUI 字体或系统字体。  
  
##  <a name="a-nameputforecolora--iaxwinambientdispatchputforecolor"></a><a name="put_forecolor"></a>IAxWinAmbientDispatch::put_ForeColor  
 `ForeColor`属性指定的容器的环境前景色。  
  
```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```  
  
### <a name="parameters"></a>参数  
 *clrForeground*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用此属性的默认值作为系统窗口文本颜色。  
  
##  <a name="a-nameputlocaleida--iaxwinambientdispatchputlocaleid"></a><a name="put_localeid"></a>IAxWinAmbientDispatch::put_LocaleID  
 **LocaleID**属性指定的容器的环境的区域设置 ID。  
  
```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```  
  
### <a name="parameters"></a>参数  
 *lcidLocaleID*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用此属性的默认值作为用户的默认区域设置。  
  
##  <a name="a-nameputmessagereflecta--iaxwinambientdispatchputmessagereflect"></a><a name="put_messagereflect"></a>IAxWinAmbientDispatch::put_MessageReflect  
 **MessageReflect**环境属性指定是否在容器将反映到所承载的控件的消息。  
  
```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```  
  
### <a name="parameters"></a>参数  
 `bMessageReflect`  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
##  <a name="a-nameputoptionkeypatha--iaxwinambientdispatchputoptionkeypath"></a><a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put_OptionKeyPath  
 **OptionKeyPath**属性指定为用户设置的注册表项路径。  
  
```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```  
  
### <a name="parameters"></a>参数  
 *bstrOptionKeyPath*  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-nameputusermodea--iaxwinambientdispatchputusermode"></a><a name="put_usermode"></a>IAxWinAmbientDispatch::put_UserMode  
 **UserMode**属性指定的容器的环境的用户模式。  
  
```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```  
  
### <a name="parameters"></a>参数  
 `bUserMode`  
 [in]此属性的新值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 ATL 宿主对象实现使用`VARIANT_TRUE`作为此属性的默认值。  
  
## <a name="see-also"></a>另请参阅  
 [IAxWinAmbientDispatchEx 接口](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [IAxWinHostWindow 接口](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](http://msdn.microsoft.com/library/ad1f4f16-608d-4e96-8d30-04d4ca906a7b)










