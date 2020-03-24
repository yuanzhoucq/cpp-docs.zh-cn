---
title: 编译器警告（等级 1）C4624
ms.date: 11/04/2016
f1_keywords:
- C4624
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
ms.openlocfilehash: 5d6e89efb042b8f757feec3911b160961e51f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199688"
---
# <a name="compiler-warning-level-1-c4624"></a>编译器警告（等级 1）C4624

“derived class”：析构函数隐式定义为已删除，因为基类析构函数不可访问或已删除

基类中的析构函数不可访问或已删除，因而没有为派生类生成析构函数。 任何在堆栈上创建此类型对象的尝试都将导致编译器错误。

下面的示例生成 C4624，并演示如何修复此错误：

```cpp
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```
