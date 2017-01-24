---
title: "CHtmlView 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHtmlView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "浏览器，对...的 MFC 支持"
  - "CHtmlView 类"
  - "WebBrowser 控件"
  - "WebBrowser 控件，MFC 支持"
ms.assetid: 904976af-73de-4aba-84ac-cfae8e2be09a
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHtmlView 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 MFC 文档\/视图体系结构上下文中的 Web 浏览器控件功能。  
  
## 语法  
  
```  
class CHtmlView : public CFormView  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CHtmlView::Create](../Topic/CHtmlView::Create.md)|创建 WebBrowser 控件。|  
|[CHtmlView::CreateControlSite](../Topic/CHtmlView::CreateControlSite.md)|可重写，用于创建控件站点实例以承载窗体上的控件。|  
|[CHtmlView::ExecFormsCommand](../Topic/CHtmlView::ExecFormsCommand.md)|使用 `IOleCommandTarget::Exec` 方法执行指定的命令。|  
|[CHtmlView::ExecWB](../Topic/CHtmlView::ExecWB.md)|执行命令。|  
|[CHtmlView::GetAddressBar](../Topic/CHtmlView::GetAddressBar.md)|确定 Internet Explorer 对象的地址栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::GetApplication](../Topic/CHtmlView::GetApplication.md)|检索一个应用程序对象，该对象表示包含 Internet Explorer 应用程序的当前实例的应用程序。|  
|[CHtmlView::GetBusy](../Topic/CHtmlView::GetBusy.md)|检索一个值，该值指示下载或其他活动是否仍在进行中。|  
|[CHtmlView::GetContainer](../Topic/CHtmlView::GetContainer.md)|检索 WebBrowser 控件的容器。|  
|[CHtmlView::GetFullName](../Topic/CHtmlView::GetFullName.md)|检索 web 浏览器中显示的资源的完整名称，包括路径。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::GetFullScreen](../Topic/CHtmlView::GetFullScreen.md)|指示 WebBrowser 控件是在全屏模式下还是在正常窗口模式下运行。|  
|[CHtmlView::GetHeight](../Topic/CHtmlView::GetHeight.md)|检索 Internet Explorer 主窗口的高度。|  
|[CHtmlView::GetHtmlDocument](../Topic/CHtmlView::GetHtmlDocument.md)|检索活动的 HTML 文档。|  
|[CHtmlView::GetLeft](../Topic/CHtmlView::GetLeft.md)|检索 Internet Explorer 主窗口左边缘的屏幕坐标。|  
|[CHtmlView::GetLocationName](../Topic/CHtmlView::GetLocationName.md)|检索 WebBrowser 当前正在显示的资源的名称。|  
|[CHtmlView::GetLocationURL](../Topic/CHtmlView::GetLocationURL.md)|检索 WebBrowser 当前正在显示的资源的 URL。|  
|[CHtmlView::GetMenuBar](../Topic/CHtmlView::GetMenuBar.md)|检索一个值，该值确定菜单栏是否可见。|  
|[CHtmlView::GetOffline](../Topic/CHtmlView::GetOffline.md)|检索一个值，该值确定控件是否处于脱机状态。|  
|[CHtmlView::GetParentBrowser](../Topic/CHtmlView::GetParentBrowser.md)|检索指向 `IDispatch` 接口的指针。 有关更多信息，请参见[Implementing the IDispatch Interface](http://msdn.microsoft.com/zh-cn/0e171f7f-0022-4e9b-ac8e-98192828e945)。|  
|[CHtmlView::GetProperty](../Topic/CHtmlView::GetProperty.md)|检索与给定对象关联的属性的当前值。|  
|[CHtmlView::GetReadyState](../Topic/CHtmlView::GetReadyState.md)|检索 web 浏览器对象的就绪状态。|  
|[CHtmlView::GetRegisterAsBrowser](../Topic/CHtmlView::GetRegisterAsBrowser.md)|指示是否将 WebBrowser 控件注册为目标名称解析的顶级浏览器。|  
|[CHtmlView::GetRegisterAsDropTarget](../Topic/CHtmlView::GetRegisterAsDropTarget.md)|指示是否将 WebBrowser 控件注册为导航的放置目标。|  
|[CHtmlView::GetSilent](../Topic/CHtmlView::GetSilent.md)|指示是否可以显示任何对话框。|  
|[CHtmlView::GetSource](../Topic/CHtmlView::GetSource.md)|网页的 HTML 源代码。|  
|[CHtmlView::GetStatusBar](../Topic/CHtmlView::GetStatusBar.md)|指示 Internet Explorer 的状态栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::GetTheaterMode](../Topic/CHtmlView::GetTheaterMode.md)|指示 WebBrowser 控件是否处于影院模式。|  
|[CHtmlView::GetToolBar](../Topic/CHtmlView::GetToolBar.md)|检索一个值，该值确定工具栏是否可见。|  
|[CHtmlView::GetTop](../Topic/CHtmlView::GetTop.md)|检索 Internet Explorer 主窗口顶部边缘的屏幕坐标。|  
|[CHtmlView::GetTopLevelContainer](../Topic/CHtmlView::GetTopLevelContainer.md)|检索一个值，该值指示当前对象是否为 WebBrowser 控件的顶级容器。|  
|[CHtmlView::GetType](../Topic/CHtmlView::GetType.md)|检索文档对象的类型名称。|  
|[CHtmlView::GetVisible](../Topic/CHtmlView::GetVisible.md)|检索一个值，该值指示对象是可见还是隐藏。|  
|[CHtmlView::GetWidth](../Topic/CHtmlView::GetWidth.md)|检索 Internet Explorer 主窗口的宽度。|  
|[CHtmlView::GoBack](../Topic/CHtmlView::GoBack.md)|导航至历史记录列表中的上一项。|  
|[CHtmlView::GoForward](../Topic/CHtmlView::GoForward.md)|导航至历史记录列表中的下一项。|  
|[CHtmlView::GoHome](../Topic/CHtmlView::GoHome.md)|导航至当前主页或起始页。|  
|[CHtmlView::GoSearch](../Topic/CHtmlView::GoSearch.md)|导航至当前搜索页。|  
|[CHtmlView::LoadFromResource](../Topic/CHtmlView::LoadFromResource.md)|加载 WebBrowser 控件中的资源。|  
|[CHtmlView::Navigate](../Topic/CHtmlView::Navigate.md)|导航至由 URL 标识的资源。|  
|[CHtmlView::Navigate2](../Topic/CHtmlView::Navigate2.md)|导航至由 URL 标识的资源或由完整路径标识的文件。|  
|[CHtmlView::OnBeforeNavigate2](../Topic/CHtmlView::OnBeforeNavigate2.md)|在给定 WebBrowser 中发生导航之前调用（在窗口或框架集元素上）|  
|[CHtmlView::OnCommandStateChange](../Topic/CHtmlView::OnCommandStateChange.md)|调用以通知应用程序 Web 浏览器命令的启用状态已更改。|  
|[CHtmlView::OnDocumentComplete](../Topic/CHtmlView::OnDocumentComplete.md)|调用以通知的应用程序文档已到达 `READYSTATE_COMPLETE` 状态。|  
|[CHtmlView::OnDocWindowActivate](../Topic/CHtmlView::OnDocWindowActivate.md)|从 [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281) 的 Internet Explorer 或 MSHTML 实现调用，该操作将在激活或停用容器文件窗口时通知活动的就地对象。|  
|[CHtmlView::OnDownloadBegin](../Topic/CHtmlView::OnDownloadBegin.md)|调用以通知应用程序将开始导航操作|  
|[CHtmlView::OnDownloadComplete](../Topic/CHtmlView::OnDownloadComplete.md)|在导航操作完成、暂停或失败时调用。|  
|[CHtmlView::OnEnableModeless](../Topic/CHtmlView::OnEnableModeless.md)|调用以在容器创建或销毁模式对话框时启用或禁用无模式对话框。|  
|[CHtmlView::OnFilterDataObject](../Topic/CHtmlView::OnFilterDataObject.md)|由 Internet Explorer 或 MSHTML 对主机调用，以允许主机替换 Internet Explorer 或 MSHTML 的数据对象。|  
|[CHtmlView::OnFrameWindowActivate](../Topic/CHtmlView::OnFrameWindowActivate.md)|从 [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) 调用以在容器的顶级框架窗口被激活或停用时通知对象。|  
|[CHtmlView::OnFullScreen](../Topic/CHtmlView::OnFullScreen.md)|当 FullScreen 属性已更改时调用。|  
|[CHtmlView::OnGetDropTarget](../Topic/CHtmlView::OnGetDropTarget.md)|当用作放置目标时由 Internet Explorer 或 MSHTML 调用以允许主机提供替代的 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)。|  
|[CHtmlView::OnGetExternal](../Topic/CHtmlView::OnGetExternal.md)|由 Internet Explorer 或 MSHTML 调用以获取主机的 `IDispatch` 接口。|  
|[CHtmlView::OnGetHostInfo](../Topic/CHtmlView::OnGetHostInfo.md)|检索 Internet Explorer 或 MSHTML 主机的用户界面功能。|  
|[CHtmlView::OnGetOptionKeyPath](../Topic/CHtmlView::OnGetOptionKeyPath.md)|返回 Internet Explorer 或 MSHTML 在其下存储用户首选项的注册表项。|  
|[CHtmlView::OnHideUI](../Topic/CHtmlView::OnHideUI.md)|当 Internet Explorer 或 MSHTML 删除其菜单和工具栏时调用。|  
|[CHtmlView::OnMenuBar](../Topic/CHtmlView::OnMenuBar.md)|当 MenuBar 属性已更改时调用。|  
|[CHtmlView::OnNavigateComplete2](../Topic/CHtmlView::OnNavigateComplete2.md)|完成到超链接的导航后调用（在窗口或框架集元素上）。|  
|[CHtmlView::OnNavigateError](../Topic/CHtmlView::OnNavigateError.md)|当导航到超链接失败时由框架调用。|  
|[CHtmlView::OnNewWindow2](../Topic/CHtmlView::OnNewWindow2.md)|当要创建新窗口以显示资源时调用。|  
|[CHtmlView::OnProgressChange](../Topic/CHtmlView::OnProgressChange.md)|调用以通知应用程序下载操作的进度已更新。|  
|[CHtmlView::OnPropertyChange](../Topic/CHtmlView::OnPropertyChange.md)|调用以通知应用程序 [PutProperty](../Topic/CHtmlView::PutProperty.md) 方法已更改一个属性的值。|  
|[CHtmlView::OnQuit](../Topic/CHtmlView::OnQuit.md)|调用以通知应用程序 Internet Explorer 应用程序已准备退出。 （仅适用于 Internet Explorer）|  
|[CHtmlView::OnResizeBorder](../Topic/CHtmlView::OnResizeBorder.md)|从[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053) 的 Internet Explorer 或 MSHTML 实现调用，该操作警告对象需要重新调整其边框空间的大小。|  
|[CHtmlView::OnShowContextMenu](../Topic/CHtmlView::OnShowContextMenu.md)|当 Internet Explorer 或 MSHTML 将要显示其上下文菜单时，从其调用。|  
|[CHtmlView::OnShowUI](../Topic/CHtmlView::OnShowUI.md)|在 Internet Explorer 或 MSHTML 显示其菜单和工具栏之前调用。|  
|[CHtmlView::OnStatusBar](../Topic/CHtmlView::OnStatusBar.md)|当 StatusBar 属性已更改时调用。|  
|[CHtmlView::OnStatusTextChange](../Topic/CHtmlView::OnStatusTextChange.md)|调用以通知应用程序与 WebBrowser 控件相关联的状态栏的文本已更改。|  
|[CHtmlView::OnTheaterMode](../Topic/CHtmlView::OnTheaterMode.md)|当 TheaterMode 属性已更改时调用。|  
|[CHtmlView::OnTitleChange](../Topic/CHtmlView::OnTitleChange.md)|调用以通知应用程序 WebBrowser 控件中的文档的标题是否变为可用或是否更改。|  
|[CHtmlView::OnToolBar](../Topic/CHtmlView::OnToolBar.md)|当 ToolBar 属性已更改时调用。|  
|[CHtmlView::OnTranslateAccelerator](../Topic/CHtmlView::OnTranslateAccelerator.md)|当调用 [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) 或 [IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) 以处理来自容器消息队列的菜单快捷键消息时由 Internet Explorer 或 MSHTML 调用。|  
|[CHtmlView::OnTranslateUrl](../Topic/CHtmlView::OnTranslateUrl.md)|由 Internet Explorer 或 MSHTML 调用以允许主机有机会修改要加载的 URL。|  
|[CHtmlView::OnUpdateUI](../Topic/CHtmlView::OnUpdateUI.md)|通知主机命令状态已更改。|  
|[CHtmlView::OnVisible](../Topic/CHtmlView::OnVisible.md)|当应该显示\/隐藏 WebBrowser 控件的窗口时调用。|  
|[CHtmlView::PutProperty](../Topic/CHtmlView::PutProperty.md)|检索与给定对象关联的属性的值。|  
|[CHtmlView::QueryFormsCommand](../Topic/CHtmlView::QueryFormsCommand.md)|查询由用户界面事件生成的一个或多个命令的状态。|  
|[CHtmlView::QueryStatusWB](../Topic/CHtmlView::QueryStatusWB.md)|查询正在由 WebBrowser 控件进行处理的命令的状态。|  
|[CHtmlView::Refresh](../Topic/CHtmlView::Refresh.md)|重新加载当前文件。|  
|[CHtmlView::Refresh2](../Topic/CHtmlView::Refresh2.md)|重新加载当前文件并选择性地阻止 `pragma:nocache` 标头被发送。|  
|[CHtmlView::SetAddressBar](../Topic/CHtmlView::SetAddressBar.md)|显示 或隐藏 Internet Explorer 对象的地址栏。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetFullScreen](../Topic/CHtmlView::SetFullScreen.md)|设置一个值，用于确定 WebBrowser 控件是在全屏模式下还是在正常窗口模式下运行。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetHeight](../Topic/CHtmlView::SetHeight.md)|设置 Internet Explorer 主窗口的高度。|  
|[CHtmlView::SetLeft](../Topic/CHtmlView::SetLeft.md)|设置 Internet Explorer 主窗口的水平位置。|  
|[CHtmlView::SetMenuBar](../Topic/CHtmlView::SetMenuBar.md)|设置一个值，用以确定控件的菜单栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetOffline](../Topic/CHtmlView::SetOffline.md)|设置一个值，用以确定控件是否处于脱机状态。|  
|[CHtmlView::SetRegisterAsBrowser](../Topic/CHtmlView::SetRegisterAsBrowser.md)|设置一个值，指示是否将 WebBrowser 控件注册为目标名称解析的顶级浏览器。|  
|[CHtmlView::SetRegisterAsDropTarget](../Topic/CHtmlView::SetRegisterAsDropTarget.md)|设置一个值，指示是否将 WebBrowser 控件注册为导航的放置目标。|  
|[CHtmlView::SetSilent](../Topic/CHtmlView::SetSilent.md)|设置一个值，用以确定控件是否将显示对话框。|  
|[CHtmlView::SetStatusBar](../Topic/CHtmlView::SetStatusBar.md)|设置一个值，用以确定 Internet Explorer 的状态栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetTheaterMode](../Topic/CHtmlView::SetTheaterMode.md)|设置一个值，指示 WebBrowser 控件是否处于影院模式。|  
|[CHtmlView::SetToolBar](../Topic/CHtmlView::SetToolBar.md)|设置一个值，用以确定控件的工具栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetTop](../Topic/CHtmlView::SetTop.md)|设置 Internet Explorer 主窗口的垂直位置。|  
|[CHtmlView::SetVisible](../Topic/CHtmlView::SetVisible.md)|设置一个值，该值指示对象是可见还是隐藏。|  
|[CHtmlView::SetWidth](../Topic/CHtmlView::SetWidth.md)|设置 Internet Explorer 主窗口的宽度。|  
|[CHtmlView::Stop](../Topic/CHtmlView::Stop.md)|停止打开文件。|  
  
## 备注  
 WebBrowser 控件是一个窗口，其中用户可以浏览万维网上的站点以及本地文件系统中和网络上的文件夹。 WebBrowser 控件支持超级链接、统一资源定位器 \(URL\) 导航，并维护历史记录列表。  
  
## 在 MFC 应用程序中使用 CHtmlView 类  
 在标准 MFC 框架应用程序（基于 SDI 或 MDI）中，视图对象通常派生自专用的一组类。 这些类全部派生自 `CView`，它们提供 `CView` 所没有提供的专用功能。  
  
 将 `CHtmlView` 作为应用程序的视图类的基础可向视图提供 WebBrowser 控件。 这将有效地使应用程序成为一个 Web 浏览器。 创建一个 Web 浏览器样式的应用程序的首选方法是使用 MFC 应用程序向导，并将 `CHtmlView` 指定为视图类。 有关在 MFC 应用程序内实现和使用 WebBrowser 控件的详细信息，请参阅[创建 Web 浏览器样式的应用程序](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)。  
  
> [!NOTE]
>  WebBrowser ActiveX 控件（因此 `CHtmlView`）仅可用于在 Windows NT 4.0 版或更高版本（其中安装了 Internet Explorer 4.0 版或更高版本）下运行的程序。  
  
 `CHtmlView` 用于可访问 Web（和\/或 HTML 文档）的应用程序。 以下 `CHtmlView` 成员函数仅适用于 Internet Explorer 应用程序。 这些函数将在 WebBrowser 控件上成功运行，但不会有明显的效果。  
  
-   [GetAddressBar](../Topic/CHtmlView::GetAddressBar.md)  
  
-   [GetFullName](../Topic/CHtmlView::GetFullName.md)  
  
-   [GetStatusBar](../Topic/CHtmlView::GetStatusBar.md)  
  
-   [SetAddressBar](../Topic/CHtmlView::SetAddressBar.md)  
  
-   [SetFullScreen](../Topic/CHtmlView::SetFullScreen.md)  
  
-   [SetMenuBar](../Topic/CHtmlView::SetMenuBar.md)  
  
-   [SetStatusBar](../Topic/CHtmlView::SetStatusBar.md)  
  
-   [SetToolBar](../Topic/CHtmlView::SetToolBar.md)  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CHtmlView`  
  
## 要求  
 **标头：**afxhtml.h  
  
## 请参阅  
 [MFC 示例 MFCIE](../../top/visual-cpp-samples.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [IWebBrowser2](https://msdn.microsoft.com/en-us/library/aa752127.aspx)