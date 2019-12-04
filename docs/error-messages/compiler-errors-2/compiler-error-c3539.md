---
title: 编译器错误 C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 85381b237480b86b59c33f02601a1b9dc644a5a4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761525"
---
# <a name="compiler-error-c3539"></a>编译器错误 C3539

"type"：模板参数不能是包含 "auto" 的类型

指定的模板参数类型不能包含 `auto` 关键字的用法。

### <a name="to-correct-this-error"></a>更正此错误

1. 不要指定带有 `auto` 关键字的模板参数。

## <a name="example"></a>示例

下面的示例生成 C3539。

```cpp
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>另请参阅

[auto 关键字](../../cpp/auto-keyword.md)
