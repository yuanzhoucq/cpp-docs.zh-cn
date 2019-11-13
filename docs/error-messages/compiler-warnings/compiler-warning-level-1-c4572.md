---
title: 编译器警告（等级1） C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: 52285f391af0a8028307cbbc320af33f9cb1fca5
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965943"
---
# <a name="compiler-warning-level-1-c4572"></a>编译器警告（等级1） C4572

[ParamArray] 特性已在/clr 下弃用，请使用 "..."是

使用了指定变量参数列表的过时样式。 编译 CLR 时，请使用省略号语法而不是 <xref:System.ParamArrayAttribute>。 有关详细信息，请参阅[变量参数列表（...）C++（/cli）](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C4572。

```cpp
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```