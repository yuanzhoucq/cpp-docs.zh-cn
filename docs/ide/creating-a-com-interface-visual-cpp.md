---
title: 创建 COM 接口 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.com.creating.interfaces
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2844e9051c5e6adf14085bcd7bfcd8096c6f8f7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332577"
---
# <a name="creating-a-com-interface-visual-c"></a>创建 COM 接口 (Visual C++)
Visual C++ 提供了向导和模板，它们用于创建使用 COM 为 COM 对象和自动化类定义接口和调度接口的项目。  
  
 这些向导可用于执行以下三个常见任务：  
  
-   [向 MFC 项目添加 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     在使用 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)并运行“将 ATL 支持添加到 MFC”代码向导创建 MFC 项目之后，将 ATL 支持添加到 MFC 应用程序。 此支持仅适用于添加到 MFC 可执行文件或 DLL 项目的简单 COM 对象。 这些 ATL 对象可能有多个接口。  
  
-   [创建 MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     打开 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)创建一个 ActiveX 控件，该控件在 .idl 文件中定义了一个调度接口，在控件类中定义了一个事件映射。  
  
-   [添加 ATL 控件](../atl/reference/adding-an-atl-control.md)  
  
     结合使用 [ATL 项目向导](../atl/reference/atl-project-wizard.md)和 [ATL 控件向导](../atl/reference/atl-control-wizard.md)创建 ATL ActiveX 控件。  
  
     还可将 ATL 控件添加到已具有 ATL 支持的 MFC 项目中，如上所述。 此外，如果在“添加类”对话框中选择“ATL 控件”，但尚未将 ATL 支持添加到 MFC 项目，Visual Studio 将显示一个对话框，要求你确认是否将 ATL 支持添加到 MFC 项目。  
  
     此向导在项目类中生成 IDL 源和 COM 映射。  
  
 打开 ATL 项目后，可在[添加类](../ide/add-class-dialog-box.md)对话框选择其他向导和模板，以在项目中添加 COM 接口。 以下向导允许为对象建立一个或多个接口：  
  
-   [ATL COM+ 1.0 组件向导](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)  
  
-   [ATL Active Server Page 组件向导](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [ATL 控件向导](../atl/reference/atl-control-wizard.md)  
  
 此外，在“类视图”中右键单击对象的控件类并单击[实现接口](../ide/implement-interface-wizard.md)之后，可在 COM 控件上实现新的接口。  
  
> [!NOTE]
>  Visual Studio 不提供将接口添加到项目的向导。 可将接口添加到 ATL 项目或通过使用 [ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)添加一个简单项目，从而[向 MFC 项目添加 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。 或者打开项目的 .idl 文件并通过键入以下内容创建接口：  
  
```  
interface IMyInterface {  
};  
  
```  
  
 有关详细信息，请参阅[实现接口](../ide/implementing-an-interface-visual-cpp.md)和[向 ATL 项目添加对象和控件](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
 Visual C++ 提供了多种方式来查看和[编辑为项目定义的 COM 接口](../ide/editing-a-com-interface.md)。 [类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)显示 C++ 项目中 .idl 文件内定义的任何接口或调度接口的图标。  
  
 对于基于 ATL 的 COM 对象类，“类视图”读取 ATL 类中的 COM 映射，以显示 ATL 类与其实现的任何接口之间的关系。  
  
 在“类视图”及其快捷菜单中，可使用以下接口：  
  
-   将 ATL 对象添加到基于 MFC 的应用程序。  
  
-   添加方法、属性和事件。  
  
-   双击项目直接跳转到该项的接口代码。  
  
## <a name="see-also"></a>另请参阅  
 [使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)