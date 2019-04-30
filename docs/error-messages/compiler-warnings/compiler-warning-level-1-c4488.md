---
title: 编译器警告（等级 1）C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: c816c1b3f5481ccff19fd2a2377c5fc98f950fee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404073"
---
# <a name="compiler-warning-level-1-c4488"></a>编译器警告（等级 1）C4488

function： 需要 keyword 关键字实现接口方法 interface_method

类必须实现它直接从中继承的接口的所有成员。 实现的成员必须具有公共可访问性，并且必须标记为虚拟。

## <a name="example"></a>示例

如果不是公共实现的成员，则可能发生 C4488。 下面的示例生成 C4488。

```
// C4488.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

// implemented member not public
ref class B : MyI { virtual void f1() {} };  // C4488

// OK
ref class C : MyI {
public:
   virtual void f1() {}
};
```

## <a name="example"></a>示例

如果实现的成员未标记为虚拟，可能发生 C4488。 下面的示例生成 C4488。

```
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```