---
title: "CAccessorRowset 类 | Microsoft Docs"
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
  - "CAccessorRowset"
  - "ATL.CAccessorRowset"
  - "ATL::CAccessorRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessorRowset 类"
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorRowset 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装一行集及其关联一个访问器类。  
  
## 语法  
  
```  
template <   
   class TAccessor = CNoAccessor,    
   template <typename T> class TRowset = CRowset    
>  
class CAccessorRowset :   
   public TAccessor,    
   public TRowset<TAccessor>  
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
|[Bind](../../data/oledb/caccessorrowset-bind.md)|创建绑定 \(使用 **bBind** 时指定为错误。\)。[CCommand::Open](../../data/oledb/ccommand-open.md)|  
|[CAccessorRowset](../../data/oledb/caccessorrowset-caccessorrowset.md)|构造函数。|  
|[关闭](../../data/oledb/caccessorrowset-close.md)|关闭行集合和所有访问器。|  
|[FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md)|版本需要释放在当前记录的所有列。|  
|[GetColumnInfo](../../data/oledb/caccessorrowset-getcolumninfo.md)|实现 [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)。|  
  
## 备注  
 `TAccessor` 类管理访问器。  类 *TRowset* 管理行集。  
  
## 要求  
 **页眉：**atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)