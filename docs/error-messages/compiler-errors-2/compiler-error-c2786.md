---
title: 编译器错误 C2786
ms.date: 11/04/2016
f1_keywords:
- C2786
helpviewer_keywords:
- C2786
ms.assetid: 6676d8c0-86dd-4a39-bdda-b75a35f4d137
ms.openlocfilehash: b03155ad1a209ae59327dd31d432f5623f380ac9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511418"
---
# <a name="compiler-error-c2786"></a>编译器错误 C2786

type: __uuidof 的操作数无效

[__Uuidof](../../cpp/uuidof-operator.md)运算符采用与附加的 GUID 或用户定义类型的对象的用户定义的类型。  可能的原因：

1. 参数不是用户定义类型。

1. `__uuidof` 无法从参数中提取 GUID。

下面的示例生成 C2786:

```
// C2786.cpp
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};

int main() {
   __uuidof(int);   // C2786
   __uuidof(int *);   // C2786
   __uuidof(A **);   // C2786

   // no error
   __uuidof(A);
   __uuidof(A *);
   __uuidof(A &);
   __uuidof(A[]);

   int i;
   int *pi;
   A **ppa;

   __uuidof(i);      // C2786
   __uuidof(pi);     // C2786
   __uuidof(ppa);    // C2786
}
```