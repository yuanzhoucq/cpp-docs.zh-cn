---
title: 编译器错误 C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 813da5a2fd79c191df731937e58100d749f8690c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223403"
---
# <a name="compiler-error-c3539"></a>编译器错误 C3539

"type"：模板参数不能是包含 "auto" 的类型

指定的模板参数类型不能包含关键字的用法 **`auto`** 。

### <a name="to-correct-this-error"></a>更正此错误

1. 不要将模板参数指定为 **`auto`** 关键字。

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

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)
