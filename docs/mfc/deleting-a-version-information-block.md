---
title: "Deleting a Version Information Block | Microsoft Docs"
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
  - "vc.editors.version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "blocks, deleting"
  - "version information, deleting blocks"
  - "resources [Visual Studio], deleting version information"
ms.assetid: 4e1641eb-d5b2-4183-b273-bc5b51af1537
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Deleting a Version Information Block
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 删除版本信息块  
  
1.  通过在[资源视图](../windows/resource-view-window.md)中双击图标来打开版本信息资源。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  右键单击想要删除的块标头，然后从快捷菜单中选择“删除版本信息块”。  
  
     此命令会删除所选标头，并使其余的版本信息保持不变。 请注意此操作不能撤消。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Version Information Editor](../mfc/version-information-editor.md)   
 [版本信息 \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)