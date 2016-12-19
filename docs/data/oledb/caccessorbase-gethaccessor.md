---
title: "CAccessorBase::GetHAccessor | Microsoft Docs"
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
  - "GetHAccessor"
  - "CAccessorBase::GetHAccessor"
  - "CAccessorBase.GetHAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetHAccessor 方法"
ms.assetid: 1bb98762-0752-4aae-a0b6-ba96bec03621
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorBase::GetHAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索指定访问器的访问器处理。  
  
## 语法  
  
```  
  
      HACCESSOR GetHAccessor(  
   ULONG nAccessor   
) const;  
```  
  
#### 参数  
 `nAccessor`  
 \[in\] 访问器的零数字的偏移量。  
  
## 返回值  
 访问器处理。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CAccessorBase 类](../../data/oledb/caccessorbase-class.md)