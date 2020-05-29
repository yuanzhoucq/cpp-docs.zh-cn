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
ms.openlocfilehash: 6f5629370bc1f821dac0a08cc76b5df1450f7a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318724"
---
# <a name="caxwindow-class"></a>CAxWindow 类

此类提供了用于操作承载 ActiveX 控件的窗口的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CAxWindow : public CWindow
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[附加控制](#attachcontrol)|将现有的 ActiveX 控件附加到`CAxWindow`对象。|
|[萨克斯窗口](#caxwindow)|构造 `CAxWindow` 对象。|
|[CreateControl](#createcontrol)|创建 ActiveX 控件，初始化它，并将其托管在`CAxWindow`窗口中。|
|[创建控制Ex](#createcontrolex)|创建 ActiveX 控件并从控件中检索接口指针（或指针）。|
|[获取 WndClass 名称](#getwndclassname)|（静态）检索`CAxWindow`对象的预定义的类名称。|
|[查询控制](#querycontrol)|检索托管`IUnknown`的 ActiveX 控件。|
|[查询主机](#queryhost)|检索`IUnknown``CAxWindow`对象的指针。|
|[设置外部调度](#setexternaldispatch)|设置`CAxWindow`对象使用的外部调度接口。|
|[设置外部 UIHandler](#setexternaluihandler)|设置`CAxWindow`对象使用`IDocHostUIHandler`的外部接口。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运算符 |](#operator_eq)|将 HWND 分配给现有`CAxWindow`对象。|

## <a name="remarks"></a>备注

此类提供了用于操作承载 ActiveX 控件的窗口的方法。 托管由 **"AtlAxWin80"** 提供，由 包装`CAxWindow`。

类`CAxWindow`作为`CAxWindowT`类的专业化实现。 此专业化化声明为：

`typedef CAxWindowT<CWindow> CAxWindow;`

如果需要更改基类，可以使用`CAxWindowT`并将新基类指定为模板参数。

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a>CAx 窗口：：附加控制

如果一个主机尚未存在，则创建新的主机对象，并将指定的控件附加到主机。

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>参数

*pControl*<br/>
[在]指向控件`IUnknown`的指针。

*ppUnk容器*<br/>
[出]指向主机（`IUnknown`对象的）的`AxWin`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

在调用`AttachControl`之前，必须正确初始化所连接的控件对象。

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a>萨克斯窗口：：萨克斯窗口

使用现有窗口`CAxWindow`对象句柄构造对象。

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
现有窗口对象的句柄。

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a>CAxWindow：：创建控制

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

*lpsz名称*<br/>
指向字符串的指针以创建控件。 必须采用以下方式之一进行格式化：

- ProgID，如`"MSCAL.Calendar.7"`

- CLSID，如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，如`"<https://www.microsoft.com>"`

- 对活动文档的引用，例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必须在 HTML 片段之前，以便将其指定为 MSHTML 流。 Windows 移动平台中仅支持 ProgID 和 CLSID。 Windows CE 嵌入式平台（Windows Mobile 外，支持 CE IE）支持所有类型的内容，包括 ProgID、CLSID、URL、对活动文档的引用和 HTML 片段。

*pStream*<br/>
[在]指向用于初始化控件属性的流的指针。 可以为 NULL。

*ppUnk容器*<br/>
[出]将接收容器`IUnknown`的指针的地址。 可以为 NULL。

*德雷斯ID*<br/>
HTML 资源的资源 ID。 Web浏览器控件将创建并加载指定资源。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

如果使用此方法的第二个版本，则创建 HTML 控件并将其绑定到*dwResID*标识的资源。

此方法为您提供与调用相同的结果：

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

请参阅[CAxWindow2T：：创建控制，](../../atl/reference/caxwindow2t-class.md#createcontrollic)以创建、初始化和托管许可的 ActiveX 控件。

### <a name="example"></a>示例

有关 使用`CreateControl`的样本，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a>CAx 窗口：：创建控制Ex

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

*lpsz名称*<br/>
指向字符串的指针以创建控件。 必须采用以下方式之一进行格式化：

- ProgID，如`"MSCAL.Calendar.7"`

- CLSID，如`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，如`"<https://www.microsoft.com>"`

- 对活动文档的引用，例如`"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`必须在 HTML 片段之前，以便将其指定为 MSHTML 流。 Windows 移动平台中仅支持 ProgID 和 CLSID。 Windows CE 嵌入式平台（Windows Mobile 外，支持 CE IE）支持所有类型的内容，包括 ProgID、CLSID、URL、对活动文档的引用和 HTML 片段。

*pStream*<br/>
[在]指向用于初始化控件属性的流的指针。 可以为 NULL。

*ppUnk容器*<br/>
[出]将接收容器`IUnknown`的指针的地址。 可以为 NULL。

*ppUnkControl*<br/>
[出]将接收控件`IUnknown`的指针的地址。 可以为 NULL。

*iidSink*<br/>
[在]包含对象上传出接口的接口标识符。 可以IID_NULL。

*朋克辛克*<br/>
[在]指向接收器对象`IUnknown`接口的指针，用于连接到*iidSink*指定的包含对象上的连接点。

*德雷斯ID*<br/>
[在]HTML 资源的资源 ID。 Web浏览器控件将创建并加载指定资源。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

此方法类似于[CAxWindow：：createControl](#createcontrol)，但与该方法不同，`CreateControlEx`还允许您接收指向新创建的控件的接口指针，并设置事件接收器以接收控件触发的事件。

请参阅[CAxWindow2T：：创建控制LicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex)以创建、初始化和托管许可的 ActiveX 控件。

### <a name="example"></a>示例

有关 使用`CreateControlEx`的样本，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a>CAx 窗口：获取WndClass名称

检索窗口类的名称。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>返回值

指向一个字符串的指针，其中包含可以承载无许可的 ActiveX 控件的窗口类的名称。

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a>CAxWindow：：运算符 |

将 HWND 分配给现有`CAxWindow`对象。

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
现有窗口的句柄。

### <a name="return-value"></a>返回值

返回对当前 `CAxWindow` 对象的引用。

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a>CAx 窗口：查询控制

检索托管控件的指定接口。

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]指定控件接口的 IID。

*普恩克*<br/>
[出]指向控件接口的指针。 在此方法的模板版本中，只要传递了具有关联 UUID 的键入接口，就不需要引用 ID。

*Q*<br/>
[在]正在查询的接口。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a>CAx 窗口：：查询主机

返回主机的指定接口。

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]指定控件接口的 IID。

*普恩克*<br/>
[出]指向主机上接口的指针。 在此方法的模板版本中，只要传递了具有关联 UUID 的键入接口，就不需要引用 ID。

*Q*<br/>
[在]正在查询的接口。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

主机的接口允许访问由 实现`AxWin`的窗口托管代码的基础功能。

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>CAxWindow：：设置外部调度

设置`CAxWindow`对象的外部调度接口。

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
[在]指向接口的`IDispatch`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>CAxWindow：：设置外部UIHandler

设置`CAxWindow`对象的外部[IDocHostUIHandlerDispatch 接口](../../atl/reference/idochostuihandlerdispatch-interface.md)。

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>参数

*pUIHandler*<br/>
[在]指向接口的`IDocHostUIHandlerDispatch`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

外部`IDocHostUIHandlerDispatch`接口由查询接口主机站点`IDocHostUIHandlerDispatch`的控件使用。 Web浏览器控件是执行此功能的一个控件。

## <a name="see-also"></a>另请参阅

[ATLCON 样品](../../overview/visual-cpp-samples.md)<br/>
[CWindow 类](../../atl/reference/cwindow-class.md)<br/>
[复合控件基础知识](../../atl/atl-composite-control-fundamentals.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[控件包含常见问题](../../atl/atl-control-containment-faq.md)
