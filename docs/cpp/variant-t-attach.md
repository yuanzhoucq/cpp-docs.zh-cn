---
title: "_variant_t::Attach | Microsoft Docs"
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
  - "_variant_t::Attach"
  - "_variant_t.Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
  - "VARIANT 对象"
  - "VARIANT 对象, attach"
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将 **VARIANT** 对象附加到 `_variant_t` 对象中。  
  
## 语法  
  
```  
  
      void Attach(  
   VARIANT& varSrc   
);  
```  
  
#### 参数  
 *varSrc*  
 要附加到此 `_variant_t` 对象中的 **VARIANT** 对象。  
  
## 备注  
 通过封装取得 **VARIANT** 的所有权。  此成员函数将释放所有现有封装的 **VARIANT**，然后复制提供的 **VARIANT**，并将其 **VARTYPE** 设置为 `VT_EMPTY` 以确保其资源只能由 `_variant_t` 析构函数释放。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_variant\_t 类](../cpp/variant-t-class.md)