---
title: 编译器警告（等级 4）C4510
ms.date: 11/04/2016
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 80183e9f7ef17cbc37592f36eb8db1df2be94827
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539056"
---
# <a name="compiler-warning-level-4-c4510"></a>编译器警告（等级 4）C4510

class： 无法生成默认构造函数

没有用户定义的构造函数的创建和编译器无法生成指定的类的默认构造函数。 你将无法再创建此类型的对象。

有几种情况下，阻止编译器生成默认构造函数，包括：

- Const 数据成员。

- 为引用数据成员。

您需要创建用户定义的默认构造函数初始化这些成员的类。

下面的示例生成 C4510:

```
// C4510.cpp
// compile with: /W4
struct A {
   const int i;
   int &j;
   A& operator=( const A& ); // C4510 expected
   // uncomment the following line to resolve this C4510
   // A(int ii, int &jj) : i(ii), j(jj) {}
};   // C4510

int main() {
}
```