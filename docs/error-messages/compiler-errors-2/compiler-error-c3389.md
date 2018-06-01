---
title: 编译器错误 C3389 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3389
dev_langs:
- C++
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b540f87458c75ddf7d57626b6251248652b96213
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704296"
---
# <a name="compiler-error-c3389"></a>编译器错误 C3389

> __declspec (*关键字*) 不能与 /clr: pure 或 /clr: safe

## <a name="remarks"></a>备注

**/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。

A [__declspec](../../cpp/declspec.md)使用修饰符意味着每个进程状态。  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)意味着每个[appdomain](../../cpp/appdomain.md)状态。  因此，声明的变量`keyword` **__declspec**修饰符，并使用编译 **/clr: pure**不允许。

## <a name="example"></a>示例

下面的示例生成 C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```