---
title: "CDBPropIDSet::SetGUID | Microsoft Docs"
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
  - "CDBPropIDSet.SetGUID"
  - "ATL::CDBPropIDSet::SetGUID"
  - "SetGUID"
  - "ATL.CDBPropIDSet.SetGUID"
  - "CDBPropIDSet::SetGUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetGUID 方法"
ms.assetid: 8dd0f3bf-1490-4d53-9063-322b8d821bbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropIDSet::SetGUID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置 **DBPROPIDSET** 结构字段的 GUID。  
  
## 语法  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### 参数  
 `guid`  
 \[in\] 使用 GUID 中设置 [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) 结构 **guidPropertySet** 字段。  
  
## 备注  
 此字段可以通过 [构造函数](../../data/oledb/cdbpropidset-cdbpropidset.md) 设置。  调用此函数。无论您是为此类使用默认构造函数。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDBPropIDSet 类](../../data/oledb/cdbpropidset-class.md)