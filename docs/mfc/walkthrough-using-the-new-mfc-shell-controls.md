---
title: 演练：使用新的 MFC Shell 控件
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 5786fbbf7ec9f31e7d895a96dae27b8fc95abda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360213"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>演练：使用新的 MFC Shell 控件

在本演练中，您将创建类似于文件资源管理器的应用程序。 您将创建一个包含两个窗格的窗口。 左侧窗格将包含一个[CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md)对象，该对象在分层视图中显示您的桌面。 右侧窗格将包含一个[CMFCShellListCtrl，](../mfc/reference/cmfcshelllistctrl-class.md)该显示左侧窗格中选择的文件夹中的文件。

## <a name="prerequisites"></a>先决条件

- 在 Visual Studio 2017 及更高版本中，MFC 支持是可选组件。 要安装它，请从"Windows 开始"菜单打开可视化工作室安装程序。 查找您正在使用的 Visual Studio 版本，然后选择 **"修改"** 按钮。 确保选中**了带有C++磁贴的桌面开发**。 在 **"可选组件**"下，检查**MFC 支持**按钮。

- 本演练假定您已设置 Visual Studio 以使用**常规开发设置**。 如果您使用的是其他开发设置，则默认情况下可能不会显示我们在本演练中使用的某些 Visual Studio 窗口。

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>使用 MFC 应用程序向导创建新的 MFC 应用程序

这些步骤因您使用的 Visual Studio 版本而异。 要查看您首选版本的 Visual Studio 的文档，请使用**版本**选择器控件。 它位于此页面的目录顶部。

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中创建 MFC 项目

1. 在主菜单中，选择“文件”“新建”“项目”，打开“创建新项目”对话框**** > **** > ********。

1. 在顶部的搜索框中，键入**MFC，** 然后从结果列表中选择**MFC 应用**。

1. 单击 **“下一步”** 。 在下一页中，输入项目的名称，并根据需要指定项目位置。

1. 选择“创建”**** 按钮创建项目。

   **显示 MFC 应用程序向导**后，请使用以下选项：

   1. 选择左侧**的应用程序类型**。 然后选择 **"单一文档"** 并选择 **"文档/视图体系结构支持**"。 在 **"项目样式**"下，选择**Visual Studio**，并从**视觉样式和颜色**下拉列表中选择**Office 2007（蓝色主题）。**

   1. 在 **"复合文档支持"** 窗格中，选择 **"无**"。

   1. 不要对 **"文档模板属性"** 窗格进行任何更改。

   1. 在 **"用户界面功能"** 窗格中，请确保选择了 **"使用菜单栏"和"工具栏"** 选项。 保留所有其他选项。

   1. 在 **"高级功能**"窗格中，选择**ActiveX 控件**、**常见控件清单**和**导航窗格**选项。 保持一切不变。 "**导航窗格"** 选项将导致向导在窗口左侧创建已`CMFCShellTreeCtrl`嵌入的窗格。

   1. 我们不会对 **"生成类"** 窗格进行任何更改，因此单击 **"完成"** 以创建新的 MFC 项目。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>在 Visual Studio 2017 或更早版本创建 MFC 项目

1. 使用**MFC 应用程序向导**创建新的 MFC 应用程序。 要运行向导，请从 **"文件"** 菜单中选择 **"新建**"，然后选择 **"项目**"。 将显示"**新项目**"对话框。

1. 在 **"新项目**"对话框中，展开 **"项目类型"** 窗格中的**可视C++** 节点并选择**MFC**。 然后，在**模板**窗格中，选择**MFC 应用程序**。 键入项目的名称，如`MFCShellControls`并单击 **"确定**"。

   **显示 MFC 应用程序向导**后，请使用以下选项：

   1. 在 **"应用程序类型"** 窗格下，在 **"应用程序类型**"下，清除**选项卡式文档**选项。 接下来，选择 **"单一文档"** 并选择 **"文档/视图体系结构支持**"。 在 **"项目样式**"下，选择**Visual Studio**，并从**视觉样式和颜色**下拉列表中选择**Office 2007（蓝色主题）。**

   1. 在 **"复合文档支持"** 窗格中，选择 **"无**"。

   1. 不要对 **"文档模板字符串"** 窗格进行任何更改。

   1. 在 **"数据库支持**"窗格（Visual Studio 2015 及更高版）上，选择 **"无"，** 因为应用程序不使用数据库。

   1. 在 **"用户界面功能"** 窗格中，请确保选择了 **"使用菜单栏"和"工具栏"** 选项。 保留所有其他选项。

   1. 在 **"高级功能**"窗格中，在 **"高级功能**"下，仅选择**ActiveX 控件**和**通用控制清单**。 在 **"高级框架窗格"下**，仅选择 **"导航窗格"** 选项。 这将导致向导创建窗口左侧的窗格，其中已嵌入了窗格`CMFCShellTreeCtrl`。

   1. 我们不会对 **"生成类"** 窗格进行任何更改，因此单击 **"完成"** 以创建新的 MFC 项目。

