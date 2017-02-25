---
title: "CDHtmlDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDHtmlDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDHtmlDialog class"
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDHtmlDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用创建使用HTML而不是对话框资源实现自己的用户界面的对话框。  
  
## 语法  
  
```  
class CDHtmlDialog : public CDialog, public CDHtmlEventSink  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDHtmlDialog::CDHtmlDialog](../Topic/CDHtmlDialog::CDHtmlDialog.md)|构造CDHtmlDialog对象。|  
|[CDHtmlDialog::~CDHtmlDialog](../Topic/CDHtmlDialog::~CDHtmlDialog.md)|销毁一个CDHtmlDialog对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDHtmlDialog::CanAccessExternal](../Topic/CDHtmlDialog::CanAccessExternal.md)|可重写是否被作为的访问检查脚本在加载页的对象访问控制站点的外部计划。  确定计划的检查是或脚本撰写安全或当前区域可以为脚本是不安全的对象。|  
|[CDHtmlDialog::CreateControlSite](../Topic/CDHtmlDialog::CreateControlSite.md)|用于可重写控件创建站点实例承载在对话框的浏览器控件。|  
|[CDHtmlDialog::DDX\_DHtml\_AxControl](../Topic/CDHtmlDialog::DDX_DHtml_AxControl.md)|在变量的成员和一个ActiveX控件的属性值之间交换数据在HTML页中。|  
|[CDHtmlDialog::DDX\_DHtml\_CheckBox](../Topic/CDHtmlDialog::DDX_DHtml_CheckBox.md)|在变量的成员和复选框之间交换数据。HTML页。|  
|[CDHtmlDialog::DDX\_DHtml\_ElementText](../Topic/CDHtmlDialog::DDX_DHtml_ElementText.md)|在变量的成员和任何HTML元素的特性之间交换数据在HTML页。|  
|[CDHtmlDialog::DDX\_DHtml\_Radio](../Topic/CDHtmlDialog::DDX_DHtml_Radio.md)|在变量的成员和一个单选按钮之间交换数据在HTML页。|  
|[CDHtmlDialog::DDX\_DHtml\_SelectIndex](../Topic/CDHtmlDialog::DDX_DHtml_SelectIndex.md)|获取或设置一个列表框的索引在HTML页中。|  
|[CDHtmlDialog::DDX\_DHtml\_SelectString](../Topic/CDHtmlDialog::DDX_DHtml_SelectString.md)|获取或设置列表框项的显示文本\(基于当前索引\)在HTML页。|  
|[CDHtmlDialog::DDX\_DHtml\_SelectValue](../Topic/CDHtmlDialog::DDX_DHtml_SelectValue.md)|获取或设置列表框项的值\(基于当前索引\)在HTML页。|  
|[CDHtmlDialog::DestroyModeless](../Topic/CDHtmlDialog::DestroyModeless.md)|销毁无模式对话框。|  
|[CDHtmlDialog::EnableModeless](../Topic/CDHtmlDialog::EnableModeless.md)|启用无模式对话框。|  
|[CDHtmlDialog::FilterDataObject](../Topic/CDHtmlDialog::FilterDataObject.md)|允许对话框筛选剪贴板承载的浏览器创建的数据对象。|  
|[CDHtmlDialog::GetControlDispatch](../Topic/CDHtmlDialog::GetControlDispatch.md)|检索在HTML中嵌入的ActiveX控件的 `IDispatch` 接口文档。|  
|[CDHtmlDialog::GetControlProperty](../Topic/CDHtmlDialog::GetControlProperty.md)|检索指定的ActiveX控件的请求的属性。|  
|[CDHtmlDialog::GetCurrentUrl](../Topic/CDHtmlDialog::GetCurrentUrl.md)|检索统一资源定位器\(url\) \(URL\)与当前文件。|  
|[CDHtmlDialog::GetDHtmlDocument](../Topic/CDHtmlDialog::GetDHtmlDocument.md)|检索当前所加载的HTML的IHTMLDocument2接口文档。|  
|[CDHtmlDialog::GetDropTarget](../Topic/CDHtmlDialog::GetDropTarget.md)|调用由包含的浏览器控件，当它用于，放置目标允许对话框提供替代 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)。|  
|[CDHtmlDialog::GetElement](../Topic/CDHtmlDialog::GetElement.md)|获取在HTML元素的接口。|  
|[CDHtmlDialog::GetElementHtml](../Topic/CDHtmlDialog::GetElementHtml.md)|检索HTML元素的 **innerHTML** 属性。|  
|[CDHtmlDialog::GetElementInterface](../Topic/CDHtmlDialog::GetElementInterface.md)|从HTML元素检索请求的接口指针。|  
|[CDHtmlDialog::GetElementProperty](../Topic/CDHtmlDialog::GetElementProperty.md)|检索HTML元素的特性的值。|  
|[CDHtmlDialog::GetElementText](../Topic/CDHtmlDialog::GetElementText.md)|检索HTML元素的 **innerText** 属性。|  
|[CDHtmlDialog::GetEvent](../Topic/CDHtmlDialog::GetEvent.md)|具有 **IHTMLEventObj** 指针时事对象。|  
|[CDHtmlDialog::GetExternal](../Topic/CDHtmlDialog::GetExternal.md)|获取主机的 `IDispatch` 接口。|  
|[CDHtmlDialog::GetHostInfo](../Topic/CDHtmlDialog::GetHostInfo.md)|检索宿主的UI功能。|  
|[CDHtmlDialog::GetOptionKeyPath](../Topic/CDHtmlDialog::GetOptionKeyPath.md)|检索下用户首选项存储的注册表项。|  
|[CDHtmlDialog::HideUI](../Topic/CDHtmlDialog::HideUI.md)|隐藏宿主的UI。|  
|[CDHtmlDialog::IsExternalDispatchSafe](../Topic/CDHtmlDialog::IsExternalDispatchSafe.md)|指示主机的 `IDispatch` 接口是否为脚本是安全的。|  
|[CDHtmlDialog::LoadFromResource](../Topic/CDHtmlDialog::LoadFromResource.md)|加载指定的资源到浏览器控件。|  
|[CDHtmlDialog::Navigate](../Topic/CDHtmlDialog::Navigate.md)|定位到指定的 URL。|  
|[CDHtmlDialog::OnBeforeNavigate](../Topic/CDHtmlDialog::OnBeforeNavigate.md)|调用由框架在导航事件之前引发。|  
|[CDHtmlDialog::OnDocumentComplete](../Topic/CDHtmlDialog::OnDocumentComplete.md)|调用由框架通知应用程序，当文档已到达 `READYSTATE_COMPLETE` 状态。|  
|[CDHtmlDialog::OnDocWindowActivate](../Topic/CDHtmlDialog::OnDocWindowActivate.md)|调用由结构，当激活文档窗口或停用。|  
|[CDHtmlDialog::OnFrameWindowActivate](../Topic/CDHtmlDialog::OnFrameWindowActivate.md)|调用由框架激活时，框架窗口或停用。|  
|[CDHtmlDialog::OnInitDialog](../Topic/CDHtmlDialog::OnInitDialog.md)|调用以响应 **WM\_INITDIALOG** 消息。|  
|[CDHtmlDialog::OnNavigateComplete](../Topic/CDHtmlDialog::OnNavigateComplete.md)|调用由框架在导航操作完成之后。|  
|[CDHtmlDialog::ResizeBorder](../Topic/CDHtmlDialog::ResizeBorder.md)|警报它需要调整其边框空间中的对象。|  
|[CDHtmlDialog::SetControlProperty](../Topic/CDHtmlDialog::SetControlProperty.md)|设置ActiveX控件的属性设置为新值。|  
|[CDHtmlDialog::SetElementHtml](../Topic/CDHtmlDialog::SetElementHtml.md)|设置HTML元素的 **innerHTML** 属性。|  
|[CDHtmlDialog::SetElementProperty](../Topic/CDHtmlDialog::SetElementProperty.md)|设置HTML元素的属性。|  
|[CDHtmlDialog::SetElementText](../Topic/CDHtmlDialog::SetElementText.md)|设置HTML元素的 **innerText** 属性。|  
|[CDHtmlDialog::SetExternalDispatch](../Topic/CDHtmlDialog::SetExternalDispatch.md)|将宿主的 `IDispatch` 接口。|  
|[CDHtmlDialog::SetHostFlags](../Topic/CDHtmlDialog::SetHostFlags.md)|将宿主的UI标志。|  
|[CDHtmlDialog::ShowContextMenu](../Topic/CDHtmlDialog::ShowContextMenu.md)|调用，在上下文菜单中显示。|  
|[CDHtmlDialog::ShowUI](../Topic/CDHtmlDialog::ShowUI.md)|公开宿主的UI。|  
|[CDHtmlDialog::TranslateAccelerator](../Topic/CDHtmlDialog::TranslateAccelerator.md)|调用处理菜单快捷键按键消息。|  
|[CDHtmlDialog::TranslateUrl](../Topic/CDHtmlDialog::TranslateUrl.md)|调用以修改要加载的URL。|  
|[CDHtmlDialog::UpdateUI](../Topic/CDHtmlDialog::UpdateUI.md)|调用以通知宿主顺序状态发生了变化。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDHtmlDialog::m\_bUseHtmlTitle](../Topic/CDHtmlDialog::m_bUseHtmlTitle.md)|指示是否使用HTML文件的标题为"对话框说明。|  
|[CDHtmlDialog::m\_nHtmlResID](../Topic/CDHtmlDialog::m_nHtmlResID.md)|HTML资源资源ID要显示的。|  
|[CDHtmlDialog::m\_pBrowserApp](../Topic/CDHtmlDialog::m_pBrowserApp.md)|对浏览器应用程序的指针。|  
|[CDHtmlDialog::m\_spHtmlDoc](../Topic/CDHtmlDialog::m_spHtmlDoc.md)|对HTML的指针文档。|  
|[CDHtmlDialog::m\_strCurrentUrl](../Topic/CDHtmlDialog::m_strCurrentUrl.md)|当前URL。|  
|[CDHtmlDialog::m\_szHtmlResID](../Topic/CDHtmlDialog::m_szHtmlResID.md)|HTML资源ID.的字符串版本|  
  
## 备注  
 **CDHtmlDialog** 可以填充HTML资源或URL中显示的HTML。  
  
 `CDHtmlDialog` 还可以执行数据交换与HTML控件和处理事件来自HTML控件，如按钮单击。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CDHtmlDialog`  
  
## 要求  
 **Header:** afxdhtml.h  
  
## 请参阅  
 [MFC示例DHtmlExplore](../../top/visual-cpp-samples.md)   
 [DDX\_DHtml Helper Macros](../../mfc/reference/ddx-dhtml-helper-macros.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)