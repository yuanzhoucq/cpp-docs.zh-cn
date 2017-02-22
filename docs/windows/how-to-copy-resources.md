---
title: "How to: Copy Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resvw.resource.copying"
  - "vs.resvw.resource.copying"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], moving between files"
  - "resources [Visual Studio], copying"
  - "resource files, copying or moving resources between"
  - "resource files, tiling"
  - ".rc files, copying resources between"
  - "rc files, copying resources between"
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Copy Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以将资源从一个文件复制到另一个文件而不更改它们，或者可以[复制时更改资源的语言或条件](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md)。  
  
 可以轻松地从现有资源或可执行文件将资源复制到当前资源文件。  若要做到这一点，请同时打开包含资源的两个文件，并将项从一个文件拖动到另一个文件或者在两个文件之间进行复制和粘贴。  该方法对资源脚本 \(.rc\) 文件和资源模板 \(.rct\) 文件以及可执行 \(.exe\) 文件都有效。  
  
> [!NOTE]
>  Visual C\+\+ 包含您可在自己的应用程序中使用的示例资源文件。  有关更多信息，请参见 [CLIPART：常用资源](http://msdn.microsoft.com/zh-cn/9bac2891-b6b3-49ec-a287-cec850c707e0)。  
  
 可以在[在项目以外](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)打开的 .rc 文件之间使用拖放方法。  
  
### 使用拖放方法在文件之间复制资源  
  
1.  同时打开两个独立的资源文件（有关更多信息，请参见[在项目外查看 .rc 文件中的资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)）。  例如，打开 Source1.rc 和 Source2.rc。  
  
2.  在第一个 .rc 文件中单击要复制的资源。  例如，在 Source1.rc 中单击 IDD\_DIALOG1。  
  
3.  按住 Ctrl 键并将资源拖动到第二个 .rc 文件。  例如，将 IDD\_DIALOG1 从 Source1.rc 拖动到 Source2.rc。  
  
    > [!NOTE]
    >  在不按住 Ctrl 键的情况下拖动资源将只是移动资源而非复制它。  
  
### 使用复制和粘贴复制资源  
  
1.  同时打开两个独立的资源文件（有关更多信息，请参见[在项目外查看 .rc 文件中的资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)）。  例如，Source1.rc 和 Source2.rc。  
  
2.  在要复制资源的源文件（如 Source1.rc）中，右击资源并从快捷菜单中选择“复制”。  
  
3.  右击要粘贴资源到其中的资源文件（如 Source2.rc）。  从快捷菜单中选择“粘贴”。  
  
    > [!NOTE]
    >  无法在项目中的资源文件（“资源视图”中的文件）和独立的 .rc 文件（在文档窗口中打开的那些文件）之间进行拖放、复制、剪切或粘贴。  在该产品的早期版本中可以做到这一点。  
  
    > [!NOTE]
    >  为了避免与现有文件中的符号名或值冲突，Visual C\+\+ 可能会在您将资源复制到新文件时，更改所转移的资源的符号值或符号名和值。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [How to: Open a Resource Script File Outside of a Project \(Standalone\)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)