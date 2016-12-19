---
title: "CRowset 类 | Microsoft Docs"
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
  - "ATL.CRowset<TAccessor>"
  - "CRowset"
  - "ATL::CRowset"
  - "ATL::CRowset<TAccessor>"
  - "ATL.CRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRowset 类"
ms.assetid: b0228a90-b8dd-47cc-b397-8d4c15c1e7f4
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装 OLE DB 行集合对象和几个相关接口而对于行集合数据的处理方法。  
  
## 语法  
  
```  
template <class TAccessor = CAccessorBase>  
class CRowset  
```  
  
#### 参数  
 `TAccessor`  
 一个访问器类  默认值为 `CAccessorBase`。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/crowset-addrefrows.md)|递增引用计数与当前行。|  
|[关闭](../../data/oledb/crowset-close.md)|释放列和当前 `IRowset` 接口 。|  
|[比较](../../data/oledb/crowset-compare.md)|使用 [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx)，比较两个书签。|  
|[CRowset](../../data/oledb/crowset-crowset.md)|创建新的 `CRowset` 对象，并 \(可选\) 它与为参数中提供的 **IRowset** 接口。|  
|[Delete](../../data/oledb/crowset-delete.md)|从行集合中删除行使用 [IRowsetChange:DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx)。|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|在指定后的书签，查找下一匹配行。|  
|[GetApproximatePosition](../../data/oledb/crowset-getapproximateposition.md)|返回行的位置大概与书签的。|  
|[GetData](../../data/oledb/crowset-getdata.md)|从行的行集合副本中检索数据。|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|从指定缓冲区中检索数据。|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|从数据源获取数据传输，忽略挂起的更改。|  
|[GetRowStatus](../../data/oledb/crowset-getrowstatus.md)|返回所有行状态。|  
|[Insert](../../data/oledb/crowset-insert.md)|使用 [IRowsetChange:InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx)，创建和插入新行。|  
|[IsSameRow](../../data/oledb/crowset-issamerow.md)|将当前的行与指定的行进行比较。|  
|[MoveFirst](../../data/oledb/crowset-movefirst.md)|将下一个获取位置重新定位到其初始位置。|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|移动到最后一条记录|  
|[MoveNext](../../data/oledb/crowset-movenext.md)|从下一连续行的获取数据或位置指定数量的对象之外的下一行。|  
|[MovePrev](../../data/oledb/crowset-moveprev.md)|移动到上一条记录|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|提取书签标记的行按指定的偏移量 \(\) 从该书签。|  
|[MoveToRatio](../../data/oledb/crowset-movetoratio.md)|获取从在行集的一部分位置开始的行。|  
|[ReleaseRows](../../data/oledb/crowset-releaserows.md)|调用释放当前行句柄的 [IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx)。|  
|[SetData](../../data/oledb/crowset-setdata.md)|[CRowset::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx) 在当前行的一个或多个列中设置数据值。|  
|[撤消](../../data/oledb/crowset-undo.md)|撤消所做的任何更改。行，因为最后获取或 [更新](../../data/oledb/crowset-update.md)。|  
|[更新](../../data/oledb/crowset-update.md)|CRowset::Update 传输自从对行集合进行最后一次获取或 Update 调用以来对当前行所做的所有挂起的更改。|  
|[UpdateAll](../../data/oledb/crowset-updateall.md)|传输进行的所有挂起的更改的所有行，因为最后获取或更新。|  
  
## 备注  
 在 OLE DB 中，行集是程序设置和检索数据的对象。  
  
 此类不会实例化，而是将其作为模板参数传递到 `CTable` 或 `CCommand` \(`CRowset` 是默认值\)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [DBViewer 示例](../../top/visual-cpp-samples.md)   
 [MultiRead 示例](../../top/visual-cpp-samples.md)   
 [MultiRead 特性示例](../../top/visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)