---
title: 异常规范（throw、noexcept）（c + +）
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 1fa56ebf0a0358845ef620a89bc416992b3c0e31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221570"
---
# <a name="exception-specifications-throw-noexcept-c"></a>异常规范（throw、noexcept）（c + +）

异常规范是一项 c + + 语言功能，指示程序员对可通过函数传播的异常类型的意图。 您可以通过使用*异常规范*来指定某个函数不能由异常退出。 编译器可以使用此信息来优化对函数的调用，并在意外的异常转义函数时终止程序。

C + + 17 之前存在两种异常规范。 *Noexcept 规范*是 c + + 11 中的新规范。 它指定可以对函数进行转义的潜在异常集是否为空。 *动态异常规范*（即 `throw(optional_type_list)` 规范）在 c + + 11 中已弃用，并在 c + + 17 中删除， `throw()` 后者是的别名 `noexcept(true)` 。 此异常规范旨在提供有关可能会从函数中引发的异常的摘要信息，但实际上却发现有问题。 特别有用的一项动态异常规范是无条件 `throw()` 规范。 例如，函数声明：

```cpp
void MyFunction(int i) throw();
```

告诉编译器函数不引发任何异常。 但是，在 **/std： c + + 14**模式下，如果函数引发异常，这可能会导致未定义的行为。 因此，建议使用[noexcept](../cpp/noexcept-cpp.md)运算符而不是上述运算符：

```cpp
void MyFunction(int i) noexcept;
```

下表总结了异常规范的 Microsoft c + + 实现：

|异常规范|含义|
|-----------------------------|-------------|
|**`noexcept`**<br/>`noexcept(true)`<br/>`throw()`|函数不会引发异常。 在[/std 中： c + + 14](../build/reference/std-specify-language-standard-version.md)模式（这是默认值）， **`noexcept`** 和 `noexcept(true)` 等效。 如果异常是从声明的函数引发的 **`noexcept`** 或，则 `noexcept(true)` 调用[std：： terminate](../standard-library/exception-functions.md#terminate) 。 当在 `throw()` **/std： c + + 14**模式下声明为的函数中引发异常时，结果为未定义的行为。 不调用任何特定函数。 这是 c + + 14 标准中的一个偏离，要求编译器调用[std：：意想不到](../standard-library/exception-functions.md#unexpected)。  <br/> **Visual Studio 2017 版本15.5 及更高版本**：在 **/std 中： c + + 17**模式，、 **`noexcept`** `noexcept(true)` 和 `throw()` 都是等效的。 在 **/std 中： c + + 17**模式下， `throw()` 是的别名 `noexcept(true)` 。 在 **/std： c + + 17**模式下，当使用上述任一规范声明的函数引发异常时，将根据 c + + 17 标准的要求调用[std：： terminate](../standard-library/exception-functions.md#terminate) 。|
|`noexcept(false)`<br/>`throw(...)`<br/>无规范|函数可能会引发任何类型的异常。|
|`throw(type)`| （**C + + 14 及更早版本**）函数可能会引发类型为的异常 `type` 。 编译器接受语法，但将其解释为 `noexcept(false)` 。 在 **/std 中： c + + 17**模式下，编译器会发出警告 C5040。|

如果在应用程序中使用异常处理，则调用堆栈中必须有一个函数，该函数在退出标记为、或的函数的外部范围之前处理引发的异常 **`noexcept`** `noexcept(true)` `throw()` 。 如果在引发异常的函数和处理异常的函数之间调用的任何函数被指定为（ **`noexcept`** `noexcept(true)` 或 `throw()` 在 **/std： c + + 17**模式下），则当 noexcept 函数传播异常时，程序将终止。

函数的异常行为取决于以下因素：

- 设置的[语言标准编译模式](../build/reference/std-specify-language-standard-version.md)。
- 您是否在 C 或 C++ 下编译函数。

- 使用哪种[/EH](../build/reference/eh-exception-handling-model.md)编译器选项。

- 是否显式指定异常规范。

不允许对 C 函数使用显式异常规范。 假定 C 函数不在 **/ehsc**下引发异常，并且可能会在 **/ehs**、 **/eha**或 **/EHac**下引发结构化异常。

下表总结了 c + + 函数是否可能在各种编译器异常处理选项下引发：

|函数|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|没有异常规范的 C++ 函数|“是”|“是”|“是”|“是”|
|C + + 函数与 **`noexcept`** 、 `noexcept(true)` 或 `throw()` 异常规范|否|否|是|“是”|
|C + + 函数与 `noexcept(false)` 、 `throw(...)` 或 `throw(type)` 异常规范|“是”|“是”|“是”|是|

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
[异常和错误处理的新式 c + + 最佳做法](errors-and-exception-handling-modern-cpp.md)
