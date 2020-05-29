---
title: 编译器警告（等级 1）C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 0ba3a8f9e60ab0b84266dd25b6b9ccfe10f75561
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186707"
---
# <a name="compiler-warning-level-1-c4486"></a>编译器警告（等级 1）C4486

"function"： ref 类或值类的私有虚方法应该标记为 "sealed"

由于无法访问或重写托管类或结构的私有虚拟成员函数，因此应将其标记为[密封](../../extensions/sealed-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C4486。

```cpp
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

## <a name="example"></a>示例

下面的示例演示了一个可能使用私有密封虚函数的情况。

```cpp
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
