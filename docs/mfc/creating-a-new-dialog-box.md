---
title: "Creating a New Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.dialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dialog boxes, creating"
  - "Dialog editor, creating dialog boxes"
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a New Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 创建新对话框  
  
1.  在[资源视图](../windows/resource-view-window.md)中，右击 .rc 文件，然后从快捷菜单中选择**“添加资源”**。  
  
    > [!NOTE]
    >  如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**“添加资源”**对话框中，从**“资源类型”**列表中选择**“Dialog”**，然后单击**“新建”**。  
  
     如果一个加号 \(\+\) 出现在对话框资源类型的旁边，则表示对话框模板可用。  单击加号展开模板列表，选择一个模板，然后单击“新建”。  
  
     新对话框随即在对话框编辑器中打开。  
  
     还可以[在对话框编辑器中打开现有对话框进行编辑](../mfc/viewing-and-editing-resources-in-a-resource-editor.md)。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [How to: Create a Resource](../windows/how-to-create-a-resource.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Dialog Editor](../mfc/dialog-editor.md)