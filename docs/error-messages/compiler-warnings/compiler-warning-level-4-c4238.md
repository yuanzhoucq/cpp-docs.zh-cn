---
title: 编译器警告（等级 4）C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: 982457ded987f6aee4f2891bbb7d9103b830cc99
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541789"
---
# <a name="compiler-warning-level-4-c4238"></a>编译器警告（等级 4）C4238

使用了非标准扩展：类 rvalue 用作了 lvalue

为了与早期版本的 Visual C++兼容，Microsoft 扩展（ **/ze**）允许在隐式或显式采用其地址的上下文中将类类型用作右值。 在某些情况下（例如以下示例），这可能很危险。

## <a name="example"></a>示例

```cpp
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

此用法会导致 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下出现错误。