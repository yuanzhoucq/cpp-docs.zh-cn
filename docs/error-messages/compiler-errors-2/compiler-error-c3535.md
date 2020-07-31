---
title: 编译器错误 C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 60ffd5d8decd5c9065ca55cfed34383278359f3e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228786"
---
# <a name="compiler-error-c3535"></a>编译器错误 C3535

无法从 "type2" 推导 "type1" 的类型

**`auto`** 不能从初始化表达式的类型推导出由关键字声明的变量的类型。 例如，如果初始化表达式的计算结果为而 **`void`** 不是类型，则会发生此错误。

### <a name="to-correct-this-error"></a>更正此错误

1. 确保初始化表达式的类型不是 **`void`** 。

1. 确保声明不是指向基本类型的指针。 有关详细信息，请参阅[基本类型](../../cpp/fundamental-types-cpp.md)。

1. 请确保如果声明是指向类型的指针，则初始化表达式是指针类型。

## <a name="example"></a>示例

下面的示例生成 C3535，因为初始化表达式的计算结果为 **`void`** 。

```cpp
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>示例

下面的示例生成 C3535，因为该语句将变量声明 `x` 为指向推导出的类型的指针，而初始值设定项表达式的类型为 double。 因此，编译器无法推导出变量的类型。

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>示例

下面的示例生成 C3535，因为变量 `p` 声明指向推导出的类型的指针，但初始化表达式不是指针类型。

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)<br/>
[基本类型](../../cpp/fundamental-types-cpp.md)
