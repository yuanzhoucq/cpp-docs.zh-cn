---
title: "// Overridables 注释 | Microsoft Docs"
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
  - "MFC 源文件, 可重写注释"
  - "MFC 源文件中的可重写注释"
  - "重写, MFC 源文件中的可重写注释"
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // Overridables 注释
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 类声明中 `// Overridables` 节包含可在派生类都可以重写虚函数，需要修改基类行为时。  它们通常是命名以" On "但不是绝对必需的。  此处函数用于重写和实现通常或提供一些类“回调”或“功能”。通常，这些成员保护。  
  
 在 MFC 中，纯虚函数始终放置本节。  在 C\+\+ 纯虚函数是一种形式：  
  
 `virtual void OnDraw( ) = 0;`  
  
 在从 `CStdioFile`类的示例的列表，在 [批注的示例](../mfc/an-example-of-the-comments.md)，列表不包含 overridables 节。  类 **CDocument**，另一方面，大约 10 的列表可重写成员函数。  
  
 在这些类中，还可以查看批注 `// Advanced Overridables`。  这些是只高级程序员应尝试重写的函数。  您可能从不需要覆盖它们。  
  
> [!NOTE]
>  本文描述约定为自动化 \(原来称作为 OLE 自动化\) 方法和属性适用于，通常，还工作。  自动化方法类似于 MFC 操作。  自动化属性类似于 MFC 特性。  自动化事件 \(支持 ActiveX 控件，以前称为 OLE 控件\) 类似于 MFC 可重写的成员函数。  
  
## 请参阅  
 [使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)   
 [注释示例](../mfc/an-example-of-the-comments.md)   
 [\/\/ Implementation 注释](../mfc/decrement-implementation-comment.md)   
 [\/\/ Constructors 注释](../mfc/decrement-constructors-comment.md)   
 [\/\/ Attributes 注释](../mfc/decrement-attributes-comment.md)   
 [\/\/ Operations 注释](../mfc/decrement-operations-comment.md)