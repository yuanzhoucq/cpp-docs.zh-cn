---
title: 编译器警告（等级 1）C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: 475451b47d461e7ea1428eb715a876fb023694d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152211"
---
# <a name="compiler-warning-level-1-c4799"></a>编译器警告（等级 1）C4799

> 在函数末尾没有 EMMS '*函数*

该函数具有至少一个 MMX 指令，但不具有`EMMS`指令。 当使用多媒体指令时，`EMMS`指令或`_mm_empty`内部函数应还可用于清除多媒体标记单词末尾的 MMX 代码。

当使用 ivec.h，代码不正确使用，该值指示执行在返回之前的 EMMS 指令时，可能会收到 C4799。 这是这些标头的假警告。 您可能会禁用这些选项通过定义 _SILENCE_IVEC_C4799 ivec.h 中。 但是，请注意，这还将给出此类型的正确警告来保留编译器。

有关相关信息，请参阅[Intel 的 MMX 指令集](../../assembler/inline/intel-s-mmx-instruction-set.md)。