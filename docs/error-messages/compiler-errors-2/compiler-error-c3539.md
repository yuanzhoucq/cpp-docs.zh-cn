---
title: 编译器错误 C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: be1051859ebbcbdc22a9b71f8c5adba2e75c4e92
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025171"
---
# <a name="compiler-error-c3539"></a>编译器错误 C3539

type： 模板参数不能为包含 auto 的类型

指定的模板自变量类型不能包含的使用情况`auto`关键字。

### <a name="to-correct-this-error"></a>更正此错误

1. 未指定模板参数与`auto`关键字。

## <a name="example"></a>示例

下面的示例生成 C3539。

```
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