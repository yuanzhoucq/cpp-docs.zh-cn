---
title: "codecvt_utf16 | Microsoft Docs"
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
  - "codecvt/std::codecvt_utf16"
  - "std::codecvt_utf16"
  - "std.codecvt_utf16"
  - "codecvt_utf16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_utf16 类"
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_utf16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 [区域设置](../standard-library/locale-class.md) 宽字符为 ucs\-2 或 ucs\-4 编码和字节流编码为 UTF 16LE 或 UTF 16BE 之间进行转换的方面。  
  
## 语法  
  
```  
template<  
    class Elem,  
    unsigned long Maxcode = 0x10ffff,  
    codecvt_mode Mode = (codecvt_mode)0  
>  
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Elem`|宽字符元素类型。|  
|`Maxcode`|最大的区域设置 facet 的字符数。|  
|`Mode`|区域设置 facet 的配置信息。|  
  
## 备注  
 此模板类与之间进行转换宽字符编码为 ucs\-2 或 UCS 4 字节流编码为 UTF 16LE，如果 `Mode & little_endian`, ，或以其他方式 UTF 16BE。  
  
 字节流应写入二进制文件;如果写入到一个文本文件，它可以已损坏。  
  
## 要求  
 **标头︰** \< codecvt \>  
  
 **命名空间:** std