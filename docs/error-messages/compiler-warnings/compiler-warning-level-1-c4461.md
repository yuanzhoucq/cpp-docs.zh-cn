---
title: 编译器警告（第 1 级）C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 195e5532b6555210077e43ad3086ee3106f3e757
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966011"
---
# <a name="compiler-warning-level-1-c4461"></a>编译器警告（第 1 级）C4461

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