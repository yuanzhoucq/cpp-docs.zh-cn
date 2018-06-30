---
title: 演练： 更新 MFC 随意画图应用程序 （第 1 部分） |Microsoft 文档
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 916c6ccbdaa9512f1ee0a23a59b866678005180a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122848"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>演练： 更新 MFC 随意画图应用程序 （第 1 部分）

本演练演示如何修改现有 MFC 应用程序使用功能区用户界面。 Visual Studio 支持 Office 2007 功能区和 Windows 7 风景如画功能区。 有关功能区用户界面的详细信息，请参阅[功能区](http://go.microsoft.com/fwlink/p/?linkid=129233)MSDN 网站上。

本演练修改经典 Scribble 1.0 MFC 示例，你可以使用鼠标来创建线条图形。 本部分演练演示如何修改 Scribble 示例，使它显示功能区栏。 [第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)将更多的按钮添加到功能区栏。

## <a name="prerequisites"></a>系统必备

[Visual C++ 示例](../visual-cpp-samples.md)

[Visual C++ 示例](../visual-cpp-samples.md)

##  <a name="top"></a> 部分

本部分演练包含以下部分：

- [替换基类，这些类](#replaceclass)

- [将位图添加到项目](#addbitmap)

- [向项目添加功能区资源](#addribbon)

- [创建功能区栏的实例](#createinstance)

- [添加功能区类别](#addcategory)

- [设置应用程序的外观](#setlook)

##  <a name="replaceclass"></a> 替换基类，这些类

若要转换支持支持功能区的应用程序的菜单的应用程序，必须更新在基类中派生应用程序、 框架窗口和工具栏类。 （我们建议你不要不修改原始的 Scribble 示例; 相反，清除 Scribble 项目，将其复制到另一个目录，然后修改副本。）

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>若要替换随意画图应用程序中的基本类

1. 在 scribble.cpp，验证`CScribbleApp::InitInstance`包括对的调用[AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)。

2. 将以下代码添加到 stdafx.h 文件中。

    ```cpp
    #include <afxcontrolbars.h>
    ```

3. 在 scribble.h，修改的定义`CScribbleApp`类，使它派生自[CWinAppEx 类](../mfc/reference/cwinappex-class.md)。

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

4. Windows 应用程序使用初始化 (.ini) 文件以保存用户首选项数据时，是编写 scribble 1.0。 而不是一个初始化文件，修改 Scribble 在注册表中存储用户首选项。 若要设置的注册表项和基，键入下面的代码`CScribbleApp::InitInstance`后`LoadStdProfileSettings()`语句。

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

5. 多文档界面 (MDI) 应用程序的主框架不再派生自`CMDIFrameWnd`类。 相反，派生自[CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)类。

     在 mainfrm.h 和 mainfrm.cpp 文件中，将对所有引用`CMDIFrameWnd`与`CMDIFrameWndEx`。

6. 在 childfrm.h 和 childfrm.cpp 文件中，替换`CMDIChildWnd`与`CMDIChildWndEx`。

     在 childfrm。 h 文件替换`CSplitterWnd`与`CSplitterWndEx`。

7. 修改工具栏和状态栏，以使用新的 MFC 类。

     在 mainfrm.h 文件中：

    1. 将 `CToolBar` 替换为 `CMFCToolBar`。

    2. 将 `CStatusBar` 替换为 `CMFCStatusBar`。

8. 在 mainfrm.cpp 文件中：

    1. 替换`m_wndToolBar.SetBarStyle`与 `m_wndToolBar.SetPaneStyle`

    2. 替换`m_wndToolBar.GetBarStyle`与 `m_wndToolBar.GetPaneStyle`

    3. 替换`DockControlBar(&m_wndToolBar)`与 `DockPane(&m_wndToolBar)`

9. 在 ipframe.cpp 文件中，注释掉以下三个代码行。

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

10. 如果你想以静态方式链接你的应用程序，请将下面的代码添加到项目资源 (.rc) 文件的开头。

    ```cpp
    #include "afxribbon.rc"
    ```

     Afxribbon.rc 文件包含在运行时所需资源。 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)自动包括此文件时创建应用程序。

11. 保存更改然后生成并运行应用程序。

[[部分](#top)]

##  <a name="addbitmap"></a> 将位图添加到项目

本演练的下一步四个步骤需要位图的资源。 你可以获取相应位图以各种方式：

- 使用[资源编辑器](../windows/resource-editors.md)需创建您自己的位图。 或使用资源编辑器来组合来自附带的可移植网络图形 (.png) 映像的位图[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。 这些映像可以在`VS2008ImageLibrary`目录。

     但是，功能区用户界面需要某些位图支持透明图像。 透明的位图使用其中的 24 位指定的颜色的红色、 绿色和蓝色组件和 8 位定义的 32 位像素*alpha 通道*，它指定颜色的透明度。 当前的资源编辑器可以查看，但不是能修改使用 32 位像素的位图。 因此，使用外部图像编辑器而不是资源编辑器来操作透明的位图。

- 将相应的资源文件复制到你的项目的其他应用程序中并从该文件然后导入位图。

本演练将复制的示例目录中的应用程序资源文件。

### <a name="to-add-bitmaps-to-the-project"></a>若要将位图添加到项目

1. 使用文件资源管理器资源目录中复制以下.bmp 文件 (`res`) 的 RibbonGadgets 示例：

   1. 将 main.bmp 复制到你的 Scribble 项目。

   2. 将 filesmall.bmp 和 filelarge.bmp 复制到你的 Scribble 项目。

   3. 新文件的副本 filelarge.bmp 和 filesmall.bmp，但将副本保存在 RibbonGadgets 示例。 重命名副本 homesmall.bmp 和 homelarge.bmp，然后移动到你的 Scribble 项目的副本。

   4. 一份 toolbar.bmp 文件中，但将副本保存在 RibbonGadgets 示例。 重命名副本 panelicons.bmp，然后移动到你的 Scribble 项目的复制。

2. 导入为 MFC 应用程序的位图。 在**资源视图**，双击**scribble.rc**节点，双击**位图**节点，，然后单击**将资源添加**。 在显示的对话框中，单击**导入**。 浏览到`res`目录中，选择 main.bmp 文件，然后单击**打开**。

   Main.bmp 位图包含 26 x 26 的图像。 更改为 IDB_RIBBON_MAIN 位图的 ID。

3. 导入文件菜单附加到的应用程序按钮的位图。

   1. 导入 filesmall.bmp 文件，其中包含十个 16 x 16 (16 x 160) 映像。 由于我们需要仅八个 16 x 16 映像 (16 x 128)，使用**资源视图**从 160 的该位图的宽度更改为 128。 更改为 IDB_RIBBON_FILESMALL 位图的 ID。

   2. 导入 filelarge.bmp，其中包含八个 32 x 32 (32 x 256) 映像。 更改为 IDB_RIBBON_FILELARGE 位图的 ID。

4. 导入功能区类别和面板的位图。 在功能区栏上的每个选项卡是一种类别，并包含文本标签和一个可选图像。

   1. 导入 homesmall.bmp 位图，其中包含八个 16 x 16 小按钮位图图像。 更改为 IDB_RIBBON_HOMESMALL 位图的 ID。

   2. 导入 homelarge.bmp 位图，其中包含八个 32 x 32 大按钮位图图像。 更改为 IDB_RIBBON_HOMELARGE 位图的 ID。

5. 导入已调整大小功能区面板的位图。 如果功能区是太小以致无法显示整个面板，这些位图或面板图标，则使用后执行大小调整操作。

   1. 导入 panelicons.bmp 位图，其中包含八个 16 x 16 映像。 在**属性**窗口**位图编辑器**，调整为 64 (16 x 64) 位图的宽度。 更改为 IDB_PANEL_ICONS 位图的 ID。

[[部分](#top)]

##  <a name="addribbon"></a> 向项目添加功能区资源

在转换使用到使用功能区的应用程序的菜单的应用程序时，你无需删除或禁用现有的菜单。 相反，创建功能区资源、 添加功能区按钮，并将新按钮添加与现有的菜单项。 虽然的菜单不再可见，但通过菜单进行路由的功能区栏中的消息。 此外，菜单快捷键继续正常工作。

功能区组成的应用程序按钮，即左上方的功能区上的大按钮和一个或多个类别选项卡。 每个类别选项卡包含一个或多个作为容器的功能区按钮和控件的面板。 以下过程演示如何创建功能区资源，然后自定义的应用程序按钮。

### <a name="to-add-a-ribbon-resource-to-the-project"></a>若要向项目添加功能区资源

1. 上**项目**菜单上，单击**添加资源**。

2. 在**添加资源**对话框中，选择**功能区**，然后单击**新建**。

   Visual Studio 创建功能区资源，并在设计视图中打开它。 功能区资源 ID 是 IDR_RIBBON1，将显示在**资源视图**。 功能区包含一个类别和一个面板。

3. 通过修改其属性，可以自定义应用程序按钮。 在菜单中，此代码中使用的消息 Id 已为 Scribble 1.0 定义。

4. 在设计视图中，单击应用程序按钮以显示其属性。 如下所示更改属性值：**映像**到`IDB_RIBBON_MAIN`，**提示**到`File`，**密钥**到`f`，**大型图像**到`IDB_RIBBON_FILELARGE`，和**小型图像**到`IDB_RIBBON_FILESMALL`。

5. 以下修改之处创建显示当用户单击的应用程序按钮的菜单中。 单击省略号 (**...**) 旁边**Main 项**以打开**项编辑器**。

   1. 单击**添加**添加一个按钮。 更改**标题**到`&New`， **ID**到`ID_FILE_NEW`，**映像**到`0`，**大图标**到`0`.

   2. 单击**添加**添加第二个按钮。 更改**标题**到`&Save`， **ID**到`ID_FILE_SAVE`，**映像**到`2`，和**大图标**到`2`.

   3. 单击**添加**添加第三个按钮。 更改**标题**到`Save &As`， **ID**到`ID_FILE_SAVE_AS`，**映像**到`3`，和**大图标**到`3`.

   4. 单击**添加**添加第四个按钮。 更改**标题**到`&Print`， **ID**到`ID_FILE_PRINT`，**映像**到`4`，和**大图标**到`4`.

   5. 更改**项**键入到**分隔符**，然后单击**添加**。

   6. 更改**项**键入到**按钮**。 单击**添加**添加的第五个按钮。 更改**标题**到`&Close`， **ID**到`ID_FILE_CLOSE`，**映像**到`5`，和**大图标**到`5`.

6. 以下修改之处创建你在上一步中创建的打印按钮下子菜单。

   1. 单击**打印**按钮，更改**项**键入到**标签**，然后单击**插入**。 更改**标题**到`Preview and print the document`。

   2. 单击**打印**按钮，更改**项**键入到**按钮**，然后单击**插入**。 更改**标题**到`&Print`， **ID**到`ID_FILE_PRINT`，**映像**到`4`，和**大图标**到`4`.

   3. 单击**打印**按钮，然后单击**插入**添加一个按钮。 更改**标题**到`&Quick Print`， **ID**到`ID_FILE_PRINT_DIRECT`，**映像**到`7`，和**大图标**到`7`.

   4. 单击**打印**按钮，然后单击**插入**添加另一个按钮。 更改**标题**到`Print Pre&view`， **ID**到`ID_FILE_PRINT_PREVIEW`，**映像**到`6`，和**大图标**到`6`.

   5. 现在已修改**Main 项**。 单击**关闭**退出**项编辑器**。

7. 以下修改在应用程序按钮菜单的底部创建一个退出按钮，将出现。

   1. 在**属性**窗口中，单击省略号 (**...**) 旁边**按钮**以打开**项编辑器**。

   2. 单击**添加**添加一个按钮。 更改**标题**到`E&xit`， **ID**到`ID_APP_EXIT`，**映像**到`8`。

[[部分](#top)]

##  <a name="createinstance"></a> 创建功能区栏的实例

以下步骤演示如何创建功能区栏的实例，你的应用程序启动时。 若要将功能区栏添加到应用程序中，声明 mainfrm.h 文件中的功能区栏。 然后，在 mainfrm.cpp 文件中，编写代码以加载功能区资源。

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>若要创建的功能区栏实例

1. 在 mainfrm.h 文件中，将数据成员添加到受保护节`CMainFrame`，主框架的类定义。 此成员表示功能区栏。

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. 在 mainfrm.cpp 文件中，添加以下代码之前最终`return`末尾的语句`CMainFrame::OnCreate`函数。 这将创建功能区栏的实例。

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

[[部分](#top)]

##  <a name="addcategory"></a> 自定义功能区资源

既然你已经创建的应用程序按钮，你可以将元素添加到功能区中。

> [!NOTE]
> 本演练使用所有面板相同的面板图标。 但是，你可以使用其他图像列表索引以显示其他图标。

### <a name="to-add-a-home-category-and-edit-panel"></a>若要添加主页类别和编辑面板

1. Scribble 程序需要只有一个类别。 在设计视图中，单击**类别**以显示其属性。 如下所示更改属性值：**标题**到`&Home`，**大型图像**到`IDB_RIBBON_HOMELARGE`，**小型图像**到`IDB_RIBBON_HOMESMALL`。

2. 每个功能区类别分为命名面板。 每个面板包含一组执行相关的操作的控件。 此类别中包含一个面板。 单击**面板**，然后将更改**标题**到`Edit`和**映像索引**到`0`。

3. 到**编辑**面板中，添加一个按钮，它负责清除文档的内容。 此按钮的消息 ID 已 IDR_SCRIBBTYPE 菜单资源中定义。 指定`Clear All`作为按钮文本的修饰按钮位图的索引。 打开**工具箱**，然后拖动**按钮**到**编辑**面板。 单击按钮，然后更改**标题**到`Clear All`， **ID**到`ID_EDIT_CLEAR_ALL`，**映像索引**到`0`，**大型图像索引**到`0`。

4. 保存更改，然后生成并运行应用程序。 应显示随意画图应用程序，并且它应该具有位于窗口而不是菜单栏的顶部功能区栏。 功能区栏应具有一个类别，**主页**，和**主页**应具有一个面板中，**编辑**。 你添加的功能区按钮应在现有的事件处理程序，与关联和**打开**，**关闭**，**保存**，**打印**，和**全部清除**按钮应该按预期方式工作。

[[部分](#top)]

##  <a name="setlook"></a> 设置应用程序的外观

A*视觉管理器*是控制应用程序的所有绘图的全局对象。 由于原始随意画图应用程序使用 Office 2000 用户界面 (UI) 样式，该应用程序可能看起来过时。 你可以重置此应用程序，使它类似于 Office 2007 应用程序使用 Office 2007 视觉管理器。

### <a name="to-set-the-look-of-the-application"></a>若要设置的应用程序的外观

1. 在`CMainFrame::OnCreate`函数中，键入以下代码以更改默认视觉管理器和样式。

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

2. 保存更改，然后生成并运行应用程序。 应用程序 UI 应类似于 Office 2007 用户界面。

[[部分](#top)]

## <a name="next-steps"></a>后续步骤

你已修改经典的 Scribble 1.0 MFC 示例，以使用功能区设计器。 现在请转到[第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。

## <a name="see-also"></a>请参阅

[演练](../mfc/walkthroughs-mfc.md)  
[演练： 更新 MFC 随意画图应用程序 （第 2 部分）](../ mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md）  
