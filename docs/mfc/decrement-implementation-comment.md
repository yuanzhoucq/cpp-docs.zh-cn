---
title: -实现注释 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89f87c33abfec7b9d055b589726639fcd741e59d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930269"
---
# <a name="-implementation-comment"></a>// Implementation 注释
`// Implementation` 节是任何 MFC 类声明的最重要的部分。  
  
 此节存储所有实现详细信息。 成员变量和成员函数都可在此节中出现。 此行下的所有内容在未来版本的 MFC 中都可能会更改。 除非您无法避免，否则不应依赖 `// Implementation` 行下面的详细信息。 此外，在实现行下声明的成员未记录，尽管某些实现在技术说明中讨论过。 无论基类函数是在哪个节中定义的，基类中的虚函数的重写都位于此节中，因为函数重写基类实现被视为实现详细信息。 通常，这些成员是受保护的，但并不总是这样。  
  
 请注意从`CStdioFile`列出下[注释的示例](../mfc/an-example-of-the-comments.md)成员声明下面`// Implementation`注释可能声明为**公共**，**保护**，或**私有**。 您应该谨慎地使用这些成员，因为它们在将来可能会更改。 声明的一组作为成员**公共**可能有必要为类库实现正常工作。 但是，这并不意味着您可以安全地使用以这种方式声明的成员。  
  
> [!NOTE]
>  您可以在 `// Implementation` 注释的上面或下面找到剩余类型的注释。 在任一情况下，这些注释都描述在其下面声明的类型的成员。 如果这些注释出现在 `// Implementation` 注释下面，则应假设成员在将来版本的 MFC 中可能会更改。  
  
## <a name="see-also"></a>请参阅  
 [使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)   
 [注释示例](../mfc/an-example-of-the-comments.md)   
 [/ / Constructors 注释](../mfc/decrement-constructors-comment.md)   
 [/ / Attributes 注释](../mfc/decrement-attributes-comment.md)   
 [/ / Operations 注释](../mfc/decrement-operations-comment.md)   
 [/ / Overridables 注释](../mfc/decrement-overridables-comment.md)

