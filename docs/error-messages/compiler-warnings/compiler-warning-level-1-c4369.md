---
title: 编译器警告（等级 1）C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b374b67fa3319be35490358d7664bcb45bc640db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623946"
---
# <a name="compiler-warning-level-1-c4369"></a>编译器警告（等级 1）C4369

枚举器： 不能为 type 表示枚举器值 value，值为 new_value

一个枚举器的计算结果为大于指定的基础类型的最大值。  这会导致溢出，编译器包装类型的最小可能值的枚举器值。

## <a name="example"></a>示例

下面的示例生成 C4369。

```
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```