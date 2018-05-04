---
title: 调用方被调用方保存的寄存器 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f65e88c8609d6a2097e9e54c3f52cbd27dce36d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="callercallee-saved-registers"></a>由调用方或被调用方保存的寄存器
函数调用上销毁 RAX、 RCX、 RDX、 R8、 R9、 R10、 R11 被视为易失性，必须考虑的寄存器 (除非否则为安全-丰厚通过分析例如全程序优化)。  
  
 寄存器 RBX、 RBP、 RDI、 RSI、 RSP、 R12、 R13、 R14 和 R15 被视为非易失性和必须保存并还原函数使用它们。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)