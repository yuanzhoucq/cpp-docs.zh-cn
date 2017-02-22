---
title: "_ATL_BASE_MODULE70 Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::_ATL_BASE_MODULE70"
  - "ATL._ATL_BASE_MODULE70"
  - "_ATL_BASE_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_BASE_MODULE70 structure"
  - "ATL_BASE_MODULE70 structure"
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# _ATL_BASE_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用ATL的任何项目。  
  
## 语法  
  
```  
  
      struct _ATL_BASE_MODULE70{  
   UINT cbSize;  
   HINSTANCE m_hInst;  
   HINSTANCE m_hInstResource;  
   bool m_bNT5orWin98;  
   DWORD dwAtlBuildVer;  
   GUID* pguidVer;  
   CRITICAL_SECTION m_csResource;  
   CSimpleArray<HINSTANCE> m_rgResourceInstance;  
};  
```  
  
## 成员  
 `cbSize`  
 结构的大小，用于控制。  
  
 `m_hInst`  
 此模块的 **hInstance** \(exe或dll）。  
  
 `m_hInstResource`  
 默认实例资源句柄。  
  
 **m\_bNT5orWin98**  
 操作系统版本信息。  在内部使用由ATL。  
  
 **dwAtlBuildVer**  
 存储ATL的版本。  当前0x0700。  
  
 **pguidVer**  
 ATL的内部GUID。  
  
 **m\_csResource**  
 用于同步对 **m\_rgResourceInstance** 数组的访问。  在内部使用由ATL。  
  
 **m\_rgResourceInstance**  
 用于的数组搜索在ATL了解的所有资源实例的资源。  在内部使用由ATL。  
  
## 备注  
 [\_ATL\_BASE\_MODULE](../Topic/_ATL_BASE_MODULE.md) 定义为 `_ATL_BASE_MODULE70`typedef。  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [结构](../../atl/reference/atl-structures.md)