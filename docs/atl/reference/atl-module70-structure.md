---
title: "_ATL_MODULE70 Structure | Microsoft Docs"
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
  - "_ATL_MODULE70"
  - "ATL::_ATL_MODULE70"
  - "ATL._ATL_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_MODULE70 structure"
  - "ATL_MODULE70 structure"
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _ATL_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含每个ATL模块使用的数据。  
  
## 语法  
  
```  
  
      struct _ATL_MODULE70{  
   UINT cbSize;  
   LONG m_nLockCnt;  
   _ATL_TERMFUNC_ELEM* m_pTermFuncs;  
   CComCriticalSection m_csStaticDataInitAndTypeInfo;  
};  
```  
  
## 成员  
 `cbSize`  
 结构的大小，用于控制。  
  
 `m_nLockCnt`  
 引用计数确定模块时间应减少运行。  
  
 **m\_pTermFuncs**  
 跟踪注册调用函数，当ATL关闭。  
  
 **m\_csStaticDataInitAndTypeInfo**  
 用于协调对内部数据的访问在多线程的情况。  
  
## 备注  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md) 定义为 `_ATL_MODULE70`typedef。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [结构](../../atl/reference/atl-structures.md)