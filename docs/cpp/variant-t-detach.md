---
title: "_variant_t::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::Detach"
  - "_variant_t.Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach 方法"
  - "VARIANT 对象"
  - "VARIANT 对象, detatch"
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# _variant_t::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 从该 `_variant_t` 对象中分离封装的 **VARIANT** 对象。  
  
## 语法  
  
```  
  
VARIANT Detach( );  
  
```  
  
## 返回值  
 封装的 **VARIANT**。  
  
## 备注  
 提取和返回封装的 **VARIANT**，然后清除此 `_variant_t` 对象而不销毁它。  此成员函数从封装中移除 **VARIANT**，并将此 `_variant_t` 对象的 **VARTYPE** 设置为 `VT_EMPTY`。  由您通过调用 [VariantClear](http://msdn.microsoft.com/zh-cn/28741d81-8404-4f85-95d3-5c209ec13835) 函数来释放返回的 **VARIANT**。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_variant\_t 类](../cpp/variant-t-class.md)