---
title: "CArrayRowset 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CArrayRowset<TAccessor>"
  - "ATL.CArrayRowset"
  - "CArrayRowset"
  - "ATL::CArrayRowset"
  - "ATL::CArrayRowset<TAccessor>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArrayRowset 类"
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CArrayRowset 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以使用数组语法，访问行集合的元素。  
  
## 语法  
  
```  
template < class TAccessor >  
class CArrayRowset :   
   public CVirtualBuffer <TAccessor>,   
   protected CBulkRowset <TAccessor>  
```  
  
#### 参数  
 `TAccessor`  
 访问器类类型需要行集合。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CArrayRowset](../../data/oledb/carrayrowset-carrayrowset.md)|构造函数。|  
|[快照](../../data/oledb/carrayrowset-snapshot.md)|读取整个行集到内存中。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符 &#91;&#93;](../../data/oledb/carrayrowset-operator.md)|访问行集合的元素。|  
  
### 数据成员  
  
|||  
|-|-|  
|[CArrayRowset::m\_nRowsRead](../../data/oledb/carrayrowset-m-nrowsread.md)|行数已经被读取。|  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CRowset 类](../../data/oledb/crowset-class.md)