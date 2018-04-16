---
title: 断言和用户提供的消息 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3465202908cb0ca375ab5dcc77a085b208071f3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="assertion-and-user-supplied-messages-c"></a>断言和用户提供的消息 (C++)
C + + 语言支持三个错误处理机制来帮助你调试应用程序： [#error 指令](../preprocessor/hash-error-directive-c-cpp.md)、 [static_assert](../cpp/static-assert.md)关键字，与[断言宏、 _assert、 _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)宏。 所有的三种机制都会发出错误消息，其中两个还会测试软件断言。 软件断言指定在程序的某个特定点应满足的条件。 如果编译时断言失败，编译器将发出诊断消息和编译错误。 如果运行时断言失败，操作系统将发出诊断消息并关闭应用程序。  
  
## <a name="remarks"></a>备注  
 应用程序的生存期由预处理、编译和运行时阶段组成。 每个错误处理机制都会访问在这三个阶段之一中可用的调试信息。 若要有效地调试，请选择提供有关该阶段的相应信息的机制：  
  
-   [#Error 指令](../preprocessor/hash-error-directive-c-cpp.md)实际上是在预处理时。 它将无条件地发出用户指定的消息并导致编译因错误而失败。 该消息可包含由预处理器指令操作的文本，但不会计算任何生成的表达式。  
  
-   [Static_assert](../cpp/static-assert.md)声明实际上是编译时。 它将测试由用户指定且可以转换为布尔值的整数表达式表示的软件断言。 如果表达式的计算结果为零 (false)，编译器将发出用户指定的消息，并且编译因错误而失败。  
  
     `static_assert` 声明对调试模板尤其有用，因为模板参数可包含在用户指定的表达式中。  
  
-   [断言宏、 _assert、 _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)宏实际上是在运行时。 它会计算用户指定的表达式，如果结果为零，系统将发出诊断消息并关闭应用程序。 许多其他宏，如[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)和`_ASSERTE`，类似于此宏，但发出不同系统定义的或用户定义的诊断消息。  
  
## <a name="see-also"></a>请参阅  
 [#error 指令 （C/c + +）](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert 宏、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [static_assert](../cpp/static-assert.md)   
 [_STATIC_ASSERT 宏](../c-runtime-library/reference/static-assert-macro.md)   
 [模板](../cpp/templates-cpp.md)