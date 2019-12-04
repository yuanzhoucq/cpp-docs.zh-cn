---
title: 编译器错误 C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: e306c5a8f9175bc3c7902b20263aa2e451944182
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759927"
---
# <a name="compiler-error-c2356"></a>编译器错误 C2356

初始化段在翻译单元期间不能更改

可能的原因：

- `#pragma init_seg`，前面是段初始化代码

- `#pragma init_seg` 前面有另一个 `#pragma init_seg`

若要解决此问题，请将段初始化代码移到模块的开头。 如果必须初始化多个区域，请将它们移到单独的模块中。

下面的示例生成 C2356：

```cpp
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```
