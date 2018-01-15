---
title: "调用方被调用方保存的寄存器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 61e8d57c177ded8102f257cf84adedc0de0e312a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="callercallee-saved-registers"></a>由调用方或被调用方保存的寄存器
函数调用上销毁 RAX、 RCX、 RDX、 R8、 R9、 R10、 R11 被视为易失性，必须考虑的寄存器 (除非否则为安全-丰厚通过分析例如全程序优化)。  
  
 寄存器 RBX、 RBP、 RDI、 RSI、 RSP、 R12、 R13、 R14 和 R15 被视为非易失性和必须保存并还原函数使用它们。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)