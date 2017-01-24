---
title: "返回值 (C++) | Microsoft Docs"
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
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 返回值 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以适合于 64 位的标量返回值通过 RAX 返回，这包括 \_\_m64 类型。  非标量类型（包括浮点数、双精度数和矢量类型，如 [\_\_m128](../cpp/m128.md)、[\_\_m128i](../cpp/m128i.md)、[\_\_m128d](../cpp/m128d.md)）以 XMM0 返回。  返回到 RAX 或 XMM0 中的值的未使用位数的状态未定义。  
  
 用户定义类型可以从全局函数和静态成员函数通过值返回。  若要把值返回 RAX，用户定义类型的长度必须为 1、2、4、8、16、32 或 64 位；没有用户定义的构造函数、析构函数或复制赋值运算符；没有私有或受保护的非静态数据成员；没有引用类型的非静态数据成员；没有任何基类；没有虚函数；没有数据成员也不符合这些要求。  （这实质上是 C\+\+03 POD 类型的定义。  由于 C\+\+11 标准中的定义已更改，我们不建议使用`std::is_pod`进行此测试。） 否则，调用方有责任分配内存并为返回值传递一个指针作为第一个参数。  然后，后续参数将向右移动一个参数。  相同的指针必须在 RAX 中被调用方返回。  
  
 这些示例说明如何为具有指定声明的函数传递参数和返回值：  
  
## 返回值 1 示例 – 64 位结果  
  **\_\_int64 func1\(int a, float b, int c, int d, int e\);**  
**\/\/ 调用方在 RCX 中传递 a，在 XMM1 中传递 b，在 R8 中传递 c，在 R9 中传递 d，在堆栈上压入 e，**  
**\/\/ 被调用方在 RAX 中返回 \_\_int64 结果。**   
## 返回值 2 示例 – 128 位结果  
  **\_\_m128 func2\(float a, double b, int c, \_\_m64 d\);**   
**\/\/ 调用方在 XMM0 中传递 a，在 XMM1 中传递 b，在 R8 中传递 c，在 R9 中传递 d，**  
**\/\/ 被调用方在 XMM0 中返回 \_\_m128 结果。**   
## 返回值 3 示例 – 指针的用户类型结果  
  **struct Struct1 {**  
 **int j, k, l;    \/\/ Struct1 超过 64 位。  };**  
**Struct1 func3\(int a, double b, int c, float d\);**   
**\/\/ 调用方为返回的 Struct1 分配内存，并在 RCX 中传递指针，**  
**\/\/ 在 RDX 中传递 a，在 XMM2 中传递 b，在 R9 中传递 c，在堆栈上压入 d；**   
**\/\/ 被调用方在 RAX 中返回指向 Struct1 结果的指针。**    
## 返回值 4 示例 – 值的用户类型结果  
  **struct Struct2 {**  
 **int j, k;    \/\/ Struct2 符合 64 位，并符合通过值返回的要求。  };**  
**Struct2 func4\(int a, double b, int c, float d\);**   
**\/\/ 调用方在 RCX 中传递 a，在 XMM1 中传递 b，在 R8 中传递 c，在 XMM3 中传递 d；**   
**\/\/ 被调用方在 RAX 中通过值返回 Struct2 结果。**    
## 请参阅  
 [调用约定](../build/calling-convention.md)