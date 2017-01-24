---
title: "naked (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "naked_cpp"
  - "naked"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec keyword [C++], naked"
  - "naked __declspec 关键字"
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# naked (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 对于使用 `naked` 特性声明的函数，编译器将生成编码，而无需 prolog 和 epilog 代码。  可以使用此功能来编写使用汇编程序代码的您自己的 prolog\/epilog 代码顺序。  裸函数尤为用在编写虚拟设备驱动程序。请注意 `naked` 特性仅适用于 x86和ARM，并不用于 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 。  
  
## 语法  
  
```  
__declspec(naked) declarator  
```  
  
## 备注  
 由于 `naked` 属性仅与函数定义相关且不是类型修饰符，因此裸函数必须使用扩展属性语法和 [\_\_declspec](../cpp/declspec.md) 关键字。  
  
 该编译器无法生成具有 naked 特性的内联函数，即使该函数也标有 [\_\_forceinline](../misc/inline-inline-forceinline.md) 关键字。  
  
 如果 `naked` 特性应用于任何非成员方法定义，该编译器会释放一个错误。  
  
## 示例  
 此代码用 `naked` 特性定义了函数：  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 或者，轮流地：  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 `naked` 特性仅影响函数 prolog 和 epilog 序列的编译器代码生成的性质。  它不影响为调用这些功能生成的代码。  因此，`naked` 特性视为一部分的功能的类型，因此，函数指针不能有 `naked` 特性。  此外， `naked` 特性不能应用于数据定义。  例如，下面的示例将生成错误：  
  
```  
__declspec( naked ) int i;       // Error--naked attribute not  
                                 // permitted on data declarations.  
```  
  
 `naked` 属性仅与函数的定义相关，不能在函数原型中指定。  例如，此声明生成编译器错误：  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not   
                                 // permitted on function declarations  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [Naked 函数调用](../cpp/naked-function-calls.md)