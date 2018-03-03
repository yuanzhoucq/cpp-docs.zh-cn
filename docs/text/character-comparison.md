---
title: "字符比较 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28c2cd3a2e868a595d73d06b5cae8e71ec8cc313
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [缓冲区溢出](../text/buffer-overflow.md)