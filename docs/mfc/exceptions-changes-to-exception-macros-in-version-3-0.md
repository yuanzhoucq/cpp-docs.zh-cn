---
title: 异常： 更改版本 3.0 中对异常宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4e6c7744c3d5328985eee24e67ee1eb359fb3c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931013"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>异常：3.0 版本中对异常宏的修改
这是一个高级的主题。  
  
 在 MFC 3.0 版及更高版本中，异常处理宏已更改为使用 c + + 异常。 本文介绍了这些更改如何影响使用宏的现有代码的行为。  
  
 本文介绍了以下主题：  
  
-   [异常类型和 CATCH 宏](#_core_exception_types_and_the_catch_macro)  
  
-   [重新引发异常](#_core_re.2d.throwing_exceptions)  
  
##  <a name="_core_exception_types_and_the_catch_macro"></a> 异常类型和 CATCH 宏  
 在早期版本的 MFC，**捕获**宏使用 MFC 运行时类型信息来确定异常的类型; 该异常的类型确定，换而言之，在 catch 站点。 使用 c + + 异常，但是，该异常的类型始终在 throw 站点由确定引发的异常对象的类型。 这将导致不兼容问题的罕见情况下则引发该异常对象的指针的类型而不同于则引发该异常对象的类型中。  
  
 下面的示例阐释了这种差异之间 MFC 3.0 版及更早版本的后果：  
  
 [!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]  
  
 此代码在版本 3.0 中的行为有所不同，因为控件始终将传递给第一个**捕获**代码块替换匹配异常声明。 Throw 表达式的结果  
  
 [!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]  
  
 引发作为`CException*`，即使它被构造为`CCustomException`。 **捕获**MFC 版本 2.5 和更早版本使用中的宏`CObject::IsKindOf`若要在运行时测试的类型。 因为表达式  
  
 [!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]  
  
 为 true，第一个 catch 块捕获异常。 在版本 3.0 中，使用 c + + 异常来实现许多异常处理宏，第二个 catch 块与引发`CException`。  
  
 类似下面的代码不常见。 它通常出现在异常对象传递给另一个函数接受泛型的`CException*`，执行"预引发"处理，最后会引发异常。  
  
 若要解决此问题，将引发表达式从函数移动到调用代码，并引发在生成的异常时编译器知道实际类型的异常。  
  
##  <a name="_core_re.2d.throwing_exceptions"></a> 重新引发异常  
 Catch 块不能引发它捕获的异常相同的指针。  
  
 例如，此代码有效在以前版本，但将有 3.0 版意外的结果：  
  
 [!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]  
  
 使用**引发**在 catch 块会导致指针`e`要删除，因此，外部 catch 站点将收到了无效的指针。 使用**THROW_LAST**重新引发`e`。  
  
 有关详细信息，请参阅[异常： 捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)

