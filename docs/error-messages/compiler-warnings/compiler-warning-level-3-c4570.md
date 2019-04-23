---
title: 编译器警告（等级 3）C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: 386d7c210c77469d67a75d66f7d8ae35c105b3b0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777908"
---
# <a name="compiler-warning-level-3-c4570"></a>编译器警告（等级 3）C4570

type： 没有显式声明为抽象的但具有抽象函数

包含的类型[抽象](../../extensions/abstract-cpp-component-extensions.md)函数应本身标记为抽象。

## <a name="example"></a>示例

下面的示例生成 C4570。

```
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```