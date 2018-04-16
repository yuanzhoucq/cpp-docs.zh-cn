---
title: "递增和递减指针 |Microsoft 文档"
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
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9eccf65f091c8c5c273f6a65cb7e81b0d386afa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="incrementing-and-decrementing-pointers"></a>递增和递减指针
使用以下提示：  
  
-   指向前导字节而非尾字节。 它是有一个指针指向结尾字节通常不安全的。 它是通常更安全扫描字符串转发而不是按相反的顺序。  
  
-   有指针递增/递减函数和宏可用，将指针移到整个字符：  
  
    ```  
    sz1++;  
    ```  
  
     会成为：  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     `_mbsinc`和`_mbsdec`函数正确递增和递减中`character`单位，而不考虑字符大小。  
  
-   对于递减，你需要指向的字符串，如下所示的开头的指针：  
  
    ```  
    sz2--;  
    ```  
  
     会成为：  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     或者，你头的指针可以指向有效的字符在字符串中，以便：  
  
    ```  
    sz2Head < sz2  
    ```  
  
     你必须有一个指针指向一个已知的有效前导字节。  
  
-   你可能想要维护一个指向前一个字符为更快地调用`_mbsdec`。  
  
## <a name="see-also"></a>请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [字节索引](../text/byte-indices.md)