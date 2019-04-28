---
title: 编译器错误 C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: cc6c3a3a29665ccf65b77a3d9866986cb0a46b9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353185"
---
# <a name="compiler-error-c2555"></a>编译器错误 C2555

class1::function1： 重写虚函数返回类型有差异，不是从 class2::function2 协变

虚函数和派生的重写函数具有相同的参数列表，但不同的返回类型。 在派生类中的重写函数不能从基类仅由其返回类型中的虚拟函数。

若要解决此错误，将返回值转换后调用的虚拟函数。

如果您使用 /clr 进行编译，也可能会看到此错误。   例如，视觉对象C++等效于以下C#声明：

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

下面的示例生成 C2555:

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