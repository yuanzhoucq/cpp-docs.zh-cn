---
title: "演练： 使用新的 MFC Shell 控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: be882671da836f7d96f4c726753d6235735f363d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>演练：使用新的 MFC Shell 控件
在本演练中，您将创建一个类似文件资源管理器的应用程序。 你将创建包含两个窗格的窗口。 左窗格中将包含[CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md)的层次结构视图中显示你的桌面的对象。 右窗格中将包含[CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) ，在左窗格中选择的文件夹中显示的文件。  
  
## <a name="prerequisites"></a>系统必备  
 本演练假定你已设置了[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]使用**常规开发设置**。 如果某些使用不同的开发设置，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]默认情况下可能不会显示我们在本演练中使用的 windows。  
  
### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>若要使用 MFC 应用程序向导创建新的 MFC 应用程序  
  
1.  使用**MFC 应用程序向导**创建新的 MFC 应用程序。 若要从运行向导，**文件**菜单中选择**新建**，然后选择**项目**。 **新项目**将显示对话框。  
  
2.  在**新项目**对话框框中，展开**Visual c + +**中的节点**项目类型**窗格中，然后选择**MFC**。 然后，在**模板**窗格中，选择**MFC 应用程序**。 为项目键入名称，如`MFCShellControls`单击**确定**。 **MFC 应用程序向导**将显示。  
  
3.  在**MFC 应用程序向导**对话框中，单击**下一步**。 **应用程序类型**将显示窗格。  
  
4.  上**应用程序类型**窗格中，在**应用程序类型**，清除**选项卡式文档**选项。 接下来，选择**单个文档**和选择**文档/视图体系结构支持**。 下**项目样式**，选择**Visual Studio**，和从**视觉样式和颜色**下拉列表中，选择**Office 2007 （蓝色主题）**. 将所有其他选项保留原样。 单击**下一步**以显示**复合文档支持**窗格。  
  
5.  上**复合文档支持**窗格中，选择**无**。 单击**下一步**以显示**文档模板字符串**窗格。  
  
6.  不进行任何更改到**文档模板字符串**窗格。 单击**下一步**以显示**数据库支持**窗格。  
  
7.  上**数据库支持**窗格中，选择**无**因为此应用程序不使用数据库。 单击**下一步**以显示**用户界面功能**窗格。  
  
8.  上**用户界面功能**窗格中，请确保**使用菜单栏和工具栏**选项。 将所有其他选项保留原样。 单击**下一步**以显示**高级功能**窗格。  
  
9. 上**高级功能**窗格中，在**高级功能**，仅选择**ActiveX 控件**和**公共控件清单**。 下**高级框架窗格**，仅选择**导航窗格中**选项。 这将导致向导以创建到与窗口的左窗格中`CMFCShellTreeCtrl`已嵌入。 单击**下一步**以显示**生成的类**窗格。  
  
10. 我们将不会进行任何更改到**生成的类**窗格。 因此，请单击**完成**创建新的 MFC 项目。  
  
11. 验证应用程序已成功创建，可以通过生成并运行它。 若要从生成应用程序，**生成**菜单中选择**生成解决方案**。 如果成功生成了应用程序，通过选择运行该应用程序**启动调试**从**调试**菜单。  
  
     向导将自动创建的应用程序，并且在标准菜单栏、 标准工具栏、 标准状态栏，Outlook 栏与窗口左侧**文件夹**视图和**日历**视图.  
  
### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Shell 列表控件添加到文档视图  
  
