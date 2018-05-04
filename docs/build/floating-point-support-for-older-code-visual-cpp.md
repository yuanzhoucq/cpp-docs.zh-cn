---
title: 针对旧代码 （Visual c + +） 的浮点支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd7cbf955fbf795d06d9cd2448d0736dc435f3b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="floating-point-support-for-older-code-visual-c"></a>针对旧代码的浮点支持 (Visual C++)
跨上下文切换保留 MMX 和浮点堆栈寄存器 (MM0-MM7/ST0-ST7)。  没有这些寄存器显式调用约定。  使用这些寄存器严禁内核模式代码中。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)