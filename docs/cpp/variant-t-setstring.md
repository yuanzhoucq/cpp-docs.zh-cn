---
title: "_variant_t::SetString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::SetString"
  - "_variant_t.SetString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetString 方法"
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _variant_t::SetString
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将字符串分配给此 `_variant_t` 对象。  
  
## 语法  
  
```  
  
      void SetString(  
   const char* pSrc   
);  
```  
  
#### 参数  
 `pSrc`  
 指向字符串的指针。  
  
## 备注  
 将 ANSI 字符串转换为 Unicode `BSTR` 字符串并将其分配给此 `_variant_t` 对象。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_variant\_t 类](../cpp/variant-t-class.md)