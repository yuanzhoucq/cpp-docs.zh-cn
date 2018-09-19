---
title: 编译器错误 C3190 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3190
dev_langs:
- C++
helpviewer_keywords:
- C3190
ms.assetid: 7c701afa-85a7-4f7a-8881-0662436ac244
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bed7f3b29ffeab2ae26516c51cf6ce09acab3e54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088522"
---
# <a name="compiler-error-c3190"></a>编译器错误 C3190

实例，并且它提供的模板参数不是 type 的任何成员函数的显式实例化

编译器检测到尝试使显式函数实例化;但是，提供的类型参数不匹配任何可能的函数。

下面的示例生成 C3190:

```
// C3190.cpp
// compile with: /LD
template<class T>
struct A {
   A(int x = 0) {
   }
   A(int x, int y) {
   }
};

template A<float>::A();   // C3190
// try the following line instead
// template A<int>::A(int);

struct Y {
   template<class T> void f(T);
};

template<class T> void Y::f(T) { }

template void Y::f(int,int);   // C3190

template<class OT> class X {
   template<class T> void f2(T,OT);
};

template<class OT> template<class T> void X<OT>::f2(T,OT) {}

template void X<float>::f2<int>(int,char);   // C3190
// try one of the following lines instead
// template void X<char>::f2(int, char);
// template void X<char>::f2<int>(int,char);
// template void X<char>::f2<>(int,char);
```