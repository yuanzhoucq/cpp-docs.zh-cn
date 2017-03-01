---
title: "CMFCOutlookBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBar class
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ff58cf786e4979d64aa2b5d7ad4d1a32b96bec3d
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar 类
在 Microsoft Outlook 2000 或 Outlook 2003 中具有 **“导航窗格”** 可视外观的选项卡式窗格。 `CMFCOutlookBar`对象包含[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)对象和一系列选项卡。 这些选项卡可以[CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)对象或`CWnd`-派生的对象。 对于用户，Outlook 栏显示为一系列按钮和一个显示区域。 用户单击按钮时，将显示相应控件或按钮窗格。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCOutlookBar::CMFCOutlookBar`|默认构造函数。|  
|`CMFCOutlookBar::~CMFCOutlookBar`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可销毁一个空的选项卡式的窗格。 (重写[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane)。)|  
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|确定是否可以到 Outlook 栏窗格停靠的另一窗格。 （覆盖 CDockablePane::CanAcceptPane。）|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|确定选项卡式窗格的标题是否为活动选项卡显示相同的文本。 (重写[CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname)。)|  
|[CMFCOutlookBar::Create](#create)|创建 Outlook 栏控件。|  
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|创建自定义 Outlook 栏选项卡。|  
|`CMFCOutlookBar::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|确定用户是否可以将 Outlook 栏的外边缘处的控件条固定。|  
|[CMFCOutlookBar::FloatTab](#floattab)|仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。 (重写[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。)|  
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|返回上的 Outlook 栏按钮的文本的字体。|  
|[CMFCOutlookBar::GetTabArea](#gettabarea)|返回的大小和位置的选项卡区域在 Outlook 栏上。 (重写[CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea)。)|  
|`CMFCOutlookBar::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCOutlookBar::IsMode2003](#ismode2003)|确定是否 Outlook 栏的行为类似于是，Microsoft Office Outlook 2003 （请参见备注）。|  
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|由调用[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)使用动画设置活动选项卡后。|  
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|由调用[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)前一个选项卡页设置为活动选项卡使用的动画。|  
|[CMFCOutlookBar::OnScroll](#onscroll)|如果 Outlook 栏向上或向下滚动，由框架调用。|  
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|删除自定义 Outlook 栏选项卡。|  
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|设置上的 Outlook 栏按钮的文本的字体。|  
|[CMFCOutlookBar::SetMode2003](#setmode2003)|指定是否将 Outlook 栏的行为模拟的 Outlook 2003 （请参见备注）。|  
  
## <a name="remarks"></a>备注  
 Outlook 栏的示例，请参阅[OutlookDemo 示例︰ MFC OutlookDemo 应用程序](../../visual-cpp-samples.md)。  
  
## <a name="implementing-the-outlook-bar"></a>实现 Outlook 栏  
 若要在应用程序中使用 `CMFCOutlookBar` 控件，请执行以下步骤：  
  
1.  将 `CMFCOutlookBar` 对象嵌入主框架窗口类。  
  
 ```  
    class CMainFrame : public CMDIFrameWnd  
 { ...  
    CMFCOutlookBar m_wndOutlookBar;  
    CMFCOutlookBarPane m_wndOutlookPane;  
 ... };  
 ```  
2.  在处理时`WM_CREATE`消息在主框架中，调用[CMFCOutlookBar::Create](#create)方法来创建 Outlook 栏选项卡控件。  
  
 ```  
    m_wndOutlookBar.Create (_T("Shortcuts"),
    this,
    CRect (0,
    0,
    100,
    100),
    ID_VIEW_OUTLOOKBAR,
    WS_CHILD | WS_VISIBLE | CBRS_LEFT);

 ```  
3.  获取对基础指针`CMFCOutlookBarTabCtrl`通过[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)。  
  
 ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();

 ```  
4.  创建[CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)每个选项卡包含按钮的对象。  
  
 ```  
    m_wndOutlookPane.Create (&m_wndOutlookBar,
    AFX_DEFAULT_TOOLBAR_STYLE,
    ID_OUTLOOK_PANE_GENERAL,
    AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);
*// make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking (CBRS_ALIGN_ANY);
*// add buttons  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_MAINFRAME), "About",
    ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON), "Open",
    ID_FILE_OPEN);

 ```  
5.  调用[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)添加每个新选项卡。 设置`bDetachable`参数`FALSE`将页面作为非可拆分。 或者，使用[CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol)以添加可插拔的页面。  
  
 ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1,
    TRUE);

 ```  
6.  若要添加`CWnd`-派生的控件 (例如， [CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)) 作为一个选项卡，创建控件并将调用[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)将其添加到 Outlook 栏。  
  
> [!NOTE]
>  应为每个使用唯一的控件 Id [CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)对象对于每个`CWnd`-派生的对象。  
  
 若要动态添加或删除新页能够在运行时，使用[CMFCOutlookBar::CreateCustomPage](#createcustompage)和[CMFCOutlookBar::RemoveCustomPage](#removecustompage)。  
  
## <a name="outlook-2003-mode"></a>Outlook 2003 模式  
 在 Outlook 2003 模式下，Outlook 栏窗格的底部放置选项卡按钮。 当没有足够的空间来显示按钮时，它们显示为窗格中的底部工具栏类似区域中的图标。  
  
 使用[CMFCOutlookBar::SetMode2003](#setmode2003)若要启用 Outlook 2003 模式。 使用[CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist)设置包含在 Outlook 栏底部显示的图标的位图。 位图中的图标，必须按 tab 键索引进行排序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxoutlookbar.h  
  
##  <a name="a-nameallowdestroyemptytabbedpanea--cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::AllowDestroyEmptyTabbedPane  
 指定是否可销毁一个空的选项卡式的窗格。  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可销毁一个空的选项卡式的窗格;否则为`FALSE`。 默认实现始终返回`TRUE`。  
  
### <a name="remarks"></a>备注  
 如果不能被销毁空的选项卡式窗格中，框架会改为隐藏它。  
  
##  <a name="a-namecanacceptpanea--cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane  
 确定是否可以到 Outlook 栏窗格停靠的另一窗格。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向要停靠此窗格中的另一个窗格的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果另一个窗格可以停靠到 Outlook 栏窗格;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果在 Outlook 2003 模式下的 Outlook 栏，停靠不支持，因此返回值是`FALSE`。  
  
 如果`pBar`参数是`NULL`，此方法返回`FALSE`。  
  
 否则，此方法的行为与基类方法[cbasepane:: Canacceptpane](../../mfc/reference/cbasepane-class.md#canacceptpane)以外，即使未启用停靠，Outlook 栏仍可以启用要停靠在其上的另一个 Outlook 栏。  
  
##  <a name="a-namecansetcaptiontexttotabnamea--cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetCaptionTextToTabName  
 确定选项卡式窗格的标题是否为活动选项卡显示相同的文本。  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗口标题栏 Outlook 将自动设置为活动选项卡; 的文本否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname)启用或禁用此功能。  
  
 在 Outlook 2003 模式下，始终启用此设置。  
  
##  <a name="a-namecreatea--cmfcoutlookbarcreate"></a><a name="create"></a>CMFCOutlookBar::Create  
 创建 Outlook 栏控件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszCaption`  
 指定的窗口标题。  
  
 [in] `pParentWnd`  
 指定指向父窗口的指针。 不得为 NULL。  
  
 [in] `rect`  
 指定 outlook 栏的大小和位置以像素为单位。  
  
 [in] `nID`  
 指定控件 id。 必须不同于其他控件在应用程序中使用的 Id。  
  
 [in] `dwStyle`  
 指定所需的控件栏样式。 有关可能的值，请参阅[窗口样式](../../mfc/reference/window-styles.md)。  
  
 [in] `dwControlBarStyle`  
 指定的特殊库定义样式。  
  
 [in] `pContext`  
 创建上下文。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CMFCOutlookBar`两个步骤中的对象。 第一次调用构造函数中，，然后调用`Create`，它创建 outlook 栏控件并将其附加到`CMFCOutlookBar`对象。  
  
 请参阅[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)有关可用的库定义样式，通过指定列表`dwControlBarStyle`。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Create`方法`CMFCOutlookBar`类。 此代码段属于[Outlook 多视图示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews #&1;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews #&2;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]  
  
##  <a name="a-namecreatecustompagea--cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a>CMFCOutlookBar::CreateCustomPage  
 创建自定义 Outlook 栏选项卡。  
  
```  
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,  
    BOOL bActivatePage=TRUE,  
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,  
    BOOL bEnableTextLabels=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszPageName`  
 页标签。  
  
 [in] `bActivatePage`  
 如果`TRUE`，页上将变为活动状态时创建。  
  
 [in] `dwEnabledDocking`  
 当分离页上指定已启用的停靠边 CBRS_ALIGN_ 标志的组合。  
  
 [in] `bEnableTextLabels`  
 如果`TRUE`，驻留在页面的按钮已启用的文本标签。  
  
### <a name="return-value"></a>返回值  
 指向新建页上，或`NULL`如果创建失败。  
  
### <a name="remarks"></a>备注  
 使用此方法以使用户能够创建自定义 Outlook 栏页。 您可以创建每个应用程序的最多为 100 页。 页面控件 Id 开始从 0xF000。 如果自定义 Outlook 栏页总数超过了 100，则创建将失败。  
  
 使用[CMFCOutlookBar::RemoveCustomPage](#removecustompage)若要删除自定义页面。  
  
##  <a name="a-namedoesallowdyninsertbeforea--cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertBefore  
 指定用户是否可以将位于的外边缘的 Outlook 栏窗格的停靠。  
  
```  
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>返回值  
 默认实现返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 框架将调用`DoesAllowDynInsertBefore`方法时将动态窗格停靠的位置，它查找。 如果该函数将返回`FALSE`，框架不允许在窗格中的外边缘的任何动态窗格的停靠。  
  
 通常情况下，创建 Outlook 栏为静态的非浮点控制。 你可以重写此函数在派生类中的，并返回`TRUE`来更改此行为。  
  
> [!NOTE]
>  因为动态窗格停靠时检查静态的停靠窗格的状态，应将动态窗格停靠后应尽可能的静态窗格。  
  
##  <a name="a-namefloattaba--cmfcoutlookbarfloattab"></a><a name="floattab"></a>CMFCOutlookBar::FloatTab  
 浮动窗格。  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向为浮点型窗格中的指针。  
  
 [in] `nTabID`  
 为浮动选项卡的从零开始索引。  
  
 [in] `dockMethod`  
 指定要用于使窗格浮动的方法。  有关详细信息，请参阅[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。  
  
 [in] `bHide`  
 `TRUE`若要在浮动; 之前隐藏窗格否则为`FALSE`。 与不同的是此方法的基类版本，此参数没有默认值。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中浮动。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法就像[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)之处在于它不支持的最后一个剩余选项卡上为 float 的 Outlook 栏控件。  
  
##  <a name="a-namegetbuttonsfonta--cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a>CMFCOutlookBar::GetButtonsFont  
 返回的文本的字体页上的 Outlook 栏按钮选项卡。  
  
```  
CFont* GetButtonsFont() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向用于页面按钮选项卡栏在 Outlook 中显示文本的字体对象的指针。  
  
### <a name="remarks"></a>备注  
 使用此函数可检索用于在 Outlook 页面按钮选项卡上显示文本的字体。 您可以通过调用上设置字体[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)。  
  
##  <a name="a-namegettabareaa--cmfcoutlookbargettabarea"></a><a name="gettabarea"></a>CMFCOutlookBar::GetTabArea  
 确定的大小和 Outlook 栏上的选项卡区域的位置。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rectTabAreaTop`  
 当函数返回时包含的大小和位置 （以工作区坐标表示） 的顶部的选项卡区域。  
  
 [out] `rectTabAreaBottom`  
 当函数返回时包含的大小和底部的选项卡区域的位置 （以工作区坐标表示）。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定停靠在目标窗格中的类型。 当框架确定用户拖动通过目标窗格中的选项卡区域停靠窗格中时，它将尝试将第一个窗格添加为目标窗格中的新选项卡。 否则，它将尝试为停靠在目标窗格中的相应侧的第一个窗格。 框架使用滑块来容纳附加停靠窗格中创建一个新的容器。  
  
 默认实现`GetTabArea`返回 Outlook 栏的整个客户端区域，如果 Outlook 栏静态; 即，如果 Outlook 栏不能浮动。 否则，它将返回页面按钮看顶部和底部的 Outlook 栏控件的区域。  
  
 重写此方法在派生类中的`CMFCOutlookBar`来更改此行为。  
  
##  <a name="a-nameismode2003a--cmfcoutlookbarismode2003"></a><a name="ismode2003"></a>CMFCOutlookBar::IsMode2003  
 指定是否将 Outlook 栏的行为模拟，Microsoft Office Outlook 2003。  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果 Outlook 栏正在运行 Microsoft Office 2003 模式，则为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 您可以启用此模式，通过使用[CMFCOutlookBar::SetMode2003](#setmode2003)。  
  
##  <a name="a-nameonafteranimationa--cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation  
 由调用[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)使用动画设置活动选项卡后。  
  
```  
virtual void OnAfterAnimation(int nPage);
```  
  
### <a name="parameters"></a>参数  
 [in] `nPage`  
 已活动的选项卡页的从零开始的索引。  
  
### <a name="remarks"></a>备注  
 设置活动选项卡上的视觉效果取决于您是否已启用动画。 有关详细信息，请参阅[CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation)。  
  
##  <a name="a-nameonbeforeanimationa--cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation  
 由调用[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)前一个选项卡页设置为活动选项卡使用的动画。  
  
```  
virtual BOOL OnBeforeAnimation(int nPage);
```  
  
### <a name="parameters"></a>参数  
 [in] `nPage`  
 要设置活动选项卡页的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果在设置新的活动选项卡上，应使用动画或`FALSE`是否应禁用动画。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonscrolla--cmfcoutlookbaronscroll"></a><a name="onscroll"></a>CMFCOutlookBar::OnScroll  
 如果 Outlook 栏向上或向下滚动，由框架调用。  
  
```  
virtual void OnScroll(BOOL bDown);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDown`  
 `TRUE`如果 Outlook 栏是向下滚动，或`FALSE`如果向上滚动。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameremovecustompagea--cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a>CMFCOutlookBar::RemoveCustomPage  
 删除自定义 Outlook 栏选项卡页。  
  
```  
BOOL RemoveCustomPage(
    UINT uiPage,  
    CMFCOutlookBarTabCtrl* pTargetWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiPage`  
 父 Outlook 窗口中的页的从零开始索引。  
  
 [in] `pTargetWnd`  
 Pointerto 父 Outlook 窗口。  
  
### <a name="return-value"></a>返回值  
 如果成功，则已删除自定义页上，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数可删除自定义页。 当该页面将删除其控件 ID 返回到可用 Id 池。  
  
 您必须提供一个指向[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)中页后，可以删除当前所驻留的对象。 请注意，用户可以不同的 Outlook 栏之间移动可拆分页，但自定义页有关的信息位于 Outlook 栏对象已调用[CMFCOutlookBar::CreateCustomPage](#createcustompage)。  
  
 使用[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)以获取指向 Outlook 窗口的指针。  
  
##  <a name="a-namesetbuttonsfonta--cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont  
 设置上的 Outlook 栏按钮的文本的字体。  
  
```  
void SetButtonsFont(
    CFont* pFont,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pFont`  
 指定新的字体。  
  
 [in] `bRedraw`  
 如果`TRUE`，Outlook 栏将重绘。  
  
### <a name="remarks"></a>备注  
 此方法用于设置 outlook 选项卡页的按钮上显示的文本的字体。  
  
##  <a name="a-namesetmode2003a--cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a>CMFCOutlookBar::SetMode2003  
 指定是否将 Outlook 栏的行为模拟的 Outlook 2003。  
  
```  
void SetMode2003(BOOL bMode2003=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bMode2003`  
 如果为 TRUE，则启用 Office 2003 模式下运行。  
  
### <a name="remarks"></a>备注  
 使用此函数以启用或禁用 Office 2003 模式下运行。 在此模式下，Outlook 栏具有附加工具栏与自定义按钮。 Outlook 栏的行为符合在 Microsoft Office 2003 Outlook 栏的行为。  
  
 默认情况下，此模式下处于禁用状态。  
  
> [!NOTE]
>  前必须调用此函数[CMFCOutlookBar::Create](#create)。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)

