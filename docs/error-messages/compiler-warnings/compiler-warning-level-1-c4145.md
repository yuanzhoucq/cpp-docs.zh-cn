---
title: 编译器警告（等级 1）C4145
ms.date: 11/04/2016
f1_keywords:
- C4145
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
ms.openlocfilehash: 10c0211bfda354a00e05cba3131d047fce843df8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553785"
---
# <a name="compiler-warning-level-1-c4145"></a>编译器警告（等级 1）C4145

“expression1”: 关系表达式用作 switch 表达式；可能和“expression2”混淆

`switch` 语句使用关系表达式作为其控制表达式，这会导致的 **case** 语句的布尔值。 是否希望使用 *expression2*?

## <a name="example"></a>示例

下面的示例生成 C4145:

```
// C4145.cpp
// compile with: /W1
int main() {
   int i = 0;
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve
      case 1:
         break;
      default:
         break;
   }
}
```