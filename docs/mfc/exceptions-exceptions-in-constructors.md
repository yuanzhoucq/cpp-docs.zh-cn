---
title: "异常： 在构造函数中异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0fb42a88c60b89909f104873ff20e36192b13c69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="exceptions-exceptions-in-constructors"></a>异常：构造函数中的异常
构造函数中引发异常时, 所需的对象，内存分配所做在引发异常之前, 中所述清理[异常： 从您自己的函数引发异常](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)。  
  
 在构造函数中引发异常时，则在调用构造函数时已为对象本身分配内存。 因此，在异常引发之后，编译器将自动释放对象占用的内存。  
  
 有关详细信息，请参阅[异常： 释放异常中的对象](../mfc/exceptions-freeing-objects-in-exceptions.md)。  
  
## <a name="see-also"></a>另请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)

