---
title: "字符比较 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 0b9098dc20c33cccfd64631e7732be0128cb5bb0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="character-comparison"></a>字符比较
使用以下提示：  
  
-   比较 ASCII 字符与一个已知的前导字节可正常工作：  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   比较两个未知的字符需要使用其中一个 Mbstring.h 中定义的宏：  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     这可确保双字节字符的两个字节会比较相等性。  
  
## <a name="see-also"></a>另请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [缓冲区溢出](../text/buffer-overflow.md)