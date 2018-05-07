---
title: -特性注释 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74398d731c51223ea74fc6b827b0626af89286b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="-attributes-comment"></a>// Attributes 注释
MFC 类声明的 `// Attributes` 部分包含对象的公共特性（或属性）。 通常，它们是成员变量或 Get/Set 函数。 “Get”和“Set”函数可能是或可能不是虚拟的。 "Get"函数通常是**const**，因为在大多数情况下它们不具有副作用。 这些成员通常是公共的；通常可在实现部分中找到受保护的特性和私有特性。  
  
 在此示例中列出从类`CStdioFile`下[注释的示例](../mfc/an-example-of-the-comments.md)，该列表包含一个成员变量， `m_pStream`。 类 `CDC` 在此注释下列出了近 20 个成员。  
  
> [!NOTE]
>  大型类（如 `CDC` 和 `CWnd`）可能具有非常多的成员，因此只是在一个组中列出所有特性并不会大幅提高清晰性。 在这种情况下，类库使用其他注释作为标题来进一步描述这些成员。 例如，`CDC` 使用 `// Device-Context Functions`、`// Drawing Tool Functions`、`// Drawing Attribute Functions` 等。 表示特性的组将采用上述常用语法。 许多 OLE 类都具有一个称为 `// Interface Maps` 的实现部分。  
  
## <a name="see-also"></a>请参阅  
 [使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)   
 [注释示例](../mfc/an-example-of-the-comments.md)   
 [/ / Implementation 注释](../mfc/decrement-implementation-comment.md)   
 [/ / Constructors 注释](../mfc/decrement-constructors-comment.md)   
 [/ / Operations 注释](../mfc/decrement-operations-comment.md)   
 [/ / Overridables 注释](../mfc/decrement-overridables-comment.md)

