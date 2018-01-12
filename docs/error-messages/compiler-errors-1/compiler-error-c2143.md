---
title: "编译器错误 C2143 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2143
dev_langs: C++
helpviewer_keywords: C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fa7560b3b7d13beb416c2f500c0ab692e9f0d717
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2143"></a>编译器错误 C2143
语法错误： 缺少 token1 之前 token2  
  
 编译器需要一个特定的标记 （即，空白区域以外的语言元素），但发现另一个标记。  
  
 有关此错误的信息时它发生在使用该函数 try 块时，请参阅[知识库文章 241706](http://support.microsoft.com/kb/241706)。  
  
 检查[c + + 语言参考](../../cpp/cpp-language-reference.md)以确定其中代码的语法不正确。 该错误前面代码的多个的行，因为编译器可能会报告此错误，在它遇到导致问题的行之后，检查。  
  
 在不同情况下可能发生 C2143。  
  
 可限定名称（`::`、`->` 和 `.`）的运算符后面必须跟有关键字 `template` 时可能发生，如下例所示：  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143  
    {  
    };  
};  
  
```  
  
 默认情况下，C++ 会假定 `Ty::PutFuncType` 不是模板；因此，后面的 `<` 解释为小于号。  必须显式告知编译器 `PutFuncType` 是模板，以便其正确分析尖括号。 若要更正此错误，请在依赖类型的名称上使用 `template` 关键字，如下所示：  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct  
    {  
    };  
};  
  
```  
  
 可能发生 C2143 时**/clr**使用和`using`指令有语法错误：  
  
```cpp  
// C2143a.cpp  
// compile with: /clr /c  
using namespace System.Reflection;   // C2143  
using namespace System::Reflection;  
```  
  
 当你尝试编译源代码文件，方法是使用 CLR 语法而不使用它也会发生**/clr**:  
  
```cpp  
// C2143b.cpp  
ref struct A {   // C2143 error compile with /clr  
   void Test() {}  
};  
  
int main() {  
   A a;  
   a.Test();  
}  
```  
  
 跟在 `if` 语句后的第一个非空白字符必须是左括号。 编译器无法转换任何其他内容：  
  
```cpp  
// C2143c.cpp  
int main() {  
   int j = 0;  
  
   // OK  
   if (j < 25)  
      ;  
  
   if (j < 25)   // C2143  
}  
```  
  
 在检测到错误的行上或紧靠该行的上面某行中缺少右大括号、圆括号或分号时，可能发生 C2143：  
  
```cpp  
// C2143d.cpp  
// compile with: /c  
class X {  
   int member1;  
   int member2   // C2143  
} x;  
```  
  
 或者类声明中存在无效的标记时：  
  
```cpp  
// C2143e.cpp  
class X {  
   int member;  
} x;  
  
class + {};   // C2143 + is an invalid tag name  
class ValidName {};   // OK  
```  
  
 或者一个标签未附加到语句时。 如果你必须将标签放置的本身，例如，在复合语句的末尾将其附加到 null 语句：  
  
```cpp  
// C2143f.cpp  
// compile with: /c  
void func1() {  
   // OK  
   end1:  
      ;  
  
   end2:   // C2143  
}  
```  
  
 C + + 标准库中的类型进行非限定的调用时，会发生此错误：  
  
```cpp  
// C2143g.cpp  
// compile with: /EHsc /c  
#include <vector>  
static vector<char> bad;   // C2143  
static std::vector<char> good;   // OK  
```  
  
 或者缺失 `typename` 关键字：  
  
```cpp  
// C2143h.cpp  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
template <typename T>  
X<T>::Y X<T>::memFunc() {   // C2143  
// try the following line instead  
// typename X<T>::Y X<T>::memFunc() {  
   return Y();  
}  
```  
  
 或者尝试定义显式实例化：  
  
```cpp  
// C2143i.cpp  
// compile with: /EHsc /c  
// template definition  
template <class T>  
void PrintType(T i, T j) {}  
  
template void PrintType(float i, float j){}   // C2143  
template void PrintType(float i, float j);   // OK  
```  
  
 在 C 程序中，变量必须声明开头的函数，而且它们不能声明该函数执行非声明说明后变量。  
  
```C  
// C2143j.c  
int main()   
{  
    int i = 0;  
    i++;  
    int j = 0; // C2143  
}  
```  
