---
title: 编译器错误 C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 823b28deae3e3cfc18cdad8d37007bf8e8cff494
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221050"
---
# <a name="compiler-error-c3389"></a>编译器错误 C3389

> __declspec （*关键字*）不能与/clr： pure 或/clr： safe 一起使用

## <a name="remarks"></a>备注

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

使用的[__declspec](../../cpp/declspec.md)修饰符隐含每个进程状态。  [/clr： pure](../../build/reference/clr-common-language-runtime-compilation.md)表示每个[appdomain](../../cpp/appdomain.md)状态。  因此，不允许在声明变量时使用 `keyword` **`__declspec`** 修饰符并使用 **/clr： pure**进行编译。

## <a name="example"></a>示例

下面的示例生成 C3389：

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
