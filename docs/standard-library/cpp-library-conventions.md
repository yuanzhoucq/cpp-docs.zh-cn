---
title: "C++ Library Conventions | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, conventions
- classes [C++]
- functions [C++], library naming conventions
- naming conventions [C++], C++ Standard Library
- conventions [C++], C++ Standard Library
- function names [C++]
- coding conventions, C++ Standard Library
- naming conventions [C++], C++ library
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
caps.latest.revision: 9
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 55d3959b12b1b1a25a6c4b5c65fce59db57cf838
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="c-library-conventions"></a>C++ 库约定
C++ 库遵循的约定与标准 C 库大致相同，同时还遵循此处所述的一些其他约定。  
  
 实现在 C++ 库中声明类型和函数时存在某些限制：  
  
-   标准 C 库中的函数名称可能带有 extern #"C++" 或 extern"C" 链接。 包含相应的标准 C 标头，不要声明一个库实体内联。  
  
-   库类中的成员函数名称除了本文档中列出的内容可能还有其他函数签名。 可以确定此处所述的函数调用将按预期执行，但你无法可靠地采用库成员函数的地址。 （类型可能不是你所预期的。）  
  
-   库类可能具有未记录的（非虚拟）基类。 事实上，记录为从另一个类派生的类可能是通过其他未记录的类而从该类派生而来的。  
  
-   一个类型如果被定义为某个整数类型的同义词，则该类型可能与几种不同整数类型中的某个类型相同。  
  
-   位掩码类型可以作为整数类型或枚举来实现。 在任一情况下，可以对相同位掩码类型的值执行位运算（如 `AND` 和 `OR`）。 位掩码类型的元素 `A` 和 `B` 为非零值，以便 `A` & `B` 为零。  
  
-   无异常规范的库函数可能引发任意异常，除非其定义清楚地限制这种可能性。  
  
 另一方面还存在着一些限制：  
  
-   标准 C 库不使用掩码宏。 仅保留特定的函数签名，而不会保留函数本身的名称。  
  
-   类的外部库函数名称不包含额外的未记录函数签名。 可以可靠地采用其地址。  
  
-   被称为虚拟的基类和成员函数肯定为虚拟，而那些被称为非虚拟的对象肯定为非虚拟。  
  
-   由 C++ 库定义的两种类型始终不同，除非此文档明确提供不同的建议。  
  
-   库提供的函数（包括可替换函数的默认版本）*最多*可能会引发任何异常规范中列出的那些异常。 库提供的析构函数不会引发异常。 标准 C 库中的函数可能会传播异常，比如当 `qsort` 调用比较函数时引发的异常，但它们不会另行引发异常。  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


