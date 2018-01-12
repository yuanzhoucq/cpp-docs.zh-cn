---
title: "创建 COM 接口 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.com.creating.interfaces
dev_langs: C++
helpviewer_keywords: COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7b5820686c3e6f01c37cbf527d0e631e5bcc25c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-com-interface-visual-c"></a>创建 COM 接口 (Visual C++)
Visual c + + 提供向导和模板来创建用于 COM 对象和自动化类 COM 定义接口和支持的项目。  
  
 可以使用这些向导执行以下三个常见任务：  
  
-   [向 MFC 项目添加 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     在创建 MFC 项目使用后向 MFC 应用程序添加 ATL 支持[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)，然后运行**到 MFC 添加 ATL 支持**代码向导。 此支持仅适用于简单的 MFC 可执行文件或 DLL 项目的 COM 对象。 这些 ATL 对象可能具有多个接口。  
  
-   [创建 MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     打开[MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)来创建具有调度接口和事件映射分别在.idl 文件和控件的类中定义的 ActiveX 控件。  
  
-   [添加 ATL 控件](../atl/reference/adding-an-atl-control.md)  
  
     结合使用[ATL 项目向导](../atl/reference/atl-project-wizard.md)和[ATL 控件向导](../atl/reference/atl-control-wizard.md)创建 ATL ActiveX 控件。  
  
     如上面所述，还可以向具有向其添加 ATL 支持 MFC 项目添加 ATL 控件。 此外，如果你选择**ATL 控件**中**添加类**对话框中，并且你已经不尚未添加 ATL 支持向 MFC 项目，Visual Studio 将显示对话框中确认添加 ATL 支持添加到你MFC 项目。  
  
     此向导中的项目类生成 IDL 源和 COM 映射。  
  
 ATL 项目打开，一旦[添加类](../ide/add-class-dialog-box.md)对话框中显示其他向导和模板将 COM 接口添加到你的项目的选择。 以下向导允许你建立对象的一个或多个接口：  
  
-   [ATL COM+ 1.0 组件向导](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)  
  
-   [ATL Active Server Page 组件向导](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [ATL 控件向导](../atl/reference/atl-control-wizard.md)  
  
 此外，你可以实现新接口对 COM 控件通过右键单击类视图中的对象的控件类并单击[实现接口](../ide/implement-interface-wizard.md)。  
  
> [!NOTE]
>  Visual Studio 不提供向导，将接口添加到项目。 你可以将接口添加到 ATL 项目或[向 MFC 项目添加 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)通过添加简单对象使用[ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)。 或者，打开项目的.idl 文件，然后通过键入创建接口：  
  
```  
interface IMyInterface {  
};  
  
```  
  
 请参阅[实现接口](../ide/implementing-an-interface-visual-cpp.md)和[向 ATL 项目添加对象和控件](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)有关详细信息。  
  
 Visual c + + 提供多种方式来查看和[编辑 COM 接口](../ide/editing-a-com-interface.md)定义为你的项目。 [类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)显示任何接口或调度接口在 c + + 项目中的.idl 文件中定义的图标。  
  
 对于基于 ATL COM 对象类，类视图中读取要显示的 ATL 类与它实现任何接口之间的关系的 ATL 类中的 COM 映射。  
  
 在类视图和其快捷菜单中，您可以使用接口，如下所示：  
  
-   将 ATL 对象添加到基于 MFC 的应用程序。  
  
-   添加方法、 属性和事件。  
  
-   直接跳转到代码项的接口通过双击项。  
  
## <a name="see-also"></a>请参阅  
 [使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)