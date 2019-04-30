---
title: 编译器警告 （等级 C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 46418063625e16385497740a4f7e3d837e923156
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401548"
---
# <a name="compiler-warning-level-4-c4800"></a>编译器警告 （等级 C4800

::: moniker range=">= vs-2019"
2019 及更高版本的 visual Studio:
> 从隐式转换*类型*为布尔值。 可能会丢失信息
::: moniker-end

C4800 为级别 3 警告，在 Visual Studio 2015 及更早版本：
> '*类型*： 值强制到 bool 'true' 或 'false' （性能警告）

一个值隐式转换为类型时，会生成此警告`bool`。 通常情况下，此消息由分配`int`到变量`bool`变量其中`int`变量仅包含值**true**并**false**，并且可能重新声明为类型`bool`。 如果您不能重写表达式以使用类型`bool`，然后可以将添加"`!=0`"到表达式中，它可使表达式类型`bool`。 强制转换表达式到类型`bool`不会禁用警告，这是设计使然。

::: moniker range=">= vs-2017"
在 Visual Studio 2017 中不发出此警告。
::: moniker-end

::: moniker range=">= vs-2019"
默认情况下，从 Visual Studio 2019 情况下，此警告处于关闭状态。 使用 __/w__*n*__4800__以便作为级别 C4800 *n*警告，或[/wall](../../build/reference/compiler-option-warning-level.md)若要启用所有警告，默认情况下处于关闭状态。 有关详细信息，请参阅[编译器警告，是 Off By Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
::: moniker-end

## <a name="example"></a>示例

下面的示例生成 C4800 并演示如何修复此错误：

```cpp
// C4800.cpp
// compile with: /W4 /w44800
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```