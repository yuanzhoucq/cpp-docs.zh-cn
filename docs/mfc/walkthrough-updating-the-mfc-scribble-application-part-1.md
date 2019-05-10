---
title: 演练：正在更新 MFC 随意画图应用程序 （第 1 部分）
ms.date: 04/25/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: cba28039cb7755149b35a47ddee82b6274fe4c72
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558220"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>演练：正在更新 MFC 随意画图应用程序 （第 1 部分）

本演练演示如何修改现有 MFC 应用程序中使用功能区用户界面。 Visual Studio 支持 Office 2007 功能区和 Windows 7 Scenic 功能区。 有关功能区用户界面的详细信息，请参阅[功能区](/windows/desktop/uxguide/cmd-ribbons)。

本演练中修改经典 Scribble 1.0 MFC 示例，可以使用鼠标来创建线条图形。 此部分演练演示如何修改 Scribble 示例，以便它将显示功能区栏。 [第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)将多个按钮添加到功能区栏。

## <a name="prerequisites"></a>系统必备

[Scribble 1.0 MFC 示例](http://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe)。 有关转换到 Visual Studio 2017 或更高版本的帮助，请参阅[移植指南：MFC Scribble](../porting/porting-guide-mfc-scribble.md)。

##  <a name="top"></a> 部分

本演练的此部分包含以下部分：

- [替换为基的类](#replaceclass)

- [将位图添加到项目](#addbitmap)

- [向项目添加功能区资源](#addribbon)

- [创建实例的功能区栏](#createinstance)

- [添加功能区类别](#addcategory)

- [设置应用程序的外观](#setlook)

##  <a name="replaceclass"></a> 替换为基的类

若要转换支持 menu 的支持功能区的应用程序的应用程序，必须更新在基类中派生应用程序、 框架窗口和工具栏类。 （我们建议，你无需修改原始的 Scribble 示例。 相反，清理 Scribble 项目、 将其复制到另一个目录，然后修改副本。）

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>若要替换中随意画图应用程序的基本类

1. 在 scribble.cpp，确认`CScribbleApp::InitInstance`包括对的调用[AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)。

1. 将以下代码添加到 stdafx.h 文件中。

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. 在 scribble.h，修改的定义`CScribbleApp`类，使它派生自[CWinAppEx 类](../mfc/reference/cwinappex-class.md)。

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Windows 应用程序使用初始化 (.ini) 文件来保存用户首选项数据时写入 scribble 1.0。 而不是初始化文件，修改 Scribble 若要在注册表中存储用户首选项。 若要设置的注册表项和基准，键入下面的代码`CScribbleApp::InitInstance`后`LoadStdProfileSettings()`语句。

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. 多文档界面 (MDI) 应用程序主框架不再派生自`CMDIFrameWnd`类。 相反，派生自[CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)类。

    在 mainfrm.h 和 mainfrm.cpp 文件中，将为对所有引用`CMDIFrameWnd`与`CMDIFrameWndEx`。

1. 在 childfrm.h 和 childfrm.cpp 文件中，替换`CMDIChildWnd`与`CMDIChildWndEx`。

    在 childfrm。 h 文件中，替换`CSplitterWnd`与`CSplitterWndEx`。

1. 修改工具栏和状态栏，若要使用新的 MFC 类。

    在 mainfrm.h 中文件中：

    1. 将 `CToolBar` 替换为 `CMFCToolBar`。

    1. 将 `CStatusBar` 替换为 `CMFCStatusBar`。

1. 在 mainfrm.cpp 文件中：

    1. 替换为`m_wndToolBar.SetBarStyle`与 `m_wndToolBar.SetPaneStyle`

    1. 替换为`m_wndToolBar.GetBarStyle`与 `m_wndToolBar.GetPaneStyle`

    1. 替换为`DockControlBar(&m_wndToolBar)`与 `DockPane(&m_wndToolBar)`

1. 在 ipframe.cpp 文件中，注释掉以下三行代码。

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. 保存所做的更改，然后生成并运行应用程序。

##  <a name="addbitmap"></a> 将位图添加到项目

本演练的下一步四个步骤需要位图资源。 可以以多种方式来获取相应的位图：

- 使用[资源编辑器](../windows/resource-editors.md)创造您自己的位图。 或使用资源编辑器来组合来自于包含在 Visual Studio，可以从下载的可移植网络图形 (.png) 映像的位图[Visual Studio 图像库](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library)。

    但是，**功能区**用户界面要求某些位图支持透明图像。 透明位图使用其中的 24 位指定颜色的红色、 绿色和蓝色组件和 8 位定义的 32 位像素*alpha 通道*，它指定颜色的透明度。 当前的资源编辑器可以查看，但不是修改使用 32 位像素的位图。 因此，使用而不是资源编辑器外部图像编辑器处理透明位图。

- 将相应的资源文件复制到你的项目的其他应用程序，然后从该文件导入位图。

本演练将资源文件中创建的示例从复制[演练：使用 MFC 创建功能区应用程序](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)。

### <a name="to-add-bitmaps-to-the-project"></a>若要将位图添加到项目

1. 使用文件资源管理器资源目录中复制以下.bmp 文件 (`res`) 的资源目录的功能区示例 (`res`) 的 Scribble 项目：

   1. 将 main.bmp 复制到你的 Scribble 项目。

   1. 将 filesmall.bmp 和 filelarge.bmp 复制到你的 Scribble 项目。

   1. 创建新副本 filelarge.bmp 和 filesmall.bmp 文件，但将副本保存在功能区的示例。 重命名副本 homesmall.bmp 和 homelarge.bmp，然后将副本移到 Scribble 项目。

   1. 制作一份 toolbar.bmp 文件，但将副本保存在功能区的示例。 重命名副本 panelicons.bmp，然后将副本移动到 Scribble 项目。

1. 导入的 MFC 应用程序的位图。 在中**资源视图**，双击**scribble.rc**节点中，双击**位图**节点，并单击**将资源添加**。 在出现的对话框中，单击**导入**。 浏览到`res`目录中，选择 main.bmp 文件，然后单击**打开**。

   Main.bmp 位图包含 26 x 26 映像。 更改为位图的 ID `IDB_RIBBON_MAIN`。

1. 导入附加到文件菜单的位图**应用程序**按钮。

   1. 导入 filesmall.bmp 文件，其中包含十一个 16 x 16 (16 x 176) 映像。 更改为位图的 ID `IDB_RIBBON_FILESMALL`。

   > [!NOTE]
   > 因为我们需要只有前八个 16 x 16 映像 (16 x 128)，或者可能会出现意外从 176 128 到此位图的右侧的宽度。

   1. 导入 filelarge.bmp，其中包含九个 32 x 32 (32 x 288) 映像。 更改为位图的 ID `IDB_RIBBON_FILELARGE`。

1. 导入的功能区类别和面板的位图。 在功能区栏上的每个选项卡是一种类别，以及组成的文本标签和一个可选的图像。

   1. 导入 homesmall.bmp 位图，其中包含十一个 16 x 16 的小按钮位图图像。 更改为位图的 ID `IDB_RIBBON_HOMESMALL`。

   1. 导入 homelarge.bmp 位图，其中包含九个 32 x 32 的大按钮位图图像。 更改为位图的 ID `IDB_RIBBON_HOMELARGE`。

1. 导入已调整大小的功能区面板的位图。 如果功能区是太小，无法显示整个面板，这些位图或面板图标，则使用后调整大小操作。

   1. 导入 panelicons.bmp 位图，其中包含八个 16 x 16 映像。 在中**属性**窗口中的**位图编辑器**，调整到 64 (16 x 64) 位图的宽度。 更改为位图的 ID `IDB_PANEL_ICONS`。

   > [!NOTE]
   > 因为我们需要只有前四个 16 x 16 映像 (16 x 64)，或者可能会出现意外介于 128 到 64 将该位图的右侧的宽度。

##  <a name="addribbon"></a> 向项目添加功能区资源

在转换使用菜单到使用功能区的应用程序的应用程序时，您无需删除或禁用现有的菜单。 只需创建功能区资源、 添加功能区按钮，然后将新的按钮与现有的菜单项相关联。 尽管菜单都不再可见，但从功能区栏中的消息将路由通过菜单和菜单快捷方式继续工作。

功能区组成**应用程序**按钮，这是在功能区的左上方的大按钮和一个或多个类别选项卡。 每个类别选项卡包含一个或多个作为容器的功能区按钮和控件的面板。 下面的过程演示如何创建功能区资源，然后自定义**应用程序**按钮。

### <a name="to-add-a-ribbon-resource-to-the-project"></a>若要向项目添加功能区资源

1. 使用在所选的 Scribble 项目**解决方案资源管理器**，在**项目**菜单中，单击**添加资源**。

1. 在中**添加资源**对话框中，选择**功能区**，然后单击**新建**。

   Visual Studio 创建功能区资源，并在设计视图中打开它。 功能区资源 ID 是`IDR_RIBBON1`，其中显示在**资源视图**。 在功能区包含一个类别和一个面板。

1. 你可以自定义**应用程序**按钮通过修改其属性。 在菜单中，此代码中使用的消息 Id 已经为 Scribble 1.0 定义。

1. 在设计视图中，单击**应用程序**按钮以显示其属性。 按如下所示更改属性值：**图像**到`IDB_RIBBON_MAIN`，**提示**到`File`，**密钥**到`f`，**大图像**到`IDB_RIBBON_FILELARGE`，和**较小的图像**到`IDB_RIBBON_FILESMALL`。

1. 以下修改创建用户单击时显示的菜单**应用程序**按钮。 单击省略号 (**...**) 旁边**Main 项**以打开**项编辑器**。

   1. 与**项**类型**按钮**选中状态，单击**添加**添加一个按钮。 更改**标题**到`&New`， **ID**到`ID_FILE_NEW`，**映像**到`0`，**大型图像**到`0`.

   1. 单击**添加**添加一个按钮。 更改**标题**到`&Save`， **ID**到`ID_FILE_SAVE`，**映像**到`2`，并**大型图像**到`2`.

   1. 单击**添加**添加一个按钮。 更改**标题**到`Save &As`， **ID**到`ID_FILE_SAVE_AS`，**映像**到`3`，并**大型图像**到`3`.

   1. 单击**添加**添加一个按钮。 更改**标题**到`&Print`， **ID**到`ID_FILE_PRINT`，**映像**到`4`，并**大型图像**到`4`.

   1. 更改**项**键入到**分隔符**，然后单击**添加**。

   1. 更改**项**键入到**按钮**。 单击**添加**添加的第五个按钮。 更改**标题**到`&Close`， **ID**到`ID_FILE_CLOSE`，**映像**到`5`，并**大型图像**到`5`.

1. 以下修改之处创建一个子菜单下的**打印**在上一步中创建的按钮。

   1. 单击**打印**按钮，更改**项**键入到**标签**，然后单击**插入**。 更改**标题**到`Preview and print the document`。

   1. 单击**打印**按钮，更改**项**键入到**按钮**，然后单击**插入**。 更改**标题**到`&Print`， **ID**到`ID_FILE_PRINT`，**映像**到`4`，并**大型图像**到`4`.

   1. 单击**打印**按钮，然后单击**插入**添加一个按钮。 更改**标题**到`&Quick Print`， **ID**到`ID_FILE_PRINT_DIRECT`，**映像**到`7`，并**大型图像**到`7`.

   1. 单击**打印**按钮，然后单击**插入**以添加另一个按钮。 更改**标题**到`Print Pre&view`， **ID**到`ID_FILE_PRINT_PREVIEW`，**映像**到`6`，并**大型图像**到`6`.

   1. 现在已修改**Main 项**。 单击**关闭**退出**项编辑器**。

1. 以下修改创建的底部将显示一个退出按钮**应用程序**按钮菜单。

   1. 在中**属性**窗口中，单击省略号 (**...**) 旁边**按钮**以打开**项编辑器**。

   1. 与**项**类型**按钮**选中状态，单击**添加**添加一个按钮。 更改**标题**到`E&xit`， **ID**到`ID_APP_EXIT`，**映像**到`8`。

   1. 在你修改**按钮**。 单击**关闭**退出**项编辑器**。

##  <a name="createinstance"></a> 创建实例的功能区栏

以下步骤说明如何启动应用程序时创建功能区栏的一个实例。 若要向应用程序添加功能区栏，声明在 mainfrm.h 中文件的功能区栏。 然后，在 mainfrm.cpp 文件中，编写代码以加载功能区资源。

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>若要创建功能区栏的实例

1. 在 mainfrm.h 中文件中，将数据成员添加到受保护节`CMainFrame`，主框架的类定义。 此成员是为功能区栏。

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. 在 mainfrm.cpp 文件中，添加以下代码之前最终`return`语句的末尾`CMainFrame::OnCreate`函数。 创建功能区栏的实例。

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

##  <a name="addcategory"></a> 自定义功能区资源

现在，已创建**应用程序**按钮，可以将元素添加到功能区。

> [!NOTE]
> 本演练使用的所有面板相同的面板图标。 但是，可以使用其他图像列表索引以显示其他图标。

### <a name="to-add-a-home-category-and-edit-panel"></a>若要将主类别添加和编辑面板

1. Scribble 程序要求只有一个类别。 在设计视图中，在**工具箱**，双击**类别**添加一个并显示其属性。 按如下所示更改属性值：**标题**到`&Home`，**大型映像**到`IDB_RIBBON_HOMELARGE`，**较小的图像**到`IDB_RIBBON_HOMESMALL`。

1. 每个功能区类别划分为多个命名的面板。 每个面板包含一组控件该完成相关的操作。 此类别都有一个面板。 单击**面板**，然后将更改**标题**到`Edit`。

1. 向**编辑**面板中，添加一个按钮用于清除文档的内容负责。 已在中定义此按钮的消息 ID`IDR_SCRIBBTYPE`菜单资源。 指定`Clear All`作为按钮文本的修饰按钮位图的索引。 打开**工具箱**，然后拖动**按钮**到**编辑**面板。 单击该按钮，然后更改**标题**到`Clear All`， **ID**到`ID_EDIT_CLEAR_ALL`，**图像索引**到`0`， **Large Image Index**到`0`。

1. 保存所做的更改，然后生成并运行应用程序。 应显示随意画图应用程序，并且它应该具有位于窗口而不是菜单栏的顶部功能区栏。 功能区栏应具有一个类别**主页**，并**主页**应具有一个面板**编辑**。 你添加的功能区按钮应与现有的事件处理程序相关联并**开放**，**关闭**，**保存**，**打印**，并**全部清除**按钮应按预期方式工作。

##  <a name="setlook"></a> 设置应用程序的外观

一个*视觉管理器*是控制应用程序的所有绘制一个全局对象。 由于原始随意画图应用程序使用 Office 2000 用户界面 (UI) 样式，该应用程序可能看起来老式。 你可以重置此应用程序，使其类似于 Office 2007 应用程序使用 Office 2007 视觉管理器。

### <a name="to-set-the-look-of-the-application"></a>若要设置应用程序的外观

1. 在中`CMainFrame::OnCreate`函数中，键入以下代码之前`return 0;`语句来更改默认视觉管理器和样式。

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. 保存所做的更改，然后生成并运行应用程序。 应用程序 UI 应类似于 Office 2007 用户界面。

## <a name="next-steps"></a>后续步骤

在你修改经典的 Scribble 1.0 MFC 示例，使用**功能区设计器**。 现在，转到[第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。

## <a name="see-also"></a>请参阅

[演练](../mfc/walkthroughs-mfc.md)<br/>
[演练：更新 MFC 自由曲线应用程序（第 2 部分）](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
