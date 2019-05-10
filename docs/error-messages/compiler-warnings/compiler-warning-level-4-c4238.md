---
title: 编译器警告（等级 4）C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: c5ffa07b06f010d10edc14aa7576bb614aa9dd04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401028"
---
# <a name="compiler-warning-level-4-c4238"></a>编译器警告（等级 4）C4238

使用了非标准扩展： 类 rvalue 用作了 lvalue

与视觉对象的以前版本的兼容性C++，Microsoft 扩展 (**/Ze**)，可以使用类类型，如在上下文中的右值的隐式或显式采用其地址。 在某些情况下，如以下示例中，这可能很危险。

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