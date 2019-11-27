---
title: 异常规范（throw、noexcept）（C++）
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 8245704de16ba94dbe0479a3c19d2a83fb170989
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245882"
---
# <a name="exception-specifications-throw-noexcept-c"></a>异常规范（throw、noexcept）（C++）

异常规范是 C++ 语言功能，它指示的异常类型的函数可以传播的程序员的意图。 您可以通过使用*异常规范*来指定某个函数不能由异常退出。 编译器可以使用此信息来优化对函数的调用，并在意外的异常转义函数时终止程序。

在 C++ 17 之前没有两种类型的异常规范。 *Noexcept 规范*是 c + + 11 中的新规范。 它指定的潜在可以转义函数的异常集是否为空。 *动态异常规范*（或 `throw(optional_type_list)` 规范）在 c + + 11 中已弃用，在 c + + 17 中被删除，但 `throw()`是 `noexcept(true)`的别名。 此异常规范旨在提供有关可以跳出函数引发哪些异常的摘要信息，但在实践中找到它就会出现问题。 一种动态异常规范，该规范在某种程度上非常有用，因为无条件 `throw()` 规范。 例如，以下函数声明中：

```cpp
void MyFunction(int i) throw();
```
告诉编译器函数不引发任何异常。 但是，在 **/std： c + + 14**模式下，如果函数引发异常，这可能会导致未定义的行为。 因此，建议使用[noexcept](../cpp/noexcept-cpp.md)运算符而不是上述运算符：

```cpp
void MyFunction(int i) noexcept;
```
下表总结了 Microsoft C++的异常规范实现：

|异常规范|含义|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|函数不会引发异常。 在[/std 中： c + + 14](../build/reference/std-specify-language-standard-version.md)模式（这是默认值），`noexcept` 和 `noexcept(true)` 等效。 当从 `noexcept` 或 `noexcept(true)`声明的函数中引发异常时，将调用[std：： terminate](../standard-library/exception-functions.md#terminate) 。 当在 **/std： c + + 14**模式下声明为 `throw()` 的函数引发异常时，结果为未定义的行为。 不调用任何特定函数。 这是 c + + 14 标准中的一个偏离，要求编译器调用[std：：意想不到](../standard-library/exception-functions.md#unexpected)。  <br/> **Visual Studio 2017 版本15.5 及更高版本**：在 **/std 中： c + + 17**模式下，`noexcept`、`noexcept(true)`和 `throw()` 都是等效的。 在 **/std： c + + 17**模式下，`throw()` 是 `noexcept(true)`的别名。 在 **/std： c + + 17**模式下，当使用上述任一规范声明的函数引发异常时，将根据 c + + 17 标准的要求调用[std：： terminate](../standard-library/exception-functions.md#terminate) 。|
|`noexcept(false)`<br/>`throw(...)`<br/>无规范|函数可能会引发任何类型的异常。|
|`throw(type)`| （**C + + 14 及更早版本**）函数可能引发 `type`类型的异常。 编译器接受语法，但会将其解释为 `noexcept(false)`。 在 **/std 中： c + + 17**模式下，编译器会发出警告 C5040。|

如果在应用程序中使用异常处理，则调用堆栈中必须有一个函数，该函数在退出标记为 `noexcept`、`noexcept(true)`或 `throw()`的函数的外部范围之前，处理引发的异常。 如果在引发异常的函数和处理异常的函数之间调用的任何函数被指定为 `noexcept`，`noexcept(true)` （或者在 **/std： c + + 17**模式下 `throw()`），则当 noexcept 函数传播异常时，程序将终止。

函数的异常行为取决于以下因素：

- 设置的[语言标准编译模式](../build/reference/std-specify-language-standard-version.md)。
- 您是否在 C 或 C++ 下编译函数。

- 使用哪种[/EH](../build/reference/eh-exception-handling-model.md)编译器选项。

- 是否显式指定异常规范。

不允许对 C 函数使用显式异常规范。 假定 C 函数不在 **/ehsc**下引发异常，并且可能会在 **/ehs**、 **/eha**或 **/EHac**下引发结构化异常。

下表总结了 C++ 函数可能会有可能引发下处理选项的各种编译器异常是否：

|函数|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|没有异常规范的 C++ 函数|是|是|是|是|
|C++带有 `noexcept`、`noexcept(true)`或 `throw()` 异常规范的函数|是|是|是|是|
|C++带有 `noexcept(false)`、`throw(...)`或 `throw(type)` 异常规范的函数|是|是|是|是|

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

[try、throw 和 catch 语句 (C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[异常C++和错误处理的新式最佳实践](errors-and-exception-handling-modern-cpp.md)