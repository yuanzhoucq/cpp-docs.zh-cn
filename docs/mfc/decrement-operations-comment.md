---
title: "-操作注释 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 53d2470e0be0ca314da8486d74d8fc618e134c35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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

