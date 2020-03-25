---
title: 编译器警告（等级 1）C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: fa736e8dbab775fcd6cdffc467aee1312004fa60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162148"
---
# <a name="compiler-warning-level-1-c4584"></a>编译器警告（等级 1）C4584

"class1"：基类 "class2" 已是 "a.class3" 的基类

你定义的类继承自两个类，其中一个类继承自另一个类。 例如：

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

在这种情况下，将在类 C 上发出警告，因为该类继承自类 A 和类 B，后者也从类 A 继承。此警告可作为提醒，你必须完全限定这些基类的成员使用情况，否则将生成编译器错误，因为你引用了哪个类成员。
