---
title: 编译器警告（等级1） C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: 617cb2cc3774b288581a3868125ced19b28ba45a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966512"
---
# <a name="compiler-warning-level-1-c4369"></a>编译器警告（等级1） C4369

"枚举器"：枚举器值 "value" 不能表示为 "type"，值为 "new_value"

计算出的枚举数大于指定的基础类型的最大值。  这会导致溢出，并且编译器会将枚举器值包装为该类型的最小可能值。

## <a name="example"></a>示例

下面的示例生成 C4369。

```cpp
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```