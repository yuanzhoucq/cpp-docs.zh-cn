---
title: CAxWindow 类
ms.date: 11/04/2016
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 6f5c178090a970906209e41da9298be61a61c639
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927862"
---
# <a name="caxwindow-class"></a>CAxWindow 类

此类提供用于操作承载 ActiveX 控件的窗口的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CAxWindow : public CWindow
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[AttachControl](#attachcontrol)|将现有 ActiveX 控件附加到`CAxWindow`对象。|
|[CAxWindow](#caxwindow)|构造 `CAxWindow` 对象。|
|[CreateControl](#createcontrol)|创建 ActiveX 控件，对`CAxWindow`其进行初始化，并在窗口中承载它。|
|[CreateControlEx](#createcontrolex)|创建一个 ActiveX 控件，并从该控件中检索一个接口指针。|
|[GetWndClassName](#getwndclassname)|静止检索`CAxWindow`对象的预定义类名称。|
|[QueryControl](#querycontrol)|`IUnknown`检索承载的 ActiveX 控件的。|
|[QueryHost](#queryhost)|检索对象`CAxWindow`的指针。 `IUnknown`|
|[SetExternalDispatch](#setexternaldispatch)|设置`CAxWindow`对象使用的外部调度接口。|
|[SetExternalUIHandler](#setexternaluihandler)|设置`CAxWindow`对象使用`IDocHostUIHandler`的外部接口。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](#operator_eq)|将 HWND 分配给现有`CAxWindow`对象。|

## <a name="remarks"></a>备注

此类提供用于操作承载 ActiveX 控件的窗口的方法。 托管由 " **AtlAxWin80"** 提供，由包装`CAxWindow`。

类`CAxWindow`实现为`CAxWindowT`类的专用化。 此特殊化声明为：

`typedef CAxWindowT<CWindow> CAxWindow;`

如果需要更改基类，则可以使用`CAxWindowT`并将新基类指定为模板参数。

## <a name="requirements"></a>要求

**标头：** atlwin。h

##  <a name="attachcontrol"></a>CAxWindow::AttachControl

如果一个宿主对象尚不存在，则创建一个新的宿主对象，并将指定的控件附加到宿主。

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>参数

*pControl*<br/>
中指向`IUnknown`控件的的指针。

*ppUnkContainer*<br/>
弄指向`IUnknown` 主机`AxWin` （对象）的的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

在调用`AttachControl`之前，必须正确初始化要附加的控件对象。

##  <a name="caxwindow"></a>CAxWindow::CAxWindow

使用现有的窗口对象句柄构造对象。`CAxWindow`

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
现有窗口对象的句柄。

##  <a name="createcontrol"></a>CAxWindow：： CreateControl

创建 ActiveX 控件，初始化它并在指定窗口中承载它。

```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
指向用于创建控件的字符串的指针。 必须采用下列方式之一进行格式化：

- ProgID，如`"MSCAL.Calendar.7"`

- CLSID，如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，如`"<https://www.microsoft.com>"`

- 对活动文档的引用，例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段，如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必须在 HTML 片段之前，才能指定为 MSHTML 流。 Windows Mobile 平台仅支持 ProgID 和 CLSID。 除了支持 CE IE 的 Windows Mobile 外，Windows CE 嵌入式平台支持所有类型，包括 ProgID、CLSID、URL、对活动文档的引用以及 HTML 片段。

*pStream*<br/>
中指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
弄将接收`IUnknown`容器的的指针地址。 可以为 NULL。

*dwResID*<br/>
HTML 资源的资源 ID。 将用指定的资源创建并加载 WebBrowser 控件。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果使用此方法的第二个版本，则会创建一个 HTML 控件，并将其绑定到由*dwResID*标识的资源。

此方法提供与调用相同的结果：

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

若要创建、初始化和托管许可的 ActiveX 控件，请参阅[CAxWindow2T：： CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) 。

### <a name="example"></a>示例

有关使用`CreateControl`的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="createcontrolex"></a>CAxWindow::CreateControlEx

创建 ActiveX 控件，初始化它并在指定窗口中承载它。

```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
指向用于创建控件的字符串的指针。 必须采用下列方式之一进行格式化：

- ProgID，如`"MSCAL.Calendar.7"`

- CLSID，如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，如`"<https://www.microsoft.com>"`

- 对活动文档的引用，例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段，如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必须在 HTML 片段之前，才能指定为 MSHTML 流。 Windows Mobile 平台仅支持 ProgID 和 CLSID。 除了支持 CE IE 的 Windows Mobile 外，Windows CE 嵌入式平台支持所有类型，包括 ProgID、CLSID、URL、对活动文档的引用以及 HTML 片段。

*pStream*<br/>
中指向用于初始化控件的属性的流的指针。 可以为 NULL。

*ppUnkContainer*<br/>
弄将接收`IUnknown`容器的的指针地址。 可以为 NULL。

*ppUnkControl*<br/>
弄将接收`IUnknown`控件的的指针的地址。 可以为 NULL。

*iidSink*<br/>
中所包含对象上的传出接口的接口标识符。 可以是 IID_NULL。

*punkSink*<br/>
中指向接收器对象的`IUnknown`接口的指针，该接收器对象将连接到*iidSink*指定的包含对象上的连接点。

*dwResID*<br/>
中HTML 资源的资源 ID。 将用指定的资源创建并加载 WebBrowser 控件。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

此方法类似于[CAxWindow：： CreateControl](#createcontrol)，但与该方法不同， `CreateControlEx`还允许你接收指向新创建的控件的接口指针，并设置一个事件接收器来接收由控件触发的事件。

若要创建、初始化和托管许可的 ActiveX 控件，请参阅[CAxWindow2T：： CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) 。

### <a name="example"></a>示例

有关使用`CreateControlEx`的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="getwndclassname"></a>CAxWindow::GetWndClassName

检索窗口类的名称。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>返回值

一个指向字符串的指针，该字符串包含可以承载 nonlicensed ActiveX 控件的窗口类的名称。

##  <a name="operator_eq"></a>CAxWindow：： operator =

将 HWND 分配给现有`CAxWindow`对象。

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
现有窗口的句柄。

### <a name="return-value"></a>返回值

返回对当前 `CAxWindow` 对象的引用。

##  <a name="querycontrol"></a>CAxWindow::QueryControl

检索寄宿控件的指定接口。

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>参数

*iid*<br/>
中指定控件的接口的 IID。

*ppUnk*<br/>
弄指向控件的接口的指针。 在此方法的模板版本中，只要传递具有关联 UUID 的类型化接口，就不需要引用 ID。

*Q*<br/>
中正在查询的接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="queryhost"></a>CAxWindow::QueryHost

返回宿主的指定接口。

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>参数

*iid*<br/>
中指定控件的接口的 IID。

*ppUnk*<br/>
弄指向主机上接口的指针。 在此方法的模板版本中，只要传递具有关联 UUID 的类型化接口，就不需要引用 ID。

*Q*<br/>
中正在查询的接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

宿主的接口允许访问由实现的`AxWin`窗口承载代码的基础功能。

##  <a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

设置`CAxWindow`对象的外部调度接口。

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
中指向`IDispatch`接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

设置`CAxWindow`对象的外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)接口。

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>参数

*pUIHandler*<br/>
中指向`IDocHostUIHandlerDispatch`接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

外部`IDocHostUIHandlerDispatch`接口由查询宿主的`IDocHostUIHandlerDispatch`接口的站点的控件使用。 WebBrowser 控件是实现此功能的一个控件。

## <a name="see-also"></a>请参阅

[ATLCON 示例](../../overview/visual-cpp-samples.md)<br/>
[CWindow 类](../../atl/reference/cwindow-class.md)<br/>
[复合控件基础知识](../../atl/atl-composite-control-fundamentals.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[控制包含常见问题](../../atl/atl-control-containment-faq.md)
