---
title: "Adding Version Information for Another Language | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "languages, version information"
  - "New Version Info Block"
  - "blocks, adding"
  - "resources [Visual Studio], adding version information"
  - "version information, adding for languages"
ms.assetid: 17f6273c-e1cc-441a-a3d8-f564341cbf20
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Adding Version Information for Another Language
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 添加其他语言的版本信息（新版本信息块）  
  
1.  通过在[资源视图](../windows/resource-view-window.md)中双击鼠标打开版本信息资源。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在版本信息表中单击右键并在快捷菜单中选择“新建版本信息块”。  
  
     此命令将其他信息块添加到当前版本信息资源，并在[属性窗口](../Topic/Properties%20Window.md)中打开其相应属性。  
  
3.  在“属性”窗口中，为新块选择合适的语言和字符集。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Version Information Editor](../mfc/version-information-editor.md)   
 [版本信息 \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)