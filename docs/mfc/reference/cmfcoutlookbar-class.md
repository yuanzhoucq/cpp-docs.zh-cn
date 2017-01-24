---
title: "CMFCOutlookBar 类 | Microsoft Docs"
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
  - "CMFCOutlookBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCOutlookBar 类"
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
caps.latest.revision: 34
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCOutlookBar 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

具有 **导航窗格** 的可视外观的一个选项卡式窗格 Microsoft Outlook 2000 或 Outlook 2003\)。  `CMFCOutlookBar` 对象包含一个 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) 对象和一系列选项。  选项可以是 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) 对象或 `CWnd`派生的对象。  给用户，Outlook 栏显示为一系列按钮和显示区域。  当用户单击按钮时，相应的控件或按钮窗格中显示。  
  
## 语法  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|`CMFCOutlookBar::CMFCOutlookBar`|默认构造函数。|  
|`CMFCOutlookBar::~CMFCOutlookBar`|析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](../Topic/CMFCOutlookBar::AllowDestroyEmptyTabbedPane.md)|指定是否可以销毁一个空选项卡式窗格。  \(重写 [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../Topic/CBaseTabbedPane::AllowDestroyEmptyTabbedPane.md)。\)|  
|[CMFCOutlookBar::CanAcceptPane](../Topic/CMFCOutlookBar::CanAcceptPane.md)|确定另一个窗格是否可以停靠到 Outlook 栏窗格。  \(重写 CDockablePane::CanAcceptPane。\)|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](../Topic/CMFCOutlookBar::CanSetCaptionTextToTabName.md)|确定选项卡式窗格的声明是否显示文本的并且有效选项相同。  \(重写 [CBaseTabbedPane::CanSetCaptionTextToTabName](../Topic/CBaseTabbedPane::CanSetCaptionTextToTabName.md)。\)|  
|[CMFCOutlookBar::Create](../Topic/CMFCOutlookBar::Create.md)|创建 Outlook 栏控件。|  
|[CMFCOutlookBar::CreateCustomPage](../Topic/CMFCOutlookBar::CreateCustomPage.md)|创建自定义 Outlook 栏选项。|  
|`CMFCOutlookBar::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](../Topic/CMFCOutlookBar::DoesAllowDynInsertBefore.md)|确定用户是否可以将控件停靠栏位于 Outlook 栏的外边缘。|  
|[CMFCOutlookBar::FloatTab](../Topic/CMFCOutlookBar::FloatTab.md)|只有 \+ 当窗格当前位于一个可拆的选项，浮动窗格中，但。  \(重写 [CBaseTabbedPane::FloatTab](../Topic/CBaseTabbedPane::FloatTab.md)。\)|  
|[CMFCOutlookBar::GetButtonsFont](../Topic/CMFCOutlookBar::GetButtonsFont.md)|返回文本的字体在 Outlook 栏按钮的。|  
|[CMFCOutlookBar::GetTabArea](../Topic/CMFCOutlookBar::GetTabArea.md)|返回选项区域的大小和位置在 Outlook 栏。  \(重写 [CBaseTabbedPane::GetTabArea](../Topic/CBaseTabbedPane::GetTabArea.md)。\)|  
|`CMFCOutlookBar::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCOutlookBar::IsMode2003](../Topic/CMFCOutlookBar::IsMode2003.md)|确定是否 Microsoft Office Outlook 2003 Outlook 栏类似于的行为 \(请参见"备注"\)。|  
|[CMFCOutlookBar::OnAfterAnimation](../Topic/CMFCOutlookBar::OnAfterAnimation.md)|使用动画，调用 [CMFCOutlookBarTabCtrl::SetActiveTab](../Topic/CMFCOutlookBarTabCtrl::SetActiveTab.md) 在活动选项后设置。|  
|[CMFCOutlookBar::OnBeforeAnimation](../Topic/CMFCOutlookBar::OnBeforeAnimation.md)|使用动画，调用 [CMFCOutlookBarTabCtrl::SetActiveTab](../Topic/CMFCOutlookBarTabCtrl::SetActiveTab.md) 在选项卡页之前设置为有效的选项。|  
|[CMFCOutlookBar::OnScroll](../Topic/CMFCOutlookBar::OnScroll.md)|调用由框架，如果 Outlook 栏上移或下移。|  
|[CMFCOutlookBar::RemoveCustomPage](../Topic/CMFCOutlookBar::RemoveCustomPage.md)|移除自定义 Outlook 栏选项。|  
|[CMFCOutlookBar::SetButtonsFont](../Topic/CMFCOutlookBar::SetButtonsFont.md)|设置文本的字体在 Outlook 栏按钮的。|  
|[CMFCOutlookBar::SetMode2003](../Topic/CMFCOutlookBar::SetMode2003.md)|指定是否 Outlook 2003 Outlook 栏类似于的行为 \(请参见"备注"\)。|  
  