1.  在本部分中，你将添加的实例`CMFCShellListCtrl`到向导创建的视图。 通过双击 MFCShellControlsView.h 中的打开视图标头文件**解决方案资源管理器**。  
  
     找到`#pragma once`指令的标头文件的顶部附近。 立即它下面添加以下代码以包括的头文件`CMFCShellListCtrl`:  
  
 ```  
    #include <afxShellListCtrl.h>  
 ```  
  
     现在添加的类型的成员变量`CMFCShellListCtrl`。 首先，在头文件中找到以下注释：  
  
 ' * / / 生成的消息映射函数  
 ```  
  
     Immediately above that comment add this code:  
  
 ```  
    私有： CMFCShellListCtrl m_wndList;  
 ```  
  
2.  The **MFC Application Wizard** already created a `CMFCShellTreeCtrl` object in the `CMainFrame` class, but it is a protected member. We will access this object later. Therefore, create an accessor for it now. Open the MainFrm.h header file by double-clicking it in the **Solution Explorer**. Locate the following comment:  
  
 ``` *// Attributes  
 ```  
  
     立即在其下添加以下方法声明：  
  
 ```  
    public: 
    CMFCShellTreeCtrl& GetShellTreeCtrl();

 ```  
  
     接下来，通过在中双击打开 MainFrm.cpp 源文件**解决方案资源管理器**。 在该文件的底部，将添加以下方法定义：  
  
 ```  
    CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()  
 {  
    return m_wndTree;  
 }  
 ```  
  
3.  现在我们更新`CMFCShellControlsView`类来处理**WM_CREATE** windows 消息。 打开 MFCShellControlsView.h 标头文件，然后单击此代码行：  
  
 ```  
    class CMFCShellControlsView : public CView  
 ```  
  
     接下来，在**属性**窗口中，单击**消息**图标。 向下滚动直到找到**WM_CREATE**消息。 从下拉列表下一步**WM_CREATE**，选择**\<添加 > OnCreate**。 这为我们将消息处理程序，并自动更新的 MFC 消息映射。  
  
     在`OnCreate`方法现在，我们将创建我们`CMFCShellListCtrl`对象。 查找`OnCreate`MFCShellControlsView.cpp 中的方法定义源文件，并将其实现替换为以下代码：  
  
 ```  
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)  
 {  
    if (CView::OnCreate(lpCreateStruct) == -1)  
    return -1;  
 
    CRect rectDummy (0,
    0,
    0,
    0);

    m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,  
    rectDummy,
    this,
    1);

 
    return 0;  
 }  
 ```  
  
4.  重复上述步骤，但对于**WM_SIZE**消息。 这将导致你的应用程序视图重绘每当用户更改应用程序窗口的大小。 将为定义`OnSize`方法替换为以下代码：  
  
 ```  
    void CMFCShellControlsView::OnSize(UINT nType,
    int cx,
    int cy)  
 {  
    CView::OnSize(nType,
    cx,
    cy);

    m_wndList.SetWindowPos(NULL, -1, -1,
    cx,
    cy,  
    SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);

 }  
 ```  
  
5.  最后一步是连接`CMFCShellTreeCtrl`和`CMFCShellListCtrl`通过使用对象[CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist)方法。 调用此方法之后,`CMFCShellListCtrl`将自动显示在选定的项的内容`CMFCShellTreeCtrl`。 我们将执行此操作`OnActivateView`方法，从重写[CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview)。  
  
     在 MFCShellControlsView.h 标头文件中，内部`CMFCShellControlsView`类声明中，添加以下方法声明：  
  
 ```  
    protected: 
    virtual void OnActivateView(BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView);

 ```  
  
     接下来，将此方法的定义添加到 MFCShellControlsView.cpp 源文件：  
  
 ```  
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView)   
 {  
    if (bActivate&& AfxGetMainWnd() != NULL)  
 {  
 ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);

 }  
 
    CView::OnActivateView(bActivate,
    pActivateView,
    pDeactiveView);

 }  
 ```  
  
     因为我们正在呼叫中的方法`CMainFrame`类，我们必须添加`#include`指令 MFCShellControlsView.cpp 源文件顶部：  
  
 ```  
    #include "MainFrm.h"  
 ```  
  
6.  验证应用程序已成功创建，可以通过生成并运行它。 若要从生成应用程序，**生成**菜单中选择**生成解决方案**。 如果成功生成了应用程序，运行通过选择**启动调试**从**调试**菜单。  
  
     现在，你应看到中选定的项的详细信息`CMFCShellTreeCtrl`在视图窗格中。 当单击中的节点`CMFCShellTreeCtrl`、`CMFCShellListCtrl`将自动更新。 同样，如果你双击中的文件夹`CMFCShellListCtrl`、`CMFCShellTreeCtrl`应自动更新。  
  
     右键单击树控件中或在列表控件中的任何项。 请注意，你可以获得相同的上下文菜单，像使用真实的文件资源管理器。  
  
## <a name="next-steps"></a>后续步骤  
  
-   该向导将 Outlook 栏创建两个**文件夹**窗格和一个**日历**窗格。 它可能不会不具有意义**日历**资源管理器窗口中的窗格。 因此，现在删除该窗格。  
  
-   `CMFCShellListCtrl`支持在不同模式下，如查看文件**大图标**，**小图标**，**列表**，和**详细信息**。 更新你的应用程序，以实现此功能。 提示： 请参阅[Visual c + + 示例](../visual-cpp-samples.md)。  
  
## <a name="see-also"></a>请参阅  
 [演练](../mfc/walkthroughs-mfc.md)

