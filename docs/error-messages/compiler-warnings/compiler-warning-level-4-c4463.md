---
title: 编译器警告 （等级 C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: e125a532f87533958ec43ed5580665ad4108856b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474808"
---
# <a name="compiler-warning-level-4-c4463"></a>编译器警告 （等级 C4463

> 地址信息溢出;将分配*值*到只包含中的值的位域*low_value*到*high_value*

已分配*值*之外的值的位域所能容纳的范围。 有符号的位域类型使用高顺序位表示符号，因此，如果*n*是位域大小范围的有符号的位域，-2<sup>n-1</sup>到 2<sup>n-1</sup>-1，而无符号位域使范围介于 0 到 2<sup>n</sup>-1。

## <a name="example"></a>示例

此示例生成 C4463，因为它尝试分配给类型的位字段的值为 3`int`大小为 2，其中包含从-2 到 1 的范围。

若要解决此问题，可以分配的值更改为所允许的范围中的某些内容。 如果位字段旨在在范围从 0 到 3 中保存无符号的值，您可以将声明类型更改为`unsigned`。 如果该字段用于在范围-4 到 3 中保存值，然后可以更改位字段大小为 3。

```cpp
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S {
    int x : 2; // int type treats high-order bit as sign
};

int main() {
    S s;
    s.x = 3; // warning C4463: overflow; assigning 3
    // to bit-field that can only hold values from -2 to 1
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type
    // to unsigned.
}
```
