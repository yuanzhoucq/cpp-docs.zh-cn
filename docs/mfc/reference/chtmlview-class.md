---
title: "由 CHtmlView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlView
dev_langs:
- C++
helpviewer_keywords:
- browsers, MFC support for
- CHtmlView class
- WebBrowser control
- WebBrowser control, MFC support
ms.assetid: 904976af-73de-4aba-84ac-cfae8e2be09a
caps.latest.revision: 24
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d9d96ab02a0c49a2ece12c933f5d550a46204a39
ms.lasthandoff: 02/24/2017

---
# <a name="chtmlview-class"></a>CHtmlView 类
提供 MFC 文档/视图体系结构上下文中的 Web 浏览器控件功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CHtmlView : public CFormView  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CHtmlView::Create](#create)|创建 WebBrowser 控件。|  
|[CHtmlView::CreateControlSite](#createcontrolsite)|可重写，用于创建控件站点实例以承载窗体上的控件。|  
|[CHtmlView::ExecFormsCommand](#execformscommand)|使用 `IOleCommandTarget::Exec` 方法执行指定的命令。|  
|[CHtmlView::ExecWB](#execwb)|执行命令。|  
|[CHtmlView::GetAddressBar](#getaddressbar)|确定 Internet Explorer 对象的地址栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::GetApplication](#getapplication)|检索一个应用程序对象，该对象表示包含 Internet Explorer 应用程序的当前实例的应用程序。|  
|[CHtmlView::GetBusy](#getbusy)|检索一个值，该值指示下载或其他活动是否仍在进行中。|  
|[CHtmlView::GetContainer](#getcontainer)|检索 WebBrowser 控件的容器。|  
|[CHtmlView::GetFullName](#getfullname)|检索 web 浏览器中显示的资源的完整名称，包括路径。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::GetFullScreen](#getfullscreen)|指示 WebBrowser 控件是在全屏模式下还是在正常窗口模式下运行。|  
|[CHtmlView::GetHeight](#getheight)|检索 Internet Explorer 主窗口的高度。|  
|[CHtmlView::GetHtmlDocument](#gethtmldocument)|检索活动的 HTML 文档。|  
|[CHtmlView::GetLeft](#getleft)|检索 Internet Explorer 主窗口左边缘的屏幕坐标。|  
|[CHtmlView::GetLocationName](#getlocationname)|检索 WebBrowser 当前正在显示的资源的名称。|  
|[CHtmlView::GetLocationURL](#getlocationurl)|检索 WebBrowser 当前正在显示的资源的 URL。|  
|[CHtmlView::GetMenuBar](#getmenubar)|检索一个值，该值确定菜单栏是否可见。|  
|[CHtmlView::GetOffline](#getoffline)|检索一个值，该值确定控件是否处于脱机状态。|  
|[CHtmlView::GetParentBrowser](#getparentbrowser)|检索指向 `IDispatch` 接口的指针。 有关详细信息，请参阅[实现 IDispatch 接口](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。|  
|[CHtmlView::GetProperty](#getproperty)|检索与给定对象关联的属性的当前值。|  
|[CHtmlView::GetReadyState](#getreadystate)|检索 web 浏览器对象的就绪状态。|  
|[CHtmlView::GetRegisterAsBrowser](#getregisterasbrowser)|指示是否将 WebBrowser 控件注册为目标名称解析的顶级浏览器。|  
|[CHtmlView::GetRegisterAsDropTarget](#getregisterasdroptarget)|指示是否将 WebBrowser 控件注册为导航的放置目标。|  
|[CHtmlView::GetSilent](#getsilent)|指示是否可以显示任何对话框。|  
|[CHtmlView::GetSource](#getsource)|网页的 HTML 源代码。|  
|[CHtmlView::GetStatusBar](#getstatusbar)|指示 Internet Explorer 的状态栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::GetTheaterMode](#gettheatermode)|指示 WebBrowser 控件是否处于影院模式。|  
|[CHtmlView::GetToolBar](#gettoolbar)|检索一个值，该值确定工具栏是否可见。|  
|[CHtmlView::GetTop](#gettop)|检索 Internet Explorer 主窗口顶部边缘的屏幕坐标。|  
|[CHtmlView::GetTopLevelContainer](#gettoplevelcontainer)|检索一个值，该值指示当前对象是否为 WebBrowser 控件的顶级容器。|  
|[CHtmlView::GetType](#gettype)|检索文档对象的类型名称。|  
|[CHtmlView::GetVisible](#getvisible)|检索一个值，该值指示对象是可见还是隐藏。|  
|[CHtmlView::GetWidth](#getwidth)|检索 Internet Explorer 主窗口的宽度。|  
|[CHtmlView::GoBack](#goback)|导航至历史记录列表中的上一项。|  
|[CHtmlView::GoForward](#goforward)|导航至历史记录列表中的下一项。|  
|[CHtmlView::GoHome](#gohome)|导航至当前主页或起始页。|  
|[CHtmlView::GoSearch](#gosearch)|导航至当前搜索页。|  
|[CHtmlView::LoadFromResource](#loadfromresource)|加载 WebBrowser 控件中的资源。|  
|[CHtmlView::Navigate](#navigate)|导航至由 URL 标识的资源。|  
|[CHtmlView::Navigate2](#navigate2)|导航至由 URL 标识的资源或由完整路径标识的文件。|  
|[CHtmlView::OnBeforeNavigate2](#onbeforenavigate2)|在给定 WebBrowser 中发生导航之前调用（在窗口或框架集元素上）|  
|[CHtmlView::OnCommandStateChange](#oncommandstatechange)|调用以通知应用程序 Web 浏览器命令的启用状态已更改。|  
|[CHtmlView::OnDocumentComplete](#ondocumentcomplete)|调用以通知的应用程序文档已到达 `READYSTATE_COMPLETE` 状态。|  
|[CHtmlView::OnDocWindowActivate](#ondocwindowactivate)|从 Internet Explorer 或 MSHTML 实现调用[IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281)，该容器的文档窗口处于激活或停用时通知活动就地对象。|  
|[CHtmlView::OnDownloadBegin](#ondownloadbegin)|调用以通知应用程序将开始导航操作|  
|[CHtmlView::OnDownloadComplete](#ondownloadcomplete)|在导航操作完成、暂停或失败时调用。|  
|[CHtmlView::OnEnableModeless](#onenablemodeless)|调用以在容器创建或销毁模式对话框时启用或禁用无模式对话框。|  
|[CHtmlView::OnFilterDataObject](#onfilterdataobject)|由 Internet Explorer 或 MSHTML 对主机调用，以允许主机替换 Internet Explorer 或 MSHTML 的数据对象。|  
|[CHtmlView::OnFrameWindowActivate](#onframewindowactivate)|从调用[IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)以便通知对象，当容器的顶层框架窗口激活或停用。|  
|[CHtmlView::OnFullScreen](#onfullscreen)|当 FullScreen 属性已更改时调用。|  
|[CHtmlView::OnGetDropTarget](#ongetdroptarget)|它被用作放置目标，它使主机提供一种替代方法时由 Internet Explorer 或 MSHTML 调用[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)。|  
|[CHtmlView::OnGetExternal](#ongetexternal)|由 Internet Explorer 或 MSHTML 调用以获取主机的 `IDispatch` 接口。|  
|[CHtmlView::OnGetHostInfo](#ongethostinfo)|检索 Internet Explorer 或 MSHTML 主机的用户界面功能。|  
|[CHtmlView::OnGetOptionKeyPath](#ongetoptionkeypath)|返回 Internet Explorer 或 MSHTML 在其下存储用户首选项的注册表项。|  
|[CHtmlView::OnHideUI](#onhideui)|当 Internet Explorer 或 MSHTML 删除其菜单和工具栏时调用。|  
|[CHtmlView::OnMenuBar](#onmenubar)|当 MenuBar 属性已更改时调用。|  
|[CHtmlView::OnNavigateComplete2](#onnavigatecomplete2)|完成到超链接的导航后调用（在窗口或框架集元素上）。|  
|[CHtmlView::OnNavigateError](#onnavigateerror)|当导航到超链接失败时由框架调用。|  
|[CHtmlView::OnNewWindow2](#onnewwindow2)|当要创建新窗口以显示资源时调用。|  
|[CHtmlView::OnProgressChange](#onprogresschange)|调用以通知应用程序下载操作的进度已更新。|  
|[CHtmlView::OnPropertyChange](#onpropertychange)|调用以通知应用程序，[只有](#putproperty)方法已更改属性的值。|  
|[CHtmlView::OnQuit](#onquit)|调用以通知应用程序 Internet Explorer 应用程序已准备退出。 （仅适用于 Internet Explorer）|  
|[CHtmlView::OnResizeBorder](#onresizeborder)|调用与的 Internet Explorer 或 MSHTML 实现[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)，来提醒的对象，它需要调整其边框空间的大小。|  
|[CHtmlView::OnShowContextMenu](#onshowcontextmenu)|当 Internet Explorer 或 MSHTML 将要显示其上下文菜单时，从其调用。|  
|[CHtmlView::OnShowUI](#onshowui)|在 Internet Explorer 或 MSHTML 显示其菜单和工具栏之前调用。|  
|[CHtmlView::OnStatusBar](#onstatusbar)|当 StatusBar 属性已更改时调用。|  
|[CHtmlView::OnStatusTextChange](#onstatustextchange)|调用以通知应用程序与 WebBrowser 控件相关联的状态栏的文本已更改。|  
|[CHtmlView::OnTheaterMode](#ontheatermode)|当 TheaterMode 属性已更改时调用。|  
|[CHtmlView::OnTitleChange](#ontitlechange)|调用以通知应用程序 WebBrowser 控件中的文档的标题是否变为可用或是否更改。|  
|[CHtmlView::OnToolBar](#ontoolbar)|当 ToolBar 属性已更改时调用。|  
|[CHtmlView::OnTranslateAccelerator](#ontranslateaccelerator)|通过 Internet Explorer 或 MSHTML 调用时[IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360)或[IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756)调用来处理菜单加速键从容器的消息队列的消息。|  
|[CHtmlView::OnTranslateUrl](#ontranslateurl)|由 Internet Explorer 或 MSHTML 调用以允许主机有机会修改要加载的 URL。|  
|[CHtmlView::OnUpdateUI](#onupdateui)|通知主机命令状态已更改。|  
|[CHtmlView::OnVisible](#onvisible)|当应该显示/隐藏 WebBrowser 控件的窗口时调用。|  
|[CHtmlView::PutProperty](#putproperty)|检索与给定对象关联的属性的值。|  
|[CHtmlView::QueryFormsCommand](#queryformscommand)|查询由用户界面事件生成的一个或多个命令的状态。|  
|[CHtmlView::QueryStatusWB](#querystatuswb)|查询正在由 WebBrowser 控件进行处理的命令的状态。|  
|[CHtmlView::Refresh](#refresh)|重新加载当前文件。|  
|[CHtmlView::Refresh2](#refresh2)|重新加载当前文件并选择性地阻止 `pragma:nocache` 标头被发送。|  
|[CHtmlView::SetAddressBar](#setaddressbar)|显示 或隐藏 Internet Explorer 对象的地址栏。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetFullScreen](#setfullscreen)|设置一个值，用于确定 WebBrowser 控件是在全屏模式下还是在正常窗口模式下运行。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetHeight](#setheight)|设置 Internet Explorer 主窗口的高度。|  
|[CHtmlView::SetLeft](#setleft)|设置 Internet Explorer 主窗口的水平位置。|  
|[CHtmlView::SetMenuBar](#setmenubar)|设置一个值，用以确定控件的菜单栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetOffline](#setoffline)|设置一个值，用以确定控件是否处于脱机状态。|  
|[CHtmlView::SetRegisterAsBrowser](#setregisterasbrowser)|设置一个值，指示是否将 WebBrowser 控件注册为目标名称解析的顶级浏览器。|  
|[CHtmlView::SetRegisterAsDropTarget](#setregisterasdroptarget)|设置一个值，指示是否将 WebBrowser 控件注册为导航的放置目标。|  
|[CHtmlView::SetSilent](#setsilent)|设置一个值，用以确定控件是否将显示对话框。|  
|[CHtmlView::SetStatusBar](#setstatusbar)|设置一个值，用以确定 Internet Explorer 的状态栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetTheaterMode](#settheatermode)|设置一个值，指示 WebBrowser 控件是否处于影院模式。|  
|[CHtmlView::SetToolBar](#settoolbar)|设置一个值，用以确定控件的工具栏是否可见。 （WebBrowser 控件仅忽略；Internet Explorer。）|  
|[CHtmlView::SetTop](#settop)|设置 Internet Explorer 主窗口的垂直位置。|  
|[CHtmlView::SetVisible](#setvisible)|设置一个值，该值指示对象是可见还是隐藏。|  
|[CHtmlView::SetWidth](#setwidth)|设置 Internet Explorer 主窗口的宽度。|  
|[CHtmlView::Stop](#stop)|停止打开文件。|  
  
## <a name="remarks"></a>备注  
 WebBrowser 控件是一个窗口，其中用户可以浏览万维网上的站点以及本地文件系统中和网络上的文件夹。 WebBrowser 控件支持超级链接、统一资源定位器 (URL) 导航，并维护历史记录列表。  
  
## <a name="using-the-chtmlview-class-in-an-mfc-application"></a>在 MFC 应用程序中使用 CHtmlView 类  
 在标准 MFC 框架应用程序（基于 SDI 或 MDI）中，视图对象通常派生自专用的一组类。 这些类全部派生自 `CView`，它们提供 `CView`所没有提供的专用功能。  
  
 将 `CHtmlView` 作为应用程序的视图类的基础可向视图提供 WebBrowser 控件。 这将有效地使应用程序成为一个 Web 浏览器。 创建一个 Web 浏览器样式的应用程序的首选方法是使用 MFC 应用程序向导，并将 `CHtmlView` 指定为视图类。 有关实现和使用 MFC 应用程序内的 web 浏览器控件的详细信息，请参阅[创建的 Web 浏览器样式应用](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)。  
  
> [!NOTE]
>  WebBrowser ActiveX 控件（因此 `CHtmlView`）仅可用于在 Windows NT 4.0 版或更高版本（其中安装了 Internet Explorer 4.0 版或更高版本）下运行的程序。  
  
 `CHtmlView`用于访问 Web 应用程序 （和/或 HTML 文档）。 以下 `CHtmlView` 成员函数仅适用于 Internet Explorer 应用程序。 这些函数将在 WebBrowser 控件上成功运行，但不会有明显的效果。  
  
- [GetAddressBar](#getaddressbar)  
  
- [GetFullName](#getfullname)  
  
- [GetStatusBar](#getstatusbar)  
  
- [SetAddressBar](#setaddressbar)  
  
- [SetFullScreen](#setfullscreen)  
  
- [SetMenuBar](#setmenubar)  
  
- [SetStatusBar](#setstatusbar)  
  
- [SetToolBar](#settoolbar)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CHtmlView`  
  
## <a name="requirements"></a>要求  
 **标头：** afxhtml.h  
  
##  <a name="a-namecreatea--chtmlviewcreate"></a><a name="create"></a>CHtmlView::Create  
 调用此成员函数来创建一个 web 浏览器控件或容器 Internet explorer 可执行文件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszClassName`  
 指向以 null 结尾的字符串名称的 Windows 类 string。 类名可以是任何名称注册[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全局函数或**RegisterClass** Windows 函数。 如果**NULL**，使用预定义的默认[CFrameWnd](../../mfc/reference/cframewnd-class.md)属性。  
  
 `lpszWindowName`  
 指向以 null 结尾的字符串表示窗口名称。  
  
 `dwStyle`  
 指定的窗口样式特性。 默认情况下， **WS_VISIBLE**和**WS_CHILD**设置窗口的样式。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定的大小和窗口的位置。 `rectDefault`值使 Windows 可以指定的大小和新窗口的位置。  
  
 `pParentWnd`  
 指向控件的父窗口的指针。  
  
 `nID`  
 视图的 ID 号。 默认情况下，将设置为**AFX_IDW_PANE_FIRST**。  
  
 `pContext`  
 一个指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)。 **NULL**默认情况下。  
  
##  <a name="a-namecreatecontrolsitea--chtmlviewcreatecontrolsite"></a><a name="createcontrolsite"></a>CHtmlView::CreateControlSite  
 可重写，用于创建控件站点实例以承载窗体上的控件。  
  
```  
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,  
    COleControlSite** ppSite,  
    UINT nID,  
    REFCLSID clsid);
```  
  
### <a name="parameters"></a>参数  
 `pContainer`  
 一个指向[COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)对象，其中包含该控件。  
  
 `ppSite`  
 指针到指向[COleControlSite](../../mfc/reference/colecontrolsite-class.md)对象，以便该站点提供的控件。  
  
 `nID`  
 要承载的控件的标识符。  
  
 `clsid`  
 要承载控件的 CLSID  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 您可以重写该成员函数以返回您自己控件站点类的实例。  
  
##  <a name="a-nameexecformscommanda--chtmlviewexecformscommand"></a><a name="execformscommand"></a>CHtmlView::ExecFormsCommand  
 使用 `IOleCommandTarget::Exec` 方法执行指定的命令。  
  
```  
HRESULT ExecFormsCommand(
    DWORD dwCommandID,  
    VARIANT* pVarIn,  
    VARIANT* pVarOut);
```  
  
### <a name="parameters"></a>参数  
 `dwCommandID`  
 要执行的命令。 此命令必须属于**CMDSETID3_Forms3**组。  
  
 *pVarIn*  
 指向**VARIANT**结构，它包含输入的参数。 可以是**NULL**。  
  
 *pVarOut*  
 指向**VARIANT**结构就可以接收命令输出。 可以是**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。 有关可能的值的完整列表，请参阅[IOleCommandTarget::Exec](http://msdn.microsoft.com/library/windows/desktop/ms690300)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 **ExecFormsCommand**实现的行为[IOleCommandTarget::Exec](http://msdn.microsoft.com/library/windows/desktop/ms690300)方法。  
  
##  <a name="a-nameexecwba--chtmlviewexecwb"></a><a name="execwb"></a>CHtmlView::ExecWB  
 调用该成员函数以在 web 浏览器或 Internet Explorer 中执行命令。  
  
```  
void ExecWB(
    OLECMDID cmdID,  
    OLECMDEXECOPT cmdexecopt,  
    VARIANT* pvaIn,  
    VARIANT* pvaOut);
```  
  
### <a name="parameters"></a>参数  
 `cmdID`  
 要执行的命令。  
  
 *cmdexecopt*  
 为执行该命令设置的选项。  
  
 `pvaIn`  
 一个用于指定命令的输入的参数的变量。  
  
 *pvaOut*  
 一个用于指定命令的输出参数的变量。  
  
### <a name="remarks"></a>备注  
 请参阅[IWebBrowser2::ExecWB](https://msdn.microsoft.com/library/aa752117.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetaddressbara--chtmlviewgetaddressbar"></a><a name="getaddressbar"></a>CHtmlView::GetAddressBar  
 调用此成员函数以检索 Internet Explorer 地址栏。  
  
```  
BOOL GetAddressBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果地址栏中可见，则为非否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer。 如果使用 WebBrowser 控件使用此调用，它将返回没有错误，但它将忽略此调用。  
  
##  <a name="a-namegetapplicationa--chtmlviewgetapplication"></a><a name="getapplication"></a>CHtmlView::GetApplication  
 调用此成员函数以检索包含 web 浏览器控件的应用程序支持的自动化对象。  
  
```  
LPDISPATCH GetApplication() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`IDispatch`活动文档对象的接口。 有关详细信息，请参阅[实现 IDispatch 接口](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetbusya--chtmlviewgetbusy"></a><a name="getbusy"></a>CHtmlView::GetBusy  
 调用该成员函数以确定 web 浏览器控件所从事的导航或下载操作。  
  
```  
BOOL GetBusy() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果 web 浏览器正忙;否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetcontainera--chtmlviewgetcontainer"></a><a name="getcontainer"></a>CHtmlView::GetContainer  
 调用此成员函数以检索到的容器的 web 浏览器的计算结果的对象。  
  
```  
LPDISPATCH GetContainer() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`IDispatch`活动文档对象的接口。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetfullnamea--chtmlviewgetfullname"></a><a name="getfullname"></a>CHtmlView::GetFullName  
 调用该成员函数以检索当前显示 Internet explorer 中的文件的完整路径。  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含的路径和名称当前显示的文件。 如果不存在任何路径和文件名，`GetFullName`返回一个空`CString`。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer。 如果使用 WebBrowser 控件使用此调用，它将返回没有错误，但它将忽略此调用。  
  
##  <a name="a-namegetfullscreena--chtmlviewgetfullscreen"></a><a name="getfullscreen"></a>CHtmlView::GetFullScreen  
 调用此成员函数来确定在全屏幕模式下或在正常窗口模式下是否运行 web 浏览器控件。  
  
```  
BOOL GetFullScreen() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果在全屏幕模式，则操作 webbrowser 控件中，非零值否则为零。  
  
### <a name="remarks"></a>备注  
 在全屏幕模式下，Internet 资源管理器主窗口已最大化和隐藏状态栏、 工具栏、 菜单栏和标题栏。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetheighta--chtmlviewgetheight"></a><a name="getheight"></a>CHtmlView::GetHeight  
 调用此成员函数可检索的高度，以像素为单位，WebBrowser 控件的框架窗口。  
  
```  
long GetHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件的框架窗口高度，以像素为单位。  
  
##  <a name="a-namegethtmldocumenta--chtmlviewgethtmldocument"></a><a name="gethtmldocument"></a>CHtmlView::GetHtmlDocument  
 调用此成员函数以检索活动文档的 HTML 文档。  
  
```  
LPDISPATCH GetHtmlDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`IDispatch`活动文档对象的接口。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetlefta--chtmlviewgetleft"></a><a name="getleft"></a>CHtmlView::GetLeft  
 调用此成员函数以检索 web 浏览器控件的内部左边的缘与其容器左边的缘之间的距离。  
  
```  
long GetLeft() const;  
```  
  
### <a name="return-value"></a>返回值  
 左边缘的距离，以像素为单位。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetlocationnamea--chtmlviewgetlocationname"></a><a name="getlocationname"></a>CHtmlView::GetLocationName  
 调用该成员函数以获取显示在 webbrowser 控件中的资源的名称。  
  
```  
CString GetLocationName() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，它包含当前在 webbrowser 控件中显示的资源的名称。  
  
### <a name="remarks"></a>备注  
 如果资源是在万维网上的 HTML 页面，名称将为该页面的标题。 如果资源是文件夹或文件在网络或本地计算机上的，名称为 UNC 或文件夹或文件的完整路径。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetlocationurla--chtmlviewgetlocationurl"></a><a name="getlocationurl"></a>CHtmlView::GetLocationURL  
 调用该成员函数以检索 web 浏览器控件当前显示的资源的 URL。  
  
```  
CString GetLocationURL() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，它包含当前在 webbrowser 控件中显示的资源的 URL。  
  
### <a name="remarks"></a>备注  
 如果资源是文件夹或文件在网络或本地计算机上的，名称为 UNC 或文件夹或文件的完整路径。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetmenubara--chtmlviewgetmenubar"></a><a name="getmenubar"></a>CHtmlView::GetMenuBar  
 调用此成员函数可确定在菜单栏是否可见。  
  
```  
BOOL GetMenuBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该菜单栏是可见的则非零值否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetofflinea--chtmlviewgetoffline"></a><a name="getoffline"></a>CHtmlView::GetOffline  
 调用此成员函数来确定是否脱机运行 web 浏览器。  
  
```  
BOOL GetOffline() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果 web 浏览器当前处于脱机状态; 则为非否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetparentbrowsera--chtmlviewgetparentbrowser"></a><a name="getparentbrowser"></a>CHtmlView::GetParentBrowser  
 调用此成员函数以检索指向 web 浏览器控件的父对象的指针。  
  
```  
LPDISPATCH GetParentBrowser() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`IDispatch`是 web 浏览器控件的父对象的接口。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetpropertya--chtmlviewgetproperty"></a><a name="getproperty"></a>CHtmlView::GetProperty  
 调用该成员函数以获取当前与该控件关联的属性的值。  
  
```  
BOOL GetProperty(
    LPCTSTR lpszProperty,  
    CString& strValue);  
  
COleVariant GetProperty(LPCTSTR lpszProperty);
```  
  
### <a name="parameters"></a>参数  
 `lpszProperty`  
 指向包含要检索的属性的字符串的指针。  
  
 `strValue`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，它接收的属性的当前值。  
  
### <a name="return-value"></a>返回值  
 在第一个版本中，非零，如果成功地完成。否则为零。 在第二个版本中， [COleVariant](../../mfc/reference/colevariant-class.md)对象。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetreadystatea--chtmlviewgetreadystate"></a><a name="getreadystate"></a>CHtmlView::GetReadyState  
 调用此成员函数以检索 web 浏览器对象的就绪状态。  
  
```  
READYSTATE GetReadyState() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[READYSTATE](https://msdn.microsoft.com/library/aa768362.aspx)值，如下所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetregisterasbrowsera--chtmlviewgetregisterasbrowser"></a><a name="getregisterasbrowser"></a>CHtmlView::GetRegisterAsBrowser  
 调用该成员函数以确定是否将 web 浏览器对象注册为目标的名称解析的顶层浏览器。  
  
```  
BOOL GetRegisterAsBrowser() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果浏览器注册顶层浏览器; 为非零值否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetregisterasdroptargeta--chtmlviewgetregisterasdroptarget"></a><a name="getregisterasdroptarget"></a>CHtmlView::GetRegisterAsDropTarget  
 调用该成员函数以确定是否将 WebBrowser 控件注册为放置目标进行导航。  
  
```  
BOOL GetRegisterAsDropTarget() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果浏览器注册为放置目标;否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetsilenta--chtmlviewgetsilent"></a><a name="getsilent"></a>CHtmlView::GetSilent  
 调用该成员函数以确定是否可以在 web 浏览器控件中显示任何对话框。  
  
```  
BOOL GetSilent() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果不能从 web 浏览器控件，则显示对话框否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetsourcea--chtmlviewgetsource"></a><a name="getsource"></a>CHtmlView::GetSource  
 调用此成员函数以检索 web 页的 HTML 源代码。  
  
```  
BOOL GetSource(CString& strRef);
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="parameters"></a>参数  
 `refString`  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，将存放的源代码。  
  
### <a name="remarks"></a>备注  
 此函数是等效于 Internet Explorer 中的"查看源文件"命令，只不过中返回的源代码`CString`。  
  
##  <a name="a-namegetstatusbara--chtmlviewgetstatusbar"></a><a name="getstatusbar"></a>CHtmlView::GetStatusBar  
 调用该成员函数以确定是否显示状态栏，web 浏览器控件。  
  
```  
BOOL GetStatusBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以显示状态栏，则非零值否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer。 如果使用 WebBrowser 控件使用此调用，它将返回没有错误，但它将忽略此调用。  
  
##  <a name="a-namegettheatermodea--chtmlviewgettheatermode"></a><a name="gettheatermode"></a>CHtmlView::GetTheaterMode  
 调用该成员函数以确定 web 浏览器是否处于影院模式。  
  
```  
BOOL GetTheaterMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果 web 浏览器处于影院模式，则为非零值否则为零。  
  
### <a name="remarks"></a>备注  
 影院模式的 web 浏览器时，浏览器主窗口填满整个屏幕，会出现与导航工具的最小集一个工具栏，和状态栏显示在屏幕的右上角中。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegettoolbara--chtmlviewgettoolbar"></a><a name="gettoolbar"></a>CHtmlView::GetToolBar  
 调用该成员函数以确定指示工具栏是否可见。  
  
```  
int GetToolBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个值，该值指示工具栏是否可见。 如果工具栏可见，则非零值否则为零。  
  
##  <a name="a-namegettopa--chtmlviewgettop"></a><a name="gettop"></a>CHtmlView::GetTop  
 调用此成员函数以检索 web 浏览器控件的主窗口的上边缘的屏幕坐标。  
  
```  
long GetTop() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个变量来接收主窗口的上边缘的屏幕坐标的地址。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegettoplevelcontainera--chtmlviewgettoplevelcontainer"></a><a name="gettoplevelcontainer"></a>CHtmlView::GetTopLevelContainer  
 调用该成员函数以确定 Internet Explorer 是否为 web 浏览器控件的顶级容器。  
  
```  
BOOL GetTopLevelContainer() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零值的容器是顶级容器;否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegettypea--chtmlviewgettype"></a><a name="gettype"></a>CHtmlView::GetType  
 调用此成员函数以检索包含的活动文档的类型名称。  
  
```  
CString GetType() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含所包含的活动文档的类型名称。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetvisiblea--chtmlviewgetvisible"></a><a name="getvisible"></a>CHtmlView::GetVisible  
 调用该成员函数以确定包含的对象是否可见。  
  
```  
BOOL GetVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果对象是可见的则非零值否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetwidtha--chtmlviewgetwidth"></a><a name="getwidth"></a>CHtmlView::GetWidth  
 检索 Internet Explorer 主窗口的宽度。  
  
```  
long GetWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 窗口中，以像素为单位的当前宽度。  
  
##  <a name="a-namegobacka--chtmlviewgoback"></a><a name="goback"></a>CHtmlView::GoBack  
 导航历史记录列表中的向后一个项目。  
  
```  
void GoBack();
```  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegoforwarda--chtmlviewgoforward"></a><a name="goforward"></a>CHtmlView::GoForward  
 导航历史记录列表中的正向一个项。  
  
```  
void GoForward();
```  
  
##  <a name="a-namegohomea--chtmlviewgohome"></a><a name="gohome"></a>CHtmlView::GoHome  
 导航到当前主页，或者启动“Internet Explorer Internet 选项”对话框或“Internet 属性”对话框（可从“控制面板”访问）中指定的网页。  
  
```  
void GoHome();
```  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegosearcha--chtmlviewgosearch"></a><a name="gosearch"></a>CHtmlView::GoSearch  
 导航到当前搜索页，指定在 Internet Explorer Internet 选项对话框中或 Internet 属性对话框中，从控制面板中访问。  
  
```  
void GoSearch();
```  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-nameloadfromresourcea--chtmlviewloadfromresource"></a><a name="loadfromresource"></a>CHtmlView::LoadFromResource  
 调用该成员函数以加载到 WebBrowser 控件中指定的资源。  
  
```  
BOOL LoadFromResource(LPCTSTR lpszResource);  
BOOL LoadFromResource(UINT nRes);
```  
  
### <a name="parameters"></a>参数  
 `lpszResource`  
 指向包含要加载的资源名称的字符串的指针。  
  
 `nRes`  
 要加载包含资源的名称的缓冲区的 ID。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namenavigatea--chtmlviewnavigate"></a><a name="navigate"></a>CHtmlView::Navigate  
 调用该成员函数以导航到由 URL 进行标识的资源。  
  
```  
void Navigate(
    LPCTSTR URL,  
    DWORD dwFlags = 0,  
    LPCTSTR lpszTargetFrameName = NULL,  
    LPCTSTR lpszHeaders = NULL,  
    LPVOID lpvPostData = NULL,  
    DWORD dwPostDataLen = 0);
```  
  
### <a name="parameters"></a>参数  
 *URL*  
 包含要导航到的 URL 的调用方分配的字符串或要显示的文件的完整路径。  
  
 `dwFlags`  
 用于指定是否要将资源添加到历史记录列表、 是否读取或写入从缓存中，以及是否在新窗口中显示的资源的变量的标志。 变量可以是由定义值的组合[BrowserNavConstants](https://msdn.microsoft.com/library/aa768360.aspx)枚举。  
  
 `lpszTargetFrameName`  
 指向包含要在其中显示该资源框架的名称的字符串的指针。  
  
 `lpszHeaders`  
 指向一个值，指定要向服务器发送的 HTTP 标头的指针。 这些标头添加到默认的 Internet Explorer 标头中。 标头可以指定为所需的服务器，传递到该服务器或状态代码的数据类型的操作等。 如果忽略此参数*URL*不是一个 HTTP URL。  
  
 `lpvPostData`  
 指向要发送的 HTTP POST 事务的数据的指针。 例如，开机自检事务用于发送 HTML 窗体所收集的数据。 如果此参数未指定发送的所有数据，**导航**发出 HTTP GET 的事务。 如果忽略此参数*URL*不是一个 HTTP URL。  
  
 `dwPostDataLen`  
 若要使用 HTTP POST 事务发送的数据。 例如，开机自检事务用于发送 HTML 窗体所收集的数据。 如果此参数未指定发送的所有数据，**导航**发出 HTTP GET 的事务。 如果忽略此参数*URL*不是一个 HTTP URL。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namenavigate2a--chtmlviewnavigate2"></a><a name="navigate2"></a>CHtmlView::Navigate2  
 调用该成员函数以导航到一个 URL，标识的资源或完整路径所标识的文件。  
  
```  
void Navigate2(
    LPITEMIDLIST pIDL,  
    DWORD dwFlags = 0,  
    LPCTSTR lpszTargetFrameName = NULL);

 
void Navigate2(
    LPCTSTR lpszURL,  
    DWORD dwFlags = 0,  
    LPCTSTR lpszTargetFrameName = NULL,  
    LPCTSTR lpszHeaders = NULL,  
    LPVOID lpvPostData = NULL,  
    DWORD dwPostDataLen = 0);

 
void Navigate2(
    LPCTSTR lpszURL,  
    DWORD dwFlags,  
    CByteArray& baPostedData,  
    LPCTSTR lpszTargetFrameName = NULL,  
    LPCTSTR lpszHeader = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pIDL*  
 一个指向[ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321)结构。  
  
 `dwFlags`  
 用于指定是否要将资源添加到历史记录列表、 是否读取或写入从缓存中，以及是否在新窗口中显示的资源的变量的标志。 变量可以是由定义值的组合[BrowserNavConstants](https://msdn.microsoft.com/library/aa768360.aspx)枚举。  
  
 `lpszTargetFrameName`  
 指向包含要在其中显示该资源框架的名称的字符串的指针。  
  
 `lpszURL`  
 指向包含 URL 的字符串的指针。  
  
 `lpvPostData`  
 若要使用 HTTP POST 事务发送的数据。 例如，开机自检事务用于发送 HTML 窗体所收集的数据。 如果此参数未指定发送的所有数据，`Navigate2`发出 HTTP GET 的事务。 如果忽略此参数*URL*不是 HTTP 或 HTTPS URL。  
  
 `dwPostDataLen`  
 指向以字节为单位的数据的长度`lpvPostData`参数。  
  
 `lpszHeaders`  
 指向一个值，指定要向服务器发送的 HTTP 或 HTTPS 标头的指针。 这些标头添加到默认的 Internet Explorer 标头中。 标头可以指定为所需的服务器，传递到该服务器或状态代码的数据类型的操作等。 如果忽略此参数*URL*不是 HTTP 或 HTTPS URL。  
  
 `baPostedData`  
 对引用[CByteArray](../../mfc/reference/cbytearray-class.md)对象。  
  
### <a name="remarks"></a>备注  
 此成员函数可能延长**导航**通过支持在桌面和我的电脑等特殊文件夹，该参数表示上进行浏览的成员函数*pIDL*。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCHtmlHttp #&7;](../../mfc/reference/codesnippet/cpp/chtmlview-class_1.cpp)]  
  
##  <a name="a-nameonbeforenavigate2a--chtmlviewonbeforenavigate2"></a><a name="onbeforenavigate2"></a>CHtmlView::OnBeforeNavigate2  
 此成员函数是由框架调用以导致在 web 浏览器中发生导航之前引发该事件。  
  
```  
virtual void OnBeforeNavigate2(
    LPCTSTR lpszURL,  
    DWORD nFlags,  
    LPCTSTR lpszTargetFrameName,  
    CByteArray& baPostedData,  
    LPCTSTR lpszHeaders,  
    BOOL* pbCancel);
```  
  
### <a name="parameters"></a>参数  
 `lpszURL`  
 包含要导航到 URL 的字符串的指针。  
  
 `nFlags`  
 留待将来使用。  
  
 `lpszTargetFrameName`  
 一个字符串，包含要在其中显示该资源，框架的名称或**NULL**如果没有命名的框架目标的资源。  
  
 `baPostedData`  
 对引用`CByteArray`对象，其中包含要发送到服务器，如果正在使用 HTTP POST 事务的数据。  
  
 `lpszHeaders`  
 指向包含附加的 HTTP 标头将发送到服务器 (仅适用于 HTTP Url) 的字符串的指针。 标头可以指定为所需的服务器，传递到该服务器或状态代码的数据类型的操作等。  
  
 `pbCancel`  
 指向一个取消标记的指针。 应用程序可以将此参数设置为非零，若要取消导航的操作，或为零以允许应用程序继续执行。  
  
##  <a name="a-nameoncommandstatechangea--chtmlviewoncommandstatechange"></a><a name="oncommandstatechange"></a>CHtmlView::OnCommandStateChange  
 此成员函数是由框架调用以通知应用程序启用的 web 浏览器命令状态已更改。  
  
```  
virtual void OnCommandStateChange(
    long nCommand,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 *nCommand*  
 更改了已启用的状态的命令标识符。  
  
 `bEnable`  
 已启用的状态。 如果该命令已启用，或者如果它处于禁用状态为零，则此参数为非零。  
  
##  <a name="a-nameondocumentcompletea--chtmlviewondocumentcomplete"></a><a name="ondocumentcomplete"></a>CHtmlView::OnDocumentComplete  
 此成员函数由框架调用以通知应用程序的文档已达到`READYSTATE_COMPLETE`状态。  
  
```  
virtual void OnDocumentComplete(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>参数  
 `lpszURL`  
 指向字符串的计算结果为 URL、 UNC 文件名称，或导航到的 PIDL （指向项标识符列表的指针）。  
  
### <a name="remarks"></a>备注  
 不是每个框架就会触发此事件，但激发每个帧[OnDownloadBegin](#ondownloadbegin)事件将激发相应`OnDocumentComplete`事件。  
  
 该 URL 由`lpszURL`可以不同于浏览器被告知要导航到，因为此 URL 是规范化的限定的 URL 的 URL。 例如，如果应用程序在调用中指定的 URL"www.microsoft.com"[导航](#navigate)或[Navigate2](#navigate2)，通过传递 URL`OnNavigateComplete2`将"http://www.microsoft.com/"。 此外，如果服务器已经重浏览器定向到另一个 URL，重定向的 URL 将会反映在此处。  
  
##  <a name="a-nameondocwindowactivatea--chtmlviewondocwindowactivate"></a><a name="ondocwindowactivate"></a>CHtmlView::OnDocWindowActivate  
 从 **IOleInPlaceActiveObject::OnDocWindowActivate**的 Internet Explorer 或 MSHTML 实现调用，该操作将在激活或停用容器文件窗口时通知活动的就地对象。  
  
```  
virtual HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="parameters"></a>参数  
 `fActivate`  
 指示文档窗口的状态。 如果此值为零，正在激活窗口中。 如果此值为零，正在停用窗口中。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或以其他方式 OLE 定义的错误代码。  
  
### <a name="remarks"></a>备注  
 重写`OnDocWindowActivate`以响应`OnDocWindowActivate`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameondownloadbegina--chtmlviewondownloadbegin"></a><a name="ondownloadbegin"></a>CHtmlView::OnDownloadBegin  
 此成员函数是由框架调用以开始下载文档。  
  
```  
virtual void OnDownloadBegin();
```  
  
### <a name="remarks"></a>备注  
 此事件激发后不久[OnBeforeNavigate2](#onbeforenavigate2)事件，除非取消导航。 任何动画或需要显示容器的"忙"指示应该连接到此事件。  
  
##  <a name="a-nameondownloadcompletea--chtmlviewondownloadcomplete"></a><a name="ondownloadcomplete"></a>CHtmlView::OnDownloadComplete  
 此成员函数是由框架调用以指示导航操作完成、 已暂停，还是已失败。  
  
```  
virtual void OnDownloadComplete();
```  
  
##  <a name="a-nameonenablemodelessa--chtmlviewonenablemodeless"></a><a name="onenablemodeless"></a>CHtmlView::OnEnableModeless  
 当 Internet Explorer 或 MSHTML 显示模式 UI 时调用。  
  
```  
virtual HRESULT OnEnableModeless(BOOL fEnable);
```  
  
### <a name="parameters"></a>参数  
 `fEnable`  
 指示是否启用或禁用该主机的无模式对话框。 如果此值不为零，则会启用无模式对话框。 如果此值为零，将禁用无模式对话框。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或以其他方式 OLE 定义的错误代码。  
  
### <a name="remarks"></a>备注  
 启用或禁用无模式对话框创建或销毁模式对话框中的容器。 重写`OnEnableModeless`以响应`EnableModeless`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameonfilterdataobjecta--chtmlviewonfilterdataobject"></a><a name="onfilterdataobject"></a>CHtmlView::OnFilterDataObject  
 由 Internet Explorer 或 MSHTML 对主机调用，以允许主机替换 Internet Explorer 或 MSHTML 的数据对象。  
  
```  
virtual HRESULT OnFilterDataObject(
    LPDATAOBJECT pDataObject,  
    LPDATAOBJECT* ppDataObject);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 地址的指针[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)为由 Internet Explorer 或 MSHTML 提供的接口。  
  
 *ppDataObject*  
 接收地址`IDataObject`宿主所提供的接口指针。 此参数的内容始终应初始化为**NULL**，即使该方法将失败。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果此数据对象被替换， **S_FALSE**如果不替换数据对象，则如果发生错误则返回 OLE 定义的错误代码。  
  
### <a name="remarks"></a>备注  
 重写`OnFilterDataObject`以响应`FilterDataObject`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameonframewindowactivatea--chtmlviewonframewindowactivate"></a><a name="onframewindowactivate"></a>CHtmlView::OnFrameWindowActivate  
 从调用[IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)以便通知对象，当容器的顶层框架窗口激活或停用。  
  
```  
virtual HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="parameters"></a>参数  
 `fActivate`  
 指示容器的顶层框架窗口的状态。 如果此值为零，正在激活窗口中。 如果此值为零，正在停用窗口中。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或以其他方式 OLE 定义的错误代码。  
  
### <a name="remarks"></a>备注  
 重写`OnFrameWindowActivate`以响应`OnFrameWindowActivate`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameonfullscreena--chtmlviewonfullscreen"></a><a name="onfullscreen"></a>CHtmlView::OnFullScreen  
 由框架调用此成员函数时[全屏幕](https://msdn.microsoft.com/library/aa752119.aspx)属性已更改。  
  
```  
virtual void OnFullScreen(BOOL bFullScreen);
```  
  
### <a name="parameters"></a>参数  
 *bFullScreen*  
 如果 Internet 资源管理器处于全屏显示模式，则非零值否则为零。  
  
##  <a name="a-nameongetdroptargeta--chtmlviewongetdroptarget"></a><a name="ongetdroptarget"></a>CHtmlView::OnGetDropTarget  
 它被用作放置目标，它使主机提供一种替代方法时由 Internet Explorer 或 MSHTML 调用`IDropTarget`。  
  
```  
virtual HRESULT OnGetDropTarget(
    LPDROPTARGET pDropTarget,  
    LPDROPTARGET* ppDropTarget);
```  
  
### <a name="parameters"></a>参数  
 `pDropTarget`  
 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) Internet Explorer 或 MSHTML 提出建议使用。  
  
 `ppDropTarget`  
 地址的指针`IDropTarget`接收`IDropTarget`主机需要提供的接口指针。  
  
### <a name="return-value"></a>返回值  
 请参阅[IDocHostUIHandler::GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关返回代码的列表。  
  
### <a name="remarks"></a>备注  
 重写`OnGetDropTarget`以响应`GetDropTarget`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameongetexternala--chtmlviewongetexternal"></a><a name="ongetexternal"></a>CHtmlView::OnGetExternal  
 由 Internet Explorer 或 MSHTML 调用以获取主机的 `IDispatch` 接口。  
  
```  
virtual HRESULT OnGetExternal(LPDISPATCH* lppDispatch);
```  
  
### <a name="parameters"></a>参数  
 *lppDispatch*  
 指向接收的地址的指针`IDispatch`宿主应用程序的接口指针。 如果主机公开自动化接口，它可以提供对 Internet Explorer 或 MSHTML 通过此参数的引用。 此参数的内容始终应初始化为**NULL**，即使该方法将失败。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或以其他方式 OLE 定义的错误代码。  
  
### <a name="remarks"></a>备注  
 重写`OnGetExternal`以响应`GetExternal`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameongethostinfoa--chtmlviewongethostinfo"></a><a name="ongethostinfo"></a>CHtmlView::OnGetHostInfo  
 检索 Internet Explorer 或 MSHTML 主机的用户界面功能。  
  
```  
virtual HRESULT OnGetHostInfo(DOCHOSTUIINFO* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pInfo`  
 地址的指针[DOCHOSTUIINFO](https://msdn.microsoft.com/library/aa770044.aspx)结构，它接收主机的用户界面功能。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或以其他方式 OLE 定义的错误代码。  
  
### <a name="remarks"></a>备注  
 重写`OnGetHostInfo`以响应`GetHostInfo`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameongetoptionkeypatha--chtmlviewongetoptionkeypath"></a><a name="ongetoptionkeypath"></a>CHtmlView::OnGetOptionKeyPath  
 调用该成员函数以获取在其下 Internet Explorer 或 MSHTML 存储用户首选项的注册表项。  
  
```  
virtual HRESULT OnGetOptionKeyPath(
    LPOLESTR* pchKey,  
    DWORD dwReserved);
```  
  
### <a name="parameters"></a>参数  
 `pchKey`  
 地址的指针`LPOLESTR`接收主机存储其默认选项的位置的注册表子项字符串。 此子项将是在 HKEY_CURRENT_USER 键下。 分配此内存使用[CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)。 调用应用程序负责释放此内存使用[CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)。 此参数应始终将初始化为**NULL**，即使该方法将失败。  
  
 `dwReserved`  
 留待将来使用。 当前未使用。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或**S_FALSE**否则为。 如果**S_FALSE**，Internet Explorer 或 MSHTML 将默认为自己的用户选项。  
  
### <a name="remarks"></a>备注  
 重写`OnGetOptionKeyPath`以响应`GetOptionKeyPath`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameonhideuia--chtmlviewonhideui"></a><a name="onhideui"></a>CHtmlView::OnHideUI  
 当 Internet Explorer 或 MSHTML 删除其菜单和工具栏，将由框架调用此成员函数。  
  
```  
virtual HRESULT OnHideUI();
```  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或以其他方式 OLE 定义的错误代码。  
  
### <a name="remarks"></a>备注  
 重写`OnHideUI`以响应`HideUI`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::HideUI](https://msdn.microsoft.com/library/aa753259.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameonmenubara--chtmlviewonmenubar"></a><a name="onmenubar"></a>CHtmlView::OnMenuBar  
 由框架调用此成员函数时[MenuBar](https://msdn.microsoft.com/library/aa752131.aspx)属性已更改。  
  
```  
virtual void OnMenuBar(BOOL bMenuBar);
```  
  
### <a name="parameters"></a>参数  
 *bMenuBar*  
 如果 Internet 资源管理器菜单栏可见，则为非否则为零。  
  
##  <a name="a-nameonnavigatecomplete2a--chtmlviewonnavigatecomplete2"></a><a name="onnavigatecomplete2"></a>CHtmlView::OnNavigateComplete2  
 （在窗口或框架集元素上） 为超链接导航完成后，将由框架调用此成员函数。  
  
```  
virtual void OnNavigateComplete2(LPCTSTR strURL);
```  
  
### <a name="parameters"></a>参数  
 *strURL*  
 字符串表达式的计算结果为 URL、 UNC 文件名称或导航到的 PIDL （指向项标识符列表的指针）。  
  
### <a name="remarks"></a>备注  
 URL 参数可以是在没有任何 URL 表示形式的命令行程序名称空间实体的情况下 PIDL。  
  
 请注意，该 URL 包含在*strURL*可以不同于浏览器被告知要导航到，因为此 URL 是规范化的限定的 URL 的 URL。 例如，如果应用程序在调用中指定的 URL"www.microsoft.com"[导航](#navigate)或[Navigate2](#navigate2)，通过传递 URL`OnNavigateComplete2`将"http://www.microsoft.com/"。 此外，如果服务器已经重浏览器定向到另一个 URL，重定向的 URL 将会反映在此处。  
  
##  <a name="a-nameonnavigateerrora--chtmlviewonnavigateerror"></a><a name="onnavigateerror"></a>CHtmlView::OnNavigateError  
 当导航到超链接失败时由框架调用。  
  
```  
virtual void OnNavigateError(
    LPCTSTR lpszURL,  
    LPCTSTR lpszFrame,  
    DWORD dwError,  
    BOOL* pbCancel);
```  
  
### <a name="parameters"></a>参数  
 `lpszURL`  
 失败导航 URL。  
  
 *lpszFrame*  
 在其中的资源是要显示，或者，如果没有命名的框架的目标资源的框架的名称。  
  
 `dwError`  
 错误状态代码，如果可用。 可能的 HRESULT 和 HTTP 状态代码的列表，请参阅[如何事件状态代码。](https://msdn.microsoft.com/library/aa768365.aspx)  
  
 `pbCancel`  
 指定是否要取消导航到错误页或任何进一步的自动搜索。 如果**TRUE** （默认值），继续使用导航到错误页或自动搜索; 如果**FALSE**，取消导航到错误页或自动搜索。  
  
### <a name="remarks"></a>备注  
 重写此方法以提供自定义导航错误处理。  
  
 有关详细信息，请参阅[DWebBrowserEvents2::NavigateError](https://msdn.microsoft.com/library/aa768286.aspx)  
  
##  <a name="a-nameonnewwindow2a--chtmlviewonnewwindow2"></a><a name="onnewwindow2"></a>CHtmlView::OnNewWindow2  
 要为显示资源创建一个新的窗口时，将由框架调用此成员函数。  
  
```  
virtual void OnNewWindow2(
    LPDISPATCH* ppDisp,  
    BOOL* Cancel);
```  
  
### <a name="parameters"></a>参数  
 `ppDisp`  
 （可选） 接收的接口指针指向的指针`IDispatch`新的 web 浏览器或 Internet 资源管理器对象的接口指针。  
  
 `Cancel`  
 指向一个取消标记的指针。 应用程序可以将此参数设置为非零，若要取消导航的操作，或为零以允许应用程序继续执行。  
  
### <a name="remarks"></a>备注  
 此事件之前从 webbrowser 控件中的一个新窗口的创建。  
  
##  <a name="a-nameonprogresschangea--chtmlviewonprogresschange"></a><a name="onprogresschange"></a>CHtmlView::OnProgressChange  
 此成员函数是由框架调用以通知应用程序已更新的下载操作的进度。  
  
```  
virtual void OnProgressChange(
    long nProgress,  
    long nProgressMax);
```  
  
### <a name="parameters"></a>参数  
 *nProgress*  
 显示，或者为-1 时进度已完成的总进度的量。  
  
 *nProgressMax*  
 最大的进度值。  
  
### <a name="remarks"></a>备注  
 若要显示到目前为止下载的字节数，或要更新进度指示器，容器可以使用此事件提供的信息。  
  
##  <a name="a-nameonpropertychangea--chtmlviewonpropertychange"></a><a name="onpropertychange"></a>CHtmlView::OnPropertyChange  
 此成员函数由框架调用以通知应用程序，[只有](#putproperty)已更改属性的值。  
  
```  
virtual void OnPropertyChange(LPCTSTR lpszProperty);
```  
  
### <a name="parameters"></a>参数  
 `lpszProperty`  
 指向包含的属性名称的字符串的指针。  
  
##  <a name="a-nameonquita--chtmlviewonquit"></a><a name="onquit"></a>CHtmlView::OnQuit  
 此成员函数是由框架调用以通知 Internet Explorer 应用程序已准备好退出应用程序。  
  
```  
virtual void OnQuit();
```  
  
##  <a name="a-nameonresizebordera--chtmlviewonresizeborder"></a><a name="onresizeborder"></a>CHtmlView::OnResizeBorder  
 调用与的 Internet Explorer 或 MSHTML 实现[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)，来提醒的对象，它需要调整其边框空间的大小。  
  
```  
virtual HRESULT OnResizeBorder(
    LPCRECT prcBorder,  
    LPOLEINPLACEUIWINDOW pUIWindow,  
    BOOL fFrameWindow);
```  
  
### <a name="parameters"></a>参数  
 `prcBorder`  
 边框空间的新外部矩形。  
  
 `pUIWindow`  
 指向已更改其边框的框架或文档窗口对象的接口的指针。  
  
 `fFrameWindow`  
 **TRUE**如果框架窗口正在调用[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)，否则为**FALSE**。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或以其他方式 OLE 定义的错误代码。  
  
### <a name="remarks"></a>备注  
 重写`OnResizeBorder`以响应`ResizeBorder`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameonshowcontextmenua--chtmlviewonshowcontextmenu"></a><a name="onshowcontextmenu"></a>CHtmlView::OnShowContextMenu  
 当 Internet Explorer 或 MSHTML 将要显示其上下文菜单时，从其调用。  
  
```  
virtual HRESULT OnShowContextMenu(
    DWORD dwID,  
    LPPOINT ppt,  
    LPUNKNOWN pcmdtReserved,  
    LPDISPATCH pdispReserved);
```  
  
### <a name="parameters"></a>参数  
 `dwID`  
 要显示的上下文菜单的标识符。 请参阅**IDocHostUIHandler::ShowContextMenu**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值的列表。  
  
 `ppt`  
 菜单上的屏幕坐标。  
  
 `pcmdtReserved`  
 [IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)接口用来查询命令状态和在此对象上执行命令。  
  
 `pdispReserved`  
 屏幕坐标处的对象的 IDispatch 接口。 这使宿主能够区分特定的对象来提供更具体的上下文。  
  
### <a name="return-value"></a>返回值  
 请参阅[IDocHostUIHandler::ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值的列表。  
  
### <a name="remarks"></a>备注  
 重写`OnShowContextMenu`以响应`ShowContextMenu`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameonshowuia--chtmlviewonshowui"></a><a name="onshowui"></a>CHtmlView::OnShowUI  
 在 Internet Explorer 或 MSHTML 显示其菜单和工具栏之前调用。  
  
```  
virtual HRESULT OnShowUI(
    DWORD dwID,  
    LPOLEINPLACEACTIVEOBJECT pActiveObject,  
    LPOLECOMMANDTARGET pCommandTarget,  
    LPOLEINPLACEFRAME pFrame,  
    LPOLEINPLACEUIWINDOW pDoc);
```  
  
### <a name="parameters"></a>参数  
 `dwID`  
 留待将来使用。  
  
 `pActiveObject`  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299)当前处于活动状态的对象的接口。  
  
 `pCommandTarget`  
 [IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)接口的对象。  
  
 `pFrame`  
 [IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770)接口的对象。 这需要菜单和工具栏。  
  
 `pDoc`  
 [IOleInPlaceUIWindow](http://msdn.microsoft.com/library/windows/desktop/ms680716)对象接口。 需要执行此工具栏。  
  
### <a name="return-value"></a>返回值  
 请参阅[IDocHostUIHandler::ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值的列表。  
  
### <a name="remarks"></a>备注  
 重写`OnShowUI`以响应`ShowUI`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameonstatusbara--chtmlviewonstatusbar"></a><a name="onstatusbar"></a>CHtmlView::OnStatusBar  
 由框架调用此成员函数时[StatusBar](https://msdn.microsoft.com/library/aa768270.aspx)属性已更改。  
  
```  
virtual void OnStatusBar(BOOL bStatusBar);
```  
  
### <a name="parameters"></a>参数  
 *bStatusBar*  
 如果 Internet Explorer 状态栏可见，则为非零，则为或。  
  
##  <a name="a-nameonstatustextchangea--chtmlviewonstatustextchange"></a><a name="onstatustextchange"></a>CHtmlView::OnStatusTextChange  
 此成员函数是由框架调用以通知应用程序与 web 浏览器控件相关联的状态栏文本已更改。  
  
```  
virtual void OnStatusTextChange(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 一个包含新状态栏文本的字符串。  
  
##  <a name="a-nameontheatermodea--chtmlviewontheatermode"></a><a name="ontheatermode"></a>CHtmlView::OnTheaterMode  
 由框架调用此成员函数时[TheaterMode](https://msdn.microsoft.com/library/aa768273.aspx)属性已更改。  
  
```  
virtual void OnTheaterMode(BOOL bTheaterMode);
```  
  
### <a name="parameters"></a>参数  
 *bTheaterMode*  
 如果 Internet 资源管理器处于影院模式，则为非零值否则为零。  
  
##  <a name="a-nameontitlechangea--chtmlviewontitlechange"></a><a name="ontitlechange"></a>CHtmlView::OnTitleChange  
 此成员函数是由框架以便在 web 浏览器控件中的文档的标题将变为可用时通知应用程序或更改的调用。  
  
```  
virtual void OnTitleChange(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 新的文档标题。  
  
### <a name="remarks"></a>备注  
 以 html 格式，可能会更改标题;虽然仍在下载 HTML，文档的 URL 将设置为标题。 实际的标题 （如果有） 从分析 HTML 后，标题会更改以反映实际的标题。  
  
##  <a name="a-nameontoolbara--chtmlviewontoolbar"></a><a name="ontoolbar"></a>CHtmlView::OnToolBar  
 由框架调用此成员函数时[工具栏](https://msdn.microsoft.com/library/aa768274.aspx)属性已更改。  
  
```  
virtual void OnToolBar(BOOL bToolBar);
```  
  
### <a name="parameters"></a>参数  
 *bToolBar*  
 如果 Internet Explorer 工具栏是否可见，则为非零，则为或。  
  
##  <a name="a-nameontranslateacceleratora--chtmlviewontranslateaccelerator"></a><a name="ontranslateaccelerator"></a>CHtmlView::OnTranslateAccelerator  
 通过 Internet Explorer 或 MSHTML 调用时[IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360)或[IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756)调用来处理菜单加速键从容器的消息队列的消息。  
  
```  
virtual HRESULT OnTranslateAccelerator(
    LPMSG lpMsg,  
    const GUID* pguidCmdGroup,  
    DWORD nCmdID);
```  
  
### <a name="parameters"></a>参数  
 `lpMsg`  
 指向以条消息，可能需要进行转换。  
  
 `pguidCmdGroup`  
 命令组标识符。  
  
 `nCmdID`  
 命令标识符。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或**S_FALSE**否则为。  
  
### <a name="remarks"></a>备注  
 重写`OnTranslateAccelerator`以响应`TranslateAccelerator`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameontranslateurla--chtmlviewontranslateurl"></a><a name="ontranslateurl"></a>CHtmlView::OnTranslateUrl  
 由 Internet Explorer 或 MSHTML 调用以允许主机有机会修改要加载的 URL。  
  
```  
virtual HRESULT OnTranslateUrl(
    DWORD dwTranslate,  
    OLECHAR* pchURLIn,  
    OLECHAR** ppchURLOut);
```  
  
### <a name="parameters"></a>参数  
 `dwTranslate`  
 留待将来使用。  
  
 `pchURLIn`  
 通过 Internet Explorer 或表示要转换的 URL 的 MSHTML 提供的字符串的地址。  
  
 `ppchURLOut`  
 接收已翻译的 URL 地址的字符串指针的地址。 主机分配的缓冲区，使用任务内存分配器。 此参数的内容始终应初始化为**NULL**，即使该 URL 不会进行转换或该方法将失败。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果该 URL 已翻译， **S_FALSE**如果不转换该 URL，或 OLE 定义的错误代码是否发生了错误。  
  
### <a name="remarks"></a>备注  
 重写`OnTranslateUrl`以响应`TranslateUrl`从 Microsoft Web 浏览器控件的通知。 请参阅[IDocHostUIHandler::TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameonupdateuia--chtmlviewonupdateui"></a><a name="onupdateui"></a>CHtmlView::OnUpdateUI  
 通知主机命令状态已更改。  
  
```  
virtual HRESULT OnUpdateUI();
```  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果成功，或以其他方式 OLE 定义的错误代码。  
  
### <a name="remarks"></a>备注  
 主机应更新工具栏按钮的状态。 无论从返回的值调用此方法`ShowUI`。 重写`OnUpdateUI`以响应`UpdateUI`从 Microsoft Web 浏览器控件的通知。  
  
##  <a name="a-nameonvisiblea--chtmlviewonvisible"></a><a name="onvisible"></a>CHtmlView::OnVisible  
 Webbrowser 控件中的窗口应显示或隐藏时，将由框架调用此成员函数。  
  
```  
virtual void OnVisible(BOOL bVisible);
```  
  
### <a name="parameters"></a>参数  
 `bVisible`  
 如果对象是可见，则为非零，则为或。  
  
### <a name="remarks"></a>备注  
 这样，对象控制主机窗口具有相同的表现的 Internet Explorer 窗口的行为。  
  
##  <a name="a-nameputpropertya--chtmlviewputproperty"></a><a name="putproperty"></a>CHtmlView::PutProperty  
 调用此成员函数可设置与给定对象关联的属性。  
  
```  
void PutProperty(
    LPCTSTR lpszProperty,  
    const VARIANT& vtValue);

 
void PutProperty(
    LPCTSTR lpszPropertyName,  
    double dValue);

 
void PutProperty(
    LPCTSTR lpszPropertyName,  
    long lValue);

 
void PutProperty(
    LPCTSTR lpszPropertyName,  
    LPCTSTR lpszValue);

 
void PutProperty(
    LPCTSTR lpszPropertyName,  
    short nValue);
```  
  
### <a name="parameters"></a>参数  
 `lpszProperty`  
 包含要设置的属性的字符串。  
  
 *vtValue*  
 该属性的新值由`lpszProperty`。  
  
 *lpszPropertyName*  
 指向包含要设置的属性的名称的字符串的指针。  
  
 *dValue*  
 属性的新值。  
  
 `lValue`  
 属性的新值。  
  
 `lpszValue`  
 指向包含该属性的新值的字符串的指针。  
  
 `nValue`  
 属性的新值。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namequeryformscommanda--chtmlviewqueryformscommand"></a><a name="queryformscommand"></a>CHtmlView::QueryFormsCommand  
 查询由用户界面事件生成的一个或多个命令的状态。  
  
```  
HRESULT QueryFormsCommand(
    DWORD dwCommandID,  
    BOOL* pbSupported,  
    BOOL* pbEnabled,  
    BOOL* pbChecked);
```  
  
### <a name="parameters"></a>参数  
 `dwCommandID`  
 要查询的命令标识符。  
  
 *pbSupported*  
 一个指向**BOOL**指定如果命令 (由标识`dwCommandID`) 支持。 如果为 TRUE，则支持该命令;否则为 FALSE。  
  
 `pbEnabled`  
 一个指向**BOOL**指定如果命令 (由标识`dwCommandID`) 启用。 如果为 TRUE，则支持该命令;否则为 FALSE。  
  
 *pbChecked*  
 一个指向**BOOL**指定如果命令 (由标识`dwCommandID`) 检查。 如果为 TRUE，则支持该命令;否则为 FALSE。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。 有关可能的值的完整列表，请参阅[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 `QueryFormsCommand`实现的行为[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491)方法。  
  
##  <a name="a-namequerystatuswba--chtmlviewquerystatuswb"></a><a name="querystatuswb"></a>CHtmlView::QueryStatusWB  
 调用此成员函数来查询命令状态。  
  
```  
OLECMDF QueryStatusWB(OLECMDID cmdID) const;  
```  
  
### <a name="parameters"></a>参数  
 `cmdID`  
 [OLECMDID](http://msdn.microsoft.com/library/windows/desktop/ms691264)调用方需要其状态信息的命令的值。  
  
### <a name="return-value"></a>返回值  
 地址[OLECMDF](http://msdn.microsoft.com/library/windows/desktop/ms695237)接收命令的状态的值。  
  
### <a name="remarks"></a>备注  
 `QueryStatusWB`实现的行为[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491)方法。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namerefresha--chtmlviewrefresh"></a><a name="refresh"></a>CHtmlView::Refresh  
 重新加载 URL 或 web 浏览器当前显示的文件。  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>备注  
 **刷新**不包含任何参数用于设置刷新级别。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namerefresh2a--chtmlviewrefresh2"></a><a name="refresh2"></a>CHtmlView::Refresh2  
 重新加载当前显示 Internet explorer 中的文件。  
  
```  
void Refresh2(int nLevel);
```  
  
### <a name="parameters"></a>参数  
 `nLevel`  
 指定刷新级别的变量的地址。 可能的变量中定义[RefreshConstants](https://msdn.microsoft.com/library/aa768363.aspx)，请在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 与不同[刷新](#refresh)，`Refresh2`包含一个参数，指定刷新级别。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetaddressbara--chtmlviewsetaddressbar"></a><a name="setaddressbar"></a>CHtmlView::SetAddressBar  
 调用该成员函数以显示或隐藏 Internet Explorer 对象的地址栏中。  
  
```  
void SetAddressBar(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 非零值，显示地址栏;否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer。 如果使用 WebBrowser 控件使用此调用，它将返回没有错误，但它将忽略此调用。  
  
##  <a name="a-namesetfullscreena--chtmlviewsetfullscreen"></a><a name="setfullscreen"></a>CHtmlView::SetFullScreen  
 调用该成员函数以将 Internet Explorer 设置为任何一种全屏幕或正常窗口模式。  
  
```  
void SetFullScreen(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 全屏显示模式，则为非零值否则为零。  
  
### <a name="remarks"></a>备注  
 在全屏幕模式下，Internet 资源管理器主窗口已最大化和隐藏状态栏、 工具栏、 菜单栏和标题栏。  
  
 适用于 Internet Explorer。 如果使用 WebBrowser 控件使用此调用，它将返回没有错误，但它将忽略此调用。  
  
##  <a name="a-namesetheighta--chtmlviewsetheight"></a><a name="setheight"></a>CHtmlView::SetHeight  
 调用此成员函数可设置 Internet 资源管理器主窗口的高度。  
  
```  
void SetHeight(long nNewValue);
```  
  
### <a name="parameters"></a>参数  
 `nNewValue`  
 以像素为单位，在主窗口的高度。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetlefta--chtmlviewsetleft"></a><a name="setleft"></a>CHtmlView::SetLeft  
 设置 Internet Explorer 主窗口的水平位置。  
  
```  
void SetLeft(long nNewValue);
```  
  
### <a name="parameters"></a>参数  
 `nNewValue`  
 主窗口的左边缘屏幕坐标。  
  
##  <a name="a-namesetmenubara--chtmlviewsetmenubar"></a><a name="setmenubar"></a>CHtmlView::SetMenuBar  
 调用该成员函数以显示或隐藏 Internet Explorer 菜单栏。  
  
```  
void SetMenuBar(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 非零值，显示菜单栏。否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer。 如果使用 WebBrowser 控件使用此调用，它将返回没有错误，但它将忽略此调用。  
  
##  <a name="a-namesetofflinea--chtmlviewsetoffline"></a><a name="setoffline"></a>CHtmlView::SetOffline  
 调用此成员函数可设置一个值，该值指示 web 浏览器控件当前在脱机模式下操作。  
  
```  
void SetOffline(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 非零值，从本地缓存中; 读取否则为零。  
  
### <a name="remarks"></a>备注  
 在脱机模式下，浏览器中从本地缓存，而不是源文档中读取的 HTML 页。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetregisterasbrowsera--chtmlviewsetregisterasbrowser"></a><a name="setregisterasbrowser"></a>CHtmlView::SetRegisterAsBrowser  
 调用此成员函数可设置一个值，该值指示是否将 WebBrowser 控件注册为目标的名称解析的顶层浏览器。  
  
```  
void SetRegisterAsBrowser(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 确定是否将 Internet Explorer 注册为顶层浏览器。 如果非零值，作为顶层浏览器; 注册的 web 浏览器如果为零，它不是顶层浏览器。 默认值为&0;。  
  
### <a name="remarks"></a>备注  
 顶层浏览器是作为默认浏览器的注册表中设置浏览器。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetregisterasdroptargeta--chtmlviewsetregisterasdroptarget"></a><a name="setregisterasdroptarget"></a>CHtmlView::SetRegisterAsDropTarget  
 调用此成员函数可设置一个值，该值指示是否将 WebBrowser 控件注册为放置目标进行导航。  
  
```  
void SetRegisterAsDropTarget(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 确定是否 web 浏览器控件注册为放置目标进行导航。 如果非零，将对象注册为放置目标;如果为零，它不是拖放目标。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetsilenta--chtmlviewsetsilent"></a><a name="setsilent"></a>CHtmlView::SetSilent  
 调用此成员函数可设置一个值，该值指示是否可以显示任何对话框。  
  
```  
void SetSilent(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 如果非零，则不会显示对话框;如果为零，将显示对话框。 默认值为&0;。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetstatusbara--chtmlviewsetstatusbar"></a><a name="setstatusbar"></a>CHtmlView::SetStatusBar  
 调用该成员函数以显示状态栏。  
  
```  
void SetStatusBar(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 如果状态栏可见，则为非否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer。 如果使用 WebBrowser 控件使用此调用，它将返回没有错误，但它将忽略此调用。  
  
##  <a name="a-namesettheatermodea--chtmlviewsettheatermode"></a><a name="settheatermode"></a>CHtmlView::SetTheaterMode  
 调用此成员函数可设置一个值，该值指示 web 浏览器控件是否处于影院模式。  
  
```  
void SetTheaterMode(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 将 WebBrowser 控件设置为影院模式，则为非零值否则为零。 默认值为&0;。  
  
### <a name="remarks"></a>备注  
 影院模式的 web 浏览器时，浏览器主窗口填满整个屏幕，会出现与导航工具的最小集一个工具栏，和状态栏显示在屏幕的右上角中。  
  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesettoolbara--chtmlviewsettoolbar"></a><a name="settoolbar"></a>CHtmlView::SetToolBar  
 调用该成员函数以显示或隐藏 Internet Explorer 工具栏。  
  
```  
void SetToolBar(int nNewValue);
```  
  
### <a name="parameters"></a>参数  
 `nNewValue`  
 指示是否显示工具栏。 如果工具栏显示，则非零值否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer。 如果使用 WebBrowser 控件使用此调用，它将返回没有错误，但它将忽略此调用。  
  
##  <a name="a-namesettopa--chtmlviewsettop"></a><a name="settop"></a>CHtmlView::SetTop  
 调用此成员函数以设置 WebBrowser 控件的内部上边缘与其容器上的边缘之间的距离  
  
```  
void SetTop(long nNewValue);
```  
  
### <a name="parameters"></a>参数  
 `nNewValue`  
 在主窗口的上边缘的屏幕坐标。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetvisiblea--chtmlviewsetvisible"></a><a name="setvisible"></a>CHtmlView::SetVisible  
 调用此成员函数可设置 WebBrowser 控件的可见性状态。  
  
```  
void SetVisible(BOOL bNewValue);
```  
  
### <a name="parameters"></a>参数  
 `bNewValue`  
 如果控件是可见的则非零值否则为零。  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetwidtha--chtmlviewsetwidth"></a><a name="setwidth"></a>CHtmlView::SetWidth  
 设置 Internet Explorer 主窗口的宽度。  
  
```  
void SetWidth(long nNewValue);
```  
  
### <a name="parameters"></a>参数  
 `nNewValue`  
 以像素为单位的 Internet 资源管理器主窗口的宽度。  
  
##  <a name="a-namestopa--chtmlviewstop"></a><a name="stop"></a>CHtmlView::Stop  
 调用该成员函数以取消所有挂起的导航或下载操作并停止所有动态页元素，如背景声音和动画。  
  
```  
void Stop();
```  
  
### <a name="remarks"></a>备注  
 适用于 Internet Explorer 和 WebBrowser。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 MFCIE](../../visual-cpp-samples.md)   
 [CFormView 类](../../mfc/reference/cformview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx)


