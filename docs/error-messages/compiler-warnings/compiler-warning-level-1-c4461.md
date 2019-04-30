---
title: 编译器警告（第 1 级）C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 5cc9b08f0f25e9c92b4185f060ab123684c5d9e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408259"
---
# <a name="compiler-warning-level-1-c4461"></a>编译器警告（第 1 级）C4461

type： 此类具有终结器 finalizer，但没有析构函数 dtor

一种类型中的终结器存在表示要删除资源。 除非显式类型的析构函数从调用终结器，公共语言运行时确定在运行终结器，您的对象超出范围后的时间。

如果类型中定义析构函数并显式从析构函数调用的终结器，可以确定地运行您终结器。

有关详细信息，请参阅[析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>示例

下面的示例生成 C4461。

```
// C4461.cpp
// compile with: /W1 /clr /c
ref class A {
protected:
   !A() {}   // C4461
};

// OK
ref struct B {
   ~B() {
      B::!B();
   }

   !B() {}
};
```