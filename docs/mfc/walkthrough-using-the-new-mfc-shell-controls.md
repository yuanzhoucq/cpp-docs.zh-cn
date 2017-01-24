---
title: "演练：使用新的 MFC Shell 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shell 控件 (MFC)"
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：使用新的 MFC Shell 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在本演练中，您将创建一个与文件资源管理器类似的应用程序。  您将要创建一个包含两个窗格的窗口。  左窗格将包含一个将以层次结构视图显示您的桌面的 [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) 对象。  右窗格将包含一个显示左窗格中选定的文件夹中的文件的 [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) 对象。  
  
## 系统必备  
 本演练假定您已经建立 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 以便使用 “常规开发设置”。  如果您使用一个不同的开发设置，在本演练中使用的一些[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 窗口默认情况下可能不会被显示。  
  
### 使用 MFC 应用程序向导创建一个新的 MFC 应用程序  
  
1.  使用  “MFC 应用程序向导”创建 MFC 应用程序。  想要运行向导，请在  “文件”菜单中，选择  “新建”，然后选择  “项目”。  将显示  “新建项目”对话框。  
  
2.  在  “新建项目”对话框中，展开在  “项目类别”窗格里的  “Visual C\+\+”节点，然后选择  “MFC”。  然后，在  “模板”窗格中，选择  “MFC 应用程序”。  为项目键入一个名字，例如，`MFCShellControls`，单击“确定”。  将显示  “MFC 应用程序向导”。  
  
3.  在  “MFC 应用程序向导”对话框中，单击  “下一步”。  将显示  “应用程序类型”窗格。  
  
4.  在  “应用程序类型”窗格，  “应用程序类型”下，清除  “选项卡式文档”选项。  然后，选择  “单文本”，然后选择  “文本\/视图架构支持”。  在  “项目类型”下，选择  “Visual Studio”，从  “视觉样式和颜色”下拉列表中选择的  Office 2007（蓝色主题）。  保留所有其他选项。  单击  “下一步”以显示  “复合文本支持”窗格。  
  
5.  在  “复合文本支持”窗格上，选择  “无”。  单击  “下一步”以显示  “文本模块字符串”窗格。  
  
6.  不要对  "文本模块字符串"窗格做任何改变。  单击  “下一步”以显示  “数据库支持”窗格。  
  
7.  在  “数据库支持”窗格，选择  “无”，因为该应用程序不使用数据库。  单击  “下一步”以显示  “用户界面特性”窗格。  
  
8.  在  “用户界面特性”窗格，确保  “使用菜单栏和工具栏”选项已选上。  保留所有其他选项。  单击  “下一步”以显示  “高级特性”窗格。  
  
9. 在  “高级特性”窗格，  “高级特性”下，仅选择  “Active 控件”和  “常见的控件清单”。  在“高级框架窗格” 仅选择  “导航窗格”选项。  这将引起向导用已嵌入的 `CMFCShellTreeCtrl` 在窗口左侧创建窗格。  单击  “下一步”以显示  “生成类”窗格。  
  
10. 我们不准备对  “生成类”窗格做任何改变。  因此，单击  “完成”以建立新的MFC项目。  
  
11. 通过生成并运行应用程序来验证该应用程序已成功创建。  若要生成应用程序，请从  “创建”菜单上选择  “建立解决方案”。  如果成功生成了该应用程序，请选择  “调试”菜单上的  “开始调试”来运行该应用程序。  
  
     该向导会自动创建以  “文件夹”视图和 **Calendar** “日历”视图都具有一个标准的菜单栏，一个标准工具栏，一个标准状态栏和一个在窗口左边的Outlook栏的应用程序。  
  
### 将 shell 列表控件添加到文档视图  
  
1.  在本节中，你将添加一个 `CMFCShellListCtrl` 例子到向导创建的视图中  通过在 “解决方案资源管理器”中双击 MFCShellControlsView.h 来打开视图头文件。  
  
     定位头文件顶部附近的 `#pragma once` 指令。  紧随其下为 `CMFCShellListCtrl` 添加包括头文件的代码:  
  
    ```  
    #include <afxShellListCtrl.h>  
    ```  
  
     现在添加一个 `CMFCShellListCtrl`类型的成员变量。  首先，定位头文件中的以下注释：  
  
    ```  
    // Generated message map functions  
    ```  
  
     紧随上的注释添加以下代码：  
  
    ```  
    private:  
        CMFCShellListCtrl m_wndList;  
    ```  
  
2.  “MFC应用程序向导”已经在 `CMainFrame` 类中创建了一个 `CMFCShellTreeCtrl` 对象，但是它是一个保护成员。  我们将在稍后访问该对象。  因此，此时创建它的访问器。  通过在 “解决方案资源管理器”中双击它来打开 MainFrm.h 头文件。  定位到以下注释：  
  
    ```  
    // Attributes  
    ```  
  
     紧随其下，添加以下方法声明：  
  
    ```  
    public:  
        CMFCShellTreeCtrl& GetShellTreeCtrl();  
    ```  
  
     接下来，通过在 “解决方案资源管理器”中双击它来打开 MainFrm.cpp 资源文件。  在该文件底部，添加以下的方法定义：  
  
    ```  
    CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()  
    {  
        return m_wndTree;  
    }  
    ```  
  
3.  现在我们更新 `CMFCShellControlsView` 类来处理 **WM\_CREATE** 窗口信息。  打开 MFCShellControlsView.h 头文件并单击此代码行：  
  
    ```  
    class CMFCShellControlsView : public CView  
    ```  
  
     接下来，在  “属性”窗口中，单击  “消息”图标。  向下滚动直到找到 **WM\_CREATE** 消息。  从下拉列表旁 **WM\_CREATE**，选择 **\<添加\> OnCreate**。  这将为我们创建消息处理程序并自动更新 MFC 消息映射。  
  
     在 `OnCreate` 方法中我们现在将创建 `CMFCShellListCtrl` 对象。  在 MFCShellControlsView.cpp 资源文件中找到 `OnCreate` 方法定义，并且用以下代码代替它的实现：  
  
    ```  
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)  
    {  
        if (CView::OnCreate(lpCreateStruct) == -1)  
            return -1;  
  
        CRect rectDummy (0, 0, 0, 0);  
        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,  
            rectDummy, this, 1);  
  
        return 0;  
    }  
    ```  
  
4.  重复上述步骤，除了 **WM\_SIZE** 消息。  这将导致重绘你的应用程序视图，只要用户更改了应用程序窗口的大小。  用下面的代码替换 `OnSize` 方法定义：  
  
    ```  
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)  
    {  
        CView::OnSize(nType, cx, cy);  
        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,  
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);  
    }  
    ```  
  
5.  最后一步是使用 [CMFCShellTreeCtrl::SetRelatedList](../Topic/CMFCShellTreeCtrl::SetRelatedList.md) 方法连接 `CMFCShellTreeCtrl` 和 `CMFCShellListCtrl`。  调用该方法后， `CMFCShellListCtrl` 将自动显示在`CMFCShellTreeCtrl` 选择的条目内容。  我们将用 `OnActivateView` 方法实现，该方法是对 [CView::OnActivateView](../Topic/CView::OnActivateView.md) 的重写。  
  
     在 MFCShellControlsView.h 头文件的 `CMFCShellControlsView` 类定义中，添加以下方法声明：  
  
    ```  
    protected:  
        virtual void OnActivateView(BOOL bActivate,  
            CView* pActivateView,  
            CView* pDeactiveView);  
    ```  
  
     接下来，添加此方法的定义到 MFCShellControlsView.cpp 源文件中：  
  
    ```  
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,  
        CView* pActivateView,  
        CView* pDeactiveView)   
    {  
        if (bActivate && AfxGetMainWnd() != NULL)  
        {  
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);  
        }  
  
        CView::OnActivateView(bActivate, pActivateView, pDeactiveView);  
    }  
    ```  
  
     因为我们从 `CMainFrame` 类调用方法，所以我们必须在 MFCShellControlsView.cpp 资源文件的顶部添加一个 `#include` 指令。  
  
    ```  
    #include "MainFrm.h"  
    ```  
  
6.  通过生成并运行应用程序来验证该应用程序已成功创建。  若要生成应用程序，请从  “创建”菜单上选择  “建立解决方案”。  如果成功生成了该应用程序，请选择 “调试”菜单上的 **“开始调试”** 来运行该应用程序。  
  
     你现在应该在视图窗格看到从 `CMFCShellTreeCtrl` 选择的项目细节。  当你单击 `CMFCShellTreeCtrl` 中的一个节点时，  `CMFCShellListCtrl` 将自动更新。  同样，如果你在 `CMFCShellListCtrl` 双击一个文件夹， `CMFCShellTreeCtrl` 应自动更新。  
  
     右击树控件或在列表控件的任意项。  请注意可以获得相同的上下文菜单，如同你是在使用真正的文件资源管理器。  
  
## 后续步骤  
  
-   向导创建一个具有  “文件夹”窗格和  “日历”窗格的 Outlook 栏。  在资源管理器窗口中具有  “日历”窗格可能没有任何意义。  因此，现在请移除该窗格。  
  
-   `CMFCShellListCtrl` 以不同模式查看文件，例如  “大图标”，  “小图标”， “列表”和  “详细信息”。  更新应用程序以实现此功能。  提示：请参阅 [Visual C\+\+ 示例](../top/visual-cpp-samples.md)。  
  
## 请参阅  
 [演练](../mfc/walkthroughs-mfc.md)