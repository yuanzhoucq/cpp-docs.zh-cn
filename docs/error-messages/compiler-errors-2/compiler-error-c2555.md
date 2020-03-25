---
title: 编译器错误 C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ebf3e4a3aff48311edd5fb95b01a7b2d23990231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202419"
---
# <a name="compiler-error-c2555"></a>编译器错误 C2555

"class1：： function1"：重写虚函数返回类型不同，并且不是 "class2：： function2" 的协变

虚函数和派生的重写函数具有相同的参数列表，但不同的返回类型。 派生类中的重写函数不能与基类中的虚函数在其返回类型上有所不同。

若要解决此错误，请在调用虚函数之后强制转换返回值。

如果用/clr 进行编译，还可能会看到此错误。   例如，与以下C++ C#声明等效的视觉对象：

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

是

```
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
