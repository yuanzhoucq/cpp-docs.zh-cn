---
title: 编译器错误 C3398 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b870479977bfb49ff39d5a15fe19fc700ed66b8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255825"
---
# <a name="compiler-error-c3398"></a>编译器错误 C3398
“operator”：无法从“function_signature”转换为“function_pointer”。 源表达式必须是函数符号  
  
 当使用 [/clr](../../cpp/clrcall.md) 进行编译时，如果未指定 **__clrcall**调用约定，编译器将为每个函数生成两个入口点（地址）：一个本机入口点和一个托管入口点。  
  
 默认情况下，编译器返回本机入口点，但有些情况需要托管入口点（例如将地址分配给 `__clrcall` 函数指针时）。 为了使编译器能够在分配中可靠地选择托管入口点，右侧必须为函数符号。