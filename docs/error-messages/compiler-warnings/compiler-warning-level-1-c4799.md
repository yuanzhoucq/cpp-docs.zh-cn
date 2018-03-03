---
title: "编译器警告 （等级 1） C4799 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f41535c01d67e28baa2569ace2684865407a1d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4799"></a>编译器警告（等级 1）C4799  
  
> 在函数末尾没有 EMM*函数*  
  
该函数具有至少一个 MMX 指令，但不具有`EMMS`指令。 当使用多媒体指令时，`EMMS`指令或`_mm_empty`内部函数还应该使用清除 MMX 代码的结尾处的多媒体标记字。  
  
当使用 ivec.h，，该值指示代码不正确使用执行 EMMS 指令在返回之前，可能受到 C4799。 这是这些标头的 false 警告。 你可以打开这些通过定义 _SILENCE_IVEC_C4799 ivec.h 中。 但是，请注意，这还将给出此类型的正确警告来保留编译器。  
  
有关相关信息，请参阅[Intel 的 MMX 指令集](../../assembler/inline/intel-s-mmx-instruction-set.md)。