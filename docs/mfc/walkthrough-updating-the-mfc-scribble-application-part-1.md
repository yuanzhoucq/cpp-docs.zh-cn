---
title: "演练：更新 MFC 随意画图应用程序（第 1 部分） | Microsoft Docs"
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
  - "示例 [C++], 更新现有应用程序"
  - "MFC 功能包, 更新现有应用程序"
  - "Office Fluent UI, 迁移到"
  - "功能区 UI, 迁移到"
  - "示例 [C++], 更新现有应用程序"
  - "演练 [C++], 更新现有应用程序"
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
caps.latest.revision: 54
caps.handback.revision: 50
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：更新 MFC 随意画图应用程序（第 1 部分）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本演练演示如何修改现有的 MFC 应用程序使用功能区用户界面 \(ui\)。  Visual Studio 支持 Office 2007 功能区和 Windows 7 风景功能区。  有关功能区界面内容的详细信息，请参见在MSDN Web 网站上的 [功能区](http://go.microsoft.com/fwlink/?LinkId=129233) 。  
  
 本演练修改允许您使用鼠标创建线条图形的传统的 scribble MFC 示例 1.0。  此演练部分演示如何修改 SCRIBBLE 示例，以使其显示功能区栏。  [Part 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) 增加了更多按钮的功能导航栏。  
  
## 系统必备  
 [Visual C\+\+ 示例](../top/visual-cpp-samples.md)  
  
 [Visual C\+\+ 示例](../top/visual-cpp-samples.md)  
  
##  <a name="top"></a> 各节内容  
 此演练部分包含以下部分：  
  
-   [替换基类](#replaceClass)  
  
-   [位图添加到项目](#addBitmap)  
  
-   [将功能区资源添加到项目](#addRibbon)  
  
-   [创建功能区栏的实例](#createInstance)  
  
-   [添加功能区类别](#addCategory)  
  
-   [设置应用程序的外观](#setLook)  
  
##  <a name="replaceClass"></a> 替换基类  
 若要将支持菜单到应用程序支持功能区的应用程序，必须更新从基类派生应用程序、框架窗口和工具栏选件类。\(建议您不要修改原始 scribble 示例；用清理 scribble 项目，将其复制到另一个目录，然后修改副本。\)  
  
#### 替换在 scribble 应用程序的基类  
  
1.  在scribble.cpp中，验证`CScribbleApp::InitInstance` 包括一个调用到 [AfxOleInit](../Topic/AfxOleInit.md)。  
  
2.  将下面的代码添加到 stdafx.h 文件：  
  
    ```  
    #include <afxcontrolbars.h>  
    ```  
  
3.  在scribble.h，修改`CScribbleApp`类中的定义，使其从[CWinAppEx Class](../mfc/reference/cwinappex-class.md)。  
  
    ```  
    class CScribbleApp: public CWinAppEx  
    ```  
  
4.  Scribble 1.0 编写时，windows 应用程序使用初始化 \(.ini\) 文件保存用户首选项数据。  修改 scribble 存储用户首选项在注册表，来代替初始化文件。  要设置注册表项和基准，键入下面的代码在 `CScribbleApp::InitInstance` 在 `LoadStdProfileSettings()` 之后。  
  
    ```  
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));  
    SetRegistryBase(_T("Settings"));  
    ```  
  
5.  对于多文档界面（MDI）应用程序的主框架不再从`CMDIFrameWnd`类派生。  它从[CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) 类派生。  
  
     在mainfrm.h 和 mainfrm.cpp文件，替换到所有引用`CMDIFrameWnd`为 `CMDIFrameWndEx`。  
  
6.  在childfrm.h 和 childfrm.cpp文件，替代`CMDIChildWnd` 为 `CMDIChildWndEx`。  
  
     在childfrm. h文件中，替代`CSplitterWnd` 为 `CSplitterWndEx`。  
  
7.  使用新 MFC 选件类修改工具栏和状态栏。  
  
     在 mainfrm.h 文件：  
  
    1.  将 `CToolBar` 替换为 `CMFCToolBar`。  
  
    2.  将 `CStatusBar` 替换为 `CMFCStatusBar`。  
  
8.  在 mainfrm.cpp 文件：  
  
    1.  将 `m_wndToolBar.SetBarStyle` 替换为 `m_wndToolBar.SetPaneStyle`。  
  
    2.  将 `m_wndToolBar.GetBarStyle` 替换为 `m_wndToolBar.GetPaneStyle`。  
  
    3.  将 `DockControlBar(&m_wndToolBar)` 替换为 `DockPane(&m_wndToolBar)`。  
  
9. 在 ipframe.cpp 文件，注释代码以下三行。  
  
    ```  
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);  
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);  
    pWndFrame->DockPane(&m_wndToolBar);  
    ```  
  
10. 如果您打算静态链接到您的应用程序中，添加以下代码添加到项目资源 \(.rc\) 文件的开头。  
  
    ```  
    #include "afxribbon.rc"  
    ```  
  
     该afxribbon.rc文件包含需要在运行时资源。  该[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)自动包含这个文件，当您创建应用程序。  
  
11. 保存改变的，然后生成并运行应用程序。  
  
 \[[各节内容](#top)\]  
  
##  <a name="addBitmap"></a> 位图添加到项目  
 下四个步骤本演练需要位图资源。  可以获取适当的位图各种方法：  
  
-   用[Resource Editors](../mfc/resource-editors.md)创建自己的位图。  或者使用资源编辑器从所包含的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]的便携式网络图形（PNG）的图像组合的位图。  这些图像是在 `VS2008ImageLibrary`目录。  
  
     但是，功能区用户界面要求某些位图支持透明的图像。  透明位图使用的32位的像素，其中24位指定的颜色的红色，绿色和蓝色分量和8位定义了一个*alpha channel*来指定颜色的透明度。  当前资源编辑器可以查看，但是，不改变位图具有 32 个像素。  结果，请使用外部图像编辑器而不是资源编辑器操作透明位图。  
  
-   复制另一个应用程序的合适的资源文件添加到您的项目从该文件中导入位图。  
  
 本演练将一个应用程序的资源文件在示例内容。  
  
#### 向项目中添位图  
  
1.  使用文件资源管理器下面的.bmp文件的资源目录（`res`）复制RibbonGadgets样例：  
  
    1.  复制 main.bmp 到 scribble 项目。  
  
    2.  复制 filesmall.bmp 和 filelarge.bmp 到 scribble 项目。  
  
    3.  提交新的副本 filelarge.bmp 和 filesmall.bmp 文件，但保存在 RibbonGadgets 示例的副本。  对复制 homesmall.bmp 和 homelarge.bmp 重命名再将复制到您的 scribble 项目。  
  
    4.  制作 toolbar.bmp 文件复本，但保存在 RibbonGadgets 示例的副本。  将该副本 panelicons.bmp 重命名然后将复制到您的 scribble 项目。  
  
2.  导入 MFC 应用程序的位图。  在资源查看 ，双击scribble.rc的节点，双击位图 节点，然后单击添加资源。  在显示的对话框中，单击导入。  浏览到`res` 目录，选择main.bmp文件，然后单击打开。  
  
     main.bmp 位图包含一个 26x26 图像。  更改位图的 ID 更改为 IDB\_RIBBON\_MAIN。  
  
3.  导入附加到应用程序按钮的"文件"菜单的位图。  
  
    1.  导入 filesmall.bmp 文件，包含十个 16x16 \(16x160\) 图像。  因为我们只需要8个16x16的图像（16X128），使用资源查看 到该位图的宽度变化从160到128。  更改位图的 ID 更改为IDB\_RIBBON\_FILESMALL。  
  
    2.  导入 filelarge.bmp，包含八个 32x32 \(32x256\) 图像。  更改位图的 ID 更改为 IDB\_RIBBON\_FILELARGE。  
  
4.  导入功能区类别和面板的位图。  在功能区栏的每个选项是类，并包含文本标签和可选图像。  
  
    1.  导入 homesmall.bmp 位图，包含一个小按钮位图的八个 16x16 图像。  更改位图的 ID 更改为 IDB\_RIBBON\_HOMESMALL。  
  
    2.  导入 homelarge.bmp 位图，包含用按钮位图的八个 32x32 图像。  更改位图的 ID 更改为 IDB\_RIBBON\_HOMELARGE 。  
  
5.  导入调整大小的功能区面板的位图。  如果功能区上太小而无法显示整个面板，在调整操作之后使用这些位图或面板图标。  
  
    1.  导入 panelicons.bmp 位图，包含八个 16x16 图像。  在位图编辑器的属性窗口，调整位图到64（16X64）的宽度。  更改位图的 ID 更改为 IDB\_PANEL\_ICONS。  
  
 \[[各节内容](#top)\]  
  
##  <a name="addRibbon"></a> 将功能区资源添加到项目  
 当您将使用菜单到应用程序使用一功能区的应用程序时，您不必移除或禁用现有菜单。  相反，您创建一个功能区资源，添加功能区按钮，然后将新的按钮与现有菜单项。  虽然菜单不再可见，从功能区栏的消息传递菜单进行路由。  此外，菜单快捷方式继续工作。  
  
 功能区都包含应用程序按钮，在功能区的左上角端的大按钮和一个或多个类别选项。  每个类别选项包含作为区按钮和控件的容器的一个或多个面板。  下面的过程演示如何创建功能区资源然后自定义应用程序按钮。  
  
#### 向项目添加功能资源  
  
1.  在“项目”菜单上，单击“添加资源”。  
  
2.  在“添加资源”对话框中，选择功能区，再单击新建。  
  
     Visual Studio 会创建一个功能资源并在设计试图中打开此文件。  功能资源ID是IDR\_RIBBON1，这是显示在资源视图。  功能区上包含一类别和一个面板。  
  
3.  可以通过修改其属性自定义应用程序按钮。  用于此代码的消息 ID 在 scribble 1.0 的菜单已定义。  
  
4.  在设计视图中，单击应用程序按钮显示其属性。  按下面改变属性的值：Image改为 `IDB_RIBBON_MAIN`，Prompt 改为`File`，Keys改为`f`，Large Images 改为 `IDB_RIBBON_FILELARGE`， Small Images 改为 `IDB_RIBBON_FILESMALL`。  
  
5.  以下修改创建显示的菜单当用户单击应用程序按钮。  单击旁的省略号（**...**），来打开项目编辑器。  
  
    1.  单击添加来添加一个按钮。  改变Caption 为 `&New`，Caption 为 `ID_FILE_NEW`，Image 为 `0`，Image Large 为 `0`。  
  
    2.  单击Add第二个按钮。  改变Caption 为 `&Save`，ID 为 `ID_FILE_SAVE`，Image 为 `2`，Image Large 为 `2`。  
  
    3.  单击Add 添加第三个按钮。  改变Caption为`Save&As`, ID为`ID_FILE_SAVE_AS`,Image 为 `3`,Image Large为`3`.  
  
    4.  单击Add增加第四个按钮。  改变 Caption为`&Print`, ID为`ID_FILE_PRINT`, Image 为`4`, Image Large为`4`。  
  
    5.  更改项目类型为Separator，然后单击Add。  
  
    6.  更改项目类型为Button。  单击Add添加第五个按钮。  改变 Caption为  `&Close`, ID为 `ID_FILE_CLOSE`, Image 为 `5`, Image Large为 `5`。  
  
6.  以下修改创建一个子菜单在上一步中创建的打印"按钮下。  
  
    1.  点击Print 按钮，改变项目 类型为Label，然后单击插入。  更改Caption 为`预览版和打印文档`。  
  
    2.  点击Print按钮，改变项目 类型为Button，然后单击Insert。  改变 Caption为`&Print`, ID为`ID_FILE_PRINT`, Image 为`4`, Image Large为`4`。  
  
    3.  点击打印按钮，然后单击插入添加一个按钮。  改变 Caption为  `&Quick Print`, ID为 `ID_FILE_PRINT_DIRECT`, Image 为 `7`, Image Large为 `7`。  
  
    4.  点击打印按钮，然后单击插入添加另一个按钮。  改变 Caption为  `&Print Pre`, ID 为 `ID_FILE_PRINT_PREVIEW`, Image 为 `6`, Image Large为 `6`。  
  
    5.  您现在已经修改了Main Items。  单击“关闭”以退出项目编辑器。  
  
7.  以下修改创建出现在应用程序中按钮菜单的底部的一个退出点按钮。  
  
    1.  在“属性”窗口中，单击省略号 \(**...**\) ， 在Button旁边，用来打开项目编辑器。  
  
    2.  单击添加来添加一个按钮。  改变Caption 为 `E&xit`, ID 为 `ID_APP_EXIT`, Image 为`8`。  
  
 \[[各节内容](#top)\]  
  
##  <a name="createInstance"></a> 创建功能区栏的实例  
 当应用程序启动时，下面的步骤演示如何创建功能区栏的实例。  若要添加功能区栏到应用程序中，声明在 mainfrm.h 文件的功能区栏。  然后，在 mainfrm.cpp 文件，加载功能区资源编写代码。  
  
#### 创建功能条的实例  
  
1.  在mainfrm.h文件，一个数据成员添加到`CMainFrame`主框架类定义的受保护的部分。  此成员表示功能区栏。  
  
    ```  
    // Ribbon bar for the application  
    CMFCRibbonBar  m_wndRibbonBar;  
    ```  
  
2.  在mainfrm.cpp文件，在`CMainFrame::OnCreate` 函数的末尾最后`return`之前添加下面的代码语句。  这将创建功能区栏的一个实例。  
  
    ```  
    // Create the ribbon bar  
    if (!m_wndRibbonBar.Create(this))  
    {  
    return -1;   //Failed to create ribbon bar  
    }  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);  
    ```  
  
 \[[各节内容](#top)\]  
  
##  <a name="addCategory"></a> 自定义功能区资源  
 现在已经创建的应用程序按钮，可以向元素添加到功能区。  
  
> [!NOTE]
>  本演练提供所有面板中使用同一面板图标。  但是，您可以使用其他图像列表索引显示其他图标。  
  
#### 添加一个 home 类别和编辑面板  
  
1.  scribble 程序只需要一个类别。  在设计视图中，单击Category显示其属性。  按下面更改属性值：Caption 为 `&Home`, Large Images 为 `IDB_RIBBON_HOMELARGE`, Small Images 为 `IDB_RIBBON_HOMESMALL`。  
  
2.  每个功能区类别进行组织到命名的面板。  每个面板包含执行相关操作的一组控件。  此类具有一个面板。  单击Panel，然后更改Caption为 `Edit` ， Image Index 为 `0`。  
  
3.  到Edit面板上，添加一个按钮来负责清除该文件的内容。  此按钮的消息 ID 在 IDR\_SCRIBBTYPE 菜单资源已经定义。  指定`Clear All`为按钮文本和装饰按钮位图的索引。  打开工具箱，拖一个按钮 到编辑 面板。  点击按钮，改变Caption 为 `Clear All`, ID为 `ID_EDIT_CLEAR_ALL`, Image Index 为 `0`, Large Image Index 为 `0`。  
  
4.  保存改变的，然后生成并运行应用程序。  应显示 scribble 应用程序，它应有功能区栏位于窗口的顶部而不是菜单栏。  功能栏应该有一个类，Home，Home应该有一个面板Edit。  您添加的功能区按钮应与现有的事件处理程序相关联，打开, 关闭, 保存, 打印, 和清除所有按钮应该如预期般运作。  
  
 \[[各节内容](#top)\]  
  
##  <a name="setLook"></a> 设置应用程序的外观  
 一个*视觉管理员*是控制所有绘制一个应用程序的全局对象。  由于原始 scribble 应用程序使用 Office 2000 用户界面 \(UI\) 样式，应用程序可能看起来古板。  可以重置应用程序使用 Office 2007 视觉管理器，以便它类似于 Office 2007 应用程序。  
  
#### 设置应用程序的外观  
  
1.  在`CMainFrame::OnCreate`函数，键入如下代码来改变默认的可视化管理和风格。  
  
    ```  
    // Set the default manager to Office 2007   
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));  
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);  
    ```  
  
2.  保存改变的，然后生成并运行应用程序。  应用程序 UI 应类似于 Office 2007 的 UI。  
  
 \[[各节内容](#top)\]  
  
## 后续步骤  
 您修改 1.0 传统的 scribble MFC 示例使用功能区设计器。  现在进入 [第二部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。  
  
## 请参阅  
 [演练](../mfc/walkthroughs-mfc.md)   
 [演练：更新 MFC 随意画图应用程序（第 2 部分）](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)