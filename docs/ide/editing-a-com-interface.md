---
title: "编辑 COM 接口 | Microsoft Docs"
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
  - "vc.codewiz.com.editing.interfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 接口, 编辑"
  - "方法 [C++], 添加到 COM 接口"
  - "属性 [C++], 添加到 COM 接口"
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 编辑 COM 接口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过使用类视图快捷菜单中的命令，可以为 Visual C\+\+ 项目中的 COM 接口定义新的方法和属性。  另外，从工具箱可以定义 ActiveX 控件的事件。  
  
 对基于 ATL 和 MFC 的 COM 对象类，可以在编辑接口的同时编辑类实现。  
  
> [!NOTE]
>  对已在“添加类”对话框外定义的接口，即使这些接口是手动添加的，Visual C\+\+ 也会将方法或属性添加到 .idl 文件，并将存根 \(stub\) 添加到实现方法的类。  
  
 下列三个向导帮助自定义现有接口。  它们可从类视图获得：  
  
|向导|项目类型|  
|--------|----------|  
|[添加属性向导](../ide/names-add-property-wizard.md)|ATL 项目或支持 ATL 的 MFC 项目。  右击要将属性添加到的接口。<br /><br /> Visual C\+\+ 检测项目类型并相应地在“添加属性向导”中修改选项：<br /><br /> -   对于通过使用 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)创建的项目中的调度接口，调用添加属性向导将提供特定于 MFC 的选项。<br />-   对于 MFC ActiveX 控件接口，“添加属性向导”提供常用方法和属性的列表，它们可用作为控件提供的或自定义的方法和属性。<br />-   对于所有其他接口，“添加属性向导”提供在大多数情况下可用的选项。|  
|[添加方法向导](../ide/add-method-wizard.md)|ATL 项目或支持 ATL 的 MFC 项目。  右击要将方法添加到的接口。<br /><br /> Visual C\+\+ 检测项目类型并相应地在“添加方法向导”中修改选项：<br /><br /> -   对于通过使用 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)创建的项目中的调度接口，调用“添加方法向导”将提供特定于 MFC 的选项。<br />-   对于 MFC ActiveX 控件接口，“添加方法向导”提供常用方法和属性的列表，它们可用作为控件提供的或自定义的方法和属性。<br />-   对于所有其他接口，“添加方法”向导提供在大多数情况下可用的选项。|  
  
 另外，还可通过在类视图中右击对象的控件类然后单击[实现接口](../ide/implement-interface-wizard.md)，在 COM 控件上实现新接口。  
  
## 请参阅  
 [Working with Resource Files](../mfc/working-with-resource-files.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Visual C\+\+ 项目类型](../ide/visual-cpp-project-types.md)