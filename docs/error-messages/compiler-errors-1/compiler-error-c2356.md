---
title: 编译器错误 C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: 0166cce6011017b8a18821666083f7c47f58b7a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508099"
---
# <a name="compiler-error-c2356"></a>编译器错误 C2356

初始化段在翻译单元期间不能更改

可能的原因：

- `#pragma init_seg` 前面有段初始化代码

- `#pragma init_seg` 前面是另一个 `#pragma init_seg`

若要解决，请移动到模块的开头段初始化代码。 如果必须初始化多个区域，将它们移到单独的模块。

下面的示例生成 C2356:

```
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```