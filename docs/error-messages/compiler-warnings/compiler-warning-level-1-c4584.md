---
title: 编译器警告（等级 1）C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 3c60575e766ea3490a40711fe26c3e402c41fbdd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397245"
---
# <a name="compiler-warning-level-1-c4584"></a>编译器警告（等级 1）C4584

class1： 基类 class2 已经是 class3 移的基类

您定义的类继承自两个类，其中一个继承自其他。 例如：

```
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

在这种情况下，将发出警告类 C 从类 A 和 B，还继承自类 a。 类继承因此此警告可提醒您必须完全限定的成员从这些基类的类的用法，或由于语意不明确引用哪个类成员将产生编译器错误。