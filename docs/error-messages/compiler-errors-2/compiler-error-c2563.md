---
title: 编译器错误 C2563
ms.date: 11/04/2016
f1_keywords:
- C2563
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
ms.openlocfilehash: 04a10c82fa6aa39bcf1098d6d4aabfc2f769e7c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539303"
---
# <a name="compiler-error-c2563"></a>编译器错误 C2563

中的形参列表不匹配

函数 （或指向函数的指针） 的形参列表不匹配的另一个函数 （或指向成员函数）。 因此，不能进行函数或指针的赋值。

下面的示例生成 C2563:

```
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```