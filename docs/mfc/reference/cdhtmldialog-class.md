---
title: CDHtml对话类
ms.date: 03/27/2019
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: 57ea8f3a1dbbce4fcfa350bd99e4ee628e9675c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375688"
---
# <a name="cdhtmldialog-class"></a>CDHtml对话类

用于创建使用 HTML 而不是对话框资源来实现其用户界面的对话框。

## <a name="syntax"></a>语法

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDHtml对话：：CDHtml对话](#cdhtmldialog)|构造 CDHtmlDialog 对象。|
|[CDHtml对话：：_CDHtml对话](#_dtorcdhtmldialog)|销毁 CDHtmlDialog 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDHtml对话：：可以访问外部](#canaccessexternal)|可重写，称为访问检查，以查看加载页上的脚本对象是否可以访问控件站点的外部调度。 检查以确保派单对脚本安全，或者当前区域允许对脚本不安全的对象。|
|[CDHtml对话：创建控制网站](#createcontrolsite)|用于创建控件站点实例以在对话框上承载 WebBrowser 控件的可重写操作。|
|[CDHtml对话：:DDX_DHtml_Ax控制](#ddx_dhtml_axcontrol)|在 HTML 页上的成员变量和 ActiveX 控件的属性值之间交换数据。|
|[CDHtml对话：:DDX_DHtml_复选框](#ddx_dhtml_checkbox)|在 HTML 页上的成员变量和复选框之间交换数据。|
|[CDHtml对话：:DDX_DHtml_元素文本](#ddx_dhtml_elementtext)|在成员变量和 HTML 页上的任何 HTML 元素属性之间交换数据。|
|[CDHtml对话：:DDX_DHtml_收音机](#ddx_dhtml_radio)|在 HTML 页上的成员变量和单选按钮之间交换数据。|
|[CDHtml对话：:DDX_DHtml_选择索引](#ddx_dhtml_selectindex)|获取或设置 HTML 页上的列表框的索引。|
|[CDHtml对话：:DDX_DHtml_选择字符串](#ddx_dhtml_selectstring)|获取或设置 HTML 页上列表框条目的显示文本（基于当前索引）。|
|[CDHtml对话：:DDX_DHtml_选择值](#ddx_dhtml_selectvalue)|获取或设置 HTML 页上的列表框条目的值（基于当前索引）。|
|[CDHtmlDialog：:D无摩模式](#destroymodeless)|销毁无模式对话框。|
|[CDHtmlDialog：启用无模式](#enablemodeless)|启用无模式对话框。|
|[CDHtml对话：：筛选数据对象](#filterdataobject)|允许对话框筛选托管浏览器创建的剪贴板数据对象。|
|[CDHtmlDialog：获取控制调度](#getcontroldispatch)|检索 HTML`IDispatch`文档中嵌入的 ActiveX 控件上的接口。|
|[CDHtml对话：获取控制属性](#getcontrolproperty)|检索指定的 ActiveX 控件的请求属性。|
|[CDHtml对话：获取当前Url](#getcurrenturl)|检索与当前文档关联的统一资源定位器 （URL）。|
|[CDHtml对话：获取Html文档](#getdhtmldocument)|检索当前加载的 HTML 文档上的 IHTMLDocument2 界面。|
|[CDHtml对话：：获取删除目标](#getdroptarget)|当包含的 WebBrowser 控件用作放置目标以允许对话框提供替代[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)时，由它调用它。|
|[CDHtml对话：获取元素](#getelement)|获取 HTML 元素上的接口。|
|[CDHtml对话：获取元素Html](#getelementhtml)|检索 HTML`innerHTML`元素的属性。|
|[CDHtml对话：获取元素接口](#getelementinterface)|从 HTML 元素检索请求的接口指针。|
|[CDHtml对话：获取元素属性](#getelementproperty)|检索 HTML 元素属性的值。|
|[CDHtml对话：获取元素文本](#getelementtext)|检索 HTML`innerText`元素的属性。|
|[CDHtml对话：获取事件](#getevent)|获取指向`IHTMLEventObj`当前事件对象的指针。|
|[CDHtml对话：获取外部](#getexternal)|获取主机的`IDispatch`接口。|
|[CDHtmlDialog：获取Hostinfo](#gethostinfo)|检索主机的 UI 功能。|
|[CDHtml对话：获取选项关键路径](#getoptionkeypath)|检索存储用户首选项的注册表项。|
|[CDHtml对话：：隐藏UI](#hideui)|隐藏主机的 UI。|
|[CDHtmlDialog：是外部调度安全](#isexternaldispatchsafe)|指示主机的`IDispatch`接口是否安全编写脚本。|
|[CDHtml对话：：从资源加载](#loadfromresource)|将指定的资源加载到 Web 浏览器控件中。|
|[CDHtml对话：导航](#navigate)|导航到指定的 URL。|
|[CDHtmlDialog：：在导航前打开](#onbeforenavigate)|在触发导航事件之前由框架调用。|
|[CDHtml对话：：在文档完成](#ondocumentcomplete)|由框架调用，以便在文档达到READYSTATE_COMPLETE状态时通知应用程序。|
|[CDHtml对话：：在DocWindow激活](#ondocwindowactivate)|当文档窗口激活或停用时，由框架调用。|
|[CDHtmlDialog：在框架窗口激活](#onframewindowactivate)|当框架窗口激活或停用时，框架调用。|
|[CDHtmlDialog：onInitDialog](#oninitdialog)|调用以响应WM_INITDIALOG消息。|
|[CDHtml对话：：导航完成](#onnavigatecomplete)|导航事件完成后由框架调用。|
|[CDHtml对话：调整边框大小](#resizeborder)|提醒需要调整边框空间大小的对象。|
|[CDHtml对话：：设置控制属性](#setcontrolproperty)|将 ActiveX 控件的属性设置为新值。|
|[CDHtml对话：：设置元素Html](#setelementhtml)|设置`innerHTML`HTML 元素的属性。|
|[CDHtml对话：：设置元素属性](#setelementproperty)|设置 HTML 元素的属性。|
|[CDHtml对话：：设置元素文本](#setelementtext)|设置`innerText`HTML 元素的属性。|
|[CDHtml对话：：设置外部调度](#setexternaldispatch)|设置主机的`IDispatch`接口。|
|[CDHtml对话：：设置主机标志](#sethostflags)|设置主机的 UI 标志。|
|[CDHtml对话：：显示上下文菜单](#showcontextmenu)|在显示上下文菜单时调用。|
|[CDHtml对话：：显示UI](#showui)|显示主机的 UI。|
|[CDHtml对话：翻译加速器](#translateaccelerator)|调用 以处理菜单快捷键消息。|
|[CDHtml对话：翻译Url](#translateurl)|调用以修改要加载的 URL。|
|[CDHtml对话：：更新UI](#updateui)|调用 以通知主机命令状态已更改。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDHtml对话：：m_bUseHtmlTitle](#m_busehtmltitle)|指示是否使用 HTML 文档的标题作为对话框标题。|
|[CDHtml对话：m_nHtmlResID](#m_nhtmlresid)|要显示的 HTML 资源的资源 ID。|
|[CDHtml对话：：m_pBrowserApp](#m_pbrowserapp)|指向 Web 浏览器应用程序的指针。|
|[CDHtml对话：：m_spHtmlDoc](#m_sphtmldoc)|指向 HTML 文档的指针。|
|[CDHtml对话：：m_strCurrentUrl](#m_strcurrenturl)|当前 URL。|
|[CDHtml对话：：m_szHtmlResID](#m_szhtmlresid)|HTML 资源 ID 的字符串版本。|

## <a name="remarks"></a>备注

`CDHtmlDialog`可以加载要从 HTML 资源或 URL 显示的 HTML。

`CDHtmlDialog`还可以使用 HTML 控件进行数据交换，并处理 HTML 控件中的事件，例如按钮单击。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>要求

**标题：** afxdhtml.h

## <a name="ddx_dhtml-helper-macros"></a><a name="ddx_dhtml_helper_macros"></a>DDX_DHtml帮助宏

DDX_DHtml帮助器宏允许轻松访问 HTML 页上控件的常用属性。

### <a name="data-exchange-macros"></a>数据交换宏

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|从所选控件设置或检索 Value 属性。|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|设置或检索当前元素的开始和结束标记之间的文本。|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|在当前元素的开始和结束标记之间设置或检索 HTML。|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|设置或检索目标 URL 或锚点。|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|设置或检索目标窗口或框架。|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|设置或检索文档中图像或视频剪辑的名称。|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|设置或检索关联帧的 URL。|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|设置或检索关联帧的 URL。|

## <a name="cdhtmldialogcanaccessexternal"></a><a name="canaccessexternal"></a>CDHtml对话：：可以访问外部

可重写，称为访问检查，以查看加载页上的脚本对象是否可以访问控件站点的外部调度。 检查以确保派单对脚本安全，或者当前区域允许对脚本不安全的对象。

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="cdhtmldialogcdhtmldialog"></a><a name="cdhtmldialog"></a>CDHtml对话：：CDHtml对话

构造基于资源的动态 HTML 对话框。

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*lpszTemplate 名称*<br/>
作为对话框模板资源名称的 null 终止字符串。

*什奇雷斯ID*<br/>
作为 HTML 资源名称的 null 终止字符串。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象的指针[（CWnd](../../mfc/reference/cwnd-class.md)类型）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

*nHtmlResID*<br/>
包含 HTML 资源的 ID 号。

### <a name="remarks"></a>备注

构造函数的第二种形式通过模板名称提供对对话框资源的访问。 构造函数的第三种形式通过资源模板的 ID 提供对对话框资源的访问。 通常，ID 以**IDD_** 前缀开头。

## <a name="cdhtmldialogcdhtmldialog"></a><a name="_dtorcdhtmldialog"></a>CDHtml对话：：_CDHtml对话

销毁 CDHtmlDialog 对象。

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>备注

必须使用[CWnd：:DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)成员函数来销毁由[CDialog：：：create](../../mfc/reference/cdialog-class.md#create)创建的无模式对话框。

## <a name="cdhtmldialogcreatecontrolsite"></a><a name="createcontrolsite"></a>CDHtml对话：创建控制网站

用于创建控件站点实例以在对话框上承载 WebBrowser 控件的可重写操作。

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>参数

*pContainer*<br/>
指向[COleControl 容器](../../mfc/reference/colecontrolcontainer-class.md)对象的指针

*ppSite*<br/>
指向[指向 COleControlSite](../../mfc/reference/colecontrolsite-class.md)的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

您可以重写此成员函数以返回您自己的控件站点类的实例。

## <a name="cdhtmldialogddx_dhtml_axcontrol"></a><a name="ddx_dhtml_axcontrol"></a>CDHtml对话：:DDX_DHtml_Ax控制

在 HTML 页上的成员变量和 ActiveX 控件的属性值之间交换数据。

```
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

*szId*<br/>
ActiveX 控件的 HTML 源中对象标记的 ID 参数的值。

*dispId*<br/>
要与其交换数据的属性的调度 ID。

*szProp名称*<br/>
属性的名称。

*var*<br/>
类型[VARIANT 、 COlevariant](../../mfc/reference/colevariant-class.md)或[CComvariant](../../atl/reference/ccomvariant-class.md)的数据成员，用于保存与 ActiveX 控件属换的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

## <a name="cdhtmldialogddx_dhtml_checkbox"></a><a name="ddx_dhtml_checkbox"></a>CDHtml对话：:DDX_DHtml_复选框

在 HTML 页上的成员变量和复选框之间交换数据。

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

*szId*<br/>
为 HTML 控件的 ID 参数指定的值。

*value*<br/>
要交换的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

## <a name="cdhtmldialogddx_dhtml_elementtext"></a><a name="ddx_dhtml_elementtext"></a>CDHtml对话：:DDX_DHtml_元素文本

在成员变量和 HTML 页上的任何 HTML 元素属性之间交换数据。

```
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

*szId*<br/>
为 HTML 控件的 ID 参数指定的值。

*dispId*<br/>
要与其交换数据的 HTML 元素的调度 ID。

*value*<br/>
要交换的值。

## <a name="cdhtmldialogddx_dhtml_radio"></a><a name="ddx_dhtml_radio"></a>CDHtml对话：:DDX_DHtml_收音机

在 HTML 页上的成员变量和单选按钮之间交换数据。

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

*szId*<br/>
为 HTML 控件的 ID 参数指定的值。

*value*<br/>
要交换的值。

## <a name="cdhtmldialogddx_dhtml_selectindex"></a><a name="ddx_dhtml_selectindex"></a>CDHtml对话：:DDX_DHtml_选择索引

获取或设置 HTML 页上的列表框的索引。

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

*szId*<br/>
为 HTML 控件的`id`参数指定的值。

*value*<br/>
要交换的值。

## <a name="cdhtmldialogddx_dhtml_selectstring"></a><a name="ddx_dhtml_selectstring"></a>CDHtml对话：:DDX_DHtml_选择字符串

获取或设置 HTML 页上列表框条目的显示文本（基于当前索引）。

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

*szId*<br/>
为 HTML 控件的 ID 参数指定的值。

*value*<br/>
要交换的值。

## <a name="cdhtmldialogddx_dhtml_selectvalue"></a><a name="ddx_dhtml_selectvalue"></a>CDHtml对话：:DDX_DHtml_选择值

获取或设置 HTML 页上的列表框条目的值（基于当前索引）。

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

*szId*<br/>
为 HTML 控件的 ID 参数指定的值。

*value*<br/>
要交换的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

## <a name="cdhtmldialogdestroymodeless"></a><a name="destroymodeless"></a>CDHtmlDialog：:D无摩模式

从`CDHtmlDialog`对象分离无模式对话框并销毁该对象。

```
void DestroyModeless();
```

## <a name="cdhtmldialogenablemodeless"></a><a name="enablemodeless"></a>CDHtmlDialog：启用无模式

启用无模式对话框。

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>参数

*f 启用*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))中的*fenable：：* 在 Windows SDK 中启用无模式。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：启用无模式](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))，如 Windows SDK 中所述。

## <a name="cdhtmldialogfilterdataobject"></a><a name="filterdataobject"></a>CDHtml对话：：筛选数据对象

允许对话框筛选托管浏览器创建的剪贴板数据对象。

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>参数

*Pdo*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))中的*pDO：：* 在 Windows SDK 中筛选数据对象。

*普多雷特*<br/>
请参阅 Windows SDK`IDocHostUIHandler::FilterDataObject`中的*ppDORet。*

### <a name="return-value"></a>返回值

返回S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：筛选数据对象](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))，如 Windows SDK 中所述。

## <a name="cdhtmldialoggetcontroldispatch"></a><a name="getcontroldispatch"></a>CDHtmlDialog：获取控制调度

检索嵌入`IDispatch`[GetDHtmlDocument](#getdhtmldocument)返回的 HTML 文档中的 ActiveX 控件上的界面。

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>参数

*szId*<br/>
ActiveX 控件的 HTML ID。

*普迪普*<br/>
如果在`IDispatch`网页中找到控件的界面。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="cdhtmldialoggetcontrolproperty"></a><a name="getcontrolproperty"></a>CDHtml对话：获取控制属性

检索指定的 ActiveX 控件的请求属性。

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>参数

*szId*<br/>
ActiveX 控件的 HTML ID。

*szProp名称*<br/>
当前用户默认区域设置中的属性的名称。

*pdisp控制*<br/>
ActiveX 控件的`IDispatch`指针。

*dispId*<br/>
属性的调度 ID。

### <a name="return-value"></a>返回值

如果找不到控件或属性，则包含请求的属性或空变体的变体。

### <a name="remarks"></a>备注

重载从顶部效率最低到底部效率最高列出。

## <a name="cdhtmldialoggetcurrenturl"></a><a name="getcurrenturl"></a>CDHtml对话：获取当前Url

检索与当前文档关联的统一资源定位器 （URL）。

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>参数

*szUrl*<br/>
包含要检索的 URL 的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象。

## <a name="cdhtmldialoggetdhtmldocument"></a><a name="getdhtmldocument"></a>CDHtml对话：获取Html文档

检索当前加载的 HTML 文档上的[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))界面。

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>参数

* \* \** 指向指向 HTML 文档的指针。

### <a name="return-value"></a>返回值

标准 HRESULT。 如果成功，则返回S_OK。

## <a name="cdhtmldialoggetdroptarget"></a><a name="getdroptarget"></a>CDHtml对话：：获取删除目标

当包含的 WebBrowser 控件用作放置目标以允许对话框提供替代[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)时，由它调用它。

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>参数

*pDropTarget*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))中的*pDropTarget：：* 在 Windows SDK 中获取DropTarget。

*ppDrop目标*<br/>
请参阅 Windows SDK`IDocHostUIHandler::GetDropTarget`中的*ppDropTarget。*

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：getDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))的实现，如 Windows SDK 中所述。

## <a name="cdhtmldialoggetelement"></a><a name="getelement"></a>CDHtml对话：获取元素

返回*szElementId*指定的 HTML 元素上的接口。

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

*普迪普*<br/>
指向`IDispatch`请求的元素或元素集合的指针。

*pbCollection*<br/>
一种 BOOL，指示*ppdisp*表示的对象是单个元素还是元素的集合。

*pphtml元素*<br/>
指向`IHTMLElement`请求的元素的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

如果需要处理具有指定 ID 的多个元素的情况，请使用第一个重载。 可以使用最后一个参数来找出返回的接口指针是指向集合还是单个项。 如果接口指针位于集合上，则可以查询`IHTMLElementCollection`，并使用其`item`属性按单位位置引用元素。

如果页面中有多个具有相同 ID 的元素，则第二个重载将失败。

## <a name="cdhtmldialoggetelementhtml"></a><a name="getelementhtml"></a>CDHtml对话：获取元素Html

检索`innerHTML`*szElementId*标识的 HTML 元素的属性。

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

### <a name="return-value"></a>返回值

找不到`innerHTML`该元素时，*由 szElementId*或 NULL 标识的 HTML 元素的属性。

## <a name="cdhtmldialoggetelementinterface"></a><a name="getelementinterface"></a>CDHtml对话：获取元素接口

从*szElementId*标识的 HTML 元素检索请求的接口指针。

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

*普夫奥比*<br/>
如果找到元素并且查询成功，则使用请求的接口指针填充的指针的地址。

*雷菲德*<br/>
请求接口的接口 ID （IID）。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

## <a name="cdhtmldialoggetelementproperty"></a><a name="getelementproperty"></a>CDHtml对话：获取元素属性

从*szElementId*标识的 HTML 元素中检索由*dispId*标识的属性的值。

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

*dispId*<br/>
属性的调度 ID。

### <a name="return-value"></a>返回值

如果找不到属性或元素，则属性或空变体的值。

## <a name="cdhtmldialoggetelementtext"></a><a name="getelementtext"></a>CDHtml对话：获取元素文本

检索`innerText`*szElementId*标识的 HTML 元素的属性。

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

### <a name="return-value"></a>返回值

找不到`innerText`属性或元素时，由*szElementId*或 NULL 标识的 HTML 元素的属性。

## <a name="cdhtmldialoggetevent"></a><a name="getevent"></a>CDHtml对话：获取事件

返回指向`IHTMLEventObj`当前事件对象的指针。

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>参数

*ppEventObj*<br/>
将用接口指针填充的`IHTMLEventObj`指针的地址。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

只能从 DHTML 事件处理程序中调用此函数。

## <a name="cdhtmldialoggetexternal"></a><a name="getexternal"></a>CDHtml对话：获取外部

获取主机的`IDispatch`接口。

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>参数

*ppDispatch*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))中的*ppDispatch：* 在 Windows SDK 中获取外部。

### <a name="return-value"></a>返回值

返回S_OK成功或E_NOTIMPL失败。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：get 外部](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))，如 Windows SDK 中所述。

## <a name="cdhtmldialoggethostinfo"></a><a name="gethostinfo"></a>CDHtmlDialog：获取Hostinfo

检索主机的 UI 功能。

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>参数

*pInfo*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))中的*pInfo：* 在 Windows SDK 中获取Hostinfo。

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler 的实现：：获取HostInfo，](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))如 Windows SDK 中所述。

## <a name="cdhtmldialoggetoptionkeypath"></a><a name="getoptionkeypath"></a>CDHtml对话：获取选项关键路径

检索存储用户首选项的注册表项。

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>参数

*pchKey*<br/>
请参阅 IDocHostUIHandler 中的*pchKey：* 在 Windows SDK 中[获取OptionKeyPath。](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))

*dw*<br/>
请参阅 Windows `IDocHostUIHandler::GetOptionKeyPath` SDK 中的*dw。*

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler 的实现：：获取选项KeyPath，](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))如 Windows SDK 中所述。

## <a name="cdhtmldialoghideui"></a><a name="hideui"></a>CDHtml对话：：隐藏UI

隐藏主机的 UI。

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：隐藏UI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))的实现，如 Windows SDK 中所述。

## <a name="cdhtmldialogisexternaldispatchsafe"></a><a name="isexternaldispatchsafe"></a>CDHtmlDialog：是外部调度安全

指示主机的`IDispatch`接口是否安全编写脚本。

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>返回值

返回 FALSE。

## <a name="cdhtmldialogloadfromresource"></a><a name="loadfromresource"></a>CDHtml对话：：从资源加载

在 DHTML 对话框中将指定资源加载到 Web 浏览器控件中。

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>参数

*lpsz资源*<br/>
指向包含要加载的资源名称的字符串的指针。

*nRes*<br/>
要加载的资源的 ID。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

## <a name="cdhtmldialogm_busehtmltitle"></a><a name="m_busehtmltitle"></a>CDHtml对话：：m_bUseHtmlTitle

指示是否使用 HTML 文档的标题作为对话框标题。

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>备注

如果 m = bUseHtmlTitle 为 TRUE，则对话框标题设置为等于 HTML 文档的标题;如果**m**= **bUseHtmlTitle 为**TRUE，则对话框标题设置为等于 HTML 文档的标题。否则，将使用对话框资源中的标题。

## <a name="cdhtmldialogm_nhtmlresid"></a><a name="m_nhtmlresid"></a>CDHtml对话：m_nHtmlResID

要显示的 HTML 资源的资源 ID。

```
UINT m_nHtmlResID;
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

## <a name="cdhtmldialogm_pbrowserapp"></a><a name="m_pbrowserapp"></a>CDHtml对话：：m_pBrowserApp

指向 Web 浏览器应用程序的指针。

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

## <a name="cdhtmldialogm_sphtmldoc"></a><a name="m_sphtmldoc"></a>CDHtml对话：：m_spHtmlDoc

指向 HTML 文档的指针。

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

## <a name="cdhtmldialogm_strcurrenturl"></a><a name="m_strcurrenturl"></a>CDHtml对话：：m_strCurrentUrl

当前 URL。

```
CString m_strCurrentUrl;
```

## <a name="cdhtmldialogm_szhtmlresid"></a><a name="m_szhtmlresid"></a>CDHtml对话：：m_szHtmlResID

HTML 资源 ID 的字符串版本。

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

## <a name="cdhtmldialognavigate"></a><a name="navigate"></a>CDHtml对话：导航

导航到由*lpszURL*指定的 URL 标识的资源。

```
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>参数

*lpszURL*<br/>
指向包含要定位的 URL 的字符串的指针。

dwFlags**<br/>
变量的标志，用于指定是将资源添加到历史记录列表、是读取到缓存还是从缓存写入，以及是否在新窗口中显示资源。 变量可以是[浏览器导航常点](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\))枚举定义的值的组合。

*lpsz目标帧名称*<br/>
指向字符串的指针，其中包含要在其中显示资源的框架的名称。

*lpszHeaders*<br/>
指向指定要发送到服务器的 HTTP 标头的值的指针。 这些标头将添加到默认的 Internet 资源管理器标头中。 标头可以指定服务器所需的操作、传递给服务器的数据类型或状态代码等信息。 如果 URL 不是 HTTP URL，则忽略此参数。

*lpvPostData*<br/>
指向要随 HTTP POST 事务发送的数据的指针。 例如，POST 事务用于发送 HTML 表单收集的数据。 如果此参数未指定任何发布数据，则`Navigate`发出 HTTP GET 事务。 如果 URL 不是 HTTP URL，则忽略此参数。

*德沃斯特数据伦*<br/>
与 HTTP POST 事务一起发送的数据。 例如，POST 事务用于发送 HTML 表单收集的数据。 如果此参数未指定任何发布数据，则`Navigate`发出 HTTP GET 事务。 如果 URL 不是 HTTP URL，则忽略此参数。

## <a name="cdhtmldialogonbeforenavigate"></a><a name="onbeforenavigate"></a>CDHtmlDialog：：在导航前打开

框架调用，导致在导航发生之前触发事件。

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
指向 `IDispatch` 对象的指针。

*szUrl*<br/>
指向包含要导航到的 URL 的字符串的指针。

## <a name="cdhtmldialogondocumentcomplete"></a><a name="ondocumentcomplete"></a>CDHtml对话：：在文档完成

由框架调用，以便在文档达到READYSTATE_COMPLETE状态时通知应用程序。

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
指向 `IDispatch` 对象的指针。

*szUrl*<br/>
指向包含导航到的 URL 的字符串的指针。

## <a name="cdhtmldialogondocwindowactivate"></a><a name="ondocwindowactivate"></a>CDHtml对话：：在DocWindow激活

当文档窗口激活或停用时，由框架调用。

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>参数

*f 激活*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))中的*fActivate：* 在 Windows SDK 中激活 OnDocWindow。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler 的实现：：OnDocWindowActivate，](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))如 Windows SDK 中所述。

## <a name="cdhtmldialogonframewindowactivate"></a><a name="onframewindowactivate"></a>CDHtmlDialog：在框架窗口激活

当框架窗口激活或停用时，框架调用。

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>参数

*f 激活*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))中的*fActivate：* 在 Windows SDK 中启用 FrameWindow。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler 的实现：：在FrameWindow激活上](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))，如 Windows SDK 中所述。

## <a name="cdhtmldialogoninitdialog"></a><a name="oninitdialog"></a>CDHtmlDialog：onInitDialog

调用以响应WM_INITDIALOG消息。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

默认实现返回 TRUE。

### <a name="remarks"></a>备注

此消息在`Create`期间发送到对话框，`CreateIndirect`或`DoModal`调用，该对话框在显示对话框之前发生。

如果在初始化对话框时需要执行特殊处理，则重写此成员函数。 在重写版本中，首先调用基类`OnInitDialog`，但忽略其返回值。 您通常会从重写的成员函数返回 TRUE。

Windows 通过`OnInitDialog`所有 Microsoft 基础类库对话框共有的标准全局对话框过程（而不是通过消息映射）调用该函数，因此不需要此成员函数的消息映射条目。

## <a name="cdhtmldialogonnavigatecomplete"></a><a name="onnavigatecomplete"></a>CDHtml对话：：导航完成

导航到指定 URL 后由框架调用。

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
指向 `IDispatch` 对象的指针。

*szUrl*<br/>
指向包含导航到的 URL 的字符串的指针。

## <a name="cdhtmldialogresizeborder"></a><a name="resizeborder"></a>CDHtml对话：调整边框大小

提醒需要调整边框空间大小的对象。

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>参数

*prc边界*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))中的*prcBorder：：* 在 Windows SDK 中调整边框大小。

*pUI窗口*<br/>
请参阅 Windows SDK`IDocHostUIHandler::ResizeBorder`中的*pUIWindow。*

*fFrame 窗口*<br/>
请参阅 Windows SDK`IDocHostUIHandler::ResizeBorder`中的*fFrame Window。*

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

## <a name="cdhtmldialogsetcontrolproperty"></a><a name="setcontrolproperty"></a>CDHtml对话：：设置控制属性

将 ActiveX 控件的属性设置为新值。

```
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
ActiveX 控件的 HTML ID。

*dispId*<br/>
要设置的属性的调度 ID。

*普瓦尔*<br/>
指向包含新属性值的 VARIANT 的变体的指针。

*pdisp控制*<br/>
指向 ActiveX 控件的接口`IDispatch`的指针。

*szProp名称*<br/>
包含要设置的属性的名称的字符串。

## <a name="cdhtmldialogsetelementhtml"></a><a name="setelementhtml"></a>CDHtml对话：：设置元素Html

设置`innerHTML`HTML 元素的属性。

```
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

*bstrText*<br/>
`innerHTML` 属性的新值。

*朋克埃莱姆*<br/>
HTML`IUnknown`元素的指针。

## <a name="cdhtmldialogsetelementproperty"></a><a name="setelementproperty"></a>CDHtml对话：：设置元素属性

设置 HTML 元素的属性。

```
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

*dispId*<br/>
要设置的属性的调度 ID。

*普瓦尔*<br/>
属性的新值。

## <a name="cdhtmldialogsetelementtext"></a><a name="setelementtext"></a>CDHtml对话：：设置元素文本

设置`innerText`HTML 元素的属性。

```
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

*bstrText*<br/>
`innerText` 属性的新值。

*朋克埃莱姆*<br/>
HTML`IUnknown`元素的指针。

## <a name="cdhtmldialogsetexternaldispatch"></a><a name="setexternaldispatch"></a>CDHtml对话：：设置外部调度

设置主机的`IDispatch`接口。

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>参数

*pdisp 外部*<br/>
新`IDispatch`接口。

## <a name="cdhtmldialogsethostflags"></a><a name="sethostflags"></a>CDHtml对话：：设置主机标志

设置主机 UI 标志。

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>参数

dwFlags**<br/>
有关可能的值，请参阅 Windows SDK 中的[DOCHOSTUIFLAG。](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\))

## <a name="cdhtmldialogshowcontextmenu"></a><a name="showcontextmenu"></a>CDHtml对话：：显示上下文菜单

在显示上下文菜单时调用。

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>参数

*dwID*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))中的*dwID：* 在 Windows SDK 中显示上下文菜单。

*Ppt*<br/>
请参阅 Windows `IDocHostUIHandler::ShowContextMenu` SDK 中的*分页*。

*pcmdt保留*<br/>
请参阅 Windows SDK`IDocHostUIHandler::ShowContextMenu`中的*pcmdt 保留*。

*pdisp保留*<br/>
请参阅 Windows SDK`IDocHostUIHandler::ShowContextMenu`中的*pdisp 保留*。

### <a name="return-value"></a>返回值

返回S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：显示上下文菜单](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))，如 Windows SDK 中所述。

## <a name="cdhtmldialogshowui"></a><a name="showui"></a>CDHtml对话：：显示UI

显示主机的 UI。

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>参数

*dwID*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))中的*dwID：：* 在 Windows SDK 中显示 UI。

*p活动对象*<br/>
请参阅 Windows SDK`IDocHostUIHandler::ShowUI`中的*d 活动对象*。

*pCommand目标*<br/>
请参阅 Windows SDK`IDocHostUIHandler::ShowUI`中的*pCommandTarget。*

*pFrame*<br/>
请参阅 Windows `IDocHostUIHandler::ShowUI` SDK 中的*pFrame。*

*pDoc*<br/>
请参阅 Windows `IDocHostUIHandler::ShowUI` SDK 中的*pDoc。*

### <a name="return-value"></a>返回值

返回S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：：ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))的实现，如 Windows SDK 中所述。

## <a name="cdhtmldialogtranslateaccelerator"></a><a name="translateaccelerator"></a>CDHtml对话：翻译加速器

调用 以处理菜单快捷键消息。

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>参数

*lpMsg*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))中的*lpMsg：Windows* SDK 中的翻译加速器。

*普吉德集团*<br/>
请参阅 Windows SDK 中的`IDocHostUIHandler::TranslateAccelerator` *pguidCmd 组*。

*nCmdID*<br/>
请参阅 Windows SDK`IDocHostUIHandler::TranslateAccelerator`中的*nCmdID。*

### <a name="return-value"></a>返回值

返回S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：翻译加速器](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))的实现，如 Windows SDK 中所述。

## <a name="cdhtmldialogtranslateurl"></a><a name="translateurl"></a>CDHtml对话：翻译Url

调用以修改要加载的 URL。

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>参数

*dwTranslate*<br/>
请参阅[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))中的*dwTranslate：Windows* SDK 中的翻译 Url。

*普乔林*<br/>
请参阅 Windows SDK`IDocHostUIHandler::TranslateUrl`中的*pchURLIn。*

*ppchURLOut*<br/>
请参阅 Windows SDK`IDocHostUIHandler::TranslateUrl`中的*ppchURLOut。*

### <a name="return-value"></a>返回值

返回S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：翻译Url](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))的实现，如 Windows SDK 中所述。

## <a name="cdhtmldialogupdateui"></a><a name="updateui"></a>CDHtml对话：：更新UI

调用 以通知主机命令状态已更改。

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler：：updateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))的实现，如 Windows SDK 中所述。

## <a name="see-also"></a>另请参阅

[MFC 样品 DHtml 探索](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml帮助宏](#ddx_dhtml_helper_macros)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
