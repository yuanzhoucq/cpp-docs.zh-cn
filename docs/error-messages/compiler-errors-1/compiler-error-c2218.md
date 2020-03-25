---
title: 编译器错误 C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: db14c37992fc1e2dd409c653d622d3419fcae4f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206643"
---
# <a name="compiler-error-c2218"></a>编译器错误 C2218

“__vectorcall”不能和“/arch:IA32”一起使用

`__vectorcall` 调用约定仅受到包括流式处理 SIMD 扩展 2 (SSE2) 和更高版本的 x86 和 x64 处理器上的本机代码的支持。 有关详细信息，请参阅[__vectorcall](../../cpp/vectorcall.md)。

若要修复此错误，请将编译器选项更改为目标 SSE2、AVX 或 AVX2 指令集的。 有关详细信息，请参阅 [/arch (x86)](../../build/reference/arch-x86.md)。
