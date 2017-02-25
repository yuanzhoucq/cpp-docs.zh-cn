---
title: "Associating Menu Commands with Status Bar Text in MFC Applications | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "status bars, associating menu items"
  - "menus, status bar text"
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Associating Menu Commands with Status Bar Text in MFC Applications
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你的应用程序可以为用户可能选择的每个菜单命令显示说明性文本。 可通过使用“属性”窗口中的**“提示”**属性将文本字符串分配给每个菜单命令来完成。 如果[字符串表](../mfc/string-editor.md)中有一个字符串，其 ID 与命令相同，则当用户悬停在菜单项上方时，MFC 应用程序将在运行的应用程序的状态栏中自动显示此字符串资源。  
  
### 若要将菜单命令与状态栏文本字符串相关联  
  
1.  在**“菜单”**编辑器中，选择菜单命令。  
  
2.  在[属性窗口](../Topic/Properties%20Window.md)的**“提示”**框中键入关联的状态栏文本。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 MFC  
  
## 请参阅  
 [字符串](../atl-mfc-shared/strings-atl-mfc.md)   
 [Adding Commands to a Menu](../windows/adding-commands-to-a-menu.md)   
 [Menu Editor](../mfc/menu-editor.md)