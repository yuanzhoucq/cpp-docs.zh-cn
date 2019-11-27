---
title: 编译器警告（等级 3）C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: fd144847ce6c4f8697cd866d304c23cb9b2be408
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188874"
---
# <a name="compiler-warning-level-3-c4570"></a>编译器警告（等级 3）C4570

"type"：没有显式声明为抽象的，但具有抽象函数

包含[抽象](../../extensions/abstract-cpp-component-extensions.md)函数的类型本身应该标记为抽象。

## <a name="example"></a>示例

下面的示例生成 C4570。

```cpp
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```