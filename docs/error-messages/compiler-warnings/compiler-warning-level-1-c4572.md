---
title: 编译器警告（等级 1）C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: e32509e4d32eef4f53b8d43a7db769844f1182c7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779461"
---
# <a name="compiler-warning-level-1-c4572"></a>编译器警告（等级 1）C4572

[ParamArray] 特性已弃用，使用在 /clr 下...改为

使用指定的变量自变量列表的已过时样式。 在针对 CLR 进行编译，使用省略号语法而不是<xref:System.ParamArrayAttribute>。 有关详细信息，请参阅[变量自变量列表 （...）(C++/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

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