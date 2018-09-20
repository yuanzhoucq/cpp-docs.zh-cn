---
title: --Constructors 注释 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f03a65c3f870b1e7648f03b70efe7242c35a21f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429345"
---
# <a name="-constructors-comment"></a>// Constructors 注释

`// Constructors` MFC 类声明的部分用于声明构造函数 （在 c + + 意义上说），以及实际使用该对象所需的任何初始化函数。 例如，`CWnd::Create`是在构造函数部分，因为使用之前`CWnd`对象，它必须"完全"通过构造第一次调用的 c + + 构造函数，然后再调用`Create`函数。 通常情况下，这些成员是公共的。

例如，类`CStdioFile`有三个构造函数，其中之一下的列表中所示[注释示例](../mfc/an-example-of-the-comments.md)。

## <a name="see-also"></a>请参阅

[使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)<br/>
[Implementation 注释](../mfc/decrement-implementation-comment.md)<br/>
[Attributes 注释](../mfc/decrement-attributes-comment.md)<br/>
[Operations 注释](../mfc/decrement-operations-comment.md)<br/>
[可重写注释](../mfc/decrement-overridables-comment.md)

