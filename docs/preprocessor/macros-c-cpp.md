---
title: 宏 （C/c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6794cb56566e552a47f19d53f4092c1a9749969c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850178"
---
# <a name="macros-cc"></a>宏 (C/C++)
预处理展开宏中不是预处理器指令的所有行 (没有行**#** 作为第一个非空白字符) 和部分中的一部分不跳过某些指令条件编译。 利用“条件编译”指令，您可以通过测试一个常量表达式或标识符取消对源文件的某些部分的编译，以确定将哪些文本块传递给编译器以及在预处理期间将从源文件中删除哪些文本块。  
  
 `#define` 指令通常用于将有用标识符与常量、关键字和常用语句或表达式关联。 表示常量的标识符有时称为“符号常量”或“清单常量”。 表示语句或表达式的标识符称为“宏”。 在该预处理器文档中，仅使用术语“宏”。  
  
 在程序源文本或某些其他预处理器命令的参数中识别宏的名称时，它将被视为对该宏的调用。 宏名称将替换为宏主体的副本。 如果宏接受自变量，则宏名称后面的实际自变量将替换为宏主体内的形式参数。 将宏调用替换为已处理的主体副本的过程称为宏调用的“扩展”。  
  
 实际上，有两种类型的宏。 “类似于对象的”宏不采用参数，但可以定义“类似于函数的”宏以接受参数，以便其外观和行为类似于函数调用。 由于宏无法生成实际函数调用，因此您有时可以将函数调用替换为宏以使程序更快地运行。 （在 C++ 中，内联函数通常是首选方法。）但是，如果未定义和小心使用宏，则宏会导致出现问题。 必须在带有参数的宏定义中使用括号，以便在表达式中保持适当的优先级。 此外，宏无法正确处理具有副作用的表达式。 请参阅`getrandom`中的示例[#define 指令](../preprocessor/hash-define-directive-c-cpp.md)有关详细信息。  
  
 一旦定义宏，则无法在未先删除原始定义的情况下将其重定义为不同的值。 但是，您可以使用完全相同的定义来重定义宏。 因此，相同的定义可在一个程序中出现多次。  
  
 #**Undef**指令删除宏的定义。 一旦删除定义，就可以将该宏重定义为不同的值。 [#Define 指令](../preprocessor/hash-define-directive-c-cpp.md)和[#undef 指令](../preprocessor/hash-undef-directive-c-cpp.md)讨论`#define`和`#undef`指令，分别。  
  
 有关详细信息，请参阅  
  
-   [宏和 C++](../preprocessor/macros-and-cpp.md)  
  
-   [Variadic 宏](../preprocessor/variadic-macros.md)  
  
-   [预定义宏](../preprocessor/predefined-macros.md)  
  
## <a name="see-also"></a>请参阅  
 [C/C++ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)