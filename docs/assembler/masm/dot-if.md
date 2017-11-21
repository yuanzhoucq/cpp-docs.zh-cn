---
title: ".如果 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .IF
dev_langs: C++
helpviewer_keywords: .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2416b73fa42f9cac629644ea624a9545f3988dc3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="if"></a>.IF
生成测试的代码`condition1`(例如，AX > 7) 并执行*语句*如果该条件为 true。  
  
## <a name="syntax"></a>语法  
  
```  
  
   .IF condition1   
statements  
[[.ELSEIF condition2   
   statements]]  
[[.ELSE  
   statements]]  
.ENDIF  
```  
  
## <a name="remarks"></a>备注  
 如果[。其他](../../assembler/masm/dot-else.md)如果原始的情况是 false，则执行其语句如下所示。 请注意，在运行时计算条件。  
  
## <a name="see-also"></a>另请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)