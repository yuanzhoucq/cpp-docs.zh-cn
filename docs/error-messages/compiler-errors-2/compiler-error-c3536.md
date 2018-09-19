---
title: 编译器错误 C3536 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7585a75ebe9733c228756e92d8e5ae57699aca27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088574"
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