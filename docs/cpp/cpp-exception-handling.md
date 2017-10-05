---
title: "C + + 异常处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling
- Visual C++, exception handling
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 9e23f99ad4c2b2a1129fa318fe6960e1c08df21d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="c-exception-handling"></a>C++ 异常处理
C++ 语言为引发和捕获异常提供内置支持。 使用 C++ 编程时，你几乎总会用到本节所述的内置 C++ 异常支持。  
  
 若要启用 c + + 异常处理代码中，使用[/EHsc](../build/reference/eh-exception-handling-model.md)。  
  
## <a name="in-this-section"></a>本节内容  
 有关 C++ 异常处理的该论述包括：  
  
-   [Try、 catch 和 throw 语句](../cpp/try-throw-and-catch-statements-cpp.md)  
  
-   [Catch 块如何计算](../cpp/how-catch-blocks-are-evaluated-cpp.md)  
  
-   [异常和堆栈展开](../cpp/exceptions-and-stack-unwinding-in-cpp.md)  
  
-   [异常规范](../cpp/exception-specifications-throw-cpp.md)  
  
-   [noexcept](../cpp/noexcept-cpp.md)  
  
-   [未处理的 C++ 异常](../cpp/unhandled-cpp-exceptions.md)  
  
-   [混合使用 C（结构化）和 C++ 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
  
## <a name="support-for-earlier-mfc-exceptions"></a>支持较早的 MFC 异常  
 从 4.0 版本开始，MFC 开始使用 C++ 异常处理机制。 虽然鼓励你在新代码中使用 C++ 异常处理，但是 MFC 4.0 和更高版本保留 MFC 早期版本中的宏，以免破坏旧代码。 这些宏和新机制也能结合起来。 混合使用宏和 c + + 异常处理以及转换旧代码以使用新机制的信息，请参阅文章[异常： 使用 MFC 宏和 c + + 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)和[异常： 从 MFC 转换异常宏](../mfc/exceptions-converting-from-mfc-exception-macros.md)。 较早的 MFC 异常宏（如果你仍在使用它们）的计算结果为 C++ 异常关键字。 请参阅[异常： 3.0 版本中对异常宏更改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。  
  
## <a name="see-also"></a>另请参阅  
 [异常处理](../cpp/exception-handling-in-visual-cpp.md)
