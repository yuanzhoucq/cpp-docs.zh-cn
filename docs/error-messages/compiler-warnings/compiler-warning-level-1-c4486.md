---
title: 编译器警告（等级 1）C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 402d5eefde6c2dfd5693e53c27edb00d1ac2e56c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404060"
---
# <a name="compiler-warning-level-1-c4486"></a>编译器警告（等级 1）C4486

function: ref 类或值类的私有虚方法应标记为 sealed

由于无法访问或重写的托管的类或结构的私有虚拟成员函数，它应标记[密封](../../extensions/sealed-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C4486。

```
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

## <a name="example"></a>示例

下面的示例显示了专用的密封虚函数的可能用途之一。

```
// C4486_b.cpp
// compile with: /clr /c
ref class B {};

ref class D : B {};

interface class I {
   B^ mf();
};

ref class E : I {
private:
   virtual B^ g() sealed = I::mf {
      return gcnew B;
   }

public:
   virtual D^ mf() {
      return gcnew D;
   }
};
```