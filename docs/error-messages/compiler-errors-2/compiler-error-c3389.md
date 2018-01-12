---
title: "编译器错误 C3389 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3389
dev_langs: C++
helpviewer_keywords: C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd88753553d2bad1cb9253cfe709e7627c4b01ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3389"></a>编译器错误 C3389
__declspec(keyword) 不能用于 /clr: pure 或 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 A [__declspec](../../cpp/declspec.md)使用修饰符意味着每个进程状态。  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)意味着每个[appdomain](../../cpp/appdomain.md)状态。  因此，声明的变量`keyword` **__declspec**修饰符，并使用编译**/clr: pure**不允许。  
  
 下面的示例生成 C3389:  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```