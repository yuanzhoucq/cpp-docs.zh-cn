---
title: "_ATL_COM_MODULE70 Structure | Microsoft Docs"
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
  - "ATL::_ATL_COM_MODULE70"
  - "ATL._ATL_COM_MODULE70"
  - "_ATL_COM_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_COM_MODULE70 structure"
  - "ATL_COM_MODULE70 structure"
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
caps.latest.revision: 15
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _ATL_COM_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用由COM相关的代码在ATL。  
  
## 语法  
  
```  
  
      struct _ATL_COM_MODULE70{  
   UINT cbSize;  
   HINSTANCE m_hInstTypeLib;  
   _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;  
   _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;  
   CRITICAL_SECTION m_csObjMap;  
};  
```  
  
## 成员  
 `cbSize`  
 结构的大小，用于控制。  
  
 `m_hInstTypeLib`  
 对类型库的实例处理此模块的。  
  
 **m\_ppAutoObjMapFirst**  
 一个映射项的开头的此模块的数组元素的地址。  
  
 **m\_ppAutoObjMapLast**  
 一个映射项的结束此模块的数组元素的地址。  
  
 `m_csObjMap`  
 对对象映射项的访问的临界区。  在内部使用由ATL。  
  
## 备注  
 [\_ATL\_COM\_MODULE](../Topic/_ATL_COM_MODULE.md) 定义为 `_ATL_COM_MODULE70`typedef。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [结构](../../atl/reference/atl-structures.md)