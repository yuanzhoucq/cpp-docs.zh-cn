---
title: 编译器错误 C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 9e20333a4fc18219f7f2514f3aefe73b81f284a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759485"
---
# <a name="compiler-error-c3068"></a>编译器错误 C3068

"function"： "naked" 函数不能包含在发生C++异常时需要展开的对象

编译器无法对引发异常的[裸](../../cpp/naked-cpp.md)函数执行堆栈展开，因为在函数中创建了临时对象，但C++指定了异常处理（[/ehsc](../../build/reference/eh-exception-handling-model.md)）。

若要解决此错误，请至少执行下列操作之一：

- 不要用/EHsc. 编译

- 不要将函数标记为 `naked`。

- 不要在函数中创建临时对象。

如果函数在堆栈上创建临时对象，则如果函数引发异常，并且如果C++启用异常处理，则编译器将在引发异常时清理堆栈。

当引发异常时，将对函数执行编译器生成的代码，该代码称为 prolog 和 epilog，而在裸函数中不存在。

## <a name="example"></a>示例

下面的示例生成 C3068：

```cpp
// C3068.cpp
// compile with: /EHsc
// processor: x86
class A {
public:
   A(){}
   ~A(){}
};

void b(A){}

__declspec(naked) void c() {
   b(A());   // C3068
};
```
