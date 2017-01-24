---
title: "添加类 (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.classes.adding"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 添加类"
  - "类 [C++], 添加"
  - "类 [C++], 创建"
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 添加类 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要在 Visual C\+\+ 项目中添加类，请在**“解决方案资源管理器”**中右击该项目，单击**“添加”**，然后单击**“类”**。  此时会打开[“添加类”对话框](../ide/add-class-dialog-box.md)对话框。  
  
 添加类时，必须指定与 MFC 或 ATL 中已存在的类不同的名称。  如果在任一个库中已存在所指定的名称，则 Visual C\+\+ 会显示一条消息，指出所指定的名称为保留名称。  
  
 如果项目命名约定要求使用某个现有名称，则只需更改名称中的一个或多个字母的大小写，因为 Visual C\+\+ 区分大小写。  例如，虽然不能将某个类命名为 `CDocument`，但可以将其命名为 `cdocument`。  
  
## 您要添加哪种类？  
 在**“添加类”**对话框中，当在左侧窗格中展开**“Visual C\+\+”**节点时，将会显示多组已安装的模板。  这些组包括**“CLR”**、**“ATL”**、**“MFC”**和**“C\+\+”**。  如果选择某个组，则将在中间窗格中显示该组中可用模板的列表。  每个模板都包含某个类所需的文件和源代码。  
  
 若要生成新类，请在中间窗格内选择一个模板，在**“名称”**框中键入该类的名称，然后单击**“添加”**。  此时会打开**“添加类向导”**，这样您就可为该类指定选项。  
  
-   有关如何创建 MFC 类的更多信息，请参见[MFC 类](../mfc/reference/adding-an-mfc-class.md)。  
  
-   有关如何创建 ATL 类的更多信息，请参见[ATL Simple Object](../atl/reference/adding-an-atl-simple-object.md)。  
  
> [!NOTE]
>  **“向 MFC 添加 ATL 支持”**模板不能创建类，但是可以配置项目以使用 ATL。  有关更多信息，请参见[MFC 项目中的 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
 若要创建不使用 MFC、ATL 或 CLR 的 C\+\+ 类，请使用已安装模板的**“C\+\+”**组中的**“C\+\+ 类”**模板。  有关更多信息，请参见[添加一般 C\+\+ 类](../ide/adding-a-generic-cpp-class.md)。  
  
 有两种基于窗体的 C\+\+ 类可用。  第一种 [CFormView Class](../mfc/reference/cformview-class.md) 可创建 MFC 类。  第二种可创建 CLR Windows 窗体类。  
  
## 请参阅  
 [创建基于窗体的 MFC 应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)   
 [“添加类”对话框](../ide/add-class-dialog-box.md)   
 [使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)