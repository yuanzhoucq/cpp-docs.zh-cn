---
title: "使用 MFC 源文件 | Microsoft Docs"
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
  - "注释, MFC"
  - "MFC 源文件"
  - "MFC, 源文件"
  - "私有成员访问"
  - "受保护的成员访问"
  - "公共成员"
  - "源文件"
  - "源文件, MFC"
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 MFC 源文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类\(MFC\) 库提供完整源代码。  头文件 \(.h\) 在\\ atlmfc \\ include 目录下；实现文件在 \(.cpp\) 在\\ atlmfc \\ \\ mfc src 目录下。  
  
 此系列文章说明 MFC 中的一些约定，其中有MFC用来注释每个类的各个部分的约定，这些批注表示什么，和你可能在这个区域找到什么。  Visual C\+\+ 向导已为您创建的类使用相同的约定，因此，您很可能会觉得这些约定对您自己的代码很有帮助。  
  
 您可能对C\+\+**public**、`protected`和 `private` 关键字很熟悉。  在查看 MFC 头文件时，您会发现每类可能有数头文件。  例如，公共成员变量和函数可以在多个 **public**关键字 下。  这是因为，MFC将成员变量和函数根据他们的用途分开，而不是根据访问类型的级别。  慎重使用 MFC `private` ;即使项的实现细节通常是被保护的，并且很多时间是公共的。  虽然对详细实现的访问是不被鼓励的，但MFC将决定权留给了您。  
  
 在 MFC 源文件和 MFC 应用程序向导"创建的文件中，您将发现许多像这种在类声明中的注释 \(通常按此顺序\):  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 在此系列包括文章的主题包括：  
  
-   [注释示例](../mfc/an-example-of-the-comments.md)  
  
-   [\/\/ 实现的注释](../mfc/decrement-implementation-comment.md)  
  
-   [\/\/ 构造函数的注释](../mfc/decrement-constructors-comment.md)  
  
-   [属性的注释。](../mfc/decrement-attributes-comment.md)  
  
-   [\/\/操作的注释](../mfc/decrement-operations-comment.md)  
  
-   [\/\/ 重写的注释](../mfc/decrement-overridables-comment.md)  
  
## 请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)