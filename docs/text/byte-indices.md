---
title: 字节索引 |Microsoft 文档
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 509e66c7ea458519eaa9dc4f52c8a6b65c789d0f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863795"
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