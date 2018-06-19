---
title: -操作注释 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee6bf4a330a5fdf1ac294157e69dab39b5f2bdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342266"
---
# <a name="-operations-comment"></a>// Operations 注释
`// Operations`的 MFC 类声明的部分包含你可以调用要使其执行操作或执行的操作 （执行操作） 的对象的成员函数。 这些函数是通常非**const**因为它们通常具有副作用。 它们可能是虚方法或非虚拟具体取决于类的需求。 通常情况下，这些成员是公共的。  
  
 在此示例中列出从类`CStdioFile`中[注释的示例](../mfc/an-example-of-the-comments.md)，该列表包含在此注释的两个成员函数：`ReadString`和`WriteString`。  
  
 与属性一样，可以进一步细分操作。  
  
## <a name="see-also"></a>请参阅  
 [使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)   
 [注释示例](../mfc/an-example-of-the-comments.md)   
 [/ / Implementation 注释](../mfc/decrement-implementation-comment.md)   
 [/ / Constructors 注释](../mfc/decrement-constructors-comment.md)   
 [/ / Attributes 注释](../mfc/decrement-attributes-comment.md)   
 [/ / Overridables 注释](../mfc/decrement-overridables-comment.md)

