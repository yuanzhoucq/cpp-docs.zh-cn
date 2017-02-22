---
title: "CBulkRowset 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CBulkRowset"
  - "ATL.CBulkRowset"
  - "ATL::CBulkRowset<TAccessor>"
  - "CBulkRowset"
  - "ATL.CBulkRowset<TAccessor>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBulkRowset 类"
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CBulkRowset 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取和操作数据批量行处理通过检索具有唯一调用的多个行句柄旁边。  
  
## 语法  
  
```  
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
#### 参数  
 `TAccessor`  
 访问器类。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/cbulkrowset-addrefrows.md)|递增引用计数。|  
|[CBulkRowset](../../data/oledb/cbulkrowset-cbulkrowset.md)|构造函数。|  
|[MoveFirst](../../data/oledb/cbulkrowset-movefirst.md)|检索第一行数据，如果需要，执行新的批量获取。|  
|[MoveLast](../../data/oledb/cbulkrowset-movelast.md)|移动到最后一行。|  
|[MoveNext](../../data/oledb/cbulkrowset-movenext.md)|数据检索下一行。|  
|[MovePrev](../../data/oledb/cbulkrowset-moveprev.md)|移到上一行。|  
|[MoveToBookmark](../../data/oledb/cbulkrowset-movetobookmark.md)|提取书签标记的行。在该书签的指定偏移量。|  
|[MoveToRatio](../../data/oledb/cbulkrowset-movetoratio.md)|获取从行中集的一部分的位置开始行。|  
|[ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)|调整当前行 \(**m\_nCurrentRow**\) 到零和释放所有行。|  
|[SetRows](../../data/oledb/cbulkrowset-setrows.md)|设置行数。调用要检索的句柄。|  
  
## 示例  
 下面的示例演示 `CBulkRowset` 类的使用。  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/CPP/cbulkrowset-class_1.cpp)]  
  
## 要求  
 **页眉：**atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)