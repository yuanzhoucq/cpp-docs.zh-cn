---
title: "Win32 Predefined Symbols | Microsoft Docs"
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
  - "Win32 [C++], predefined symbols"
  - "symbols, Win32 predefined"
  - "Windows API [C++], predefined symbols"
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Win32 Predefined Symbols
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些符号在 Win32 头文件中定义，它们支持标准 Windows 应用程序功能和操作。  这些符号主要用于公共 UI 元素。  当在资源编辑器中处理控件时，这些符号将出现在与公共控件关联的[“属性”窗口](../Topic/Properties%20Window.md)中。  例如，如果工具栏应显示应用程序图标，该图标将与“属性”窗口中的符号 IDI\_SMALL 关联。  
  
|||  
|-|-|  
|IDABORT|控件：对话框“中止”按钮|  
|IDC\_STATIC|控件：对话框中的静态文本|  
|IDCANCEL|控件：对话框“取消”按钮|  
|IDD\_ABOUTBOX|对话框：“产品信息”对话框|  
|IDI\_PROJECTNAME|图标：当前项目图标|  
|IDI\_SMALL|图标：当前项目小图标|  
|IDIGNORE|控件：用于对话框上的“忽略”按钮|  
|IDM\_ABOUT|菜单项：用于“帮助”\-\>“关于”|  
|IDM\_EXIT|菜单项：用于“文件”\-\>“退出”|  
|IDNO|控件：对话框“否”按钮|  
|IDOK|控件：对话框“确定”按钮|  
|IDRETRY|控件：对话框“重试”按钮|  
|IDS\_APP\_TITLE|字符串：当前应用程序名|  
|IDYES|控件：对话框“是”按钮|  
  
## 要求  
 Win32  
  
## 请参阅  
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)