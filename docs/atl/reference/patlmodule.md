---
title: "_pAtlModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATLBASE/_pAtlModule"
  - "_pAtlModule"
  - "ATL::_pAtlModule"
  - "ATL._pAtlModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_pAtlModule variable"
  - "pAtlModule variable"
ms.assetid: 0ecde3a9-3f4d-4c7b-bb54-713ce05c4777
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# _pAtlModule
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存储指针的全局变量为当前模块。  
  
## 语法  
  
```  
__declspec(selectany) CAtlModule * _pAtlModule  
```  
  
## 备注  
 此全局变量的方法来提供的功能\(现在已过时\)选件类 [CComModule](../../atl/reference/ccommodule-class.md) 在Visual C\+\+ 6.0提供。  
  
## 示例  
 [!code-cpp[NVC_ATL_Windowing#97](../../atl/codesnippet/CPP/patlmodule_1.cpp)]  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [Global Variables](../../atl/reference/atl-global-variables.md)