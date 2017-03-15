---
title: "// Implementation 注释 | Microsoft Docs"
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
  - "注释, 实现注释"
  - "注释, MFC"
  - "MFC 源文件中的实现注释"
  - "MFC 源文件, 实现注释"
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // Implementation 注释
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

"\/\/ Implementation"  节是所有 MFC 类声明的最重要部分。  
  
 此节实现的详细信息。  成员变量和成员函数都可出现在此节。  一切低于此行的在 MFC 未来版本中可能会更改。  除非不能避免它，不应依赖在 `// Implementation` 行之下的详细信息。  在此外，实现行下声明的成员未记录到文档，尽管某些实现在技术备注中讨论。  基类中虚函数的重写属于此节，而忽略基类函数定义在哪节，因为函数重写基类实现将被认为是实现的详细信息。  通常，这些成员是 protected，但并不总是。  
  
 通知来自 [批注的示例](../mfc/an-example-of-the-comments.md) 下的 `CStdioFile` 列表，该示例在 `// Implementation` 注释下声明的成员可能声明为 **public**、 `protected`或 `private`。  因为它们可能会在将来更改，则应谨慎使用这些成员。  声明成员的一组为 **public** 可能是类库实现正常工作所需的。  但是，这并不意味着您可以安全使用成员中的声明。  
  
> [!NOTE]
>  您可以在 `// Implementation` 注释的上方或下方发现其保留类型的注释 。  在任何情况下，但它们描述在其下声明的类型成员。  如果它们在 `// Implementation` 注释下发生，应假设成员在 MFC 将来的版本中可能发生更改。  
  
## 请参阅  
 [使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)   
 [注释示例](../mfc/an-example-of-the-comments.md)   
 [\/\/ Constructors 注释](../mfc/decrement-constructors-comment.md)   
 [\/\/ Attributes 注释](../mfc/decrement-attributes-comment.md)   
 [\/\/ Operations 注释](../mfc/decrement-operations-comment.md)   
 [\/\/ Overridables 注释](../mfc/decrement-overridables-comment.md)