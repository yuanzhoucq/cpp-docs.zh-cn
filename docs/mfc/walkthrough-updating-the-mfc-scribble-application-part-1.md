---
title: 演练：更新 MFC 随意画图应用程序（第 1 部分）
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 18803d2222c80b80ac2b1fde75b442ea1e9a89bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360249"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>演练：更新 MFC 随意画图应用程序（第 1 部分）

本演练演示如何修改现有 MFC 应用程序以使用功能区用户界面。 Visual Studio 同时支持 Office 2007 功能区和 Windows 7 风景功能区。 有关功能区用户界面的详细信息，请参阅[功能区](/windows/win32/uxguide/cmd-ribbons)。

本演练修改经典 Scribble 1.0 MFC 示例，该示例允许您使用鼠标创建线条图。 演练的这一部分演示如何修改 Scribble 示例，以便显示功能区栏。 [第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)向功能区栏添加更多按钮。

## <a name="prerequisites"></a>先决条件

[涂鸦 1.0 MFC 样品](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe)。 有关转换为 Visual Studio 2017 或更高版本的帮助，请参阅[移植指南：MFC 涂鸦](../porting/porting-guide-mfc-scribble.md)。

## <a name="sections"></a><a name="top"></a>部分

本演练的这一部分有以下部分：

