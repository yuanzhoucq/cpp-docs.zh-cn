---
title: 编译器警告（等级 4）C4623
ms.date: 11/04/2016
f1_keywords:
- C4623
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
ms.openlocfilehash: d1b659a6aed593a2e3f01ac1b82e60878cb09c80
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585427"
---
# <a name="compiler-warning-level-4-c4623"></a>编译器警告（等级 4）C4623

“`derived class`”：默认构造函数已被隐式定义为已删除，因为基类默认构造函数不可访问或已被删除

基类中的构造函数不可访问，且没有为派生类生成构造函数。 任何在堆栈上创建此类型对象的尝试都将导致编译器错误。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

## <a name="example"></a>示例

下面的示例生成 C4623。

```
// C4623.cpp
// compile with: /W4
#pragma warning(default : 4623)
class B {
   B();
};

class C {
public:
   C();
};

class D : public B {};   // C4623 - to fix, make B's constructor public
class E : public C {};   // OK - class C constructor is public

int main() {
   // D d;  will cause an error
}
```