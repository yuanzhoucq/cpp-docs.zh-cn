---
title: --Attributes 注释
ms.date: 11/04/2016
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
ms.openlocfilehash: 33ee18400e03b55a26c4ad17e8d1ba6853ccda88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486068"
---
# <a name="-attributes-comment"></a>// Attributes 注释

MFC 类声明的 `// Attributes` 部分包含对象的公共特性（或属性）。 通常，它们是成员变量或 Get/Set 函数。 “Get”和“Set”函数可能是或可能不是虚拟的。 "Get"函数通常是**const**，因为它们在大多数情况下没有负面影响。 这些成员通常是公共的；通常可在实现部分中找到受保护的特性和私有特性。

在类中列出的示例`CStdioFile`下[注释示例](../mfc/an-example-of-the-comments.md)，该列表包含一个成员变量， *m_pStream*。 类 `CDC` 在此注释下列出了近 20 个成员。

> [!NOTE]
>  大型类（如 `CDC` 和 `CWnd`）可能具有非常多的成员，因此只是在一个组中列出所有特性并不会大幅提高清晰性。 在这种情况下，类库使用其他注释作为标题来进一步描述这些成员。 例如，`CDC` 使用 `// Device-Context Functions`、`// Drawing Tool Functions`、`// Drawing Attribute Functions` 等。 表示特性的组将采用上述常用语法。 许多 OLE 类都具有一个称为 `// Interface Maps` 的实现部分。

## <a name="see-also"></a>请参阅

[使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)<br/>
[注释示例](../mfc/an-example-of-the-comments.md)<br/>
[Implementation 注释](../mfc/decrement-implementation-comment.md)<br/>
[构造函数注释](../mfc/decrement-constructors-comment.md)<br/>
[Operations 注释](../mfc/decrement-operations-comment.md)<br/>
[可重写注释](../mfc/decrement-overridables-comment.md)

