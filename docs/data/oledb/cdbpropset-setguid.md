---
title: "CDBPropSet::SetGUID | Microsoft Docs"
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
  - "ATL.CDBPropSet.SetGUID"
  - "CDBPropSet.SetGUID"
  - "ATL::CDBPropSet::SetGUID"
  - "SetGUID"
  - "CDBPropSet::SetGUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddProperty 方法"
  - "SetGUID 方法"
ms.assetid: a4cce036-cf1f-4897-9712-7b01eaf887ff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropSet::SetGUID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将 **DBPROPSET** 结构的 **guidPropertySet** 字段。  
  
## 语法  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### 参数  
 `guid`  
 \[in\] 使用 GUID 中设置 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构的 **guidPropertySet** 字段。  
  
## 备注  
 此字段可以通过 [构造函数](../../data/oledb/cdbpropset-cdbpropset.md) 设置。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDBPropSet 类](../../data/oledb/cdbpropset-class.md)