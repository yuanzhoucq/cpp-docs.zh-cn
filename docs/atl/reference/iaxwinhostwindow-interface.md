---
title: IAxWinHostWindow 接口
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
ms.openlocfilehash: ebecc611660a788ce59bb11beb95bd60eacaf01b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329995"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow 接口

此接口提供操作控件及其宿主对象的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[附加控制](#attachcontrol)|将现有控件附加到主机对象。|
|[CreateControl](#createcontrol)|创建控件并将其附加到主机对象。|
|[创建控制Ex](#createcontrolex)|创建控件，将其附加到主机对象，并可以选择设置事件处理程序。|
|[查询控制](#querycontrol)|返回指向托管控件的接口指针。|
|[设置外部调度](#setexternaldispatch)|设置外部`IDispatch`接口。|
|[设置外部 UIHandler](#setexternaluihandler)|设置外部`IDocHostUIHandlerDispatch`接口。|

## <a name="remarks"></a>备注

此接口由 ATL 的 ActiveX 控件托管对象公开。 调用此接口上的方法以创建和/或将控件附加到主机对象、从托管控件获取接口或设置外部接口或 UI 处理程序，以便托管 Web 浏览器时使用。

## <a name="requirements"></a>要求

此接口的定义可作为 IDL 或C++，如下所示。

|定义类型|文件|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h （也包含在 ATLBase.h 中）|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHost 窗口：：附加控制

使用*hWnd*标识的窗口将现有（以前初始化）控件附加到主机对象。

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>参数

*pUnkControl*<br/>
[在]指向要附加到主机`IUnknown`对象的控件接口的指针。

*hwnd*<br/>
[在]用于托管的窗口的句柄。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHost 窗口：：创建控制

创建控件，初始化它，并将其托管在*hWnd*标识的窗口中。

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>参数

*lpTricsData*<br/>
[在]标识要创建的控件的字符串。 可以是 CLSID（必须包括大括号）、ProgID、URL 或原始 HTML（由**MSHTML**预缀： 。

*hwnd*<br/>
[在]用于托管的窗口的句柄。

*pStream*<br/>
[在]包含控件初始化数据的流的接口指针。 可以为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

此窗口将由公开此接口的主机对象进行子分类，以便消息可以反射到控件，其他容器功能将起作用。

调用此方法等效于调用[IAxWinHostWindow：：createControlEx](#createcontrolex)。

要创建许可的 ActiveX 控件，请参阅[IAxWinHostWindowlic：：创建控制项](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHost 窗口：：创建控制Ex

创建一个 ActiveX 控件，初始化它，并将其托管在指定的窗口中，类似于[IAxWinHostWindow：：创建控制](#createcontrol)。

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

*lpTricsData*<br/>
[在]标识要创建的控件的字符串。 可以是 CLSID（必须包括大括号）、ProgID、URL 或原始 HTML（与**MSHTML**一起预缀： 。

*hwnd*<br/>
[在]用于托管的窗口的句柄。

*pStream*<br/>
[在]包含控件初始化数据的流的接口指针。 可以为 NULL。

*普恩克*<br/>
[出]将接收创建控件接口`IUnknown`的指针的地址。 可以为 NULL。

*里德建议*<br/>
[在]包含对象上传出接口的接口标识符。 可以IID_NULL。

*朋克建议*<br/>
[在]指向要连接到`IUnknown`所指定包含对象的连接点的接收器对象的接口的`iidSink`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

与`CreateControl`方法不同`CreateControlEx`，还允许您接收指向新创建的控件的接口指针，并设置事件接收器以接收控件触发的事件。

要创建许可的 ActiveX 控件，请参阅[IAxWinHostWindowlic：：创建控制项](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHost 窗口：：查询控制

返回托管控件提供的指定接口指针。

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>参数

*riid*<br/>
[在]请求的控件上的接口的 ID。

*ppvObject*<br/>
[出]将接收已创建控件的指定接口的指针的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHost 窗口：：设置外部调度

设置外部接口，可通过[IDocHostUIHandlerDispatch：get 外部](../../atl/reference/idochostuihandlerdispatch-interface.md)方法包含控件。

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
[在]指向接口的`IDispatch`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHost 窗口：：设置外部 UIHandler

调用此函数以设置`CAxWindow`对象的外部[IDocHostUIHandlerDispatch 接口](../../atl/reference/idochostuihandlerdispatch-interface.md)。

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
[在]指向接口的`IDocHostUIHandlerDispatch`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

此函数由查询主机站点的`IDocHostUIHandlerDispatch`接口的控件（如 Web 浏览器控件）使用。

## <a name="see-also"></a>另请参阅

[IAxWinAmbientDispatch 接口](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAx 窗口：：查询主机](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
