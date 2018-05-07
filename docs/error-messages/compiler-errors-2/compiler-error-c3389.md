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
ms.openlocfilehash: 6f0f60a1096c070d28be3b7af161bbb924fb20dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3389"></a>编译器错误 C3389
__declspec(keyword) 不能用于 /clr: pure 或 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 A [__declspec](../../cpp/declspec.md)使用修饰符意味着每个进程状态。  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)意味着每个[appdomain](../../cpp/appdomain.md)状态。  因此，声明的变量`keyword` **__declspec**修饰符，并使用编译 **/clr: pure**不允许。  
  
 下面的示例生成 C3389:  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```