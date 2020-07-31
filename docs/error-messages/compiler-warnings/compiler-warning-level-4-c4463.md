---
title: 编译器警告（等级4） C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: acc7957493942a9c0e19ce098b74ed0b5d75a12d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214355"
---
# <a name="compiler-warning-level-4-c4463"></a>编译器警告（等级4） C4463

> 超出将*值*分配给只包含*low_value*的值的位域*high_value*

分配的*值*不在位域可以包含的值范围内。 带符号位域类型对符号使用高位位，因此，如果*n*为位域大小，则已签名位域的范围为-2<sup>n-1</sup>到 2<sup>n-1</sup>-1，而无符号位域的范围介于0到 2<sup>n</sup>-1 之间。

## <a name="example"></a>示例

此示例将生成 C4463，因为它尝试将值3分配给类型为2的位域 **`int`** ，其范围介于-2 到1之间。

若要解决此问题，可以将分配的值更改为允许范围内的某个值。 如果位域用于保存范围为0到3之间的无符号值，则可以将声明类型更改为 **`unsigned`** 。 如果字段旨在保存范围为-4 到3之间的值，则可以将位域大小更改为3。

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
