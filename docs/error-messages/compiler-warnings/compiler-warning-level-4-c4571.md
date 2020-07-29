---
title: 编译器警告（等级 4）C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 4fe99e12c5d2dfb725e1e4aa0ac2fb0b1ccb4f28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219880"
---
# <a name="compiler-warning-level-4-c4571"></a>编译器警告（等级 4）C4571

信息： catch （...）语义自 Visual C++ 7.1 后发生更改。不再捕获结构化的异常（SEH）

当用 **/ehs**编译时，将为每个 catch （...）块生成 C4571。

使用 **/ehs**编译时，catch （...）块不会捕获结构化的异常（例如，被零除指针）;catch （...）块仅捕获显式引发的 c + + 异常。  有关详细信息，请参阅[异常处理](../../cpp/exception-handling-in-visual-cpp.md)。

默认情况下，此警告处于关闭状态。  打开此警告以确保在通过 **/ehs**进行编译时，catch （...）块不会捕获结构化异常。  请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

可以通过以下方式之一解析 C4571：

- 如果仍需要 catch （...）块来捕获结构化的异常，请通过 **/eha**进行编译。

- 如果你不希望 catch （...）块捕获结构化的异常，但仍希望使用 catch （...）块，请不要启用 C4571。  你仍可以使用结构化异常处理关键字（**__try**、和）捕获结构化异常 **`__except`** **`__finally`** 。  但请记住，编译的 **/ehs**析构函数将仅在引发 c + + 异常时调用，而不会在出现 SEH 异常时调用。

- 将 catch （...）块替换为特定 c + + 异常的 catch 块，并根据需要添加有关 c + + 异常处理的结构化异常处理（**__try**、 **`__except`** 和 **`__finally`** ）。  有关详细信息，请参阅[结构化异常处理（C/c + +）](../../cpp/structured-exception-handling-c-cpp.md) 。

有关详细信息，请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md) 。

## <a name="example"></a>示例

下面的示例生成 C4571。

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```
