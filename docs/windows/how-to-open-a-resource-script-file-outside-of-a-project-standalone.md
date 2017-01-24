---
title: "How to: Open a Resource Script File Outside of a Project (Standalone) | Microsoft Docs"
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
  - "vc.editors.resource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], viewing"
  - "rc files, viewing resources"
  - ".rc files, viewing resources"
  - "resource script files, viewing resources"
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Open a Resource Script File Outside of a Project (Standalone)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你可以查看 .rc 文件中的资源，而不必打开项目。  .rc 文件将在文档窗口而不是在[资源视图](../windows/resource-view-window.md)窗口打开（如果在项目中打开该文件，则在此窗口打开）。  
  
> [!NOTE]
>  这是一个重要的区别，因为仅当（在项目外部）独立打开该文件时才能显示某些命令。  例如，当文件在项目外部打开时，只能将文件以不同的格式或不同的文件名保存（当在项目内部打开文件时，**另存为**命令不可用）。  
  
### 要在项目外部打开 .rc 文件  
  
1.  从**“文件”**菜单，选择**“打开”**，然后单击**“文件”**。  
  
2.  在**“打开文件”**对话框中，定位到要查看的资源脚本文件，突出显示该文件，然后单击**“打开”**。  
  
    > [!NOTE]
    >  如果首先打开项目（**“文件”**，**“打开”**，**“项目”**），某些命令将不可用。  “单独”打开文件意味着不先加载项目而直接打开文件。  
  
 若要打开并以文本格式查看资源文件，请参阅[编辑资源脚本 \(.rc\) 文件](../windows/how-to-open-a-resource-script-file-in-text-format.md)。  
  
#### 若要在项目外部打开多个 .rc 文件  
  
1.  同时单独打开这两个资源文件。  例如，打开 Source1.rc 和 Source2.rc。  
  
    1.  从**“文件”**菜单，选择**“打开”**，然后单击**“文件”**。  
  
    2.  在**“打开文件”**对话框中，定位到想要打开的第一个资源脚本文件 \(Source1.rc\)，突出显示该文件，然后单击**“打开”**。  
  
    3.  重复上一步，打开第二个 .rc 文件 \(Source2.rc\)。  
  
         .Rc 文件即会在单独的文档窗口中打开。  
  
2.  当同时打开这两个 .rc 文件时，平铺窗口，以便可以同时查看它们：  
  
    -   从**“窗口”**菜单，选择**“新建水平制表符组”**或**“新建垂直制表符组”**。  
  
         \- 或 \-  
  
    -   右键单击其中一个 .rc 文件，然后从快捷菜单选择 **“新建水平制表符组”**或**“新建垂直制表符组”**。  
  
> [!NOTE]
>  如果你的项目尚未包含 .rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 要求  
 Win32  
  
## 请参阅  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)