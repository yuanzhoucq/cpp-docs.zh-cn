---
title: 演练：使用新的 MFC Shell 控件
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: cf0a6bd230364b48c78c72b8e453e7e641fb2d0e
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907410"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>演练：使用新的 MFC Shell 控件

在本演练中，你将创建一个类似于文件资源管理器的应用程序。 您将创建一个具有两个窗格的窗口。 左窗格将包含一个[CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md)对象，该对象在层次结构视图中显示桌面。 右窗格将包含一个[CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) ，显示在左窗格中选择的文件夹中的文件。

## <a name="prerequisites"></a>系统必备

- 在 Visual Studio 2017 和更高版本中，MFC 支持是一个可选组件。 若要安装它，请从 Windows "开始" 菜单打开 Visual Studio 安装程序。 找到你正在使用的 Visual Studio 版本，然后选择 "**修改**" 按钮。 请确保选中 "**带C++** 磁贴的桌面开发"。 在 "**可选组件**" 下，查看**MFC 支持**按钮。

- 本演练假设已将 Visual Studio 设置为使用**常规开发设置**。 如果使用的是其他开发设置，则默认情况下，我们在本演练中使用的某些 Visual Studio 窗口可能不会显示。

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>使用 MFC 应用程序向导创建新的 MFC 应用程序

这些步骤取决于所使用的 Visual Studio 版本。 确保本页左上角的版本选择器已正确设置。

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建 MFC 项目

1. 在主菜单中，选择“文件”>“新建”>“项目”，打开“创建新项目”对话框。

1. 在顶部的 "搜索" 框中，键入 " **mfc** "，然后从 "结果" 列表中选择 " **mfc 应用**"。 

1. 单击 **“下一步”** 。 在下一页中，输入项目的名称，并指定项目位置（如果需要）。

1. 选择“创建”按钮创建项目。

   显示**MFC 应用程序向导**后，使用以下选项：
 
   1. 选择左侧的 "**应用程序类型**"。 然后选择 "**单个文档**"，并选择 "**文档/视图体系结构支持**"。 在 "**项目样式**" 下，选择 " **visual Studio**"，然后从 "**视觉样式和颜色**" 下拉列表中选择 " **Office 2007 （蓝色主题）** "。

   1. 在 "**复合文档支持**" 窗格上，选择 "**无**"。

   1. 不要对**文档模板 "属性**" 窗格进行任何更改。

   1. 在 "**用户界面功能**" 窗格上，确保已选中 "**使用菜单栏和工具栏**" 选项。 保留所有其他选项。

   1. 在 "**高级功能**" 窗格中，选择 " **ActiveX 控件**"、"**公共控件清单**" 和 "**导航窗格**选项"。 将所有其他内容保留原样。 **导航窗格**选项将使向导在窗口的左侧创建一个`CMFCShellTreeCtrl`已嵌入的窗格。

   1. 我们不会对 "**生成的类**" 窗格进行任何更改，因此请单击 "**完成**" 以创建新的 MFC 项目。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>在 Visual Studio 2017 或更早版本中创建 MFC 项目

1. 使用**Mfc 应用程序向导**创建新的 MFC 应用程序。 若要运行该向导，请从 "**文件**" 菜单中选择 "**新建**"，然后选择 "**项目**"。 将显示 "**新建项目**" 对话框。

1. 在 "**新建项目**" 对话框中，展开 "**项目类型**" 窗格中的 **C++可视**节点，然后选择 " **MFC**"。 然后，在 "**模板**" 窗格中选择 " **MFC 应用程序**"。 键入项目的名称，例如`MFCShellControls` ，然后单击 **"确定"** 。 

   显示**MFC 应用程序向导**后，使用以下选项：

   1. 在 "**应用程序类型**" 窗格中的 "**应用程序类型**" 下，清除 "**选项卡式文档**" 选项。 接下来，选择 "**单个文档**"，并选择 "**文档/视图体系结构支持**"。 在 "**项目样式**" 下，选择 " **visual Studio**"，然后从 "**视觉样式和颜色**" 下拉列表中选择 " **Office 2007 （蓝色主题）** "。

   1. 在 "**复合文档支持**" 窗格上，选择 "**无**"。

   1. 不要对**文档模板字符串**窗格进行任何更改。

   1. 在 "**数据库支持**" 窗格（Visual Studio 2015 及更早版本）上，选择 "**无**"，因为应用程序不使用数据库。

   1. 在 "**用户界面功能**" 窗格上，确保已选中 "**使用菜单栏和工具栏**" 选项。 保留所有其他选项。

   1. 在 "**高级功能**" 窗格中的 "**高级功能**" 下，仅选择 " **ActiveX 控件**" 和 "**公共控件清单**"。 在 "**高级框架" 窗格**下，仅选择 "**导航窗格**" 选项。 它将使向导在窗口的左侧创建一个`CMFCShellTreeCtrl`已嵌入的窗格。

   1. 我们不会对 "**生成的类**" 窗格进行任何更改，因此请单击 "**完成**" 以创建新的 MFC 项目。

