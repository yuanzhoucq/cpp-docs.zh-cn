---
title: "IRowsetUpdateImpl 类 | Microsoft Docs"
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
  - "IRowsetUpdateImpl"
  - "ATL.IRowsetUpdateImpl"
  - "ATL::IRowsetUpdateImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetUpdateImpl 类"
  - "提供程序, 可更新的"
  - "可更新提供程序, 延迟的更新"
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) 接口的 OLE DB 模板实现。  
  
## 语法  
  
```  
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  
class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass  
>  
```  
  
#### 参数  
 `T`  
 从 `IRowsetUpdateImpl`派生的类。  
  
 `Storage`  
 用户记录。  
  
 `UpdateArray`  
 包含更新的数组行集缓存数据。  
  
 `RowClass`  
 **HROW**的单元格。  
  
 `MapClass`  
 提供程序\) 占用的任何行句柄的单元格。  
  
## 成员  
  
### 接口方法 \(用于 IRowsetChange\)  
  
|||  
|-|-|  
|[SetData](../../data/oledb/irowsetupdateimpl-setdata.md)|将在一列或多列中可接受的数据值。|  
  
### 接口方法 \(用于 IRowsetUpdate\)  
  
|||  
|-|-|  
|[GetOriginalData](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|从数据源获取数据传输到新，或者获取忽略挂起的更改。|  
|[GetPendingRows](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|返回行列表与挂起的更改。|  
|[GetRowStatus](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|返回中指定的行状态。|  
|[撤消](../../data/oledb/irowsetupdateimpl-undo.md)|撤消对行的所有更改，因为最后获取或更新。|  
|[更新](../../data/oledb/irowsetupdateimpl-update.md)|传输进行的任何更改。行，因为最后获取或更新。|  
  
### 实现回调方法 \(\)  
  
|||  
|-|-|  
|[IsUpdateAllowed](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|用于检查安全性，完整性，方法允许在更新之前。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|包含原始数据。延迟的操作。|  
  
## 备注  
 因为中描述的内容还存在应用此处，应先阅读和理解 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)的文档。  还应读取 `OLE``DB`上设置的`Programmer's``Reference` 数据的章节 6。  
  
 `IRowsetUpdateImpl` 实现 OLE DB 接口，`IRowsetUpdate` 使使用者延迟将 `IRowsetChange` 更改传输到数据源。和传输之前撤消更改。  
  
> [!IMPORTANT]
>  强烈建议您在尝试实现提供程序读取下列文档：  
  
-   [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)  
  
-   `OLE` `DB` `Programmer's` `Reference`的章节6  
  
-   另请参见 `RUpdateRowset` 类如何在 UpdatePV 示例  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)