::: moniker-end

通过生成并运行应用程序，验证应用程序是否成功创建。 要生成应用程序，请从**生成**菜单中选择**生成解决方案**。 如果应用程序生成成功，则通过从**调试**菜单中选择 **"开始调试"** 来运行应用程序。

向导会自动创建一个应用程序，该应用程序具有标准菜单栏、标准工具栏、标准状态栏和窗口左侧的 Outlook 栏，其中有**文件夹**视图和**日历**视图。

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>将 shell 列表控件添加到文档视图

1. 在本节中，您将`CMFCShellListCtrl`向向导创建的视图添加实例。 通过在**解决方案资源管理器**中双击**MFCShellControlsView.h**打开视图头文件。

   查找`#pragma once`标头文件顶部附近的指令。 它立即添加此代码以包括 的`CMFCShellListCtrl`标头文件：

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   现在添加类型`CMFCShellListCtrl`的成员变量。 首先，在标头文件中找到以下注释：

   ```cpp
   // Generated message map functions
   ```

   在注释的紧要上方，添加此代码：

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **MFC 应用程序向导**已在`CMainFrame`类中`CMFCShellTreeCtrl`创建了一个对象，但它是受保护的成员。 稍后我们将访问该对象，因此现在为其创建一个访问器。 通过在**解决方案资源管理器**中双击 MainFrm.h 标头文件，打开该文件。 找到以下注释：

   ```cpp
   // Attributes
   ```

   立即在它下面添加以下方法声明：

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   接下来，通过在**解决方案资源管理器**中双击 MainFrm.cpp 源文件来打开该文件。 在该文件的底部，添加以下方法定义：

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. 现在，我们更新`CMFCShellControlsView`类以处理`WM_CREATE`窗口消息。 打开 **"班级视图"** 窗口并选择`CMFCShellControlsView`类。 右键单击并选择 **“属性”**。

   接下来，在["类向导"](reference/mfc-class-wizard.md)中，单击 **"消息"** 选项卡。向下滚动`WM_CREATE`，直到找到邮件。 从 旁边的下拉列表中`WM_CREATE`，选择**\<"添加>创建**。 该命令为我们创建一个消息处理程序，并自动更新 MFC 消息映射。

   在`OnCreate`方法中，我们现在将创建对象`CMFCShellListCtrl`。 在`OnCreate`MFCShellControlsView.cpp 源文件中查找方法定义，并将其实现替换为以下代码：

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

1. 重复上一步，但对`WM_SIZE`消息。 每当用户更改应用程序窗口的大小时，它将导致重新绘制应用程序视图。 将`OnSize`方法的定义替换为以下代码：

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. 最后一步是使用`CMFCShellTreeCtrl`[CMFCShellTreeCtrl：set关联列表](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist)方法连接 和`CMFCShellListCtrl`对象。 调用`CMFCShellTreeCtrl::SetRelatedList`后，`CMFCShellListCtrl`将自动显示 中所选项目的内容。 `CMFCShellTreeCtrl` 我们连接`OnActivateView`方法中的对象，该对象从[CView 重写：：onActivateView](../mfc/reference/cview-class.md#onactivateview)。

   在 MFCShellControlsView.h 标头文件中，在`CMFCShellControlsView`类声明中，添加以下方法声明：

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   接下来，将该方法的定义添加到 MFCShellControlsView.cpp 源文件中：

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

   由于我们从`CMainFrame`类调用方法，因此必须在 MFCShellControlsView.cpp 源文件的顶部添加一个`#include`指令：

    ```cpp
    #include "MainFrm.h"
    ```

1. 通过生成并运行应用程序，验证应用程序是否成功创建。 要生成应用程序，请从**生成**菜单中选择**生成解决方案**。 如果应用程序生成成功，请通过从**调试**菜单中选择 **"开始调试"** 来运行它。

   现在，您应该在视图窗格`CMFCShellTreeCtrl`中看到所选项目的详细信息。 单击 中的`CMFCShellTreeCtrl`节点时，将自动更新`CMFCShellListCtrl`。 同样，如果双击 中的文件夹`CMFCShellListCtrl`，`CMFCShellTreeCtrl`应自动更新 。

   右键单击树控件或列表控件中的任何项。 你得到的上下文菜单与使用实际**文件资源管理器**相同。

## <a name="next-steps"></a>后续步骤

- 该向导创建了一个 Outlook 栏，其中同时包含 **"文件夹"** 窗格和 **"日历"** 窗格。 在**资源管理器**窗口中使用 **"日历"** 窗格可能没有意义，因此请立即删除该窗格。

- 支持`CMFCShellListCtrl`以不同模式查看文件，如**大图标**、**小图标**、**列表**和**详细信息**。 更新应用程序以实现此功能。 提示：请参阅[视觉C++示例](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>另请参阅

[演练](../mfc/walkthroughs-mfc.md)
