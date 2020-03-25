---
title: 编译器警告 C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: c168c91f8259b744ed10dd72701d34fd60b98681
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165153"
---
# <a name="compiler-warning-c4484"></a>编译器警告 C4484

"override_function"：匹配 ref 基类方法 "base_class_function"，但未标记为 "virtual"、"new" 或 "override";假定为 "new" （而不是 "virtual"）

使用 **/clr**进行编译时，编译器不会隐式重写基类函数，这意味着该函数将获取 vtable 中的新槽。 若要解决此问题，请显式指定函数是否为重写。

有关详细信息，请参阅：

- [/cgthreads（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../extensions/override-cpp-component-extensions.md)

- [新（vtable 中的新槽）](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 始终作为错误发出。 使用[警告](../../preprocessor/warning.md)杂注取消 C4484。

## <a name="example"></a>示例

下面的示例生成 C4484。

```cpp
// C4484.cpp
// compile with: /clr
ref struct A {
   virtual void Test() {}
};

ref struct B : A {
   void Test() {}   // C4484
};

// OK
ref struct C {
   virtual void Test() {}
   virtual void Test2() {}
};

ref struct D : C {
   virtual void Test() new {}
   virtual void Test2() override {}
};
```
