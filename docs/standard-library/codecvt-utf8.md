---
title: "codecvt_utf8 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.codecvt_utf8"
  - "std::codecvt_utf8"
  - "codecvt_utf8"
  - "codecvt/std::codecvt_utf8"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_utf8 类"
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_utf8
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示在 UCS\-2 转换为编码的宽字符或 UCS\-4 之间的 [区域设置](../standard-library/locale-class.md) \(IDE\) 和为 UTF\-8 编码的字符限制。  
  
## 语法  
  
```  
template<  
    class Elem,  
    unsigned long Maxcode = 0x10ffff,  
    codecvt_mode Mode = (codecvt_mode)0  
>  
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`Elem`|宽元素类型。|  
|`Maxcode`|的最大字符数方面的区域设置。|  
|`Mode`|区域设置方面的配置信息。|  
  
## 备注  
 字节流可写入二进制文件或文本文件。  
  
## 要求  
 **页眉：** \<codecvt\>  
  
 **命名空间:**  std