## 备注  
 有关 Outlook 栏的示例，请参见 [OutlookDemo 示例：MFC OutlookDemo 应用程序](../../top/visual-cpp-samples.md)。  
  
## 实现 Outlook 栏  
 若要使用 `CMFCOutlookBar` 控件在您的应用程序，请执行以下步骤：  
  
1.  嵌入一 `CMFCOutlookBar` 对象向主框架窗口选件类。  
  
    ```  
    class CMainFrame : public CMDIFrameWnd  
     { ...  
         CMFCOutlookBar         m_wndOutlookBar;  
         CMFCOutlookBarPane     m_wndOutlookPane;  
    ... };  
    ```  
  
2.  在处理在主框架中的 `WM_CREATE` 消息，请调用 [CMFCOutlookBar::Create](../Topic/CMFCOutlookBar::Create.md) 方法创建 Outlook 栏选项卡控件。  
  
    ```  
    m_wndOutlookBar.Create (_T("Shortcuts"), this, CRect (0, 0, 100, 100), ID_VIEW_OUTLOOKBAR, WS_CHILD | WS_VISIBLE | CBRS_LEFT);  
    ```  
  
3.  使用 [CBaseTabbedPane::GetUnderlyingWindow](../Topic/CBaseTabbedPane::GetUnderlyingWindow.md)，获取指向基础 `CMFCOutlookBarTabCtrl`。  
  
    ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();  
    ```  
  
4.  创建包含按钮的每个选项卡的 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) 对象。  
  
    ```  
    m_wndOutlookPane.Create (&m_wndOutlookBar, AFX_DEFAULT_TOOLBAR_STYLE, ID_OUTLOOK_PANE_GENERAL, AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);  
    // make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking (CBRS_ALIGN_ANY);  
    // add buttons  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_MAINFRAME), "About", ID_APP_ABOUT);  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON), "Open", ID_FILE_OPEN);  
    ```  
  
5.  调用 [CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md) 添加每个新选项。  设置 `bDetachable` 参数传递给 `FALSE` 使页非可拆。  或者，使用 [CMFCOutlookBarTabCtrl::AddControl](../Topic/CMFCOutlookBarTabCtrl::AddControl.md) 添加可拆的页。  
  
    ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);   
    ```  
  
6.  若要添加 `CWnd`派生的控件 \(例如，[CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)\) 作为选项卡上，创建控件并调用 [CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md) 添加到 Outlook 栏。  
  
> [!NOTE]
>  您应使用唯一控件 ID 为每 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) 对象以及每 `CWnd`派生的对象。  
  
 动态添加或删除新页面运行时、使用 [CMFCOutlookBar::CreateCustomPage](../Topic/CMFCOutlookBar::CreateCustomPage.md) 和 [CMFCOutlookBar::RemoveCustomPage](../Topic/CMFCOutlookBar::RemoveCustomPage.md)。  
  
## Outlook 2003 架构  
 在 Outlook 2003 模式下，选项按钮确定在 Outlook 栏窗格底部。  当没有足够的空间显示按钮时，将会类似于工具栏的区域显示为图标。窗格底部。  
  
 使用 [CMFCOutlookBar::SetMode2003](../Topic/CMFCOutlookBar::SetMode2003.md) 启动 Outlook 2003 架构。  使用 [CMFCOutlookBarTabCtrl::SetToolbarImageList](../Topic/CMFCOutlookBarTabCtrl::SetToolbarImageList.md) 设置包含该图标在 Outlook 栏的底部显示的位图。  必须用制表索引按位图的图标。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
  
## 要求  
 **标头：** afxoutlookbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md)