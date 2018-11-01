---
title: --Operations 注释
ms.date: 11/04/2016
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
ms.openlocfilehash: 6b84da721bd22723d0eb5a0b520462cd8a4613e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653185"
---
# <a name="-operations-comment"></a>// Operations 注释

`// Operations` MFC 类声明的部分包含可调用对象以使其执行操作或执行的操作 （执行操作） 的成员函数。 这些函数是通常非**const**因为它们通常具有负面影响。 它们可能是虚拟或非虚拟具体取决于类的需求。 通常情况下，这些成员是公共的。

在类中列出的示例`CStdioFile`，请在[注释示例](../mfc/an-example-of-the-comments.md)，该列表包含在此注释下列两个成员函数：`ReadString`和`WriteString`。

与属性一样，可以进一步细分操作。

## <a name="see-also"></a>请参阅

[使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)<br/>
[注释示例](../mfc/an-example-of-the-comments.md)<br/>
[Implementation 注释](../mfc/decrement-implementation-comment.md)<br/>
[构造函数注释](../mfc/decrement-constructors-comment.md)<br/>
[Attributes 注释](../mfc/decrement-attributes-comment.md)<br/>
[可重写注释](../mfc/decrement-overridables-comment.md)

