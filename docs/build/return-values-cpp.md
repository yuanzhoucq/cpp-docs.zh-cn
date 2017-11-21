---
title: "返回值 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f8ac22790fa6b94dd19ba7d46cf737824e898f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="return-values-c"></a>返回值 (C++)
可以适合于 64 位的标量返回值通过 RAX 返回，这包括 __m64 类型。 非标量类型包括浮点数、 双精度型值和矢量类型，如[__m128](../cpp/m128.md)， [__m128i](../cpp/m128i.md)， [__m128d](../cpp/m128d.md)在 XMM0 中返回。 返回到 RAX 或 XMM0 中的值的未使用位数的状态未定义。  
  
 用户定义类型可以从全局函数和静态成员函数通过值返回。 若要把值返回 RAX，用户定义类型的长度必须为 1、2、4、8、16、32 或 64 位；没有用户定义的构造函数、析构函数或复制赋值运算符；没有私有或受保护的非静态数据成员；没有引用类型的非静态数据成员；没有任何基类；没有虚函数；没有数据成员也不符合这些要求。 （这实质上是 C++03 POD 类型的定义。 由于 C++11 标准中的定义已更改，我们不建议使用`std::is_pod`进行此测试。）否则，调用方有责任分配内存并为返回值传递一个指针作为第一个参数。 然后，后续参数将向右移动一个参数。 相同的指针必须在 RAX 中被调用方返回。  
  
 这些示例说明如何为具有指定声明的函数传递参数和返回值：  
  
## <a name="example-of-return-value-1---64-bit-result"></a>示例返回值 1-64 位结果  
  
```Output  
__int64 func1(int a, float b, int c, int d, int e);  
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,  
// callee returns __int64 result in RAX.  
```  
  
## <a name="example-of-return-value-2---128-bit-result"></a>示例返回值 2-128 位结果  
  
```Output  
__m128 func2(float a, double b, int c, __m64 d);   
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,   
// callee returns __m128 result in XMM0.  
```  
  
## <a name="example-of-return-value-3---user-type-result-by-pointer"></a>返回值 3-指针的用户类型结果示例  
  
```Output  
struct Struct1 {  
   int j, k, l;    // Struct1 exceeds 64 bits.   
};  
Struct1 func3(int a, double b, int c, float d);   
// Caller allocates memory for Struct1 returned and passes pointer in RCX,   
// a in RDX, b in XMM2, c in R9, d pushed on the stack;   
// callee returns pointer to Struct1 result in RAX.  
```  
  
## <a name="example-of-return-value-4---user-type-result-by-value"></a>返回值 4-按值的用户类型结果示例  
  
```Output  
struct Struct2 {  
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.  
};  
Struct2 func4(int a, double b, int c, float d);   
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;   
// callee returns Struct2 result by value in RAX.  
```  
  
## <a name="see-also"></a>另请参阅  
 [调用约定](../build/calling-convention.md)