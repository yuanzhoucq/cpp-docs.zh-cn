---
title: 使用 MFC 源文件
ms.date: 11/04/2016
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
ms.openlocfilehash: 6f23f792f750e4352494bf3e4bde08f0fe360439
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980493"
---
# <a name="using-the-mfc-source-files"></a>使用 MFC 源文件

Microsoft 基础类 (MFC) 库提供完整源代码。 标头文件 (.h) 位于 \atlmfc\include 目录中；实现文件 (.cpp) 位于 \atlmfc\src\mfc 目录中。

本系列文章介绍 MFC 用来注释每个类的各个部分的约定、这些注释的含义以及您在各个部分中可能找到的内容。 Visual C++ 向导使用为你创建的类的相似约定，你可能会发现这些约定对你自己的代码很有帮助。

你可能熟悉**公共**、**受保护**和**私有** C++关键字。 在 MFC 头文件中, 可以找到每个类, 每个类都有多个。 例如, 公共成员变量和函数可能位于多个**public**关键字下。 这是因为 MFC 根据成员变量和函数的使用来分隔它们, 而不是允许的访问类型。 MFC 使用的是**专用**的。 即使是视为实现的详细信息的项目经常**受到保护**, 而且很多时候都是**公开**的。 虽然不建议访问实现的详细信息，但 MFC 会将决定权留给您。

在 mfc 应用程序向导创建的 MFC 源文件和标头文件中, 您将在类声明 (通常按此顺序) 中找到类似于下面的注释:

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

本系列文章涉及的主题包括：

- [注释示例](../mfc/an-example-of-the-comments.md)

- [实现注释](../mfc/decrement-implementation-comment.md)

- [构造函数注释](../mfc/decrement-constructors-comment.md)

- [特性注释](../mfc/decrement-attributes-comment.md)

- [//操作注释](../mfc/decrement-operations-comment.md)

- [可重写注释](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>请参阅

[常规 MFC 主题](../mfc/general-mfc-topics.md)
