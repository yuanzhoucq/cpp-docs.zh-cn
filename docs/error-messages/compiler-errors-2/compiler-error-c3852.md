---
title: 编译器错误 C3852
ms.date: 11/04/2016
f1_keywords:
- C3852
helpviewer_keywords:
- C3852
ms.assetid: 194e5c5e-0dfb-414e-86db-791c11eb610c
ms.openlocfilehash: f264333d802967d0350caa8ab4ba4925ffe019af
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754870"
---
# <a name="compiler-error-c3852"></a>编译器错误 C3852

"member" 类型的类型为 "type"：聚合初始化未能初始化此成员

尝试将默认初始化作为聚合初始化的一部分分配给无法在聚合初始化中接收默认初始化的数据成员。

以下示例生成 C3852：

```cpp
// C3852.cpp
struct S
{
   short s;
};

struct S1
{
   int i;
   const S s;
};

struct S2
{
   int i;
   char & rc;
};

int main()
{
   S1 s1 = { 1 };   // C3852 const member
   // try the following line instead
   // S1 s1 = { 1, 2 };

   S2 s2 = { 2 };   // C3852 reference member
   // try the following line instead
   // char c = 'a';
   S2 s2 = { 2, c };
}
```
