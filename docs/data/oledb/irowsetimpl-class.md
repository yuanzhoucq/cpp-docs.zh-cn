---
title: "IRowsetImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetImpl 类"
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IRowsetImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 `IRowset` 接口的实现。  
  
## 语法  
  
```  
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*   
   >  
>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
#### 参数  
 `T`  
 类是从`IRowsetImpl` 中派生的。  
  
 `RowsetInterface`  
 类从 `IRowsetImpl` 派生。  
  
 `RowClass`  
 为 **HROW** 的存储单元。  
  
 `MapClass`  
 提供程序\) 占用的任何行句柄的单元格。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)|向现有的行句柄添加引用数。|  
|[CreateRow](../../data/oledb/irowsetimpl-createrow.md)|调用 [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) 分配新的 **HROW**。  未直接由用户调用。|  
|[GetData](../../data/oledb/irowsetimpl-getdata.md)|从行的行集合副本中检索数据。|  
|[GetDBStatus](../../data/oledb/irowsetimpl-getdbstatus.md)|返回中指定的字段的状态。|  
|[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)|按顺序获取行，同时记住以前的位置。|  
|[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)|构造函数。  未直接由用户调用。|  
|[RefRows](../../data/oledb/irowsetimpl-refrows.md)|调用 [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) 和 [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)。  未直接由用户调用。|  
|[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)|释放行。|  
|[RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)|重新定位一获取位置到其初始位置；即，在某位置集中首次创建。|  
|[SetDBStatus](../../data/oledb/irowsetimpl-setdbstatus.md)|设置指定的状态字段的标记。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)|指示提供程序是否支持向后获取。|  
|[m\_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)|指示提供程序是否可以排列其反转光标移动。|  
|[m\_bReset](../../data/oledb/irowsetimpl-m-breset.md)|指示提供程序是否重置其光标位置。  当向后滚动或向后搜索提取在 [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)时，这具有特殊含义。|  
|[m\_iRowset](../../data/oledb/irowsetimpl-m-irowset.md)|对行集合的索引，表示光标。|  
|[m\_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)|行处理列表。|  
  
## 备注  
 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) 是基础行集合接口。  
  
## 要求  
 **头文件:** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)