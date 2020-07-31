---
title: 编译器错误 C2555
description: Visual Studio c + + 编译器错误 C2555 参考。
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ecac92bc663a6344e9ddafe13c194a92ab944c51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207792"
---
# <a name="compiler-error-c2555"></a>编译器错误 C2555

> "*class1*：：*function1*"：重写虚函数返回类型不同，并且不是 "*class2*：：*function2*" 的协变

虚函数和派生的重写函数具有相同的参数列表，但不同的返回类型。

## <a name="remarks"></a>备注

在 c + + 中，派生类中的重写函数不能仅在基类中的虚函数的返回类型上有所不同。

对于某些返回类型，此规则有一个例外。 当派生类重写公共基类时，它可能会返回指向派生类的指针或引用，而不是基类指针或引用。 这些返回类型称为*协变*，因为它们的类型不同。 此规则异常不允许协变引用指针或指针到指针类型。

解决错误的一种方法是返回与基类相同的类型。 然后，在调用虚函数后，强制转换返回值。 另外，还需要更改参数列表，使派生类成员函数成为重载，而不是重写。

## <a name="examples"></a>示例

如果用编译，则可能会出现此错误 **`/clr`** 。 例如，c + + 等效于以下 c # 声明：

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

下面的示例生成 C2555：

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```

若要修复此问题，请将的返回类型更改 `Y::func` 为 **`void`** 。
