---
title: 编译器警告（等级 3）C4281
ms.date: 11/04/2016
f1_keywords:
- C4281
helpviewer_keywords:
- C4281
ms.assetid: a9771261-5725-4fc6-87b6-16cf92113a25
ms.openlocfilehash: 69496438d8078ee0298bdb447fcf4f7df1b75464
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402146"
---
# <a name="compiler-warning-level-3-c4281"></a>编译器警告（等级 3）C4281

通过类型 type 发生 operator-> 的递归

你的代码允许**运算符->** 调用自身。

下面的示例生成 C4281:

```
// C4281.cpp
// compile with: /W3 /WX
struct A;
struct B;
struct C;

struct A
{
   int z;
   B& operator->();
};

struct B
{
   C& operator->();
};

struct C
{
   A& operator->();
};

void f(A p)
{
   int i = p->z; // C4281
}
```