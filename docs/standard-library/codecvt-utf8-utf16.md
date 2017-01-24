---
title: "codecvt_utf8_utf16 | Microsoft Docs"
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
  - "codecvt_utf8_utf16"
  - "codecvt/std::cvt_utf8_utf16"
  - "std::codecvt_utf8_utf16"
  - "std.codecvt_utf8_utf16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_utf8_utf16 类"
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_utf8_utf16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示在转换为 UTF\-16 编码的宽字符和 UTF\-8 的编码限制为单词之间的 [区域设置](../standard-library/locale-class.md) 方面。  
  
## 语法  
  
```  
template<  
    class Elem,  
    unsigned long Maxcode = 0x10ffff,  
    codecvt_mode Mode = (codecvt_mode)0  
>  
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>  
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