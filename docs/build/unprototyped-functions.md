---
title: "非原型函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dbc9324753f6ec2c9a332af00a00dd85116e1943
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="unprototyped-functions"></a>非原型函数
对于不是完全原型的函数，调用方将整数值将作为传递整数和浮点值为双精度数字。 仅对于浮点值，整数寄存器和浮点寄存器将包含的 float 值在被调用方期望整数寄存器中的值的情况下。  
  
```  
func1();  
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7  
   func1(2, 1.0, 7);  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [调用约定](../build/calling-convention.md)