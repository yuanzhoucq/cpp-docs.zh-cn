---
title: 字节索引 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5beb69ef7d9d3356eddef40c6bce6483079d934a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590795"
---
# <a name="byte-indices"></a>字节索引
使用以下提示：  
  
-   使用转换为字符串的字节索引带来了问题类似于所引起的指针操作。 请考虑此扫描字符串以反斜杠字符的示例：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     这可能会编制索引结尾字节，前导字节，并因此它可能不指向`character`。  
  
-   使用[_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)函数来解决上述问题：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     它正确地索引前导字节，因此到`character`。 `_mbclen`函数确定字符 （1 或 2 个字节） 的大小。  
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [字符串中的最后一个字符](../text/last-character-in-a-string.md)