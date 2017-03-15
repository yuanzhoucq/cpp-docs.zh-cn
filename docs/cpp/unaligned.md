---
title: "__unaligned | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__unaligned_cpp"
  - "__unaligned"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__unaligned 关键字 [C++]"
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# __unaligned
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

声明带有 `__unaligned` 修饰符的指针时，编译器将假定该指针处理未对齐的数据。  因此，对于面向 Itanium Processor Family \(IPF\) 计算机的应用程序，编译器将生成逐个字节地读取未对齐数据的代码。  
  
## 备注  
 `__unaligned` 修饰符对 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 和 [!INCLUDE[vcpritanium](../Token/vcpritanium_md.md)] 编译器有效，但只会影响面向 IPF 计算机的应用程序。  此修饰符只描述已处理数据的对齐；指针本身被假定为已对齐。  
  
 [!INCLUDE[vcpritanium](../Token/vcpritanium_md.md)] 处理器在访问未对齐的数据时会产生对齐错误，而处理故障的时间会降低性能。  使用 `__unaligned` 修饰符可以让处理器逐个字节地读取数据并避免错误。  [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 应用程序不需要此修饰符，因为 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 处理器可以处理未对齐的数据，而不会出错。  
  
 有关对齐的详细信息，请参阅：  
  
-   [align](../cpp/align-cpp.md)  
  
-   [\_\_alignof 运算符](../cpp/alignof-operator.md)  
  
-   [pack](../preprocessor/pack.md)  
  
-   [\/Zp（结构成员对齐）](../build/reference/zp-struct-member-alignment.md)  
  
-   [结构对齐示例](../build/examples-of-structure-alignment.md)  
  
## 示例  
  
```  
// unaligned_keyword.cpp  
// compile with: /c  
// processor: x64 IPF  
#include <stdio.h>  
int main() {  
   char buf[100];  
  
   int __unaligned *p1 = (int*)(&buf[37]);  
   int *p2 = (int *)p1;  
  
   *p1 = 0;   // ok  
  
   __try {  
      *p2 = 0;  // throws an exception  
   }  
   __except(1) {  
      puts("exception");  
   }  
}  
```  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)