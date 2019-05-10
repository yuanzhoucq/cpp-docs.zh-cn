---
title: 异常:构造函数中的异常
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 0b11f5be18879d5ad4b9e204bb02e18b4617c6b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405867"
---
# <a name="exceptions-exceptions-in-constructors"></a>异常:构造函数中的异常

构造函数中引发异常时, 任何对象和内存分配所做之前引发异常，如中所述清理[异常：从您自己的函数引发异常](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)。

在构造函数中引发异常时，则在调用构造函数时已为对象本身分配内存。 因此，在异常引发之后，编译器将自动释放对象占用的内存。

有关详细信息，请参阅[异常：释放异常中的对象](../mfc/exceptions-freeing-objects-in-exceptions.md)。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
