---
title: "编译器错误 C2668 |Microsoft 文档"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2668
dev_langs: C++
helpviewer_keywords: C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e45bff3173013e7a26f9682bb10ec4cc1fda9364
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2668"></a>编译器错误 C2668
function： 对重载函数调用不明确  
  
 无法解析指定的重载的函数调用。 你可能想要将一个或多个实参显式转换。  
  
 此外可以通过模板使用来获取此错误。 如果在同一类中，你有正则成员函数和模板化的成员函数具有相同签名，必须出现在模板化的一个最前面。 这是 Visual c + + 的当前实现的限制。  
  
 在函数模板的部分排序，请参阅知识库文章 Q240869 有关详细信息。  
  
 如果你要生成包含 COM 对象支持 ATL 项目`ISupportErrorInfo`，请参阅知识库文章 Q243298。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2668:  
  
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
  
## <a name="example"></a>示例  
 若要解决此错误的另一个方法是使用[using 声明](../../cpp/using-declaration.md):  
  
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
  
## <a name="example"></a>示例  
 此错误还可能来自于为 Visual Studio.NET 2003年执行的编译器一致性工作： 强制转换为常量 0 上的不明确转换。  
  
 强制转换使用常量 0 上的转换是不明确，因为 int 需要这两个到转换和长到 void *。 若要解决此错误，强制转换为它正用于以便发生 （此代码将在 Visual c + + 的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中有效） 所需的任何转换的函数参数的确切类型 0。  
  
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
  
## <a name="example"></a>示例  
 由于 CRT 现在具有 float 和 double 窗体的所有数学函数，则可能出现此错误。  
  
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
  
## <a name="example"></a>示例  
 因为 pow （int，int） 已从 CRT 中的 math.h 中删除，则可能出现此错误。  
  
```  
// C2668e.cpp  
#include <math.h>  
int main() {  
   pow(9,9);   // C2668  
   pow((double)9,9);   // OK  
}  
```

## <a name="example"></a>示例  
此代码在 Visual Studio 2015 中成功，但失败 C2668 在 Visual Studio 2017 和更高版本。 在 Visual Studio 2015 中，编译器以与常规复制初始化相同的方式错误地处理复制列表初始化；它只考虑将转换构造函数用于重载决策。 

```
C++
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```