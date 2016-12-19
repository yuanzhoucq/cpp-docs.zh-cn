---
title: "// Attributes 注释 | Microsoft Docs"
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
  - "MFC 源文件中的特性注释"
  - "注释, 特性"
  - "MFC 源文件, 特性注释"
  - "公共特性注释"
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // Attributes 注释
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 类声明中 `// Attributes` 节包含公共特性 \(或属性\) 对象。  通常这些是成员变量，或者获取\/设置函数。  “Get”和“Set”函数也可能不是虚拟的。  在大多数情况下，因为它们没有任何副作用，“Get”函数通常是 **const**。  这些成员通常是公共的；保护的和私有实现特性在节通常找到。  
  
 在从 `CStdioFile`类的示例的列表，请在 [批注的示例](../mfc/an-example-of-the-comments.md)下，列表包含一个成员变量，`m_pStream`。  `CDC` 类关闭列出 20 成员此注释下。  
  
> [!NOTE]
>  大类，如 `CDC` 和 `CWnd`，还有列出所有特性在一个组中添加到清晰的多个成员。  在这种情况下，类库使用其他说明标题，进一步介绍了这些成员。  例如，`CDC` 使用 `// Device-Context Functions`、`// Drawing Tool Functions`，`// Drawing Attribute Functions`等。  表示的特性组要执行上面介绍的常见语法。  多种 OLE 类具有实现节调用 `// Interface Maps`。  
  
## 请参阅  
 [使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)   
 [注释示例](../mfc/an-example-of-the-comments.md)   
 [\/\/ Implementation 注释](../mfc/decrement-implementation-comment.md)   
 [\/\/ Constructors 注释](../mfc/decrement-constructors-comment.md)   
 [\/\/ Operations 注释](../mfc/decrement-operations-comment.md)   
 [\/\/ Overridables 注释](../mfc/decrement-overridables-comment.md)