::: moniker-end

通过生成并运行该应用程序，验证该应用程序是否已成功创建。 若要生成应用程序，请从 "**生成**" 菜单中选择 "**生成解决方案**"。 如果应用程序成功生成，则通过从 "**调试**" 菜单中选择 "**启动调试**" 来运行该应用程序。

向导会自动创建一个应用程序，该应用程序具有标准菜单栏、标准工具栏、标准状态栏和窗口左侧的 Outlook 栏以及 "**文件夹**" 视图和 "**日历**" 视图。

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>向文档视图添加 shell 列表控件

1. 在本部分中，您将向向导创建`CMFCShellListCtrl`的视图中添加一个实例。 在**解决方案资源管理器**中双击 " **MFCShellControlsView** "，打开视图标头文件。

   在标头文件的顶部附近找到指令。`#pragma once` 紧靠在它下面添加以下代码，以包含的`CMFCShellListCtrl`头文件：

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   现在，添加类型`CMFCShellListCtrl`的成员变量。 首先，在标头文件中找到以下注释：

   ```cpp
   // Generated message map functions
   ```

   紧接着该注释，添加以下代码：

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **MFC 应用程序向导**已在`CMainFrame`类`CMFCShellTreeCtrl`中创建了一个对象，但它是一个受保护的成员。 稍后我们将访问该对象，因此现在为其创建访问器。 在**解决方案资源管理器**中双击 mainfrm.cpp 头文件，将其打开。 找到以下注释：

   ```cpp
   // Attributes
   ```

   紧靠在它下面添加以下方法声明：

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   接下来，通过在**解决方案资源管理器**中双击来打开 mainfrm.cpp 源文件。 在该文件的底部，添加以下方法定义：

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. 现在，我们更新`CMFCShellControlsView`类以`WM_CREATE`处理 windows 消息。 打开 "**类视图**" 窗口并选择`CMFCShellControlsView` "类"。 右键单击并选择 "**属性**"。

   接下来，在[类向导](reference/mfc-class-wizard.md)中，单击 "**消息**" 选项卡。向下滚动，直到找到`WM_CREATE`该消息。 从下拉列表中列出在下一步`WM_CREATE`，选择 **\<添加 > OnCreate** 。 命令为我们创建消息处理程序并自动更新 MFC 消息映射。

   在方法中，我们将`CMFCShellListCtrl`创建对象。 `OnCreate` 在 MFCShellControlsView 源文件中查找方法定义，并将其实现替换为以下代码：`OnCreate`

    ```cpp
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

1. 重复上述步骤，但对`WM_SIZE`消息重复。 当用户更改应用程序窗口的大小时，将导致应用程序视图被重绘。 将`OnSize`方法的定义替换为以下代码：

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. 最后一步是使用`CMFCShellTreeCtrl` [CMFCShellTreeCtrl：： SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist)方法连接和`CMFCShellListCtrl`对象。 调用`CMFCShellTreeCtrl::SetRelatedList`后`CMFCShellTreeCtrl`，将自动显示中选定项的内容。 `CMFCShellListCtrl` 我们将连接`OnActivateView`方法中的对象，该方法从[CView：： OnActivateView](../mfc/reference/cview-class.md#onactivateview)重写。

   在 MFCShellControlsView 头文件`CMFCShellControlsView`的类声明中，添加以下方法声明：

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   接下来，将方法的定义添加到 MFCShellControlsView 源文件中：

    ```cpp
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

   由于我们要从`CMainFrame`类调用方法，因此必须在 MFCShellControlsView 源文件的顶部`#include`添加指令：

    ```cpp
    #include "MainFrm.h"
    ```

1. 通过生成并运行该应用程序，验证该应用程序是否已成功创建。 若要生成应用程序，请从 "**生成**" 菜单中选择 "**生成解决方案**"。 如果应用程序成功生成，则通过从 "**调试**" 菜单中选择 "**启动调试**" 来运行该应用程序。

   现在，应会在 "视图" 窗格中的`CMFCShellTreeCtrl`中查看所选项目的详细信息。 当单击中`CMFCShellTreeCtrl`的某个节点时`CMFCShellListCtrl` ，将自动更新。 同样，如果双击中`CMFCShellListCtrl`的文件夹，则`CMFCShellTreeCtrl`应自动更新。

   右键单击树控件或列表控件中的任何项。 您将获得与使用实际**文件资源管理器**相同的上下文菜单。

## <a name="next-steps"></a>后续步骤

- 向导创建了一个具有 "**文件夹**" 窗格和 "**日历**" 窗格的 Outlook 面板。 在**资源管理器**窗口中使用**日历**窗格可能并不合理，因此请立即删除该窗格。

- 支持查看不同模式下的文件，例如大图标、小图标、列表和详细信息。 `CMFCShellListCtrl` 更新应用程序以实现此功能。 提示：请[参阅C++ Visual 示例](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>请参阅

[演练](../mfc/walkthroughs-mfc.md)