- [替换基本类](#replaceclass)

- [向项目添加位图](#addbitmap)

- [向项目添加功能区资源](#addribbon)

- [创建功能区栏的实例](#createinstance)

- [添加功能区类别](#addcategory)

- [设置应用程序的外观](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a>替换基本类

要将支持菜单的应用程序转换为支持功能区的应用程序，必须从更新的基类派生应用程序、框架窗口和工具栏类。 （我们建议您不要修改原始涂鸦示例。 相反，请清理 Scribble 项目，将其复制到其他目录，然后修改副本。

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>替换 Scribble 应用程序中的基类

1. 在涂鸦.cpp 中，验证其中包括`CScribbleApp::InitInstance`对[AfxOleInit 的](../mfc/reference/ole-initialization.md#afxoleinit)呼叫。

1. 将以下代码添加到*pch.h*文件（Visual Studio 2017 和更早版本中的*stdafx.h）：*

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. 在 scribble.h 中，修改`CScribbleApp`类的定义，以便从[CWinAppEx 类](../mfc/reference/cwinappex-class.md)派生。

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. 当 Windows 应用程序使用初始化 （.ini） 文件保存用户首选项数据时，编写了 Scribble 1.0。 修改 Scribble 以在注册表中存储用户首选项，而不是初始化文件。 要设置注册表项和库，请键入`CScribbleApp::InitInstance``LoadStdProfileSettings()`语句之后的以下代码。

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. 多个文档接口 （MDI） 应用程序的主框架不再从类`CMDIFrameWnd`派生。 相反，它派生自[CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)类。

    在 mainfrm.h 和 mainfrm.cpp 文件中，将所有`CMDIFrameWnd`引用`CMDIFrameWndEx`替换为 。

1. 在子frm.h和子frm.cpp文件中，替换为`CMDIChildWnd``CMDIChildWndEx`。

    在孩子里 h 文件，`CSplitterWnd`替换为`CSplitterWndEx`。

1. 修改工具栏和状态栏以使用新的 MFC 类。

    在 mainfrm.h 文件中：

    1. 将 `CToolBar` 替换为 `CMFCToolBar`。

    1. 将 `CStatusBar` 替换为 `CMFCStatusBar`。

1. 在 mainfrm.cpp 文件中：

    1. 将 `m_wndToolBar.SetBarStyle` 替换为 `m_wndToolBar.SetPaneStyle`

    1. 将 `m_wndToolBar.GetBarStyle` 替换为 `m_wndToolBar.GetPaneStyle`

    1. 将 `DockControlBar(&m_wndToolBar)` 替换为 `DockPane(&m_wndToolBar)`

1. 在 ipframe.cpp 文件中，注释出以下三行代码。

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. 保存更改，然后生成并运行应用程序。

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a>向项目添加位图

本演练的后续四个步骤需要位图资源。 您可以通过多种方式获取适当的位图：

- 使用[资源编辑器](../windows/resource-editors.md)发明您自己的位图。 或者使用资源编辑器从 Visual Studio 中包含的便携式网络图形 （.png） 图像中组装位图，并且可以从[Visual Studio 图像库](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library)下载。

    但是，**功能区**用户界面要求某些位图支持透明图像。 透明位图使用 32 位像素，其中 24 位指定颜色的红色、绿色和蓝色分量，8 位定义指定颜色透明度的*Alpha 通道*。 当前资源编辑器可以查看，但不能修改具有 32 位像素的位图。 因此，使用外部图像编辑器而不是资源编辑器来操作透明的位图。

- 将适当的资源文件从其他应用程序复制到项目，然后从该文件导入位图。

本演练从演练中创建的示例复制资源文件[：使用 MFC 创建功能区应用程序](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)。

### <a name="to-add-bitmaps-to-the-project"></a>向项目添加位图

1. 使用文件资源管理器将以下 .bmp 文件从功能区示例的资源`res`目录 （） 复制到 Scribble`res`项目的资源目录 （ ）：

   1. 将 main.bmp 复制到您的涂鸦项目。

   1. 将文件 small.bmp 和 filelarge.bmp 复制到您的涂鸦项目。

   1. 制作 filelarge.bmp 和 filesmall.bmp 文件的新副本，但将副本保存在功能区示例中。 重命名副本 homesmall.bmp 和 homelarge.bmp，然后将副本移动到您的 Scribble 项目。

   1. 制作工具栏.bmp 文件的副本，但将副本保存在功能区示例中。 重命名复制面板.bmp，然后将副本移动到 Scribble 项目。

1. 导入 MFC 应用程序的位图。 在 **"资源视图**"中，双击**scribble.rc**节点，双击**位图**节点，然后单击"**添加资源**"。 在显示的对话框中，单击"**导入**"。 浏览到`res`目录，选择主.bmp 文件，然后单击"**打开**"。

   main.bmp 位图包含 26x26 图像。 将位图的 ID 更改为`IDB_RIBBON_MAIN`。

1. 导入附加到**应用程序**按钮的文件菜单的位图。

   1. 导入文件 small.bmp 文件，该文件包含 11 个 16x16 （16x176） 图像。 将位图的 ID 更改为`IDB_RIBBON_FILESMALL`。

   > [!NOTE]
   > 由于我们只需要前八张 16x16 图像 （16x128），因此您可以选择将此位图的右侧宽度从 176 裁剪到 128。

   1. 导入包含九张 32x32 （32x288） 图像的文件 large.bmp。 将位图的 ID 更改为`IDB_RIBBON_FILELARGE`。

1. 导入功能区类别和面板的位图。 功能区栏上的每个选项卡都是一个类别，由文本标签和可选图像组成。

   1. 导入 homesmall.bmp 位图，其中包含 11 个 16x16 图像，用于小按钮位图。 将位图的 ID 更改为`IDB_RIBBON_HOMESMALL`。

   1. 导入 homelarge.bmp 位图，其中包含 9 个用于大型按钮位图的 32x32 图像。 将位图的 ID 更改为`IDB_RIBBON_HOMELARGE`。

1. 导入调整大小的功能区面板的位图。 如果功能区太小而无法显示整个面板，则这些位图或面板图标在调整大小操作后使用。

   1. 导入包含八张 16x16 图像的面板图标.bmp 位图。 在**位图编辑器****的属性窗口中，** 将位图的宽度调整到 64 （16x64）。 将位图的 ID 更改为`IDB_PANEL_ICONS`。

   > [!NOTE]
   > 由于我们只需要前四个 16x16 图像 （16x64），您可以选择将此位图的右侧宽度从 128 裁剪到 64。

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a>向项目添加功能区资源

将使用菜单的应用程序转换为使用功能区的应用程序时，不必删除或禁用现有菜单。 只需创建功能区资源，添加功能区按钮，然后将新按钮与现有菜单项相关联。 尽管菜单不再可见，但功能区栏中的消息通过菜单路由，菜单快捷方式继续工作。

功能区由 **"应用程序**"按钮（功能区左上角的大按钮）和一个或多个类别选项卡组成。 每个类别选项卡包含一个或多个面板，这些面板充当功能区按钮和控件的容器。 以下过程演示如何创建功能区资源，然后自定义**应用程序**按钮。

### <a name="to-add-a-ribbon-resource-to-the-project"></a>向项目添加功能区资源

1. 在 **"解决方案资源管理器**"中选择了"涂鸦"**项目**，单击"**添加资源**"

1. 在"**添加资源"** 对话框中，选择 **"功能区**"，然后单击"**新建**"。

   Visual Studio 创建功能区资源并在设计视图中打开它。 功能区资源 ID`IDR_RIBBON1`是 ，显示在**资源视图中**。 功能区包含一个类别和一个面板。

1. 您可以通过修改**应用程序**属性来自定义应用程序按钮。 在此代码中使用的消息 ID 已在 Scribble 1.0 的菜单中定义。

1. 在设计视图中，单击 **"应用程序**"按钮以显示其属性。 按如下方式更改属性值**Image**：图像`IDB_RIBBON_MAIN`到**Prompt**、`File`提示到`f`、**键**到`IDB_RIBBON_FILELARGE`、**大图像**到`IDB_RIBBON_FILESMALL`，**将小图像**更改为 。

1. 以下修改将创建用户单击"**应用程序**"按钮时显示的菜单。 单击**主项目**旁边的省略号 （**...）** 以打开**项目编辑器**。

   1. 选中"**项目**类型 **"按钮**后，单击"**添加"** 以添加按钮。 将**标题**更改为`&New` **，ID** `ID_FILE_NEW`更改为`0`，**图像**更改为`0`**，图像大**更改为 。

   1. 单击"**添加**"以添加按钮。 将**标题**更改为`&Save` **，ID** `ID_FILE_SAVE`更改为`2`，**将图像**更改为`2`，将 **"图像"更改为 "图像"**

   1. 单击"**添加**"以添加按钮。 将**标题**更改为`Save &As` **，ID** `ID_FILE_SAVE_AS`更改为`3`，**将图像**更改为`3`，将 **"图像"更改为 "图像"**

   1. 单击"**添加**"以添加按钮。 将**标题**更改为`&Print` **，ID** `ID_FILE_PRINT`更改为`4`，**将图像**更改为`4`，将 **"图像"更改为 "图像"**

   1. 将**项目**类型更改为**分隔符**，然后单击"**添加**"。

   1. 将**项目**类型更改为**按钮**。 单击"**添加"** 可添加第五个按钮。 将**标题**更改为`&Close` **，ID** `ID_FILE_CLOSE`更改为`5`，**将图像**更改为`5`，将 **"图像"更改为 "图像"**

1. 以下修改在上一步中创建的 **"打印"** 按钮下创建子菜单。

   1. 单击 **"打印"** 按钮，将 **"项目**"类型更改为 **"标签**"，然后单击"**插入**"。 将**标题**更改为`Preview and print the document`。

   1. 单击 **"打印"** 按钮，将 **"项目**"类型更改为 **"按钮**"，然后单击"**插入**"。 将**标题**更改为`&Print` **，ID** `ID_FILE_PRINT`更改为`4`，**将图像**更改为`4`，将 **"图像"更改为 "图像"**

   1. 单击 **"打印"** 按钮，然后单击"**插入"** 以添加按钮。 将**标题**更改为`&Quick Print` **，ID** `ID_FILE_PRINT_DIRECT`更改为`7`，**将图像**更改为`7`，将 **"图像"更改为 "图像"**

   1. 单击 **"打印"** 按钮，然后单击"**插入"** 以添加另一个按钮。 将**标题**更改为`Print Pre&view` **，ID** `ID_FILE_PRINT_PREVIEW`更改为`6`，**将图像**更改为`6`，将 **"图像"更改为 "图像"**

   1. 您现在已经修改了**主要项目**。 单击 **"关闭"** 以退出**项目编辑器**。

1. 以下修改将创建一个显示在 **"应用程序"** 按钮菜单底部的退出按钮。

   1. 在**解决方案资源管理器**中选择 **"资源视图**"选项卡。
   1. 在 **"属性"** 窗口中，单击**按钮**旁边的省略号 **（...）** 以打开**项目编辑器**。

   1. 选中"**项目**类型 **"按钮**后，单击"**添加"** 以添加按钮。 将**标题**更改为`E&xit` **，ID**更改为`ID_APP_EXIT` `8`，**图像**更改为 。

   1. 您已修改**按钮**。 单击 **"关闭"** 以退出**项目编辑器**。

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a>创建功能区栏的实例

以下步骤演示如何在应用程序启动时创建功能区栏的实例。 要向应用程序添加功能区栏，请声明 mainfrm.h 文件中的功能区栏。 然后，在 mainfrm.cpp 文件中，编写代码以加载功能区资源。

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>创建功能区栏的实例

1. 在 mainfrm.h 文件中，将数据成员添加到`CMainFrame`的受保护部分，主帧的类定义。 此成员适用于功能区栏。

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. 在 mainfrm.cpp 文件中，在`return``CMainFrame::OnCreate`函数末尾的最后语句之前添加以下代码。 它创建功能区栏的实例。

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a>自定义功能区资源

现在，您已经创建了 **"应用程序"** 按钮，您可以将元素添加到功能区。

> [!NOTE]
> 本演练对所有面板使用相同的面板图标。 但是，您可以使用其他图像列表索引来显示其他图标。

### <a name="to-add-a-home-category-and-edit-panel"></a>添加"主页"类别和"编辑"面板

1. 涂鸦程序只需要一个类别。 在设计视图中，在 **"工具箱**"中，双击 **"类别"** 以添加一个并显示其属性。 将属性值更改为：**标题**到`&Home`，**大图像**更改为`IDB_RIBBON_HOMELARGE`，**小图像**更改为`IDB_RIBBON_HOMESMALL`。

1. 每个功能区类别都组织成命名面板。 每个面板包含一组完成相关操作的控件。 此类别有一个面板。 单击**面板**，然后将**标题**更改为`Edit`。

1. 到 **"编辑"** 面板，添加一个按钮，负责清除文档的内容。 此按钮的消息 ID 已在`IDR_SCRIBBTYPE`菜单资源中定义。 指定`Clear All`为按钮文本和修饰按钮的位图的索引。 打开**工具箱**，然后将**按钮**拖动到 **"编辑"** 面板。 单击该按钮，然后将 **"标题"**`Clear All`更改为 **"ID**到`ID_EDIT_CLEAR_ALL`"**图像索引**`0`"，`0`**将"大图像索引"** 更改为 。

1. 保存更改，然后生成并运行应用程序。 应显示 Scribble 应用程序，并且窗口顶部应有一个功能区栏，而不是菜单栏。 功能区栏应该有一个类别，**主页****，和主页**应该有一个面板，**编辑**。 添加的功能区按钮应与现有事件处理程序关联，**并且"打开**、**关闭**、**保存**、**打印**"和**清除所有按钮**应按预期工作。

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a>设置应用程序的外观

*可视化管理器*是控制应用程序所有绘图的全局对象。 由于原始 Scribble 应用程序使用 Office 2000 用户界面 （UI） 样式，因此应用程序可能看起来过时。 您可以重置应用程序以使用 Office 2007 可视化管理器，使其类似于 Office 2007 应用程序。

### <a name="to-set-the-look-of-the-application"></a>设置应用程序的外观

1. 在`CMainFrame::OnCreate`函数中，在`return 0;`语句之前键入以下代码以更改默认可视管理器和样式。

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. 保存更改，然后生成并运行应用程序。 应用程序 UI 应类似于 Office 2007 UI。

## <a name="next-steps"></a>后续步骤

您已修改经典 Scribble 1.0 MFC 示例以使用**功能区设计器**。 现在转到[第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。

## <a name="see-also"></a>另请参阅

[演练](../mfc/walkthroughs-mfc.md)<br/>
[演练：更新 MFC 随意画图应用程序（第 2 部分）](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
