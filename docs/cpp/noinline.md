---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: bedf17072c06ec893b9cbd83b46403dcd3bc1560
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186680"
---
# <a name="noinline"></a>noinline

**Microsoft 专用**

**`__declspec(noinline)`** 指示编译器从不内联特定成员函数（类中的函数）。

如果某个函数很小，并且对代码性能的影响不大，则不值得内联它。 即，如果函数很小并且不太可能经常调用（如处理错误条件的函数）。

请记住，如果将某个函数标记为 **`noinline`** ，则调用函数将较小，因而是编译器内联的候选项。

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[inline、__inline、\__forceinline](inline-functions-cpp.md)
