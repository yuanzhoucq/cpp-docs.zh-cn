---
title: "编译器内部函数 | Microsoft Docs"
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
  - "cl.exe 编译器, 内部函数"
  - "cl.exe 编译器, 性能"
  - "编译器内部函数"
  - "内部函数, 编译器"
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器内部函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大多数函数都包含在库中，但也有一些函数是在编译器中生成的（即内部函数）。  这些被称为内联函数或内部函数。  
  
## 备注  
 如果一个函数是内部函数，在通常会采用内联方式插入该函数的代码，从而避免函数调用的开销并可发出该函数的高效率计算机指令。  内部函数通常比等效的内联程序集速度更快，因为优化程序拥有众多内部函数行为方式的内置知识，因此可以优化使用内联程序集无法优化的内容。  此外，优化程序还可以采用不同的方式扩展内部函数、对齐缓冲区或根据上下文和调用参数进行其他方面的调整。  
  
 使用内部函数会影响到代码的可移植性，因为在 Visual C\+\+ 中可用的内部函数如果用其他编译器编译代码则可能不可用，并且对于某些目标体系结构可用的部分内部函数并非对所有体系结构都可用。  但是，内部函数通常比内联程序集可移植性更大。  64 位体系结构要求内部函数，但不支持内联程序集。  
  
 某些内部函数（例如 `__assume` 和 `__ReadWriteBarrier`）向编译器提供信息，但这会影响到优化程序的行为。  
  
 某些内部函数只能用作内部函数，某些内部函数可以同时用于函数和内部函数实现。  你可以指示编译器使用这两种方式中的一种来使用内部函数实现，具体取决于你是想仅启用特定函数还是想启用所有内部函数。  第一种方式是使用 `#pragma intrinsic(``intrinsic-function-name-list``)`。  杂注可用于指定单个内部函数或用逗号分隔的多个内部函数。  第二种方法是使用 [\/Oi（生成内部函数）](../build/reference/oi-generate-intrinsic-functions.md)编译器选项，让指定平台的所有内部函数可用。  在 **\/Oi** 下，使用 `#pragma function(``intrinsic-function-name-list``)` 强制使用函数调用而不是内部函数。  如果特定内部函数的文档规定例程只能用作内部函数，则不管是指定 **\/Oi** 还是 `#pragma intrinsic`  都会使用内部函数实现。  在所有情况下，**\/Oi** 或 `#pragma intrinsic` 允许但不是强制优化程序使用内部函数。  优化程序仍然可以调用函数。  
  
 一些标准的 C\/C\+\+ 库函数在某些体系结构上可用于内部函数实现。  调用 CRT 函数时，如果在命令行指定了 **\/Oi**，则会使用内部函数实现。  
  
 头文件 \<intrin.h\> 可用，其用于声明常用内部函数的原型。  制造商指定的内部函数可用于 \<immintrin.h\> 和 \<ammintrin.h\> 头文件。  此外，某些 Windows 头文件还可声明在编译器内部函数上映射的函数。  
  
 以下部分列出了可用于各种体系结构的所有内部函数。  有关内部函数在特定目标处理器上的工作方式的详细信息，请参阅制造商参考文档。  
  
-   [ARM 内部函数](../intrinsics/arm-intrinsics.md)  
  
-   [x86 内部函数列表](../intrinsics/x86-intrinsics-list.md)  
  
-   [x64 \(amd64\) 内部函数列表](../intrinsics/x64-amd64-intrinsics-list.md)  
  
-   [内部可在任何体系结构](../intrinsics/intrinsics-available-on-all-architectures.md)  
  
-   [按字母顺序列出内部函数](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)  
  
## 请参阅  
 [ARM Assembler Reference](../assembler/arm/arm-assembler-reference.md)   
 [Microsoft Macro Assembler Reference](../assembler/masm/microsoft-macro-assembler-reference.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)