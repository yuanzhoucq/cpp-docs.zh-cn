---
title: "异常规范 (throw) (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 异常处理, 引发异常"
  - "异常, 异常规范"
  - "throw 关键字 [C++], 异常规范"
  - "throw 关键字 [C++], throw() 与 throw(...)"
  - "引发异常, throw 关键字"
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常规范 (throw) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

异常规范是在 C\+\+11 中弃用的 C\+\+ 语言功能。  这些规范原本用来提供有关可从函数引发哪些异常的摘要信息，但在实际应用中发现这些规范存在问题。  证明确实有一定用处的一个异常规范是 throw\(\) 规范。  例如:  
  
```  
void MyFunction(int i) throw();  
```  
  
 告诉编译器函数不引发任何异常。  它相当于使用 [\_\_declspec\(nothrow\)](../cpp/nothrow-cpp.md)。  这种用法是可选的。  
  
 **\(C\+\+11\)** 在 ISO C\+\+11 标准中，引入了 [noexcept](../cpp/noexcept-cpp.md) 运算符，该运算符在 Visual Studio 2015 及更高版本中受支持。  尽可能使用 `noexcept` 指定函数是否可能会引发异常。  
  
 Visual C\+\+ 中实现的异常规范与 ISO C\+\+ 标准有所不同。  下表总结了 Visual C\+\+ 的异常规范实现：  
  
|异常规范|含义|  
|----------|--------|  
|throw\(\)|函数不会引发异常。  但是，如果从标记为 throw\(\) 函数引发异常，Visual C\+\+ 编译器将不会调用意外处理函数（有关更多信息，请参阅 [unexpected](../c-runtime-library/reference/unexpected-crt.md) 和 [unexpected](../Topic/unexpected%20\(%3Cexception%3E\).md)）。  如果使用 throw\(\) 标记一个函数，则 Visual C\+\+ 编译器假定该函数不会引发 C\+\+ 异常，并相应地生成代码。  由于 C\+\+ 编译器可能会执行代码优化（基于函数不会引发任何 C\+\+ 异常的假设），因此，如果函数引发异常，则程序可能无法正确执行。|  
|throw\(...\)|函数可以引发异常。|  
|throw\(`type`\)|函数可以引发 `type` 类型的异常。  但是，在 Visual C\+\+ .NET 中，这被解释为 throw\(...\)。  请参阅[函数异常说明符](../misc/15-4-function-exception-specifiers.md)。|  
  
 如果在应用程序中使用异常处理，则一定有一个或多个函数处理引发的异常。  在引发异常的函数和处理异常的函数间调用的所有函数必须能够引发异常。  
  
 函数的引发行为基于以下因素：  
  
-   您是否在 C 或 C\+\+ 下编译函数。  
  
-   您所使用的 [\/EH](../build/reference/eh-exception-handling-model.md) 编译器选项。  
  
-   是否显式指定异常规范。  
  
 不允许对 C 函数使用显式异常规范。  
  
 下表总结了函数的引发行为：  
  
|函数|\/EHsc|\/EHs|\/EHa|\/EHac|  
|--------|------------|-----------|-----------|------------|  
|C 函数|throw\(\)|throw\(...\)|throw\(...\)|throw\(...\)|  
|没有异常规范的 C\+\+ 函数|throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|  
|带有 throw\(\) 异常规范的 C\+\+ 函数|throw\(\)|throw\(\)|throw\(...\)|throw\(...\)|  
|带有 throw\(...\) 异常规范的 C\+\+ 函数|throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|  
|带有 throw\(`type`\) 异常规范的 C\+\+ 函数|throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|  
  
## 示例  
  
```cpp  
// exception_specification.cpp  
// compile with: /EHs  
#include <stdio.h>  
  
void handler() {  
   printf_s("in handler\n");  
}  
  
void f1(void) throw(int) {  
   printf_s("About to throw 1\n");  
   if (1)  
      throw 1;  
}  
  
void f5(void) throw() {  
   try {  
      f1();  
   }  
   catch(...) {  
      handler();  
    }  
}  
  
// invalid, doesn't handle the int exception thrown from f1()  
// void f3(void) throw() {  
//   f1();  
// }  
  
void __declspec(nothrow) f2(void) {  
   try {  
      f1();  
   }  
   catch(int) {  
      handler();  
    }  
}  
  
// only valid if compiled without /EHc   
// /EHc means assume extern "C" functions don't throw exceptions  
extern "C" void f4(void);  
void f4(void) {  
   f1();  
}  
  
int main() {  
   f2();  
  
   try {  
      f4();  
   }  
   catch(...) {  
      printf_s("Caught exception from f4\n");  
   }  
   f5();  
}  
```  
  
  **About to throw 1**  
**in handler**  
**About to throw 1**  
**Caught exception from f4**  
**About to throw 1**  
**in handler**   
## 请参阅  
 [try、throw 和 catch 语句 \(C\+\+\)](../cpp/try-throw-and-catch-statements-cpp.md)   
 [C\+\+ 异常处理](../cpp/cpp-exception-handling.md)