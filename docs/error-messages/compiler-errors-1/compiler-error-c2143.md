---
title: "编译器错误 C2143 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2143"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2143"
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2143
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 : “token2”前缺少“token1”  
  
 编译器需要特定的标记（即空白以外的语言元素），但发现了另一个标记。  
  
 有关在使用函数 try 块时出现的该错误的信息，请参见[知识库文章 241706](http://support.microsoft.com/kb/241706)。  
  
 检查 [C\+\+ 语言参考](../../cpp/cpp-language-reference.md)以确定语法不正确的代码位置。  由于编译器在遇到导致问题的行后可能会报告该错误，因此请检查该错误前面的几行代码。  
  
 C2143 可能在不同情况下发生。  
  
 它可发生在此示例中，则可以限定名称时的运算符 \(`::`、`->`和 `.`\) 必须后跟 `template`关键字：  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143  
    {  
    };  
};  
  
```  
  
 默认情况下，C\+\+假设 `Ty::PutFuncType` 不是模板；因此，下面的 `<` 解释为小于号。必须显式告诉编译器 `PutFuncType` 是通过模板，以便可以正确分析尖括号。  若要更正此错误，请使用上依赖类型名称的 `template` 关键字，如下所示：  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct  
    {  
    };  
};  
  
```  
  
 在使用 **\/clr** 并且 `using` 指令有语法错误时触发C2143 ：  
  
```cpp  
// C2143a.cpp  
// compile with: /clr /c  
using namespace System.Reflection;   // C2143  
using namespace System::Reflection;  
```  
  
 在通过使用 CLR 语法而不使用 **\/clr** 尝试编译源代码文件时它也会发生：  
  
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
  
 跟在 `if` 语句后的第一个非空白字符必须是左括号。  编译器无法翻译任何其他内容：  
  
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
  
 在检测到错误的行上或紧靠该行的上面某行中缺少右大括号、圆括号或分号时，C2143可能发生：  
  
```caml  
// C2143d.cpp  
// compile with: /c  
class X {  
   int member1;  
   int member2   // C2143  
} x;  
```  
  
 或者，当在类声明中存在无效的标记时：  
  
```cpp  
// C2143e.cpp  
class X {  
   int member;  
} x;  
  
class + {};   // C2143 + is an invalid tag name  
class ValidName {};   // OK  
```  
  
 或者当一个标签未附加到语句时。  如果必须单独放置标签（如放置在复合语句的末尾），则将其附加到 null 语句中：  
  
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
  
 当对标准 C\+\+ 库中的类型进行一次非限定调用时，错误也会发生：  
  
```cpp  
// C2143g.cpp  
// compile with: /EHsc /c  
#include <vector>  
static vector<char> bad;   // C2143  
static std::vector<char> good;   // OK  
```  
  
 或者具有缺失的 `typename` 关键字：  
  
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
  
 或者如果尝试定义显式实例化：  
  
```cpp  
// C2143i.cpp  
// compile with: /EHsc /c  
// template definition  
template <class T>  
void PrintType(T i, T j) {}  
  
template void PrintType(float i, float j){}   // C2143  
template void PrintType(float i, float j);   // OK  
```  
  
 在 C 程序中，必须在函数的开头声明变量，且不能在函数执行非声明指令后声明变量。  
  
```c  
// C2143j.c  
int main()   
{  
    int i = 0;  
    i++;  
    int j = 0; // C2143  
}  
  
```