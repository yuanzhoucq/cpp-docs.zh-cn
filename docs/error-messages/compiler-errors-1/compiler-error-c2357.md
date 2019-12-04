---
title: 编译器错误 C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: ce1926468bac7e44485be5c0a0944fdf12dce3d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759914"
---
# <a name="compiler-error-c2357"></a>编译器错误 C2357

"identifier"：必须是 "type" 类型的函数

你的代码声明了一个 `atexit` 函数的版本，该版本与编译器内部声明的版本不匹配。 按如下所示声明 `atexit`：

```
int __cdecl atexit(void (__cdecl *)());
```

有关详细信息，请参阅[init_seg](../../preprocessor/init-seg.md)。

下面的示例生成 C2357：

```cpp
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```
