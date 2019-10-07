---
title: CDHtmlDialog 类
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
ms.openlocfilehash: ec424e433dc84bf4188e349eb6450888aeeeb463
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506903"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog 类

用于创建使用 HTML 而非对话框资源来实现其用户界面的对话框。

## <a name="syntax"></a>语法

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|构造 CDHtmlDialog 对象。|
|[CDHtmlDialog::~CDHtmlDialog](#_dtorcdhtmldialog)|销毁 CDHtmlDialog 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|作为访问检查调用的可重写, 用于查看已加载页上的脚本对象是否可以访问控件站点的外部调度。 检查以确保调度对于脚本是安全的, 或者当前区域允许对不安全的对象进行脚本编写。|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|可重写, 用于创建控件站点实例以承载对话框中的 WebBrowser 控件。|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|在 HTML 页上的某个 ActiveX 控件的成员变量和属性值之间交换数据。|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|在 HTML 页上的成员变量和复选框之间交换数据。|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|在 HTML 页上的成员变量和任何 HTML 元素属性之间交换数据。|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|在 HTML 页上的成员变量和单选按钮之间交换数据。|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|获取或设置 HTML 页上的列表框的索引。|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|获取或设置 HTML 页面上列表框条目的显示文本 (基于当前索引)。|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|获取或设置 HTML 页上的列表框项的值 (基于当前索引)。|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|销毁无模式对话框。|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|启用无模式对话框。|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|允许对话框筛选由托管浏览器创建的剪贴板数据对象。|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|检索嵌入`IDispatch`在 HTML 文档中的 ActiveX 控件上的接口。|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|检索指定 ActiveX 控件的请求的属性。|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|检索与当前文档关联的统一资源定位器 (URL)。|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|检索当前加载的 HTML 文档中的 IHTMLDocument2 接口。|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|当用作放置目标以允许对话框提供备用[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)时, 由包含的 WebBrowser 控件调用。|
|[CDHtmlDialog::GetElement](#getelement)|获取 HTML 元素上的接口。|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|检索 HTML `innerHTML`元素的属性。|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|从 HTML 元素检索请求的接口指针。|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|检索 HTML 元素的属性的值。|
|[CDHtmlDialog::GetElementText](#getelementtext)|检索 HTML `innerText`元素的属性。|
|[CDHtmlDialog::GetEvent](#getevent)|获取指向`IHTMLEventObj`当前事件对象的指针。|
|[CDHtmlDialog::GetExternal](#getexternal)|获取主机的`IDispatch`接口。|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|检索主机的 UI 功能。|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|检索在其下存储用户首选项的注册表项。|
|[CDHtmlDialog::HideUI](#hideui)|隐藏主机的 UI。|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|指示主机的`IDispatch`接口是否可安全编写脚本。|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|将指定的资源加载到 WebBrowser 控件中。|
|[CDHtmlDialog::Navigate](#navigate)|导航到指定的 URL。|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|在激发导航事件之前由框架调用。|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|由框架调用, 用于在文档达到 READYSTATE_COMPLETE 状态时通知应用程序。|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|当激活或停用文档窗口时由框架调用。|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|当激活或停用框架窗口时由框架调用。|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|在响应 WM_INITDIALOG 消息时调用。|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|在导航事件完成后由框架调用。|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|警告对象它需要调整其边框空间的大小。|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|将 ActiveX 控件的属性设置为新值。|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|设置 HTML `innerHTML`元素的属性。|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|设置 HTML 元素的属性。|
|[CDHtmlDialog::SetElementText](#setelementtext)|设置 HTML `innerText`元素的属性。|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|设置宿主的`IDispatch`接口。|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|设置宿主的 UI 标志。|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|当要显示上下文菜单时调用。|
|[CDHtmlDialog::ShowUI](#showui)|显示主机的 UI。|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|调用以处理菜单快捷键-密钥消息。|
|[CDHtmlDialog::TranslateUrl](#translateurl)|调用以修改要加载的 URL。|
|[CDHtmlDialog::UpdateUI](#updateui)|调用以通知主机命令状态已更改。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|指示是否使用 HTML 文档的标题作为对话框标题。|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|要显示的 HTML 资源的资源 ID。|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|指向 Web 浏览器应用程序的指针。|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|指向 HTML 文档的指针。|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|当前 URL。|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|HTML 资源 ID 的字符串版本。|

## <a name="remarks"></a>备注

`CDHtmlDialog`可以从 HTML 资源或 URL 加载要显示的 HTML。

`CDHtmlDialog`还可以通过 HTML 控件进行数据交换, 并处理 HTML 控件 (如按钮单击) 中的事件。

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

**标头:** afxdhtml

##  <a name="ddx_dhtml_helper_macros"></a>DDX_DHtml Helper 宏

DDX_DHtml helper 宏允许在 HTML 页上轻松访问控件的常用属性。

### <a name="data-exchange-macros"></a>数据交换宏

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|设置或检索选定控件的值属性。|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|设置或检索当前元素的开始标记和结束标记之间的文本。|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|设置或检索当前元素的开始标记和结束标记之间的 HTML。|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|设置或检索目标 URL 或定位点。|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|设置或检索目标窗口或框架。|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|设置或检索文档中图像或视频剪辑的名称。|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|设置或检索关联帧的 URL。|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|设置或检索关联帧的 URL。|

##  <a name="canaccessexternal"></a>CDHtmlDialog:: CanAccessExternal

作为访问检查调用的可重写, 用于查看已加载页上的脚本对象是否可以访问控件站点的外部调度。 检查以确保调度对于脚本是安全的, 或者当前区域允许对不安全的对象进行脚本编写。

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="cdhtmldialog"></a>CDHtmlDialog:: CDHtmlDialog

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

*lpszTemplateName*<br/>
以 null 结尾的字符串, 它是对话框模板资源的名称。

*szHtmlResID*<br/>
以 null 结尾的字符串, 它是 HTML 资源的名称。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象 (类型为[CWnd](../../mfc/reference/cwnd-class.md)) 的指针。 如果为 NULL, 则对话框对象的父窗口将设置为主应用程序窗口。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

*nHtmlResID*<br/>
包含 HTML 资源的 ID 号。

### <a name="remarks"></a>备注

构造函数的第二种形式通过模板名称提供对对话框资源的访问。 第三种形式的构造函数通过资源模板的 ID 提供对对话框资源的访问。 通常, ID 以**IDD_** 前缀开头。

##  <a name="_dtorcdhtmldialog"></a>CDHtmlDialog:: ~ CDHtmlDialog

销毁 CDHtmlDialog 对象。

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>备注

[CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow)成员函数必须用于销毁[CDialog:: Create](../../mfc/reference/cdialog-class.md#create)创建的无模式对话框。

##  <a name="createcontrolsite"></a>CDHtmlDialog:: CreateControlSite

可重写, 用于创建控件站点实例以承载对话框中的 WebBrowser 控件。

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>参数

*pContainer*<br/>
指向[COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)对象的指针

*ppSite*<br/>
指向指向[COleControlSite](../../mfc/reference/colecontrolsite-class.md)的指针的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

您可以重写此成员函数以返回您自己的控件站点类的实例。

##  <a name="ddx_dhtml_axcontrol"></a>CDHtmlDialog::D DX_DHtml_AxControl

在 HTML 页上的某个 ActiveX 控件的成员变量和属性值之间交换数据。

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
要与之交换数据的属性的调度 ID。

*szPropName*<br/>
属性的名称。

*var*<br/>
类型为 VARIANT、 [COleVariant](../../mfc/reference/colevariant-class.md)或[CComVariant](../../atl/reference/ccomvariant-class.md)的数据成员, 用于保存与 ActiveX 控件属性交换的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>CDHtmlDialog::D DX_DHtml_CheckBox

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

*值*<br/>
要交换的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>CDHtmlDialog::D DX_DHtml_ElementText

在 HTML 页上的成员变量和任何 HTML 元素属性之间交换数据。

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
要与之交换数据的 HTML 元素的调度 ID。

*值*<br/>
要交换的值。

##  <a name="ddx_dhtml_radio"></a>CDHtmlDialog::D DX_DHtml_Radio

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

*值*<br/>
要交换的值。

##  <a name="ddx_dhtml_selectindex"></a>CDHtmlDialog::D DX_DHtml_SelectIndex

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

*值*<br/>
要交换的值。

##  <a name="ddx_dhtml_selectstring"></a>CDHtmlDialog::D DX_DHtml_SelectString

获取或设置 HTML 页面上列表框条目的显示文本 (基于当前索引)。

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

*值*<br/>
要交换的值。

##  <a name="ddx_dhtml_selectvalue"></a>CDHtmlDialog::D DX_DHtml_SelectValue

获取或设置 HTML 页上的列表框项的值 (基于当前索引)。

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

*值*<br/>
要交换的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>CDHtmlDialog::D estroyModeless

从`CDHtmlDialog`对象分离无模式对话框并销毁对象。

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>CDHtmlDialog:: EnableModeless

启用无模式对话框。

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>参数

*fEnable*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))中的*fEnable* 。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="filterdataobject"></a>CDHtmlDialog:: FilterDataObject

允许对话框筛选由托管浏览器创建的剪贴板数据对象。

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>参数

*pDO*<br/>
请参阅 Windows SDK 中的[IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))中的*pDO* 。

*ppDORet*<br/>
请参阅 Windows SDK `IDocHostUIHandler::FilterDataObject`中的 ppDORet。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="getcontroldispatch"></a>CDHtmlDialog:: GetControlDispatch

检索嵌入`IDispatch`在[GetDHtmlDocument](#getdhtmldocument)返回的 HTML 文档中的 ActiveX 控件上的接口。

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>参数

*szId*<br/>
ActiveX 控件的 HTML ID。

*ppdisp*<br/>
如果在网页中找到, 则为控件的接口。`IDispatch`

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="getcontrolproperty"></a>CDHtmlDialog:: GetControlProperty

检索指定 ActiveX 控件的请求的属性。

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

*szPropName*<br/>
当前用户的默认区域设置中的属性的名称。

*pdispControl*<br/>
ActiveX 控件的指针。 `IDispatch`

*dispId*<br/>
属性的调度 ID。

### <a name="return-value"></a>返回值

一个包含所请求的属性的变量, 如果找不到该控件或属性, 则为空变量。

### <a name="remarks"></a>备注

从最小的位置按最有效的重载列出重载。

##  <a name="getcurrenturl"></a>CDHtmlDialog:: GetCurrentUrl

检索与当前文档关联的统一资源定位器 (URL)。

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>参数

*szUrl*<br/>
一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象, 其中包含要检索的 URL。

##  <a name="getdhtmldocument"></a>CDHtmlDialog:: GetDHtmlDocument

检索当前加载的 HTML 文档中的[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))接口。

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>参数

pphtmlDoc 指向 HTML 文档的指针的指针。  *\* \**

### <a name="return-value"></a>返回值

标准的 HRESULT。 如果成功, 则返回 S_OK。

##  <a name="getdroptarget"></a>CDHtmlDialog:: GetDropTarget

当用作放置目标以允许对话框提供备用[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)时, 由包含的 WebBrowser 控件调用。

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>参数

*pDropTarget*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))中的*pDropTarget* 。

*ppDropTarget*<br/>
请参阅 Windows SDK `IDocHostUIHandler::GetDropTarget`中的 ppDropTarget。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="getelement"></a>CDHtmlDialog:: GetElement

返回由*szElementId*指定的 HTML 元素上的接口。

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

*ppdisp*<br/>
指向所请求元素或元素集合的指针。`IDispatch`

*pbCollection*<br/>
一个布尔值, 指示由*ppdisp*表示的对象是单个元素还是元素的集合。

*pphtmlElement*<br/>
指向所请求元素的指针。`IHTMLElement`

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果需要处理可能存在多个具有指定 ID 的元素的条件, 请使用第一个重载。 您可以使用最后一个参数来查明返回的接口指针是否指向集合或单个项。 如果接口指针位于集合上, 则可以查询`IHTMLElementCollection`并使用其`item`属性, 按序号位置引用元素。

如果页面中有多个具有相同 ID 的元素, 第二个重载将失败。

##  <a name="getelementhtml"></a>CDHtmlDialog:: GetElementHtml

检索由*szElementId*标识的 HTML 元素的属性。`innerHTML`

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

### <a name="return-value"></a>返回值

如果`innerHTML`找不到元素, 则为*szElementId*标识的 HTML 元素的属性。

##  <a name="getelementinterface"></a>CDHtmlDialog:: GetElementInterface

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

*ppvObj*<br/>
如果找到了元素并且查询成功, 则为将使用所请求的接口指针填充的指针的地址。

*refiid*<br/>
请求的接口的接口 ID (IID)。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>CDHtmlDialog:: GetElementProperty

检索由*dispId*标识的属性的值, 该属性由*szElementId*标识。

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

如果找不到属性或元素, 则为属性的值或空变量。

##  <a name="getelementtext"></a>CDHtmlDialog:: GetElementText

检索由*szElementId*标识的 HTML 元素的属性。`innerText`

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

### <a name="return-value"></a>返回值

由`innerText` *szElementId*标识的 HTML 元素的属性, 如果找不到该属性或元素, 则为 NULL。

##  <a name="getevent"></a>CDHtmlDialog:: GetEvent

返回指向`IHTMLEventObj`当前事件对象的指针。

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>参数

*ppEventObj*<br/>
将用`IHTMLEventObj`接口指针填充的指针的地址。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

只应从 DHTML 事件处理程序中调用此函数。

##  <a name="getexternal"></a>CDHtmlDialog:: GetExternal

获取主机的`IDispatch`接口。

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>参数

*ppDispatch*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))中的*ppDispatch* 。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK; 如果失败, 则返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="gethostinfo"></a>CDHtmlDialog:: GetHostInfo

检索主机的 UI 功能。

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>参数

*pInfo*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))中的*pInfo* 。

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="getoptionkeypath"></a>CDHtmlDialog:: GetOptionKeyPath

检索在其下存储用户首选项的注册表项。

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>参数

*pchKey*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))中的*pchKey* 。

*dw*<br/>
请参阅 Windows SDK `IDocHostUIHandler::GetOptionKeyPath`中的 dw。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="hideui"></a>CDHtmlDialog:: HideUI

隐藏主机的 UI。

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="isexternaldispatchsafe"></a>CDHtmlDialog:: IsExternalDispatchSafe

指示主机的`IDispatch`接口是否可安全编写脚本。

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>返回值

返回 FALSE。

##  <a name="loadfromresource"></a>CDHtmlDialog:: LoadFromResource

在 DHTML 对话框中将指定的资源加载到 WebBrowser 控件中。

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>参数

*lpszResource*<br/>
指向字符串的指针, 该字符串包含要加载的资源的名称。

*nRes*<br/>
要加载的资源的 ID。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

##  <a name="m_busehtmltitle"></a>CDHtmlDialog:: m_bUseHtmlTitle

指示是否使用 HTML 文档的标题作为对话框标题。

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>备注

如果**m**_ **bUseHtmlTitle**为 TRUE, 则将对话框标题设置为等于 HTML 文档的标题;否则, 将使用对话框资源中的标题。

##  <a name="m_nhtmlresid"></a>CDHtmlDialog:: m_nHtmlResID

要显示的 HTML 资源的资源 ID。

```
UINT m_nHtmlResID;
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>  CDHtmlDialog::m_pBrowserApp

指向 Web 浏览器应用程序的指针。

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

##  <a name="m_sphtmldoc"></a>  CDHtmlDialog::m_spHtmlDoc

指向 HTML 文档的指针。

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

##  <a name="m_strcurrenturl"></a>CDHtmlDialog:: m_strCurrentUrl

当前 URL。

```
CString m_strCurrentUrl;
```

##  <a name="m_szhtmlresid"></a>CDHtmlDialog:: m_szHtmlResID

HTML 资源 ID 的字符串版本。

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>CDHtmlDialog:: 导航

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
指向包含目标 URL 的字符串的指针。

*dwFlags*<br/>
变量的标志, 用于指定是将资源添加到历史记录列表、从缓存中读取还是写入缓存, 以及是否在新窗口中显示资源。 变量可以是[BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\))枚举定义的值的组合。

*lpszTargetFrameName*<br/>
指向字符串的指针, 该字符串包含要在其中显示资源的帧的名称。

*lpszHeaders*<br/>
一个指向值的指针, 该值指定要发送到服务器的 HTTP 标头。 这些标头将添加到默认的 Internet Explorer 标头。 标头可以指定此类信息, 如服务器所需的操作、要传递给服务器的数据类型或状态代码。 如果 URL 不是 HTTP URL, 则忽略此参数。

*lpvPostData*<br/>
指向要通过 HTTP POST transaction 发送的数据的指针。 例如, POST transaction 用于发送 HTML 窗体收集的数据。 如果此参数未指定任何 post 数据, `Navigate`则发出 HTTP GET transaction。 如果 URL 不是 HTTP URL, 则忽略此参数。

*dwPostDataLen*<br/>
要连同 HTTP POST transaction 一起发送的数据。 例如, POST transaction 用于发送 HTML 窗体收集的数据。 如果此参数未指定任何 post 数据, `Navigate`则发出 HTTP GET transaction。 如果 URL 不是 HTTP URL, 则忽略此参数。

##  <a name="onbeforenavigate"></a>CDHtmlDialog:: OnBeforeNavigate

由框架调用, 以在发生导航之前触发事件。

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
指向 `IDispatch` 对象的指针。

*szUrl*<br/>
指向字符串的指针, 该字符串包含要导航到的 URL。

##  <a name="ondocumentcomplete"></a>CDHtmlDialog:: OnDocumentComplete

由框架调用, 用于在文档达到 READYSTATE_COMPLETE 状态时通知应用程序。

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
指向 `IDispatch` 对象的指针。

*szUrl*<br/>
指向字符串的指针, 该字符串包含导航到的 URL。

##  <a name="ondocwindowactivate"></a>  CDHtmlDialog::OnDocWindowActivate

当激活或停用文档窗口时由框架调用。

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>参数

*fActivate*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))中的*fActivate* 。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="onframewindowactivate"></a>  CDHtmlDialog::OnFrameWindowActivate

当激活或停用框架窗口时由框架调用。

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>参数

*fActivate*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: onframewindowactivate 调用](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))中的*fActivate* 。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: onframewindowactivate 调用](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="oninitdialog"></a>CDHtmlDialog:: OnInitDialog

在响应 WM_INITDIALOG 消息时调用。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

默认实现返回 TRUE。

### <a name="remarks"></a>备注

此消息将在执行`Create`、 `CreateIndirect`或`DoModal`调用期间发送到对话框, 该对话框会在对话框显示之前立即发生。

如果在初始化对话框时需要执行特殊处理, 请重写此成员函数。 在重写的版本中, 首先调用基类`OnInitDialog` , 但忽略其返回值。 通常会从重写的成员函数返回 TRUE。

Windows 通过所有`OnInitDialog` Microsoft 基础类库对话框通用的标准全局对话框过程 (而不是通过消息映射) 调用函数, 因此不需要此成员函数的消息映射项。

##  <a name="onnavigatecomplete"></a>CDHtmlDialog:: OnNavigateComplete

在导航到指定的 URL 后, 由框架调用。

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
指向 `IDispatch` 对象的指针。

*szUrl*<br/>
指向字符串的指针, 该字符串包含导航到的 URL。

##  <a name="resizeborder"></a>CDHtmlDialog:: ResizeBorder

警告对象它需要调整其边框空间的大小。

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>参数

*prcBorder*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))中的*prcBorder* 。

*pUIWindow*<br/>
请参阅 Windows SDK `IDocHostUIHandler::ResizeBorder`中的 pUIWindow。

*fFrameWindow*<br/>
请参阅 Windows SDK `IDocHostUIHandler::ResizeBorder`中的 fFrameWindow。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

##  <a name="setcontrolproperty"></a>CDHtmlDialog:: SetControlProperty

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

*pVar*<br/>
指向包含新属性值的变量的指针。

*pdispControl*<br/>
指向 ActiveX 控件接口的`IDispatch`指针。

*szPropName*<br/>
包含要设置的属性名称的字符串。

##  <a name="setelementhtml"></a>CDHtmlDialog:: SetElementHtml

设置 HTML `innerHTML`元素的属性。

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

*punkElem*<br/>
HTML 元素的指针。 `IUnknown`

##  <a name="setelementproperty"></a>CDHtmlDialog:: SetElementProperty

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

*pVar*<br/>
属性的新值。

##  <a name="setelementtext"></a>CDHtmlDialog:: SetElementText

设置 HTML `innerText`元素的属性。

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

*punkElem*<br/>
HTML 元素的指针。 `IUnknown`

##  <a name="setexternaldispatch"></a>CDHtmlDialog:: SetExternalDispatch

设置宿主的`IDispatch`接口。

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>参数

*pdispExternal*<br/>
新`IDispatch`接口。

##  <a name="sethostflags"></a>CDHtmlDialog:: SetHostFlags

设置宿主 UI 标志。

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
有关可能的值, 请参阅 Windows SDK 中的[DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) 。

##  <a name="showcontextmenu"></a>CDHtmlDialog:: ShowContextMenu

当要显示上下文菜单时调用。

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>参数

*dwID*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))中的*dwID* 。

*ppt*<br/>
请参阅 Windows SDK `IDocHostUIHandler::ShowContextMenu`中的 ppt。

*pcmdtReserved*<br/>
请参阅 Windows SDK `IDocHostUIHandler::ShowContextMenu`中的 pcmdtReserved。

*pdispReserved*<br/>
请参阅 Windows SDK `IDocHostUIHandler::ShowContextMenu`中的 pdispReserved。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="showui"></a>CDHtmlDialog:: ShowUI

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
请参阅 Windows SDK 中[IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))中的*dwID* 。

*pActiveObject*<br/>
请参阅 Windows SDK 中`IDocHostUIHandler::ShowUI`的*d pActiveObject* in。

*pCommandTarget*<br/>
请参阅 Windows SDK `IDocHostUIHandler::ShowUI`中的 pCommandTarget。

*pFrame*<br/>
请参阅 Windows SDK `IDocHostUIHandler::ShowUI`中的 pFrame。

*pDoc*<br/>
请参阅 Windows SDK `IDocHostUIHandler::ShowUI`中的 pDoc。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="translateaccelerator"></a>CDHtmlDialog:: TranslateAccelerator

调用以处理菜单快捷键-密钥消息。

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>参数

*lpMsg*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))中的*lpMsg* 。

*pguidCmdGroup*<br/>
请参阅 Windows SDK `IDocHostUIHandler::TranslateAccelerator`中的 pguidCmdGroup。

*nCmdID*<br/>
请参阅 Windows SDK `IDocHostUIHandler::TranslateAccelerator`中的 nCmdID。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="translateurl"></a>  CDHtmlDialog::TranslateUrl

调用以修改要加载的 URL。

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>参数

*dwTranslate*<br/>
请参阅 Windows SDK 中[IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))中的*dwTranslate* 。

*pchURLIn*<br/>
请参阅 Windows SDK `IDocHostUIHandler::TranslateUrl`中的 pchURLIn。

*ppchURLOut*<br/>
请参阅 Windows SDK `IDocHostUIHandler::TranslateUrl`中的 ppchURLOut。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))实现, 如 Windows SDK 中所述。

##  <a name="updateui"></a>CDHtmlDialog:: UpdateUI

调用以通知主机命令状态已更改。

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的[IDocHostUIHandler:: UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))实现, 如 Windows SDK 中所述。

## <a name="see-also"></a>请参阅

[MFC 示例 DHtmlExplore](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml 帮助器宏](#ddx_dhtml_helper_macros)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
