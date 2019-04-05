---
title: 编译器错误 C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a16c5bd46d806d09861d5734b637c2c9d9b2f9d0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031890"
---
# <a name="compiler-error-c3536"></a>编译器错误 C3536

symbol： 初始化之前不能使用

它在初始化之前，不能使用指定的符号。 在实践中，这意味着无法使用变量来初始化自身。

### <a name="to-correct-this-error"></a>更正此错误

1. 未初始化变量对其自身。

## <a name="example"></a>示例

下面的示例生成 C3536，因为每个变量初始化与其自身。

```
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)