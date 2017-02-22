---
title: "编译器错误 C2668 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2668"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2668"
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 编译器错误 C2668
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 对重载函数的调用不明确  
  
 未能解析指定的重载函数调用。  可能需要显式转换一个或多个实际参数。  
  
 在模板的使用过程中也可发生此错误。  在同一个类中，如果有具有相同签名的常规成员函数和模板成员函数，则必须先有模板成员函数。  这是当前 Visual C\+\+ 实现的限制。  
  
 有关函数模板部分排序的更多信息，请参见知识库文章 Q240869。  
  
 如果要生成包含支持 `ISupportErrorInfo` 的 COM 对象的 ATL 项目，请参见知识库文章 Q243298。  
  
## 示例  
 下面的示例生成 C2668：  
  
```  
// C2668.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
  
void func( X, X ){}  
void func( A, B ){}  
D d;  
int main() {  
   func( d, d );   // C2668 D has an A, B, and X   
   func( (X)d, (X)d );   // OK, uses func( X, X )  
}  
```  
  
## 示例  
 解决此错误的另一个方式是通过 [using 声明](../../cpp/using-declaration.md)：  
  
```  
// C2668b.cpp  
// compile with: /EHsc /c  
// C2668 expected  
#include <iostream>  
class TypeA {  
public:  
   TypeA(int value) {}  
};  
  
class TypeB {  
   TypeB(int intValue);  
   TypeB(double dbValue);  
};  
  
class TestCase {  
public:  
   void AssertEqual(long expected, long actual, std::string  
                    conditionExpression = "");  
};  
  
class AppTestCase : public TestCase {  
public:  
   // Uncomment the following line to resolve.  
   // using TestCase::AssertEqual;  
   void AssertEqual(const TypeA expected, const TypeA actual,  
                    std::string conditionExpression = "");  
   void AssertEqual(const TypeB expected, const TypeB actual,  
                    std::string conditionExpression = "");  
};  
  
class MyTestCase : public AppTestCase {  
   void TestSomething() {  
      int actual = 0;  
      AssertEqual(0, actual, "Value");  
   }  
};  
```  
  
## 示例  
 也可能由于为 Visual Studio .NET 2003 进行的编译器一致性工作生成此错误：对常数 0 的转换的转换不明确。  
  
 对使用常数 0 的转换的转换不明确，因为 int 要求同时转换为 long 和 void\*。  为了解决此错误，将 0 转换为它所用于的函数参数的确切类型，这样不需要发生任何转换（此代码将在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中有效）。  
  
```  
// C2668c.cpp  
#include "stdio.h"  
void f(long) {  
   printf_s("in f(long)\n");  
}  
void f(void*) {  
   printf_s("in f(void*)\n");  
}  
int main() {  
   f((int)0);   // C2668  
  
   // OK  
   f((long)0);  
   f((void*)0);  
}  
```  
  
## 示例  
 发生此错误的可能原因是 CRT 现在具有所有算术函数的浮点和双精度形式。  
  
```  
// C2668d.cpp  
#include <math.h>  
int main() {  
   int i = 0;  
   float f;  
   f = cos(i);   // C2668  
   f = cos((float)i);   // OK  
}  
```  
  
## 示例  
 发生此错误的可能原因是从 CRT 中的 math.h 删除了 pow\(int, int\)。  
  
```  
// C2668e.cpp  
#include <math.h>  
int main() {  
   pow(9,9);   // C2668  
   pow((double)9,9);   // OK  
}  
```