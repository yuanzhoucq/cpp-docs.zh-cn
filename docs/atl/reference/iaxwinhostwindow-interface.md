---
title: "IAxWinHostWindow 接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindow
- No header/ATL::IAxWinHostWindow
- No header/ATL::AttachControl
- No header/ATL::CreateControl
- No header/ATL::CreateControlEx
- No header/ATL::QueryControl
- No header/ATL::SetExternalDispatch
- No header/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
caps.latest.revision: 21
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: ecf88a3a6b115088dd605fff2b633bff86fb086a
ms.lasthandoff: 03/31/2017

---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow 接口
此接口提供用于操作控件和其主机对象的方法。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
interface IAxWinHostWindow : IUnknown
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|将现有控件附加到该主机对象。|  
|[CreateControl](#createcontrol)|创建控件并将其附加到该主机对象。|  
|[CreateControlEx](#createcontrolex)|创建控件，将其附加到该主机对象，并根据需要设置事件处理程序。|  
|[QueryControl](#querycontrol)|返回指向托管控件的接口指针。|  
|[SetExternalDispatch](#setexternaldispatch)|设置外部`IDispatch`接口。|  
|[SetExternalUIHandler](#setexternaluihandler)|设置外部`IDocHostUIHandlerDispatch`接口。|  
  
## <a name="remarks"></a>备注  
 此接口公开的 ATL 的 ActiveX 控件承载对象。 对此接口可创建和/或将一个控件附加到该主机对象，接口获得托管的控件，或设置外部的调度接口或 UI 处理程序使用托管 Web 浏览器时调用的方法。  
  
## <a name="requirements"></a>要求  
 此接口的定义是 IDL 或 c + +，可用的如下所示。  
  
|定义类型|文件|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h （也包括在 ATLBase.h）|  
  
##  <a name="attachcontrol"></a>IAxWinHostWindow::AttachControl  
 将现有 （和以前初始化） 的控件附加到该主机对象，使用由窗口`hWnd`。  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 *pUnkControl*  
 [in]指向的指针**IUnknown**要附加到该主机对象的控件的接口。  
  
 `hWnd`  
 [in]要用于承载窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="createcontrol"></a>IAxWinHostWindow::CreateControl  
 创建控件，初始化它，并在标识窗口中承载它`hWnd`。  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>参数  
 `lpTricsData`  
 [in]标识要创建的控件的字符串。 可以是 （必须包括大括号） 的 CLSID、 ProgID，URL 或原始 HTML (前缀**MSHTML:**)。  
  
 `hWnd`  
 [in]要用于承载窗口的句柄。  
  
 `pStream`  
 [in]包含控件的初始化数据的流接口指针。 可以是**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 此窗口将公开此接口，以便消息可以发射到控件和其他容器功能将使用该主机对象通过子类化。  
  
 调用此方法等效于调用[IAxWinHostWindow::CreateControlEx](#createcontrolex)。  
  
 若要创建授权的 ActiveX 控件，请参阅[IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。  
  
##  <a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx  
 创建 ActiveX 控件，初始化它，并在指定窗口，类似于中承载它[IAxWinHostWindow::CreateControl](#createcontrol)。  
  
```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```  
  
### <a name="parameters"></a>参数  
 `lpTricsData`  
 [in]标识要创建的控件的字符串。 可以是 （必须包括大括号） 的 CLSID、 ProgID，URL 或原始 HTML (前缀为**MSHTML:**)。  
  
 `hWnd`  
 [in]要用于承载窗口的句柄。  
  
 `pStream`  
 [in]包含控件的初始化数据的流接口指针。 可以是**NULL**。  
  
 `ppUnk`  
 [out]将接收的指针的地址**IUnknown**接口创建的控件。 可以是**NULL**。  
  
 *riidAdvise*  
 [in]包含的对象上的传出接口的接口标识符。 可以是**IID_NULL**。  
  
 *punkAdvise*  
 [in]指向的指针**IUnknown**要连接到指定的包含对象上的连接点的接收器对象的接口`iidSink`。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 与不同`CreateControl`方法，`CreateControlEx`还允许您接收到新创建的控件的接口指针并将事件接收器设置为接收控件触发的事件。  
  
 若要创建授权的 ActiveX 控件，请参阅[IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。  
  
##  <a name="querycontrol"></a>IAxWinHostWindow::QueryControl  
 返回由所承载的控件的指定的接口指针。  
  
```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `riid`  
 [in]所请求的控件上某个接口 ID。  
  
 `ppvObject`  
 [out]将收到创建的控件的指定的接口的指针的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch  
 设置可供通过所含控件的外部调度接口[IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md)方法。  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>参数  
 `pDisp`  
 [in]指向的指针`IDispatch`接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler  
 调用此函数可设置外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)接口`CAxWindow`对象。  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>参数  
 `pDisp`  
 [in]指向的指针**IDocHostUIHandlerDispatch**接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 此函数可供查询主机的站点的控件 （如 Web 浏览器控件）`IDocHostUIHandlerDispatch`接口。  
  
## <a name="see-also"></a>另请参阅  
 [IAxWinAmbientDispatch 接口](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)










