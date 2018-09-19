---
title: 编译器警告 （等级 1） C4572 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4572
dev_langs:
- C++
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b87b3dd4264db9fd7ea3699f342358fa6d4d5aac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076835"
---
# <a name="compiler-warning-level-1-c4572"></a>编译器警告（等级 1）C4572

在 /clr 下的 [ParamArray] 特性不推荐使用，请使用...改为

使用指定的变量自变量列表的已过时样式。 在针对 CLR 进行编译，使用省略号语法而不是<xref:System.ParamArrayAttribute>。 有关详细信息，请参阅[变量自变量列表 （...）(C + + CLI)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>示例

下面的示例生成 C4572。

```
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```