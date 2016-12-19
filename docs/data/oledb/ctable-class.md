---
title: "CTable 类 | Microsoft Docs"
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
  - "ATL::CTable"
  - "ATL.CTable"
  - "CTable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTable 类"
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTable 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供方法直接访问一简单行集合 \(即无参数\)。  
  
## 语法  
  
```  
template <   
   class TAccessor = CNoAccessor,    
   template <typename T> class TRowset = CRowset    
>  
class CTable :    
   public CAccessorRowset <   
      TAccessor,    
      TRowset    
   >  
```  
  
#### 参数  
 `TAccessor`  
 访问器类。  
  
 `TRowset`  
 行集合类。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[打开](../../data/oledb/ctable-open.md)|打开表。|  
  
## 备注  
 参见 [CCommand](../../data/oledb/ccommand-class.md) 有关如何执行该命令的信息来访问行集合。  
  
## 要求  
 **页眉：**atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)