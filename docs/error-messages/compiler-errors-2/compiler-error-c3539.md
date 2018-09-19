---
title: 编译器错误 C3539 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3539
dev_langs:
- C++
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b2f78b69e00290dcc283e3fc340d25a4a071776
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091876"
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