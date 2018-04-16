---
title: "用代码向导 （c + +） 添加功能 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.classes
dev_langs:
- C++
helpviewer_keywords:
- code wizards [C++]
- wizards [C++], code
- Visual C++ projects, adding functionality
- projects [C++], adding functionality
- class wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c27aeb10a58c828b6503ce96ddaadf138c258f27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-functionality-with-code-wizards-c"></a>用代码向导 （c + +） 添加功能
一旦你已创建了项目，你将想要更改或添加到该项目的功能。 此类任务包括创建新类，添加新成员函数、 变量和添加自动化方法和属性。 代码向导旨在让你执行所有这些操作。  
  
> [!NOTE]
>  现在可以添加消息处理程序和将消息映射到它们以及重写 MFC 虚函数使用[属性窗口](/visualstudio/ide/reference/properties-window)。  
  
## <a name="accessing-visual-c-code-wizards"></a>访问 Visual c + + 代码向导  
 有三个位置，可以访问 Visual c + + 代码向导的位置：  
  
-   上**项目**菜单上，**添加新项**命令允许你打开`Add New Item`对话框中，可帮助你将新文件添加到你的项目。 **添加类**命令显示[添加类](../ide/add-class-dialog-box.md)对话框中，而该对话框打开向导的每个类类型你可以添加到你的项目。 **添加资源**命令显示[添加资源](../windows/add-resource-dialog-box.md)对话框中，从中你可以创建或选择要添加到你的项目的资源。  
  
     如果你突出显示一个类或接口，并在类视图中，项目中**项目**菜单还会显示以下命令：  
  
    -   **实现接口**（从仅控件类）  
  
    -   **添加函数**  
  
    -   **添加变量**  
  
    -   **添加连接点**（仅适用于 ATL 类）  
  
    -   **将方法添加**（来自仅接口）  
  
    -   **将属性添加**（来自仅接口）  
  
    -   **添加事件**（从仅控件类）  
  
-   在**解决方案资源管理器**，右键单击任何文件夹，然后单击**添加**从快捷菜单，可以添加新的或现有文件、 更多的文件夹、 项、 类、 资源，和 Web 引用项目。  
  
-   从[类视图窗口](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，右键单击相应的节点，然后单击**添加**从快捷菜单，可以添加函数、 变量、 类、 属性、 方法、 事件、 接口连接点或其他代码，以便你的项目。  
  
    > [!NOTE]
    >  Visual Studio 不提供向导，将接口添加到项目。 你可以将接口添加到 ATL 项目或[向 MFC 项目添加 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)通过添加简单对象使用[ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)。 或者，打开项目的.idl 文件，然后通过键入创建接口：  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     请参阅[实现接口](../ide/implementing-an-interface-visual-cpp.md)和[向 ATL 项目添加对象和控件](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)有关详细信息。  
  
    |从访问代码向导|描述|  
    |-----------------------------|-----------------|  
    |添加新项|添加新项代码向导添加到你的项目的源文件。 如有必要，创建其他目录包含项目的生成引擎需要找到它们的文件。 添加项图标中可用的代码向导包括：<br /><br /> -添加 c + + 源代码文件 （.cpp、.h、.idl、.rc、.srf、.def、.rgs）。<br />添加 Web 开发文件 （.html、.asp、.css、.xml）。<br />添加实用工具和资源文件 （.bmp、.cur、.ico、.rct、.sql、.txt）。<br /><br /> 通常，这些代码向导不要求你提供的任何信息，但将文件添加到你的开发树。 你可以重命名属性窗口中的文件。|  
    |“解决方案资源管理器”|可从解决方案资源管理器的代码向导依赖于光标焦点所在右键单击某个项时。 如果**添加**选项未显示时右键单击项目，然后将光标上移一级开发树中，然后重试。 代码向导将始终将放置在开发树中的适当位置中的其他代码不管光标所在。 代码向导可从解决方案资源管理器包括：<br /><br /> 添加类 (将打开**添加类**对话框，其中包含新的代码向导)。<br />添加资源 (新的、 导入或自定义)。<br />添加 Web 引用。|  
    |类视图|类视图中可用的代码向导依赖于光标焦点所在右键单击项目时。 如果**添加**选项未显示时右键单击某项，然后将光标上移一级类树中，然后重试。 代码向导将始终将放置在开发树中的适当位置中的其他代码不管光标所在。 代码向导可从类视图包括：<br /><br /> -   [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)。<br />-   [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)。<br />-   [添加类](../ide/adding-a-class-visual-cpp.md)。<br />-   [实现接口](../ide/implement-interface-wizard.md)（从仅控件类）<br />-   [添加连接点](../ide/implement-connection-point-wizard.md)（仅适用于 ATL 类）<br />-   [将方法添加](../ide/add-method-wizard.md)（来自仅接口）<br />-   [将属性添加](../ide/names-add-property-wizard.md)（来自仅接口）<br />-   [添加事件](../ide/add-event-wizard.md)（从仅控件类）<br /><br /> 添加类选项打开**添加类**对话框中，所有的新添加类代码向导使你可以访问。|  
  
## <a name="see-also"></a>请参阅  
 [重写虚函数](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)   
 [使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Visual c + + 项目类型](../ide/visual-cpp-project-types.md)   
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)