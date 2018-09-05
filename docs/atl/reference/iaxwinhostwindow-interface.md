---
title: IAxWinHostWindow 接口 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf8c27d118984422ec3a78f442a3f11f13e1c75
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766027"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow 接口

此接口提供用于操作控件和其宿主对象的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[AttachControl](#attachcontrol)|将现有控件附加到该主机对象。|
|[CreateControl](#createcontrol)|创建控件，并将其附加到该主机对象。|
|[CreateControlEx](#createcontrolex)|创建控件，将其附加到该主机对象，并根据需要设置一个事件处理程序。|
|[QueryControl](#querycontrol)|返回到所承载的控件的接口指针。|
|[SetExternalDispatch](#setexternaldispatch)|设置外部`IDispatch`接口。|
|[SetExternalUIHandler](#setexternaluihandler)|设置外部`IDocHostUIHandlerDispatch`接口。|

## <a name="remarks"></a>备注

此接口由 ATL 的 ActiveX 控件承载对象公开。 针对此接口可创建和/或将一个控件附加到该主机对象，从托管控件，获取一个接口或设置外部调度接口或 UI 处理程序，用于托管 Web 浏览器时调用的方法。

## <a name="requirements"></a>要求

此接口的定义现在以 IDL 或 c + +，如下所示。

|定义类型|文件|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h （也包括在 ATLBase.h）|

##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl

将现有 （和以前初始化） 控件附加到该主机对象，使用标识窗口*hWnd*。

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>参数

*pUnkControl*  
[in]一个指向`IUnknown`要附加到该主机对象的控件的接口。

*hWnd*  
[in]要用于承载窗口的句柄。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

创建控件，初始化它，并由标识在窗口中承载它*hWnd*。

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>参数

*lpTricsData*  
[in]标识要创建的控件的字符串。 可以是 （必须包含在大括号） 的 CLSID、 ProgID、 URL 或原始 HTML (加**MSHTML:**)。

*hWnd*  
[in]要用于承载窗口的句柄。

*pStream*  
[in]包含控件的初始化数据的流接口指针。 可以为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

此窗口将公开此接口，以便消息可以发射到控件和其他容器功能将适用的主机对象通过子类化。

调用此方法相当于调用[IAxWinHostWindow::CreateControlEx](#createcontrolex)。

若要创建授权的 ActiveX 控件，请参阅[IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

创建 ActiveX 控件，初始化它，并在指定窗口中，类似于承载[IAxWinHostWindow::CreateControl](#createcontrol)。

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

*lpTricsData*  
[in]标识要创建的控件的字符串。 可以是 （必须包含在大括号） 的 CLSID、 ProgID、 URL 或原始 HTML (带有前缀**MSHTML:**)。

*hWnd*  
[in]要用于承载窗口的句柄。

*pStream*  
[in]包含控件的初始化数据的流接口指针。 可以为 NULL。

*ppUnk*  
[out]将接收的指针的地址`IUnknown`接口创建的控件。 可以为 NULL。

*riidAdvise*  
[in]包含的对象上的传出接口的接口标识符。 可以为 IID_NULL。

*punkAdvise*  
[in]一个指向`IUnknown`接收器对象连接到指定的包含对象上的连接点的接口`iidSink`。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

与不同`CreateControl`方法，`CreateControlEx`还允许您接收到新创建的控件的接口指针并将事件接收器设置为接收控件触发的事件。

若要创建授权的 ActiveX 控件，请参阅[IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

返回提供的托管控件的指定的接口指针。

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>参数

*riid*  
[in]所请求的控件上某个接口 ID。

*ppvObject*  
[out]将收到创建的控件的指定的接口的指针的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

设置适用于所含控件通过外部 dispinterface [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md)方法。

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>参数

*pDisp*  
[in]一个指向`IDispatch`接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

调用此函数可设置外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)接口`CAxWindow`对象。

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>参数

*pDisp*  
[in]一个指向`IDocHostUIHandlerDispatch`接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

此函数可供查询的主机的站点的控件 （如 Web 浏览器控件）`IDocHostUIHandlerDispatch`接口。

## <a name="see-also"></a>请参阅

[IAxWinAmbientDispatch 接口](../../atl/reference/iaxwinambientdispatch-interface.md)   
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

