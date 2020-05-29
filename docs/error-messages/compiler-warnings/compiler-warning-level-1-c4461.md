---
title: 编译器警告（等级 1）C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 819c433a58c6b0c3a3958b483dc1d1a08bde58c1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186746"
---
# <a name="compiler-warning-level-1-c4461"></a>编译器警告（等级 1）C4461

"type"：此类具有终结器 "finalizer"，但没有析构函数 "dtor"

类型中是否存在终结器意味着要删除的资源。 除非在对象超出范围后，公共语言运行时才会从类型的析构函数中显式调用终结器，否则，公共语言运行时将确定何时运行终结器。

如果在类型中定义析构函数并从析构函数中显式调用终结器，则可以确定运行终结器。

有关详细信息，请参阅[析构函数和终结](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)器。

## <a name="example"></a>示例

下面的示例生成 C4461。

```cpp
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
