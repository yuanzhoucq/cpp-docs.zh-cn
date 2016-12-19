---
title: "ATL Predefined Symbols | Microsoft Docs"
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
  - "symbols, ATL predefined"
  - "ATL symbols"
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Predefined Symbols
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些符号在 ATL 头文件中定义，但它们支持标准的 Windows 应用程序功能和操作。  这些符号主要用于对话框。  当在[对话框编辑器](../mfc/dialog-editor.md)中处理对话框和控件时，这些符号将出现在与公共控件关联的“属性”窗口中。  例如，如果对话框有“取消”按钮，该命令将与[“属性”窗口](../Topic/Properties%20Window.md)中的符号 IDCANCEL 关联。  
  
|||  
|-|-|  
|IDABORT|控件：对话框“中止”按钮|  
|IDC\_STATIC|控件：静态控件|  
|IDCANCEL|控件：对话框“取消”按钮|  
|IDIGNORE|控件：对话框“忽略”按钮|  
|IDNO|控件：对话框“否”按钮|  
|IDOK|控件：对话框“确定”按钮|  
|IDR\_ACCELERATOR1|资源：快捷键对应表|  
|IDRETRY|控件：对话框“重试”按钮|  
|IDS\_PROJNAME|字符串：当前应用程序名|  
|IDYES|控件：对话框“是”按钮|  
  
## 要求  
 ATL  
  
## 请参阅  
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)