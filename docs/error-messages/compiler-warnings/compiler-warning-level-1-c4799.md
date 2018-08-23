---
title: 编译器警告 （等级 1） C4799 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f888d6a941ad487ce122e46c43582e1c96525c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282933"
---
# <a name="compiler-warning-level-1-c4799"></a>编译器警告（等级 1）C4799  
  
> 在函数末尾没有 EMM*函数*  
  
该函数具有至少一个 MMX 指令，但不具有`EMMS`指令。 当使用多媒体指令时，`EMMS`指令或`_mm_empty`内部函数还应该使用清除 MMX 代码的结尾处的多媒体标记字。  
  
当使用 ivec.h，，该值指示代码不正确使用执行 EMMS 指令在返回之前，可能受到 C4799。 这是这些标头的 false 警告。 你可以打开这些通过定义 _SILENCE_IVEC_C4799 ivec.h 中。 但是，请注意，这还将给出此类型的正确警告来保留编译器。  
  
有关相关信息，请参阅[Intel 的 MMX 指令集](../../assembler/inline/intel-s-mmx-instruction-set.md)。