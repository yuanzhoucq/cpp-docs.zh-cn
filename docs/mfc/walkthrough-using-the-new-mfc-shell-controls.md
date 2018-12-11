---
title: 演练：使用新的 MFC Shell 控件
ms.date: 09/20/2018
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 4ff585123fb30a4fc31460c95f8960f5cfd7b7bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507557"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>演练：使用新的 MFC Shell 控件

在本演练中，将创建一个类似于文件资源管理器的应用程序。 你将创建具有两个窗格的窗口。 左窗格中将保留[CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md)分层视图中显示您的桌面的对象。 右窗格中将保留[CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) ，显示了在左窗格中选择的文件夹中的文件。

## <a name="prerequisites"></a>系统必备

本演练假定，您安装了 Visual Studio 以使用**常规开发设置**。 如果使用的不同的开发设置，我们在本演练中使用某些 Visual Studio 窗口可能不是默认情况下显示。

### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>若要使用 MFC 应用程序向导创建新的 MFC 应用程序

1. 使用**MFC 应用程序向导**若要创建新的 MFC 应用程序。 若要从运行向导时，**文件**菜单中选择**新建**，然后选择**项目**。 **新的项目**将显示对话框。

1. 在中**新的项目**对话框框中，展开**Visual c + +** 中的节点**项目类型**窗格，然后选择**MFC**。 然后，在**模板**窗格中，选择**MFC 应用程序**。 键入项目的名称，如`MFCShellControls`然后单击**确定**。 之后**MFC 应用程序向导**显示，使用以下选项：

    1. 上**应用程序类型**窗格下**应用程序类型**，清除**选项卡式文档**选项。 接下来，选择**单个文档**，然后选择**文档/视图体系结构支持**。 下**项目样式**，选择**Visual Studio**，并从**视觉样式和颜色**下拉列表中，选择**Office 2007 （蓝色主题）**.

    1. 上**复合文档支持**窗格中，选择**None**。

    1. 请勿进行任何更改到**文档模板字符串**窗格。

    1. 上**数据库支持**(Visual Studio 2015 和更低版本) 窗格中选择**None**因为应用程序不需要使用数据库。

    1. 上**用户界面功能**窗格中，请确保**使用菜单栏和工具栏**选择选项。 将所有其他选项保留原样。

    1. 上**高级功能**窗格下**高级功能**，选择仅**ActiveX 控件**并**公共控件清单**。 下**高级框架窗格**，选择仅**导航窗格**选项。 它将导致向导以创建与窗口的左侧窗格`CMFCShellTreeCtrl`已嵌入。

    1. 我们不会进行任何更改**生成的类**窗格中，请单击**完成**创建新的 MFC 项目。

1. 验证应用程序已成功创建，可以通过生成并运行它。 若要生成应用程序，从**构建**菜单中选择**生成解决方案**。 如果成功生成了应用程序，通过选择运行应用程序**开始调试**从**调试**菜单。

   向导会自动创建具有标准菜单栏、 标准工具栏、 状态栏、 标准和 Outlook 栏与窗口的左侧的应用程序**文件夹**视图和一个**日历**视图.

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>若要将 shell 列表控件添加到文档视图

1. 在本部分中，你将添加的实例`CMFCShellListCtrl`到向导创建的视图。 通过双击打开视图标头文件**MFCShellControlsView.h**中**解决方案资源管理器**。

   找到`#pragma once`指令的标头文件的顶部附近。 立即它下面添加以下代码以包括的头文件`CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   现在，添加类型的成员变量`CMFCShellListCtrl`。 首先，该标头文件中找到以下注释：

   ```cpp
   // Generated message map functions
   ```

   立即上方的注释，添加以下代码：

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **MFC 应用程序向导**已创建`CMFCShellTreeCtrl`对象中`CMainFrame`，但它的受保护的成员。 我们将稍后访问的对象，因此现在创建它的访问器。 打开 MainFrm.h 标头文件中双击**解决方案资源管理器**。 找到以下注释：

   ```cpp
   // Attributes
   ```

   立即在其下添加以下方法声明：

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   接下来，打开 MainFrm.cpp 源文件中双击**解决方案资源管理器**。 在该文件的底部，添加以下方法定义：

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. 现在，我们更新`CMFCShellControlsView`类来处理`WM_CREATE`windows 消息。 打开**类视图**窗口，然后选择`CMFCShellControlsView`类。 右键单击并选择**属性**。

    接下来，在**属性**窗口中，单击**消息**图标。 向下滚动直到找到`WM_CREATE`消息。 从下拉列表中列出在下一步`WM_CREATE`，选择 **\<添加 > OnCreate** 。 该命令会为我们创建一个消息处理程序，并会自动更新 MFC 消息映射。

   在中`OnCreate`方法，现在我们将创建我们`CMFCShellListCtrl`对象。 查找`OnCreate`MFCShellControlsView.cpp 中的方法定义源文件，文件和它的实现替换为以下代码：

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

1. 重复上述步骤，但对于`WM_SIZE`消息。 它将导致应用程序视图，以便每当用户更改应用程序窗口的大小需要重新绘制。 替换为定义`OnSize`方法使用以下代码：

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. 最后一步是连接`CMFCShellTreeCtrl`并`CMFCShellListCtrl`通过使用对象[CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist)方法。 调用后`CMFCShellTreeCtrl::SetRelatedList`，则`CMFCShellListCtrl`将自动显示在选定的项的内容`CMFCShellTreeCtrl`。 我们连接中的对象`OnActivateView`方法，从重写[CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview)。

   在 MFCShellControlsView.h 标头文件中，内部`CMFCShellControlsView`类声明中，添加以下方法声明：

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   接下来，将方法定义添加到 MFCShellControlsView.cpp 源文件：

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

   因为我们正在呼叫中的方法`CMainFrame`类中，我们必须添加`#include`指令 MFCShellControlsView.cpp 源文件的顶部：

    ```cpp
    #include "MainFrm.h"
    ```

1. 验证应用程序已成功创建，可以通过生成并运行它。 若要生成应用程序，从**构建**菜单中选择**生成解决方案**。 如果成功生成了应用程序，运行通过选择**开始调试**从**调试**菜单。

   现在应看到在所选的项的详细信息`CMFCShellTreeCtrl`视图窗格中。 当单击中的节点`CMFCShellTreeCtrl`，则`CMFCShellListCtrl`将自动更新。 同样，如果您双击文件夹中的`CMFCShellListCtrl`，则`CMFCShellTreeCtrl`应自动更新。

   右键单击任何项目树控件中或在列表控件中。 像使用真实获取相同的上下文菜单**文件资源管理器**。

## <a name="next-steps"></a>后续步骤

- 该向导进行创建 Outlook 栏**文件夹**窗格和一个**日历**窗格。 它可能不具有意义**日历**窗格中的**资源管理器**窗口中，因此现在删除该窗格。

- `CMFCShellListCtrl`支持在不同模式下，如查看文件**大图标**，**小图标**，**列表**，并且**详细信息**。 更新应用程序以实现此功能。 提示： 请参阅[Visual c + + 示例](../visual-cpp-samples.md)。

## <a name="see-also"></a>请参阅

[演练](../mfc/walkthroughs-mfc.md)
