---
title: 编译器错误 C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: 3b688012009a87c1e3d0db05e47133893daeaf34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300448"
---
# <a name="compiler-error-c3398"></a>编译器错误 C3398

“operator”：无法从“function_signature”转换为“function_pointer”。 源表达式必须是函数符号

当使用 [/clr](../../cpp/clrcall.md) 进行编译时，如果未指定 **__clrcall**调用约定，编译器将为每个函数生成两个入口点（地址）：一个本机入口点和一个托管入口点。

默认情况下，编译器返回本机入口点，但有些情况需要托管入口点（例如将地址分配给 `__clrcall` 函数指针时）。 为了使编译器能够在分配中可靠地选择托管入口点，右侧必须为函数符号。