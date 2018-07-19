---
title: 使用 MFC 源文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69079e6f74743a82aa9e9b9b1c13703e480c904c
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951531"
---
# <a name="using-the-mfc-source-files"></a>使用 MFC 源文件
Microsoft 基础类 (MFC) 库提供完整源代码。 标头文件 (.h) 位于 \atlmfc\include 目录中；实现文件 (.cpp) 位于 \atlmfc\src\mfc 目录中。  
  
 本系列文章介绍 MFC 用来注释每个类的各个部分的约定、这些注释的含义以及您在各个部分中可能找到的内容。 Visual C++ 向导使用为你创建的类的相似约定，你可能会发现这些约定对你自己的代码很有帮助。  
  
 你可能熟悉**公共**，**保护**，和**私有**c + + 关键字。 在查看 MFC 标头文件时，您会发现每个类可能有数个标头文件。 例如，公共成员变量和函数可能位于多个**公共**关键字。 这是因为 MFC 会根据其用途将成员变量和函数分开，而不是根据所允许的访问类型。 MFC 使用**私有**很谨慎; 甚至项被视为实现详细信息通常保护，并且很多时候是公共。 虽然不建议访问实现的详细信息，但 MFC 会将决定权留给您。  
  
 在 MFC 源文件和 MFC 应用程序向导创建的文件中，您会在类声明中发现许多类似这样的注释（通常按此顺序）：  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 本系列文章涉及的主题包括：  
  
-   [注释示例](../mfc/an-example-of-the-comments.md)  
  
-   [/ / 实现注释](../mfc/decrement-implementation-comment.md)  
  
-   [/ / 构造函数注释](../mfc/decrement-constructors-comment.md)  
  
-   [/ / 特性注释](../mfc/decrement-attributes-comment.md)  
  
-   [/ / Operations 注释](../mfc/decrement-operations-comment.md)  
  
-   [/ / / Overridables 注释](../mfc/decrement-overridables-comment.md)  
  
## <a name="see-also"></a>请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)

