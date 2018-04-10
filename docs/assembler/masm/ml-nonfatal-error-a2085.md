---
title: ML 非致命错误 A2085 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29d0d58e5cd65c16c848b3cc05e10b9f57488639
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2085"></a>ML 非致命错误 A2085
**指令或不接受当前 CPU 模式中的注册**  
  
 尝试使用指令、 注册或对当前处理器模式下无效的关键字。  
  
 例如，32 位寄存器要求[.386](../../assembler/masm/dot-386.md)或更高版本。 控制寄存器如 CR0 需要特权模式下[.386P](../../assembler/masm/dot-386p.md)或更高版本。 此错误也会生成有关**NEAR32**， **FAR32**，和**平面**需要的关键字。**386**或更高版本。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)