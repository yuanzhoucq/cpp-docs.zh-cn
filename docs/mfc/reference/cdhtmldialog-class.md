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
ms.openlocfilehash: bda980c26f9791e1d4f03026f7e118e69a4ab881
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565800"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog 类

用于创建使用 HTML 对话框，而不是对话框资源来实现其用户界面。

## <a name="syntax"></a>语法

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|构造一个 CDHtmlDialog 对象。|
|[CDHtmlDialog::~CDHtmlDialog](#_dtorcdhtmldialog)|销毁 CDHtmlDialog 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|可重写的是作为调用访问检查，以查看是否已加载的页面上的脚本对象可以访问控制站点在外部调度。 检查以确保调度是用于编写脚本的安全，或者当前的区域允许不是可安全执行脚本的对象。|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|可重写用于创建控件站点实例以承载 WebBrowser 控件在对话框中。|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|成员变量和 HTML 页面上的 ActiveX 控件的属性值之间交换数据。|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|之间交换数据的成员变量和 HTML 页面上的复选框。|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|成员变量和 HTML 页面上的任何 HTML 元素属性之间交换数据。|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|成员变量和 HTML 页面上的单选按钮之间交换数据。|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|获取或设置 HTML 页上的列表框中的索引。|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|获取或设置 HTML 页上 （基于当前的索引） 的列表框项的显示文本。|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|获取或设置 HTML 页上 （基于当前的索引） 的列表框项的值。|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|销毁一个无模式对话框。|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|启用无模式对话框。|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|允许的对话框来筛选所创建的托管浏览器的剪贴板数据对象。|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|检索`IDispatch`接口上的 ActiveX 控件嵌入在 HTML 文档中。|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|检索指定 ActiveX 控件的请求的属性。|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|检索与当前文档关联的统一资源定位器 (URL)。|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|检索对当前加载的 HTML 文档的 IHTMLDocument2 接口。|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|包含的 web 浏览器控件时它被用作拖放目标以允许对话框提供一种替代方法，调用[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)。|
|[CDHtmlDialog::GetElement](#getelement)|获取 HTML 元素上的接口。|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|检索`innerHTML`HTML 元素的属性。|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|从 HTML 元素中检索请求的接口指针。|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|检索 HTML 元素的属性的值。|
|[CDHtmlDialog::GetElementText](#getelementtext)|检索`innerText`HTML 元素的属性。|
|[CDHtmlDialog::GetEvent](#getevent)|获取`IHTMLEventObj`指向当前事件对象的指针。|
|[CDHtmlDialog::GetExternal](#getexternal)|获取主机的`IDispatch`接口。|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|检索主机的 UI 功能。|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|检索其下存储用户首选项的注册表项。|
|[CDHtmlDialog::HideUI](#hideui)|隐藏主机的 UI。|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|指示是否主机的`IDispatch`接口是可安全执行脚本。|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|将指定的资源加载到 WebBrowser 控件。|
|[CDHtmlDialog::Navigate](#navigate)|导航到指定的 URL。|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|一个导航事件被激发之前由框架调用。|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|由框架调用以通知应用程序，当文档已到达 READYSTATE_COMPLETE 状态时。|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|文档窗口激活或停用时由框架调用。|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|框架窗口被激活或停用时由框架调用。|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|调用以响应 WM_INITDIALOG 消息。|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|导航事件完成后，由框架调用。|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|警告对象需要调整其边框空间的大小。|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|将 ActiveX 控件的属性设置为新值。|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|集`innerHTML`HTML 元素的属性。|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|设置 HTML 元素的属性。|
|[CDHtmlDialog::SetElementText](#setelementtext)|集`innerText`HTML 元素的属性。|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|设置主机的`IDispatch`接口。|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|设置主机的 UI 标志。|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|当即将显示上下文菜单时调用。|
|[CDHtmlDialog::ShowUI](#showui)|显示主机的 UI。|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|调用以处理菜单快捷键消息。|
|[CDHtmlDialog::TranslateUrl](#translateurl)|调用以修改要加载的 URL。|
|[CDHtmlDialog::UpdateUI](#updateui)|调用以通知主机命令状态已更改。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|指示是否使用 HTML 文档的标题为对话框标题。|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|要显示的资源 ID 的 HTML 资源。|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|指向一个 Web 浏览器应用程序的指针。|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|指向一个 HTML 文档的指针。|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|当前的 URL。|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|字符串版本的 HTML 资源 id。|

## <a name="remarks"></a>备注

`CDHtmlDialog` 可以加载资源是 HTML 中显示的 HTML 或 URL。

`CDHtmlDialog` 可以执行数据与 HTML 控件交换和处理来自 HTML 控件的事件，如按钮单击。

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

**标头：** afxdhtml.h

##  <a name="ddx_dhtml_helper_macros"></a>  DDX_DHtml 帮助器宏

DDX_DHtml 帮助器宏允许轻松访问常用的属性的 HTML 页上的控件。

### <a name="data-exchange-macros"></a>数据交换宏

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|设置或检索选定控件的 Value 属性。|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|设置或检索当前元素的开始和结束标记之间的文本。|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|设置或检索当前元素的开始和结束标记之间的 HTML。|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|设置或检索的目标 URL 或定位点。|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|设置或检索的目标窗口或框架。|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|设置或检索图像或文档中的视频剪辑的名称。|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|设置或检索关联的帧的 URL。|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|设置或检索关联的帧的 URL。|

##  <a name="canaccessexternal"></a>  CDHtmlDialog::CanAccessExternal

可重写的是作为调用访问检查，以查看是否已加载的页面上的脚本对象可以访问控制站点在外部调度。 检查以确保调度是用于编写脚本的安全，或者当前的区域允许不是可安全执行脚本的对象。

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="cdhtmldialog"></a>  CDHtmlDialog::CDHtmlDialog

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
以 null 结尾的字符串，表示对话框模板资源的名称。

*szHtmlResID*<br/>
以 null 结尾的字符串，表示的 HTML 资源的名称。

*pParentWnd*<br/>
指向父或所有者窗口对象的指针 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象属于的。 如果它为 NULL，对话框对象的父窗口设置为应用程序主窗口。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

*nHtmlResID*<br/>
包含的 HTML 资源的 ID 号。

### <a name="remarks"></a>备注

构造函数的第二种形式提供模板名称通过对话框资源的访问权限。 第三个构造函数的形式提供的资源模板的 ID 通过对话框资源的访问权限。 通常情况下，该 ID 开头**IDD_** 前缀。

##  <a name="_dtorcdhtmldialog"></a>  CDHtmlDialog:: ~ CDHtmlDialog

销毁 CDHtmlDialog 对象。

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>备注

[Cwnd:: Destroywindow](../../mfc/reference/cwnd-class.md#destroywindow)必须使用成员函数来销毁由创建无模式对话框[CDialog::Create](../../mfc/reference/cdialog-class.md#create)。

##  <a name="createcontrolsite"></a>  CDHtmlDialog::CreateControlSite

可重写用于创建控件站点实例以承载 WebBrowser 控件在对话框中。

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>参数

*pContainer*<br/>
一个指向[COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)对象

*ppSite*<br/>
指针到指向[COleControlSite](../../mfc/reference/colecontrolsite-class.md)。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

您可以重写此成员函数以返回您自己控件站点类的实例。

##  <a name="ddx_dhtml_axcontrol"></a>  CDHtmlDialog::DDX_DHtml_AxControl

成员变量和 HTML 页面上的 ActiveX 控件的属性值之间交换数据。

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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。

*szId*<br/>
ActiveX 控件的 HTML 源代码中的对象标记的 ID 参数的值。

*dispId*<br/>
进行交换数据的属性的调度 ID。

*szPropName*<br/>
属性的名称。

*var*<br/>
数据成员的类型变体[COleVariant](../../mfc/reference/colevariant-class.md)，或[CComVariant](../../atl/reference/ccomvariant-class.md)，保留交换并将 ActiveX 控件属性的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>  CDHtmlDialog::DDX_DHtml_CheckBox

之间交换数据的成员变量和 HTML 页面上的复选框。

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。

*szId*<br/>
为 HTML 控件的 ID 参数指定值。

*值*<br/>
正在交换值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>  CDHtmlDialog::DDX_DHtml_ElementText

成员变量和 HTML 页面上的任何 HTML 元素属性之间交换数据。

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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。

*szId*<br/>
为 HTML 控件的 ID 参数指定值。

*dispId*<br/>
想要交换数据的 HTML 元素的调度 ID。

*值*<br/>
正在交换值。

##  <a name="ddx_dhtml_radio"></a>  CDHtmlDialog::DDX_DHtml_Radio

成员变量和 HTML 页面上的单选按钮之间交换数据。

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。

*szId*<br/>
为 HTML 控件的 ID 参数指定值。

*值*<br/>
正在交换值。

##  <a name="ddx_dhtml_selectindex"></a>  CDHtmlDialog::DDX_DHtml_SelectIndex

获取或设置 HTML 页上的列表框中的索引。

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。

*szId*<br/>
为 HTML 控件的指定值`id`参数。

*值*<br/>
正在交换值。

##  <a name="ddx_dhtml_selectstring"></a>  CDHtmlDialog::DDX_DHtml_SelectString

获取或设置 HTML 页上 （基于当前的索引） 的列表框项的显示文本。

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。

*szId*<br/>
为 HTML 控件的 ID 参数指定值。

*值*<br/>
正在交换值。

##  <a name="ddx_dhtml_selectvalue"></a>  CDHtmlDialog::DDX_DHtml_SelectValue

获取或设置 HTML 页上 （基于当前的索引） 的列表框项的值。

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。

*szId*<br/>
为 HTML 控件的 ID 参数指定值。

*值*<br/>
正在交换值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>  CDHtmlDialog::DestroyModeless

分离一个无模式对话框`CDHtmlDialog`对象并销毁该对象。

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>  CDHtmlDialog::EnableModeless

启用无模式对话框。

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>参数

*fEnable*<br/>
请参阅*fEnable*中[IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) Windows SDK 中。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="filterdataobject"></a>  CDHtmlDialog::FilterDataObject

允许的对话框来筛选所创建的托管浏览器的剪贴板数据对象。

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>参数

*pDO*<br/>
请参阅*pDO*中[IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) Windows SDK 中。

*ppDORet*<br/>
请参阅*ppDORet*中`IDocHostUIHandler::FilterDataObject`Windows SDK 中。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="getcontroldispatch"></a>  CDHtmlDialog::GetControlDispatch

检索`IDispatch`上的 ActiveX 控件接口返回的 HTML 文档中嵌入[GetDHtmlDocument](#getdhtmldocument)。

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>参数

*szId*<br/>
ActiveX 控件的 HTML ID。

*ppdisp*<br/>
`IDispatch`控件界面如果网页中找到。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="getcontrolproperty"></a>  CDHtmlDialog::GetControlProperty

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
`IDispatch` ActiveX 控件的指针。

*dispId*<br/>
属性的调度 ID。

### <a name="return-value"></a>返回值

如果无法找到的控件或属性包含请求的属性或一个空变量的变量。

### <a name="remarks"></a>备注

重载的列出了从顶部的效率最低到最底部有效。

##  <a name="getcurrenturl"></a>  CDHtmlDialog::GetCurrentUrl

检索与当前文档关联的统一资源定位器 (URL)。

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>参数

*szUrl*<br/>
一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含要检索的 URL。

##  <a name="getdhtmldocument"></a>  CDHtmlDialog::GetDHtmlDocument

检索[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))当前加载的 HTML 文档上的接口。

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>参数

*\*\*pphtmlDoc*指向的 HTML 文档的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。 如果成功，则会返回 S_OK。

##  <a name="getdroptarget"></a>  CDHtmlDialog::GetDropTarget

包含的 web 浏览器控件时它被用作拖放目标以允许对话框提供一种替代方法，调用[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)。

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>参数

*pDropTarget*<br/>
请参阅*pDropTarget*中[IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) Windows SDK 中。

*ppDropTarget*<br/>
请参阅*ppDropTarget*中`IDocHostUIHandler::GetDropTarget`Windows SDK 中。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="getelement"></a>  CDHtmlDialog::GetElement

返回的接口上指定的 HTML 元素*szElementId*。

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
`IDispatch`指向请求的元素或元素集合。

*pbCollection*<br/>
一个布尔值，该值指示表示的对象是否*ppdisp*是单个元素的集合。

*pphtmlElement*<br/>
`IHTMLElement`指向所请求的元素。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果您需要处理在其中可能有多个具有指定 ID 的元素的条件，请使用第一个重载 最后一个参数可用于了解返回的接口指针是否为集合或单个项。 如果在集合上的接口指针，您可以查询`IHTMLElementCollection`，并使用其`item`属性来引用的元素的序号位置。

如果不存在具有相同 ID 的页中的多个元素，第二个重载将失败。

##  <a name="getelementhtml"></a>  CDHtmlDialog::GetElementHtml

检索`innerHTML`属性标识的 HTML 元素*szElementId*。

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

### <a name="return-value"></a>返回值

`innerHTML`属性标识的 HTML 元素*szElementId*或如果找不到元素，则为 NULL。

##  <a name="getelementinterface"></a>  CDHtmlDialog::GetElementInterface

从标识的 HTML 元素中检索请求的接口指针*szElementId*。

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
如果找到该元素将填入请求的接口指针的指针和查询的地址会成功。

*refiid*<br/>
接口 ID (IID) 所请求的接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>  CDHtmlDialog::GetElementProperty

检索通过标识的属性的值*dispId*标识的 HTML 元素从*szElementId*。

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

该属性或一个空的变量，如果无法找到属性或元素的值。

##  <a name="getelementtext"></a>  CDHtmlDialog::GetElementText

检索`innerText`属性标识的 HTML 元素*szElementId*。

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>参数

*szElementId*<br/>
HTML 元素的 ID。

### <a name="return-value"></a>返回值

`innerText`属性标识的 HTML 元素*szElementId*或如果无法找到属性或元素，则为 NULL。

##  <a name="getevent"></a>  CDHtmlDialog::GetEvent

返回`IHTMLEventObj`指向当前事件对象的指针。

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>参数

*ppEventObj*<br/>
将填充的指针的地址`IHTMLEventObj`接口指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

调用此函数应仅从 DHTML 事件处理程序内。

##  <a name="getexternal"></a>  CDHtmlDialog::GetExternal

获取主机的`IDispatch`接口。

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>参数

*ppDispatch*<br/>
请参阅*ppDispatch*中[IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) Windows SDK 中。

### <a name="return-value"></a>返回值

在失败时返回成功或 E_NOTIMPL，则为 S_OK。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="gethostinfo"></a>  CDHtmlDialog::GetHostInfo

检索主机的 UI 功能。

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>参数

*pInfo*<br/>
请参阅*pInfo*中[IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) Windows SDK 中。

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="getoptionkeypath"></a>  CDHtmlDialog::GetOptionKeyPath

检索其下存储用户首选项的注册表项。

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>参数

*pchKey*<br/>
请参阅*pchKey*中[IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) Windows SDK 中。

*dw*<br/>
请参阅*dw*中`IDocHostUIHandler::GetOptionKeyPath`Windows SDK 中。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="hideui"></a>  CDHtmlDialog::HideUI

隐藏主机的 UI。

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="isexternaldispatchsafe"></a>  CDHtmlDialog::IsExternalDispatchSafe

指示是否主机的`IDispatch`接口是可安全执行脚本。

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>返回值

返回 FALSE。

##  <a name="loadfromresource"></a>  CDHtmlDialog::LoadFromResource

将指定的资源加载到 WebBrowser 控件在 DHTML 对话框。

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>参数

*lpszResource*<br/>
指向包含要加载的资源名称的字符串的指针。

*nRes*<br/>
若要加载的资源 ID。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

##  <a name="m_busehtmltitle"></a>  CDHtmlDialog::m_bUseHtmlTitle

指示是否使用 HTML 文档的标题为对话框标题。

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>备注

如果**m**_ **bUseHtmlTitle**为 TRUE 时，对话框标题设置为等于 HTML 文档的标题; 否则，使用对话框资源中的标题。

##  <a name="m_nhtmlresid"></a>  CDHtmlDialog::m_nHtmlResID

要显示的资源 ID 的 HTML 资源。

```
UINT m_nHtmlResID;
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>  CDHtmlDialog::m_pBrowserApp

指向一个 Web 浏览器应用程序的指针。

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

##  <a name="m_sphtmldoc"></a>  CDHtmlDialog::m_spHtmlDoc

指向一个 HTML 文档的指针。

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

##  <a name="m_strcurrenturl"></a>  CDHtmlDialog::m_strCurrentUrl

当前的 URL。

```
CString m_strCurrentUrl;
```

##  <a name="m_szhtmlresid"></a>  CDHtmlDialog::m_szHtmlResID

字符串版本的 HTML 资源 id。

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>  CDHtmlDialog::Navigate

导航到由指定的 URL 标识的资源*lpszURL*。

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
指向包含要设定为目标的 URL 的字符串的指针。

*dwFlags*<br/>
用于指定是否要将资源添加到历史记录列表、 是否缓存读取或写入从缓存中，以及是否要在新窗口中显示该资源的变量的标志。 可以将变量定义的值的组合[BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\))枚举。

*lpszTargetFrameName*<br/>
指向包含要在其中显示资源框架的名称的字符串的指针。

*lpszHeaders*<br/>
指向一个值，指定要向服务器发送的 HTTP 标头的指针。 这些标头添加到默认的 Internet Explorer 标头中。 标头可以指定此类信息作为服务器传递到服务器或状态代码的数据类型的所需的操作。 如果 URL 不是 HTTP URL，则忽略此参数。

*lpvPostData*<br/>
指向要使用 HTTP POST 事务发送的数据的指针。 例如，POST 事务用于发送 HTML 窗体收集数据。 如果此参数未指定发送的所有数据，`Navigate`发出 HTTP GET 的事务。 如果 URL 不是 HTTP URL，则忽略此参数。

*dwPostDataLen*<br/>
若要使用 HTTP POST 事务发送的数据。 例如，POST 事务用于发送 HTML 窗体收集数据。 如果此参数未指定发送的所有数据，`Navigate`发出 HTTP GET 的事务。 如果 URL 不是 HTTP URL，则忽略此参数。

##  <a name="onbeforenavigate"></a>  CDHtmlDialog::OnBeforeNavigate

由框架调用以导致发生导航之前引发该事件。

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

##  <a name="ondocumentcomplete"></a>  CDHtmlDialog::OnDocumentComplete

由框架调用以通知应用程序，当文档已获得 READYSTATE_COMPLETE 状态时。

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
指向 `IDispatch` 对象的指针。

*szUrl*<br/>
指向包含导航到 URL 的字符串的指针。

##  <a name="ondocwindowactivate"></a>  CDHtmlDialog::OnDocWindowActivate

文档窗口激活或停用时由框架调用。

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>参数

*fActivate*<br/>
请参阅*fActivate*中[IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) Windows SDK 中。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="onframewindowactivate"></a>  CDHtmlDialog::OnFrameWindowActivate

框架窗口被激活或停用时由框架调用。

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>参数

*fActivate*<br/>
请参阅*fActivate*中[IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) Windows SDK 中。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="oninitdialog"></a>  CDHtmlDialog::OnInitDialog

调用以响应 WM_INITDIALOG 消息。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

默认实现，则返回 TRUE。

### <a name="remarks"></a>备注

此消息发送到期间对话框的`Create`， `CreateIndirect`，或`DoModal`调用，这将显示对话框之前立即发生。

如果您需要执行特殊处理对话框的初始化时，重写此成员函数。 在重写的版本中，首先调用基类`OnInitDialog`但忽略其返回值。 通常情况下将重写的成员函数返回 TRUE。

Windows 调用`OnInitDialog`函数通过所有的 Microsoft 基础类库对话框常见的标准全局对话框过程，而不是通过消息映射，因此不需要消息映射条目为此成员函数。

##  <a name="onnavigatecomplete"></a>  CDHtmlDialog::OnNavigateComplete

导航到指定的 URL 完成后，由框架调用。

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
指向 `IDispatch` 对象的指针。

*szUrl*<br/>
指向包含导航到 URL 的字符串的指针。

##  <a name="resizeborder"></a>  CDHtmlDialog::ResizeBorder

警告对象需要调整其边框空间的大小。

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>参数

*prcBorder*<br/>
请参阅*prcBorder*中[IDocHostUIHandler::ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) Windows SDK 中。

*pUIWindow*<br/>
请参阅*pUIWindow*中`IDocHostUIHandler::ResizeBorder`Windows SDK 中。

*fFrameWindow*<br/>
请参阅*fFrameWindow*中`IDocHostUIHandler::ResizeBorder`Windows SDK 中。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

##  <a name="setcontrolproperty"></a>  CDHtmlDialog::SetControlProperty

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
指向包含新的属性值的变量的指针。

*pdispControl*<br/>
向 ActiveX 控件的指针`IDispatch`接口。

*szPropName*<br/>
包含要设置的属性名称的字符串。

##  <a name="setelementhtml"></a>  CDHtmlDialog::SetElementHtml

集`innerHTML`HTML 元素的属性。

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
`IUnknown` HTML 元素的指针。

##  <a name="setelementproperty"></a>  CDHtmlDialog::SetElementProperty

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

##  <a name="setelementtext"></a>  CDHtmlDialog::SetElementText

集`innerText`HTML 元素的属性。

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
`IUnknown` HTML 元素的指针。

##  <a name="setexternaldispatch"></a>  CDHtmlDialog::SetExternalDispatch

设置主机的`IDispatch`接口。

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>参数

*pdispExternal*<br/>
新`IDispatch`接口。

##  <a name="sethostflags"></a>  CDHtmlDialog::SetHostFlags

设置宿主 UI 标志。

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
有关可能的值，请参阅[DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) Windows SDK 中。

##  <a name="showcontextmenu"></a>  CDHtmlDialog::ShowContextMenu

当即将显示上下文菜单时调用。

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>参数

*dwID*<br/>
请参阅*dwID*中[IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) Windows SDK 中。

*ppt*<br/>
请参阅*ppt*中`IDocHostUIHandler::ShowContextMenu`Windows SDK 中。

*pcmdtReserved*<br/>
请参阅*pcmdtReserved*中`IDocHostUIHandler::ShowContextMenu`Windows SDK 中。

*pdispReserved*<br/>
请参阅*pdispReserved*中`IDocHostUIHandler::ShowContextMenu`Windows SDK 中。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="showui"></a>  CDHtmlDialog::ShowUI

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
请参阅*dwID*中[IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) Windows SDK 中。

*pActiveObject*<br/>
请参阅*d pActiveObject*中`IDocHostUIHandler::ShowUI`Windows SDK 中。

*pCommandTarget*<br/>
请参阅*pCommandTarget*中`IDocHostUIHandler::ShowUI`Windows SDK 中。

*pFrame*<br/>
请参阅*pFrame*中`IDocHostUIHandler::ShowUI`Windows SDK 中。

*pDoc*<br/>
请参阅*pDoc*中`IDocHostUIHandler::ShowUI`Windows SDK 中。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="translateaccelerator"></a>  CDHtmlDialog::TranslateAccelerator

调用以处理菜单快捷键消息。

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>参数

*lpMsg*<br/>
请参阅*lpMsg*中[IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) Windows SDK 中。

*pguidCmdGroup*<br/>
请参阅*pguidCmdGroup*中`IDocHostUIHandler::TranslateAccelerator`Windows SDK 中。

*nCmdID*<br/>
请参阅*nCmdID*中`IDocHostUIHandler::TranslateAccelerator`Windows SDK 中。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))，如 Windows SDK 中所述。

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
请参阅*dwTranslate*中[IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) Windows SDK 中。

*pchURLIn*<br/>
请参阅*pchURLIn*中`IDocHostUIHandler::TranslateUrl`Windows SDK 中。

*ppchURLOut*<br/>
请参阅*ppchURLOut*中`IDocHostUIHandler::TranslateUrl`Windows SDK 中。

### <a name="return-value"></a>返回值

返回 S_FALSE。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))，如 Windows SDK 中所述。

##  <a name="updateui"></a>  CDHtmlDialog::UpdateUI

调用以通知主机命令状态已更改。

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

此成员函数是 CDHtmlDialog 的实现[IDocHostUIHandler::UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))，如 Windows SDK 中所述。

## <a name="see-also"></a>请参阅

[MFC 示例 DHtmlExplore](../../visual-cpp-samples.md)<br/>
[DDX_DHtml 帮助器宏](#ddx_dhtml_helper_macros)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
