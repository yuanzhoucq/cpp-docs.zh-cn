---
title: 编译器错误 C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 6a9568f3c3be88438eae1f28e12dc780301ead0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402575"
---
# <a name="compiler-error-c3389"></a>编译器错误 C3389

> __declspec (*关键字*) 不能用于 /clr: pure 或 /clr: safe

## <a name="remarks"></a>备注

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

一个[__declspec](../../cpp/declspec.md)修饰符意味着每个进程状态。  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)意味着每个[appdomain](../../cpp/appdomain.md)状态。  因此，声明的变量`keyword` **__declspec**修饰符，并使用编译 **/clr: pure**不允许。

## <a name="example"></a>示例

下面的示例生成 C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```