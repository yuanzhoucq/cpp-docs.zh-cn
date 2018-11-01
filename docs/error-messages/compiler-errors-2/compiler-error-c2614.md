---
title: 编译器错误 C2614
ms.date: 11/04/2016
f1_keywords:
- C2614
helpviewer_keywords:
- C2614
ms.assetid: a550c1d5-8718-4e17-a888-b2619e00fe11
ms.openlocfilehash: 71f0fe3211ce253bcf30347658692651e84ab608
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463591"
---
# <a name="compiler-error-c2614"></a>编译器错误 C2614

class1： 成员初始化非法: class2 不是基或成员

只有成员或基类，这些类可以出现在类或结构的初始化列表。

## <a name="example"></a>示例

下面的示例生成 C2614。

```
// C2614.cpp
// compile with: /c
struct A {
   int i;
   A( int ia ) : B( i ) {};   // C2614 B is not a member of A
};

struct A2 {
   int B;
   int i;
   A2( int ia ) : B( i ) {};   // OK
};
```