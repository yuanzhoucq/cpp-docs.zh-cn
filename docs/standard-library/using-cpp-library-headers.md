---
title: "使用 C++ 库标头 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "标头"
  - "标头, 在 C++ include 指令中进行命名"
  - "标头, 标准 C++ 库"
  - "INCLUDE 指令"
  - "library 标头"
  - "标准 C++ 库, 标头"
  - "C++ 中的标准标头"
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 C++ 库标头
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在包含一个标准标头的内容通过命名在包含一个指令。  
  
```  
#include <iostream>   // include I/O facilities  
```  
  
 可以包含以任何顺序的标准头，标准标头多次，或者定义同一宏或相同的两个或更多标准标头键入。  不包括在声明中的标准头。  不要定义与关键字相同，则包含一个标准标头中的宏。  
  
 用 . \+\+ 需要定义需要类型的库头包括任何其他 C\+\+ 库头。\(C\+\+ 库头，但是，所有在翻译单元始终包括显式需要，您唯恐错误有关猜测其实际依赖关系，这些依赖关系。\)标准 C 头包括从另一标准头。  一个标准标头声明或定义为描述实体的仅文档中。  
  
 每个函数在库中。一个标准标头声明。  不同于标准 C 中，提供一个标准标头不遮掩的宏。名称和的函数声明和获得相同的效果相同的函数。  有关应用蒙板的宏的更多信息，请参见 [C\+\+ 库约定](../standard-library/cpp-library-conventions.md)。  
  
 除 `operator delete` 和 `operator new` 之外的所有名称。C\+\+ 库头中定义 `std` 命名空间，也在 `std` 命名空间内作为嵌套的命名空间。  您引用名称 `cin`，例如，为 `std::cin`。  注释，但是宏名称，不会被命名空间限定的，因此，您始终写入 `__STD_COMPLEX`，没有命名空间限定符。  
  
 在某些环境转换，包括". C\+\+ 库头可以、在 `std` 命名空间声明的外部名称到全局命名空间，与每个单独的 `using` 名称声明。  否则，标头不引入任何库名到当前命名空间。  
  
 C\+\+ 标准要求 C 标准标头声明命名空间中 `std`的所有外部名称，然后将它们粘贴、与单个 `using` 声明的每个全局命名空间的名称。  但是，在某些环境转换包含 C 标准标头没有命名空间声明，声明所有名称直接在全局命名空间。  因此，最可移植的情况下处理命名空间将遵循两条规则：  
  
-   确保声明在命名空间 `std` 中 \<stdlib.h，例如\>，包括标题 cstdlib \<传统上声明的外部名称。\>  知道名称在全局命名空间可能会声明。  
  
-   确保声明位于全局命名空间中 \<stdlib.h 声明的外部名称，包括\>标题 stdlib.h \<直接\>。  知道名称在命名空间 `std`可能会声明。  
  
 因而，如果要调用 `std::abort` 导致异常终结，应包括 \<cstdlib\>。  如果要调用 `abort`时，应包括 \<stdlib.h。\>  
  
 或者，您可以编写声明：  
  
```  
using namespace std;  
```  
  
 要将名称传入任何库当前命名空间。  如果立即在所有此声明之后编写包括指令，则、名称到全局命名空间。  其后可以忽略在翻译单元的余数的命名空间考虑。  还避免跨不同的翻译。环境之间的大多数差异。  
  
 除非明确指示，否则您不能定义名称在 `std` 命名空间，也在 `std` 命名空间内的嵌套命名空间，程序内。  
  
## 请参阅  
 [STL 概述](../standard-library/cpp-standard-library-overview.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)