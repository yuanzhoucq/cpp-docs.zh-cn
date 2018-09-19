---
title: noinline |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noinline_cpp
dev_langs:
- C++
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7a2831251d00f0dc24b1cfab7beeecaff100962
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092276"
---
# <a name="noinline"></a>noinline

## <a name="microsoft-specific"></a>Microsoft 专用

**__declspec （noinline)** 告诉编译器永远不内联某个特定成员函数 （在类中的函数）。

如果某个函数很小，并且对代码性能的影响不大，则不值得内联它。 即，如果函数很小并且不太可能经常调用（如处理错误条件的函数）。

请记住，如果标记的函数**noinline**，调用函数将为较小，因此，本身编译器内联的候选项。

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

