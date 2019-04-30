---
title: 已弃用 (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: 34f9c10cd898b0359463d5933141822576fa4a11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398948"
---
# <a name="deprecated-c"></a>已弃用 (C++)

本主题提供有关特定于 Microsoft 的信息已弃用 declspec 声明。 有关 C++ 14`[[deprecated]]`属性，以及有关何时使用与 Microsoft 专用 declspec 或杂注时，该属性的指导，请参阅[C++ 标准特性](attributes.md)。

如下所示的异常**弃用**声明提供相同的功能[弃用](../preprocessor/deprecated-c-cpp.md)杂注：

- **弃用**声明允许您函数重载的特殊形式指定为已弃用，而杂注形式适用于所有重载形式的函数名称。

- **弃用**声明允许您指定在编译时将显示一条消息。 该消息的文本可以来自宏。

- 宏只标记为与已弃用**弃用**杂注。

如果编译器遇到使用不推荐使用的标识符或标准[ `[[deprecated]]` ](attributes.md)属性， [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)引发警告。

## <a name="example"></a>示例

下面的示例演示在使用已弃用的函数时，如何将函数标记为已弃用以及如何指定在编译时将显示的消息。

```cpp
// deprecated.cpp
// compile with: /W3
#define MY_TEXT "function is deprecated"
void func1(void) {}
__declspec(deprecated) void func1(int) {}
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}
__declspec(deprecated(MY_TEXT)) void func3(int) {}

int main() {
   func1();
   func1(1);   // C4996
   func2(1);   // C4996
   func3(1);   // C4996
}
```

## <a name="example"></a>示例

下面的示例演示在使用已弃用的类时，如何将类标记为已弃用以及如何指定在编译时将显示的消息。

```cpp
// deprecate_class.cpp
// compile with: /W3
struct __declspec(deprecated) X {
   void f(){}
};

struct __declspec(deprecated("** X2 is deprecated **")) X2 {
   void f(){}
};

int main() {
   X x;   // C4996
   X2 x2;   // C4996
}
```

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)