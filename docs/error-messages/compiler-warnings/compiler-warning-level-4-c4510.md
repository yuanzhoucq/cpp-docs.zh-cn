---
title: 编译器警告 （等级 C4510 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4510
dev_langs:
- C++
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2aaf7286c2e900629a18d7df5824ef4b7af1f5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048963"
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