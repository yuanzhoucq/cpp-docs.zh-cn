---
title: "ML 错误 A1011 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1011
dev_langs: C++
helpviewer_keywords: A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 470340e76897394e5b8ecb042ff97562b0c94c2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ml-fatal-error-a1011"></a>ML 错误 A1011
**指令必须在控制块**  
  
 汇编程序找到其中一个不期望值高级指令。 找到以下指令之一：  
  
-   [.其他](../../assembler/masm/dot-else.md)而无需[。如果](../../assembler/masm/dot-if.md)  
  
-   [.ENDIF](../../assembler/masm/dot-endif.md)而无需[。如果](../../assembler/masm/dot-if.md)  
  
-   [.ENDW](../../assembler/masm/dot-endw.md)而无需[。WHILE](../../assembler/masm/dot-while.md)  
  
-   [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)而无需[。重复](../../assembler/masm/dot-repeat.md)  
  
-   [.继续](../../assembler/masm/dot-continue.md)而无需[。虽然](../../assembler/masm/dot-while.md)或[。重复](../../assembler/masm/dot-repeat.md)  
  
-   [.中断](../../assembler/masm/dot-break.md)而无需[。虽然](../../assembler/masm/dot-while.md)或[。重复](../../assembler/masm/dot-repeat.md)  
  
-   [.其他](../../assembler/masm/dot-else.md)以下`.ELSE`  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)