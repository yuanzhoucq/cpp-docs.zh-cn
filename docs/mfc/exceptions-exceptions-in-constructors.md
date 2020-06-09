---
title: 异常：构造函数中的异常
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 4089f4d44f03c7de3432f137b5d28f74189e1cb9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624619"
---
# <a name="exceptions-exceptions-in-constructors"></a>异常：构造函数中的异常

当在构造函数中引发异常时，清理在引发异常之前所做的任何对象和内存分配，如[异常：从您自己的函数引发异常](exceptions-throwing-exceptions-from-your-own-functions.md)中所述。

在构造函数中引发异常时，则在调用构造函数时已为对象本身分配内存。 因此，在异常引发之后，编译器将自动释放对象占用的内存。

有关详细信息，请参阅[异常：释放异常中的对象](exceptions-freeing-objects-in-exceptions.md)。

## <a name="see-also"></a>另请参阅

[异常处理](exception-handling-in-mfc.md)
