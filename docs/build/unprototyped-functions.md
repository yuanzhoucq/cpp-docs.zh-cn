---
title: 非原型函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df159942832479807b2dfe2679e709292ff3f44b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380467"
---
# <a name="unprototyped-functions"></a>非原型函数
对于不是完全原型的函数，调用方将整数值将作为传递整数和浮点值为双精度数字。 仅对于浮点值，整数寄存器和浮点寄存器将包含的 float 值在被调用方期望整数寄存器中的值的情况下。  
  
```  
func1();  
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7  
   func1(2, 1.0, 7);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)