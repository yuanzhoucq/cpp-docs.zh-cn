---
title: ABI 边界的可移植性
description: 在C++二进制接口边界将接口平展为 C 调用约定。
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: b3b2b217739ff5900c8ef0329ff3e8909a3fe036
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303321"
---
# <a name="portability-at-abi-boundaries"></a>ABI 边界的可移植性

在二进制接口边界使用足够的可移植类型和约定。 "可移植类型" 是 C 内置类型或仅包含 C 内置类型的结构。 类类型只能在调用方和被调用方同意布局、调用约定等时使用。仅当两者都用相同的编译器和编译器设置进行编译时，才可能出现这种情况。

## <a name="how-to-flatten-a-class-for-c-portability"></a>如何为了 C 可移植性平展类

如果调用方可以使用另一种编译器/语言编译，则使用特定的调用约定 "平展" 到**extern "C"** API：

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

## <a name="see-also"></a>另请参阅

[欢迎返回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
