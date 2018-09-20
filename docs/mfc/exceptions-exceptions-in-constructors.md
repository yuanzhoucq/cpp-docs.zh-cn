---
title: 异常： 构造函数中的异常 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cab21255698c19046cfca185a0d8d7e7c530112
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421929"
---
# <a name="exceptions-exceptions-in-constructors"></a>异常：构造函数中的异常

构造函数中引发异常时, 清除了任何对象和内存分配所做之前引发异常，如中所述[异常： 从你自己的函数引发异常](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)。

在构造函数中引发异常时，则在调用构造函数时已为对象本身分配内存。 因此，在异常引发之后，编译器将自动释放对象占用的内存。

有关详细信息，请参阅[异常： 释放异常对象](../mfc/exceptions-freeing-objects-in-exceptions.md)。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)

