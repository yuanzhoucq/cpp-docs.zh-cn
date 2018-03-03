---
title: "针对旧代码 （Visual c + +） 的浮点支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 130b6efb1c05775cd7859144d91a30051fb4ca53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="floating-point-support-for-older-code-visual-c"></a>针对旧代码的浮点支持 (Visual C++)
跨上下文切换保留 MMX 和浮点堆栈寄存器 (MM0-MM7/ST0-ST7)。  没有这些寄存器显式调用约定。  使用这些寄存器严禁内核模式代码中。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)