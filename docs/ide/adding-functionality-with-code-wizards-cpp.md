---
title: "用代码向导添加功能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类向导 [C++]"
  - "代码向导 [C++]"
  - "项目 [C++], 添加功能"
  - "Visual C++ 项目, 添加功能"
  - "向导 [C++], 代码"
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用代码向导添加功能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建了项目后，需要更改或添加项目的功能。  这类任务包括创建新类，添加新成员函数和变量，以及添加自动化方法和属性。  代码向导旨在使您可以完成所有这些任务。  
  
> [!NOTE]
>  现在可以添加消息处理程序并将消息映射到它们，而且可以使用[“属性”窗口](../Topic/Properties%20Window.md)重写 MFC 虚函数。  
  
## 访问 Visual C\+\+ 代码向导  
 可以从三个位置访问 Visual C\+\+ 代码向导：  
  
-   在**“项目”**菜单上，利用**“添加新项”**命令可显示`Add New Item`对话框，该对话框可帮助您将新文件添加到项目中。  “添加类”命令显示[添加类](../ide/add-class-dialog-box.md)对话框，而该对话框打开可以添加到项目中的每个类类型的向导。  **“添加资源”**命令会显示[“添加资源”](../windows/add-resource-dialog-box.md)对话框，您可以从中创建或选择要添加到项目的资源。  
  
     如果在“类视图”中突出显示项目中的类或者接口，则“项目”菜单还显示下列命令：  
  
    -   **实现接口**（仅限从控件类中）  
  
    -   **添加函数**  
  
    -   **添加变量**  
  
    -   添加连接点（仅限 ATL 类）  
  
    -   添加方法（仅限从接口中）  
  
    -   **添加属性**（仅限从接口中）  
  
    -   **添加事件**（仅限从控件类中）  
  
-   在**“解决方案资源管理器”**中，右击任何一个文件夹并单击快捷菜单中的**“添加”**，可以向项目中添加新的或现有的文件，添加更多的文件夹、项、类、资源和 Web 引用。  
  
-   从[“类视图”窗口](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，右击适当的节点并单击快捷菜单中的“添加”，可以向项目中添加函数、变量、类、属性、方法、事件、接口、连接点或其他代码。  
  
    > [!NOTE]
    >  Visual Studio 不提供向项目添加接口的向导。  通过使用 [ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)添加简单对象，可向 ATL 项目或向[“向 MFC 项目添加 ATL 支持”](../mfc/reference/adding-atl-support-to-your-mfc-project.md)添加接口。  或者，可打开项目的 .idl 文件并通过键入以下内容创建接口：  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     有关更多信息，请参见[实现接口](../ide/implementing-an-interface-visual-cpp.md)和[向 ATL 项目添加对象和控件](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
    |访问代码向导的方法|说明|  
    |---------------|--------|  
    |添加新项|“添加新项”代码向导向项目添加源文件。  如果需要，会创建附加的目录来包含文件，项目生成引擎应该可以在这些目录中找到文件。  可通过“添加项”图标获得的代码向导包括：<br /><br /> -   添加 C\+\+ 源文件（.cpp、.h、.idl、.rc、.srf、.def、.rgs）。<br />-   添加 Web 开发文件（.html、.asp、.css、.xml）。<br />-   添加实用工具和资源文件（.bmp、.cur、.ico、.rct、.sql, .txt）。<br /><br /> 这些代码向导一般不要求任何信息，而是向开发树中添加文件。  可以在属性窗口中重命名文件。|  
    |解决方案资源管理器|解决方案资源管理器中可用的代码向导取决于右击某个项时光标焦点所在的位置。  如果右击某个项时没有出现“添加”选项，则将光标在开发树中上移一级然后重试。  无论光标在何位置，代码向导始终将附加代码放在开发树中的适当位置。  解决方案资源管理器中可用的代码向导包括：<br /><br /> -   添加类（打开包含新代码向导的**添加类**对话框）。<br />-   添加资源（“新建”、“导入”或“导出”）。<br />-   添加 Web 引用。|  
    |类视图|“类视图”中可用的代码向导取决于右击某个项时光标焦点所在的位置。  如果右击某项时没有出现“添加”选项，则将光标在类树中上移一级然后重试。  无论光标在何位置，代码向导始终将附加代码放在开发树中的适当位置。  “类视图”中可用的代码向导包括：<br /><br /> -   [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)。<br />-   [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)。<br />-   [添加类](../ide/adding-a-class-visual-cpp.md)。<br />-   [实现接口](../ide/implement-interface-wizard.md)（仅限从控件类中）<br />-   [添加连接点](../ide/implement-connection-point-wizard.md)（仅限 ATL 类）<br />-   [添加方法](../ide/add-method-wizard.md)（仅限从接口中）<br />-   [添加属性](../ide/names-add-property-wizard.md)（仅限从接口中）<br />-   [添加事件](../ide/add-event-wizard.md)（仅限从控件类中）<br /><br /> “添加类”选项将打开“添加类”对话框，通过它可以访问所有的新“添加类”代码向导。|  
  
## 请参阅  
 [重写虚函数](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)   
 [使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Visual C\+\+ 项目类型](../ide/visual-cpp-project-types.md)   
 [为 Visual C\+\+ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)