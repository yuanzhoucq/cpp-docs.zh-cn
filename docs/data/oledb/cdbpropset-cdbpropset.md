---
title: "CDBPropSet::CDBPropSet | Microsoft Docs"
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
  - "CDBPropSet.CDBPropSet"
  - "CDBPropSet::CDBPropSet"
  - "ATL::CDBPropSet::CDBPropSet"
  - "ATL.CDBPropSet.CDBPropSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropSet 类, 构造函数"
ms.assetid: 02ae5d9e-c067-47ca-8111-a03e86b5626b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropSet::CDBPropSet
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

构造函数。  初始化 **rgProperties**、**cProperties**和 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构的 **guidPropertySet** 字段。  
  
## 语法  
  
```  
  
      CDBPropSet(  
   const GUID& guid   
);  
CDBPropSet(   
   const CDBPropSet& propset    
);  
CDBPropSet( );  
```  
  
#### 参数  
 `guid`  
 \[in\] 用于的 GUID 来初始化 **guidPropertySet** 字段。  
  
 *propset*  
 \[in\] 复制构造的另一个 `CDBPropSet` 对象。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDBPropSet 类](../../data/oledb/cdbpropset-class.md)   
 [CDBPropSet::SetGUID](../../data/oledb/cdbpropset-setguid.md)   
 [DBPROP Structure](https://msdn.microsoft.com/en-us/library/ms717970.aspx)