---
title: "CDynamicAccessor::GetColumnName | Microsoft Docs"
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
  - "ATL::CDynamicAccessor::GetColumnName"
  - "GetColumnName"
  - "ATL.CDynamicAccessor.GetColumnName"
  - "CDynamicAccessor::GetColumnName"
  - "CDynamicAccessor.GetColumnName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnName 方法"
ms.assetid: 96a7452a-1f5b-41e9-ab37-88dac026f961
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetColumnName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索指定区域性的名称。  
  
## 语法  
  
```  
  
      LPOLESTR GetColumnName(   
   DBORDINAL nColumn    
) const throw( );  
```  
  
#### 参数  
 `nColumn`  
 \[in\] 列号。  列数以 1 开始。  若有的话，值 0 是指书签列。  
  
## 返回值  
 指定列的名称。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)