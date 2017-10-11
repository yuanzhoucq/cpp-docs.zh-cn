---
title: "异常规范 (throw) （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++], throw() vs. throw(...)
- throw keyword [C++], exception specifications
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6577cf489ee1c9d64689938bb8a12660cec96893
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="exception-specifications-throw-noexcept-c"></a>异常规范 （throw，noexcept） （c + +）
异常规范是 c + + 语言功能，它指示的异常类型的函数可以传播的程序员的意图。 你可以指定一个函数可能或可能不通过使用中退出的异常*异常规范*。 编译器可以使用此信息来优化对该函数调用和终止程序，如果异常转义函数。 有两种类型的异常规范。 *Noexcept 规范*是 C + + 11 中的新增功能。 它指定的潜在可以转义函数的异常集是否为空。 *动态异常规范*，或`throw(optional_type_list)`规范中，在 C + + 11 中已弃用，并且仅部分 Visual Studio 提供的支持。 此异常规范旨在提供有关可以跳出函数引发哪些异常的摘要信息，但在实践中找到它就会出现问题。 证明确实有一定用处的一个动态异常规范是无条件`throw()`规范。 例如，以下函数声明中：  
  
```cpp  
void MyFunction(int i) throw();  
```  
  
 告诉编译器函数不引发任何异常。 它等效于使用[__declspec （nothrow)](../cpp/nothrow-cpp.md)。 这种用法是可选的。  
  
ISO C + + 11 标准中， [noexcept](../cpp/noexcept-cpp.md)运算符引入作为替代。 它支持 Visual Studio 2015 及更高版本。 只要可能，使用`noexcept`表达式来指定函数是否可能引发异常。 例如，使用此函数声明，而不是上述的一个：  
  
```cpp  
void MyFunction(int i) noexcept;  
```  
  
虽然 Visual c + + 完全支持`noexcept`表达式，它有所不同 ISO c + + 标准在其实现中的动态异常规范。  下表总结了 Visual C++ 的异常规范实现：  
  
|异常规范|含义|  
|-----------------------------|-------------|  
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|函数不会引发异常。 但是，如果从标记函数引发异常`throw()`，Visual c + + 编译器调用`std::terminate`，而不`std::unexpected`。 请参阅[std::unexpected](../c-runtime-library/reference/unexpected-crt.md)有关详细信息。 如果标记一个函数`noexcept`， `noexcept(true)`，或`throw()`，Visual c + + 编译器将假定该函数不会引发 c + + 异常，并相应地生成代码。 因为基于，函数不引发任何 c + + 异常，如果一个函数会引发异常的假设 c + + 编译器可能会执行代码优化，程序可能无法正确执行。|  
|`noexcept(false)`<br/>`throw(...)`<br/>没有规范|函数可以引发任何类型的异常。|  
|`throw(type)`|函数可以引发 `type` 类型的异常。 Visual c + + 中接受此语法，但它被解释为`noexcept(false)`。|  
  
 如果应用程序中使用异常处理，则必须有一个函数引发异常之前它们退出外部函数的范围内的句柄标记为调用堆栈中`noexcept`， `noexcept(true)`，或`throw()`。 如果调用之间的任何函数会引发异常和处理异常的一个指定为`noexcept`， `noexcept(true)`，或`throw()`，程序将终止时 noexcept 函数传播异常。  
  
 函数的异常行为取决于以下因素：  
  
-   您是否在 C 或 C++ 下编译函数。  
  
-   其中[/EH](../build/reference/eh-exception-handling-model.md)你使用的编译器选项。  
  
-   是否显式指定异常规范。  
  
 不允许对 C 函数使用显式异常规范。 C 假定函数不引发异常下的**/EHsc**，并且可能会引发下的结构化的异常**/EHs**， **/EHa**，或**/EHac**。  
  
 下表总结了 c + + 函数可能会有可能引发下处理选项的各种编译器异常是否：  
  
|函数|/EHsc|/EHs|/EHa|/EHac|  
|--------------|------------|-----------|-----------|------------|  
|没有异常规范的 C++ 函数|是|是|是|是|  
|使用 c + + 函数`noexcept`， `noexcept(true)`，或`throw()`异常规范|No|No|是|是|  
|使用 c + + 函数`noexcept(false)`， `throw(...)`，或`throw(type)`异常规范|是|是|是|是|  
  
## <a name="example"></a>示例  
  
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
  
```Output  
About to throw 1  
in handler  
About to throw 1  
Caught exception from f4  
About to throw 1  
in handler  
```  
  
## <a name="see-also"></a>另请参阅  
 [try、throw 和 catch 语句 (C++)](../cpp/try-throw-and-catch-statements-cpp.md)   
 [C++ 异常处理](../cpp/cpp-exception-handling.md)
