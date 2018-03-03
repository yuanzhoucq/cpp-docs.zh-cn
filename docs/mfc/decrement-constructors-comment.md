---
title: "-构造函数注释 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constructors comment
- declarations, constructors
- MFC source files, Constructors comment
- declaring constructors, code comments
- comments, MFC
- comments, constructors comment
- constructors [MFC], declaring
- instance constructors, code comments
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f6425252df34936d4ba3c9013664205b0038d82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="-constructors-comment"></a>// Constructors 注释
`// Constructors`的 MFC 类声明的部分用于声明构造函数 （在 c + + 的意义上），以及任何所需真正使用对象的初始化函数。 例如，`CWnd::Create`是构造函数部分中，因为你在使用之前`CWnd`对象，因此必须在"完全构造"通过首先调用 c + + 构造函数，然后再调用**创建**函数。 通常情况下，这些成员是公共的。  
  
 例如，类`CStdioFile`有三个构造函数，其中之一在列表中所示[注释的示例](../mfc/an-example-of-the-comments.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)   
 [/ / Implementation 注释](../mfc/decrement-implementation-comment.md)   
 [/ / Attributes 注释](../mfc/decrement-attributes-comment.md)   
 [/ / Operations 注释](../mfc/decrement-operations-comment.md)   
 [/ / Overridables 注释](../mfc/decrement-overridables-comment.md)

