---
title: "字节索引 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 594acadeedad06e9720180c38bd0bcd657391879
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="byte-indices"></a>字节索引
使用以下提示：  
  
-   使用转换为字符串的字节索引显示了类似于指针操作所带来的问题。 请考虑此扫描反斜杠字符的字符串的示例：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     这可能索引结尾字节，而非前导字节，并因此它可能不指向`character`。  
  
-   使用[_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)函数若要解决上述问题：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     它正确地索引前导字节，因此到`character`。 `_mbclen`函数将确定字符 （1 或 2 字节） 的大小。  
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [字符串中的最后一个字符](../text/last-character-in-a-string.md)