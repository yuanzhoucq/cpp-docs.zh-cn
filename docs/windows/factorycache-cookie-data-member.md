---
title: "FactoryCache::cookie 数据成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::FactoryCache::cookie"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cookie 数据成员"
ms.assetid: b1bc79af-a896-4e3b-8afa-64733022eddf
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# FactoryCache::cookie 数据成员
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] 基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
union {   
   WINRT_REGISTRATION_COOKIE winrt;  
   DWORD com;   
} cookie;  
```  
  
## 备注  
 标识包含已注册 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 类或 COM 对象的值和用于注销后对象。  
  
## 要求  
 **标头:** module.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [FactoryCache 结构](../windows/factorycache-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)