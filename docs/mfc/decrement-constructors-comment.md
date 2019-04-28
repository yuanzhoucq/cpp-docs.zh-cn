---
title: --Constructors 注释
ms.date: 11/04/2016
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
ms.openlocfilehash: e0d02af016a0c7bfb0869b7cdd30fe0db2975102
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240856"
---
# <a name="-constructors-comment"></a>// Constructors 注释

`// Constructors` MFC 类声明的部分用于声明构造函数 (在C++意义上) 以及任何真正使用该对象所需的初始化函数。 例如，`CWnd::Create`是在构造函数部分，因为使用之前`CWnd`对象，它必须"完全构造"通过首先调用C++构造函数，然后再调用`Create`函数。 通常情况下，这些成员是公共的。

例如，类`CStdioFile`有三个构造函数，其中之一下的列表中所示[注释示例](../mfc/an-example-of-the-comments.md)。

## <a name="see-also"></a>请参阅

[使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)<br/>
[Implementation 注释](../mfc/decrement-implementation-comment.md)<br/>
[Attributes 注释](../mfc/decrement-attributes-comment.md)<br/>
[Operations 注释](../mfc/decrement-operations-comment.md)<br/>
[可重写注释](../mfc/decrement-overridables-comment.md)
