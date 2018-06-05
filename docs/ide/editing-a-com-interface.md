---
title: 编辑 COM 接口 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.com.editing.interfaces
dev_langs:
- C++
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd7a61593a1024c00c0fd0de6bd62ff3ee9323b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338677"
---
# <a name="editing-a-com-interface"></a>编辑 COM 接口
使用“类视图”上下文菜单的命令，可以在 Visual C++ 项目中为 COM 接口定义新方法和属性。 此外，从工具箱还可以定义 ActiveX 控件的事件。  
  
 对于 ATL 和基于 MFC 的 COM 对象类，可以在编辑接口的同时编辑类实现。  
  
> [!NOTE]
>  对于从“添加类”对话框以外定义的接口，Visual C++ 将方法或属性添加到 .idl 文件，并将存根添加到实现方法的类，即使已手动添加接口也是如此。  
  
 以下三个向导有助于自定义现有接口。 可以从类视图中获取：  
  
|向导|项目类型|  
|------------|------------------|  
|[添加属性向导](../ide/names-add-property-wizard.md)|支持 ATL 的 ATL 或 MFC 项目。 右键单击要添加属性的接口。<br /><br /> Visual C++ 删除项目类型并相应修改“添加属性向导”中的选项：<br /><br /> -   对于使用 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)创建的项目中的调度接口，调用“添加属性向导”将提供特定于 MFC 的选项。<br />-   对于 MFC ActiveX 控件接口，“添加属性向导”将提供一系列常用方法和属性，你可为你的控件使用所述的这些方法和属性，也可进行自定义。<br />-   对于所有其他接口，“添加属性向导”将提供可用于大多数情况的选项。|  
|[添加方法向导](../ide/add-method-wizard.md)|支持 ATL 的 ATL 或 MFC 项目。 右键单击要添加方法的接口。<br /><br /> Visual C++ 删除项目类型并相应修改“添加方法向导”中的选项：<br /><br /> -   对于使用 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)创建的项目中的调度接口，调用“添加方法向导”将提供特定于 MFC 的选项。<br />-   对于 MFC ActiveX 控件接口，“添加方法向导”将提供一系列常用方法和属性，你可为你的控件使用所述的这些方法和属性，也可进行自定义。<br />-   对于所有其他接口，“添加方法向导”将提供可用于大多数情况的选项。|  
  
 此外，在“类视图”中右键单击对象的控件类并单击[实现接口](../ide/implement-interface-wizard.md)之后，可在 COM 控件上实现新的接口。  
  
## <a name="see-also"></a>请参阅  
 [使用资源文件](../windows/working-with-resource-files.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Visual C++ 项目类型](../ide/visual-cpp-project-types.md)