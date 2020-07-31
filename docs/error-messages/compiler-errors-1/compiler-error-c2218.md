---
title: 编译器错误 C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: 97f3290ef8bcb6a91442effdbf84261c03545ce2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209521"
---
# <a name="compiler-error-c2218"></a>编译器错误 C2218

> “__vectorcall”不能和“/arch:IA32”一起使用

**`__vectorcall`** 仅在包含流式处理 Simd 扩展2（SSE2）和更高版本的 x86 和 x64 处理器上的本机代码中支持调用约定。 有关详细信息，请参阅 [`__vectorcall`](../../cpp/vectorcall.md)。

若要修复此错误，请将编译器选项更改为目标 SSE2、AVX 或 AVX2 指令集的。 有关详细信息，请参阅[ `/arch` （x86）](../../build/reference/arch-x86.md)。
