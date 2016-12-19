---
title: "// Constructors 注释 | Microsoft Docs"
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
  - "注释, 构造函数注释"
  - "注释, MFC"
  - "构造函数 [C++], 声明"
  - "构造函数注释"
  - "声明, 构造函数"
  - "声明构造函数, 代码注释"
  - "实例构造函数, 代码注释"
  - "MFC 源文件, 构造函数注释"
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // Constructors 注释
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 类的声明部分声明构造函数 `// Constructors` \(在 C\+\+ 中有效\) 以及需要的所有初始化函数实际上使用对象。  例如，`CWnd::Create`。构造函数，因为部分，则使用 `CWnd` 对象之前，必须先“调用 C\+\+ 构造函数然后调用 **创建** 函数完全构造导出”。  通常，这些成员称为公共。  
  
 例如，`CStdioFile` 具有三个构造函数的类，其中在 [批注的示例](../mfc/an-example-of-the-comments.md)下面的列表显示。  
  
## 请参阅  
 [使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)   
 [\/\/ Implementation 注释](../mfc/decrement-implementation-comment.md)   
 [\/\/ Attributes 注释](../mfc/decrement-attributes-comment.md)   
 [\/\/ Operations 注释](../mfc/decrement-operations-comment.md)   
 [\/\/ Overridables 注释](../mfc/decrement-overridables-comment.md)