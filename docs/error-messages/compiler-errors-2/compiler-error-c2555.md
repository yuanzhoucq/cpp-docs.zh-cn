---
title: 编译器错误 C2555
description: 视觉工作室C++编译器错误 C2555 的参考。
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: fe0e6379e783387506e6098c9b14a047baa8e6c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374176"
---
# <a name="compiler-error-c2555"></a>编译器错误 C2555

> '*类1*：：*函数 1'：* 重写虚拟函数返回类型不同，并且不是从 '*类2*：：*函数2*'

虚拟函数和派生重写函数具有相同的参数列表，但返回类型不同。

## <a name="remarks"></a>备注

在C++中，派生类中重写函数不能仅因返回类型与基类中的虚拟函数不同而不同。

对于某些返回类型，此规则有一个例外。 当派生类重写公共基类时，它可以返回指向派生类的指针或引用，而不是基类指针或引用。 这些返回类型称为*协变量*，因为它们随类型而变化。 此规则异常不允许对指针或指针类型的协变量引用。

解决错误的一种方法是返回与基类相同的类型。 然后，在调用虚拟函数后强制转换返回值。 另一种是更改参数列表，使派生类成员函数成为重载函数，而不是重写。

## <a name="examples"></a>示例

如果使用 编译，则可能会看到此错误**`/clr`**。 例如，等效于以下 C# 声明C++：

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

以下示例生成 C2555：

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

要修复它，将 返回`Y::func`类型更改为`void`。
