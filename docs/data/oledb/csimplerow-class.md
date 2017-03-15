---
title: "CSimpleRow 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSimpleRow"
  - "ATL::CSimpleRow"
  - "ATL.CSimpleRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleRow 类"
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CSimpleRow 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对于行句柄提供默认实现，使用 [IRowsetImpl](../../data/oledb/irowsetimpl-class.md)类。  
  
## 语法  
  
```  
class CSimpleRow  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AddRefRow](../../data/oledb/csimplerow-addrefrow.md)|向现有的行句柄添加引用数。|  
|[比较](../../data/oledb/csimplerow-compare.md)|比较两个行，以了解它们是否引用了同一个行实例。|  
|[CSimpleRow](../../data/oledb/csimplerow-csimplerow.md)|构造函数。|  
|[ReleaseRow](../../data/oledb/csimplerow-releaserow.md)|释放行。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_dwRef](../../data/oledb/csimplerow-m-dwref.md)|向现有的行句柄添加引用数。|  
|[m\_iRowset](../../data/oledb/csimplerow-m-irowset.md)|对行集合的索引，表示光标。|  
  
## 备注  
 行处理逻辑上是结果行的唯一标记。  `IRowsetImpl` 会在 [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)请求的每个行的新 `CSimpleRow`。  因为它是默认模板参数设置为 `IRowsetImpl`，则可以用您自己的实现来替换`CSimpleRow` 行句柄。  为替换此类的唯一要求是将类替换提供接受 **LONG**类型的单个参数的构造函数。  
  
## 要求  
 **头文件:** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)