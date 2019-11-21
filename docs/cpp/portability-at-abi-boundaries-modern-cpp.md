---
title: ABI 边界处的可移植性（现代 C++）
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: 379b402354c6f08e003dffb38366d1dce20e0987
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246393"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>ABI 边界处的可移植性（现代 C++）

Use sufficiently portable types and conventions at binary interface boundaries. “可迁移类型”是 C 内置类型或包含 C 内置类型的结构。 类类型只能在调用方和被调用方接受布局、调用约定等时使用。这仅在两者是使用相同的编译器和编译器设置编译时可能。

## <a name="how-to-flatten-a-class-for-c-portability"></a>如何为了 C 可移植性平展类

When callers may be compiled with another compiler/language, then “flatten” to an **extern "C"** API with a specific calling convention:

```cpp
// class widget {
//   widget();
//   ~widget();
//   double method( int, gadget& );
// };
extern "C" {        // functions using explicit "this"
   struct widget;   // opaque type (forward declaration only)
   widget* STDCALL widget_create();      // constructor creates new "this"
   void STDCALL widget_destroy(widget*); // destructor consumes "this"
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"
}
```

## <a name="see-also"></a>请参阅

[Welcome back to C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
