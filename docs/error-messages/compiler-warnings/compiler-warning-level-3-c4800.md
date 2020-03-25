---
title: 编译器警告（等级4） C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 828b38aeb184741af284f2d7722017b24f6255a3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198583"
---
# <a name="compiler-warning-level-4-c4800"></a>编译器警告（等级4） C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 及更高版本：
> 从 "*type*" 到布尔值的隐式转换。 可能的信息丢失
::: moniker-end

C4800 是 Visual Studio 2015 及更早版本中的3级警告：
> "*type*"：将值强制为布尔值 "true" 或 "false" （性能警告）

将值隐式转换为类型 `bool`时，将生成此警告。 通常，此消息是由将 `int` 变量分配给 `bool` 变量导致的，其中 `int` 变量只包含值**true**和**false**，并且可以重新声明为类型 `bool`。 如果无法重写表达式以使用类型 `bool`，则可以将 "`!=0`" 添加到表达式，该表达式将为表达式类型提供 `bool`。 将表达式强制转换为类型 `bool` 不会禁用该警告，这是设计使然。

::: moniker range=">= vs-2017"
此警告不会在 Visual Studio 2017 中发出。
::: moniker-end

::: moniker range=">= vs-2019"
从 Visual Studio 2019 开始，此警告默认为关闭状态。 使用 __/w__*n*__4800__启用 C4800 作为级别*n*警告，或使用[/Wall](../../build/reference/compiler-option-warning-level.md)启用默认情况下处于关闭状态的所有警告。 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
::: moniker-end

## <a name="example"></a>示例

下面的示例生成 C4800，并演示如何修复此问题：

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
