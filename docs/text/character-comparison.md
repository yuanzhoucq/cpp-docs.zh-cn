---
title: 字符比较 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 246801abcb04cc8d9c2fd1a005183501bde240d1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612321"
---
# <a name="character-comparison"></a>字符比较
使用以下提示：  
  
-   比较已知的前导字节的 ASCII 字符正常工作：  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   比较两个未知的字符需要使用一个 Mbstring.h 中定义的宏：  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     这可确保这两个字节的双字节字符会比较相等性。  
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [缓冲区溢出](../text/buffer-overflow.md)