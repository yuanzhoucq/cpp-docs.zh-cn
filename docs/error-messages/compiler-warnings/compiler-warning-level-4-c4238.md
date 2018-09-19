---
title: 编译器警告 （等级 C4238 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4d5f358d08f81e6b8097140ad47d54f4b3b3fed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057023"
---
# <a name="compiler-warning-level-4-c4238"></a>编译器警告（等级 4）C4238

使用了非标准扩展： 类 rvalue 用作了 lvalue

与以前版本的 Visual c + +，Microsoft 扩展的兼容性 (**/Ze**)，可以使用类类型，如在上下文中的右值的隐式或显式采用其地址。 在某些情况下，如以下示例中，这可能很危险。

## <a name="example"></a>示例

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

这种用法会导致 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。