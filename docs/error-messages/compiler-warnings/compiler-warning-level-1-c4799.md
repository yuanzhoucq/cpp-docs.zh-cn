---
title: 编译器警告（等级 1）C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: ec92da425718cd5ddc579d1d733a0bc4e56dc04a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175098"
---
# <a name="compiler-warning-level-1-c4799"></a>编译器警告（等级 1）C4799

> 函数 "*function*" 的末尾没有 emm

函数至少具有一个 MMX 指令，但没有 `EMMS` 的指令。 使用多媒体指令时，还应使用 `EMMS` 指令或 `_mm_empty` 内部函数来清除 MMX 代码末尾的多媒体标记字。

使用 ivec 时，可能会收到 C4799，指示在返回之前，代码不会正确地执行 EMM 指令。 对于这些标头，这是一个错误警告。 可以通过在 IVEC 中定义 _SILENCE_IVEC_C4799 来关闭这些。 但请注意，这也会使编译器无法提供此类型的正确警告。

有关相关信息，请参阅[Intel 的 MMX 指令集](../../assembler/inline/intel-s-mmx-instruction-set.md)。
