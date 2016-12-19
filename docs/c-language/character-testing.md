---
title: "字符测试 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 字符测试
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.3.1** 由 `isalnum`、`isalpha`、`iscntrl`、`islower`、`isprint` 和 `isupper` 函数测试的字符集。  
  
 以下列表描述了由 Microsoft C 编译器实现的这些函数。  
  
|功能|测试|  
|--------|--------|  
|`isalnum`|字符 0 – 9、A–Z、a–z ASCII 48–57、65–90、97–122|  
|`isalpha`|字符 A–Z、a–z ASCII 65–90、97–122|  
|`iscntrl`|ASCII 0 –31、127|  
|`islower`|字符 a\-z ASCII 97\-122|  
|`isprint`|字符 A–Z、a–z、0 – 9、标点、空格 ASCII 32–126|  
|`isupper`|字符 A–Z ASCII 65–90|  
  
## 请参阅  
 [库函数](../c-language/library-functions.md)