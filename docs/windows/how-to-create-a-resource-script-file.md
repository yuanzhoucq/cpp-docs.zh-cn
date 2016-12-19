---
title: "How to: Create a Resource Script File | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "rc files, creating"
  - ".rc files, creating"
  - "resource script files, creating"
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Create a Resource Script File
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  资源编辑器在 Express 版本中不可用。  
>   
>  本材料适用于 Windows 桌面应用程序。 .NET 语言的项目不使用资源脚本文件。 有关更多信息，请参阅[资源文件](../mfc/resource-files-visual-studio.md)。  
  
### 创建新资源脚本 \(.rc\) 文件  
  
1.  将焦点置于 `Solution Explorer` 中的现有项目文件夹中，例如“MyProject”。  
  
    > [!NOTE]
    >  不要将项目文件夹与解决方案资源管理器中的解决方案文件夹混淆。 如果将焦点放在解决方案文件夹中，“添加新项”对话框（第 3 步中）中的选项将有所不同。  
  
2.  在“项目”菜单中，单击“添加新项”。  
  
3.  在“添加新项”对话框中，单击 **Visual c \+ \+** 文件夹然后选择右窗格中的“资源文件 \(.rc\)”。  
  
4.  在“名称”文本框中为资源脚本文件命名，然后单击“打开”。  
  
 现在可以[创建](../windows/how-to-create-a-resource.md)新资源并将其添加到你的 .rc 文件中。  
  
> [!NOTE]
>  只能向加载到 Visual Studio IDE 的现有项目添加资源脚本（.rc 文件）。 不能创建独立.rc 文件（项目外的文件）。 可以随时创建[资源模板](../windows/how-to-use-resource-templates.md)（.rct 文件）。  
  
 RRequirements  
  
 Win32  
  
## 请参阅  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)