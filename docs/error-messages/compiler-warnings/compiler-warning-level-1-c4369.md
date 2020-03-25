---
title: 编译器警告（等级 1）C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b0d99792e3e0ea372c8629319553dd9a59ad4b47
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187058"
---
# <a name="compiler-warning-level-1-c4369"></a>编译器警告（等级 1）C4369

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
