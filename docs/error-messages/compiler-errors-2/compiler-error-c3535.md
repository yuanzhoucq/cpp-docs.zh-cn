---
title: 编译器错误 C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: e80fa62db9795838980c63e113300a554afabef3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040856"
---
# <a name="compiler-error-c3535"></a>编译器错误 C3535

无法推导出类型 type1 从 type2

通过声明的变量的类型`auto`不能从初始化表达式的类型推导关键字。 如果初始化表达式的计算结果，例如，发生此错误`void`，这不是一种。

### <a name="to-correct-this-error"></a>更正此错误

1. 确保初始化表达式的类型不是`void`。

1. 请确保声明不是指向基本类型的指针。 有关详细信息，请参阅[基本类型](../../cpp/fundamental-types-cpp.md)。

1. 请确保如果该声明是指针指向的类型，初始化表达式是指针类型。

## <a name="example"></a>示例

下面的示例会产生 C3535，因为初始化表达式的计算结果为`void`。

```
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

下面的示例会产生 C3535，因为该语句声明变量`x`为指向推导出的类型，但初始值设定项的类型的表达式是两倍。 因此，编译器无法推导出变量的类型。

```
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>示例

下面的示例会产生 C3535，因为变量`p`声明指针指向推导出的类型，但初始化表达式不是指针类型。

```
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)<br/>
[基本类型](../../cpp/fundamental-types-cpp.md)