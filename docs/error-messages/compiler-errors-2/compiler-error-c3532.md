---
title: 编译器错误 C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: 2ef5eb3c2bedd9defbd0b80e6d8c5c8912fcf16d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761928"
---
# <a name="compiler-error-c3532"></a>编译器错误 C3532

"type"： "auto" 的用法不正确

指定的类型不能用 `auto` 关键字进行声明。 例如，不能使用 `auto` 关键字声明数组或方法返回类型。

### <a name="to-correct-this-error"></a>更正此错误

1. 确保初始化表达式产生有效的类型。

1. 确保不声明数组或方法返回类型。

## <a name="example"></a>示例

下面的示例生成 C3532，因为 `auto` 关键字不能声明方法返回类型。

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>示例

下面的示例生成 C3532，因为 `auto` 关键字不能声明数组。

```cpp
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>另请参阅

[auto 关键字](../../cpp/auto-keyword.md)
