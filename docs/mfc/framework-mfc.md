---
title: "框架 (MFC) | Microsoft Docs"
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
  - "API [C++], 由 MFC Win32 封装"
  - "应用程序框架 [C++], 关于 MFC 应用程序框架"
  - "封装的 Win32 API"
  - "封装 [C++]"
  - "封装 [C++], Win32 API"
  - "MFC [C++], 应用程序框架"
  - "Win32 [C++], 由 MFC 执行的 API 封装"
  - "Windows API [C++], 由 MFC 执行的封装"
  - "包装类, 解释的"
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架 (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 Microsoft 基础类库 \(MFC\) 框架使用某个主类和多个 Visual C\+\+ 的主要工具。  某些类封装 Win32 应用程序编程接口 \(API\) 的一个主要部分。  其他类封装应用程序概念，如文档、视图和应用程序。  仍然有一些其他提供封装 OLE 功能以及 ODBC 和 DAO 的数据访问功能。  
  
 例如，Windows Win32 的概念。MFC `CWnd`类封装。  也就是说 C\+\+ 类调用的 `CWnd` 封装或“包装”表示 Windows `HWND` 的窗口句柄。  同样，`CDialog` 类封装 Win32 对话框。  
  
 封装表示 C\+\+ 类 `CWnd`，例如，包含 `HWND`类型的成员变量，并封装，函数采用 `HWND` 作为参数的调用对 Win32 类的成员函数。  类成员函数通常具有与 Win32 函数进行封装的名称。  
  
## 本节内容  
 [SDI 和 MDI](../mfc/sdi-and-mdi.md)  
  
 [文档、视图和框架](../mfc/documents-views-and-the-framework.md)  
  
 [向导和资源编辑器](../mfc/wizards-and-the-resource-editors.md)  
  
## 相关章节  
 [基于框架生成](../mfc/building-on-the-framework.md)  
  
 [框架如何调用您的代码](../mfc/how-the-framework-calls-your-code.md)  
  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)  
  
 [文档模板和文档\/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)  
  
 [消息处理和映射](../mfc/message-handling-and-mapping.md)  
  
 [窗口对象](../mfc/window-objects.md)  
  
## 请参阅  
 [使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)