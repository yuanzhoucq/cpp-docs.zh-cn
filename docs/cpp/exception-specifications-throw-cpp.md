---
title: 异常规范 （throw，noexcept） （C++） |Microsoft 文档
ms.custom: ''
ms.date: 01/18/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1dfc9c50503fcd277f34e8f5dfc4a630d888eebf
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318262"
---
# <a name="exception-specifications-throw-noexcept-c"></a>异常规范 （throw，noexcept） （C++）

异常规范是 C++ 语言功能，它指示的异常类型的函数可以传播的程序员的意图。 可以指定一个函数可能会或可能通过使用异常退出*异常规范*。 编译器可以使用此信息来优化对函数的调用并终止程序，如果异常转义函数。 

在 C++ 17 之前没有两种类型的异常规范。 *Noexcept 规范*C++ 11 中的新增功能。 它指定的潜在可以转义函数的异常集是否为空。 *动态异常规范*，或`throw(optional_type_list)`规范中，已在 C++ 11 中弃用并删除 C++ 17 中除`throw()`，即的别名`noexcept(true)`。 此异常规范旨在提供有关可以跳出函数引发哪些异常的摘要信息，但在实践中找到它就会出现问题。 证明确实有一定用处的一个动态异常规范是无条件`throw()`规范。 例如，以下函数声明中：

```cpp
void MyFunction(int i) throw();
```
告诉编译器函数不引发任何异常。 但是，在 **/std:C++ 14**模式，这可能导致未定义行为，如果该函数会引发异常。 因此我们建议使用[noexcept](../cpp/noexcept-cpp.md)运算符而不是如上所示：

```cpp
void MyFunction(int i) noexcept;
```
下表总结了异常规范的 Microsoft Visual C++ 实现：

|异常规范|含义|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|函数不会引发异常。 在[/std:C++ 14](../build/reference/std-specify-language-standard-version.md)模式 （这是默认值），`noexcept`和`noexcept(true)`是等效的。 从声明的函数引发异常`noexcept`或`noexcept(true)`， [std:: terminate](../standard-library/exception-functions.md#terminate)调用。 从函数引发异常声明为`throw()`中 **/std:C++ 14**模式时，结果是未定义的行为。 调用没有特定的函数。 这是从 C++ 14 标准，分歧，这要求编译器将调用[std::unexpected](../standard-library/exception-functions.md#unexpected)。  <br/> **Visual Studio 2017 15.5 及更高版本**： 在 **/std:C++ 17**模式下， `noexcept`， `noexcept(true)`，和`throw()`都是等效的。 在 **/std:C++ 17**模式下，`throw()`是的别名`noexcept(true)`。 在 **/std:C++ 17**模式下，当从与任意这些规范中，声明的函数引发异常[std:: terminate](../standard-library/exception-functions.md#terminate)调用通过 C++ 17 标准所需的方式。|
|`noexcept(false)`<br/>`throw(...)`<br/>无规范|函数可以引发任何类型的异常。|
|`throw(type)`| (**C++ 14 及更早版本**) 函数可以引发类型的异常`type`。 编译器接受语法，但将其作为解释`noexcept(false)`。 在 **/std:C++ 17**模式编译器发出警告 C5040。|

如果应用程序中使用异常处理，则必须有一个函数中它们退出函数的外部作用域之前引发的异常的句柄标记为在调用堆栈`noexcept`， `noexcept(true)`，或`throw()`。 如果调用之间的任何函数会引发异常和处理异常的一个指定为`noexcept`， `noexcept(true)` (或`throw()`中 **/std:C++ 17**模式)，程序将终止时noexcept 函数将此异常的传播。

一个函数的异常行为取决于以下因素：

- 这[语言标准编译模式](../build/reference/std-specify-language-standard-version.md)设置。
- 您是否在 C 或 C++ 下编译函数。

- 这[/EH](../build/reference/eh-exception-handling-model.md)您使用的编译器选项。

- 是否显式指定异常规范。

不允许对 C 函数使用显式异常规范。 C 函数假定不引发异常下的 **/EHsc**，并且可能会引发结构化的异常下 **/EHs**， **/EHa**，或 **/EHac**。

下表总结了 C++ 函数可能会有可能引发下处理选项的各种编译器异常是否：

|函数|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|没有异常规范的 C++ 函数|是|是|是|是|
|使用 C++ 函数`noexcept`， `noexcept(true)`，或`throw()`异常规范|否|否|是|是|
|使用 C++ 函数`noexcept(false)`， `throw(...)`，或`throw(type)`异常规范|是|是|是|是|

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

## <a name="see-also"></a>请参阅
 [try、throw 和 catch 语句 (C++)](../cpp/try-throw-and-catch-statements-cpp.md)  
 [C++ 异常处理](../cpp/cpp-exception-handling.md)