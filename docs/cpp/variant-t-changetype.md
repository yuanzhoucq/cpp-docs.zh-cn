---
title: "_variant_t::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::ChangeType"
  - "_variant_t.ChangeType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ChangeType 方法"
  - "VARIANT 对象"
  - "VARIANT 对象, ChangeType"
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::ChangeType
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将 `_variant_t` 对象的类型更改为指示的 **VARTYPE**。  
  
## 语法  
  
```  
  
      void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### 参数  
 `vartype`  
 此 `_variant_t` 对象的 **VARTYPE**。  
  
 `pSrc`  
 指向要转换的 `_variant_t` 对象的指针。  如果此值为 **NULL**，转换将就地执行。  
  
## 备注  
 此成员函数将 `_variant_t` 对象转换为指示的 **VARTYPE**。  如果 `pSrc` 为 **NULL**，转换将就地执行，否则，将从 `pSrc` 复制此 `_variant_t` 对象，然后进行转换。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_variant\_t 类](../cpp/variant-t-class.md)