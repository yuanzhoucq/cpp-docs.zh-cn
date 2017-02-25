---
title: "IRowsetChangeImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetChangeImpl"
  - "IRowsetChangeImpl"
  - "ATL.IRowsetChangeImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetChangeImpl 类"
  - "提供程序, 可更新的"
  - "可更新提供程序, 即时更新"
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# IRowsetChangeImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) 接口的 OLE DB 模板实现在 OLE DB 规范中。  
  
## 语法  
  
```  
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >   
>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
#### 参数  
 `T`  
 类从 `IRowsetChangeImpl` 派生。  
  
 `Storage`  
 用户记录  
  
 `BaseInterface`  
 接口的基类，如 `IRowsetChange`。  
  
 `RowClass`  
 行处理单元格。  
  
 `MapClass`  
 \(提供程序\) 占用的任何行句柄的单元格。  
  
## 成员  
  
### 接口方法 \(用于 IRowsetChange\)  
  
|||  
|-|-|  
|[DeleteRows](../../data/oledb/irowsetchangeimpl-deleterows.md)|从行集合中删除行。|  
|[InsertRow](../../data/oledb/irowsetchangeimpl-insertrow.md)|行插入到该行集合。|  
|[SetData](../../data/oledb/irowsetchangeimpl-setdata.md)|设置一行中的一列或多列中的数据值。|  
  
### 实现回调方法 \(\)  
  
|||  
|-|-|  
|[FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)|被目标的数据提供程序的 Overidden 到的存储。|  
  
## 备注  
 此接口用于立即写入操作运行到数据存储区。“即时”意味着，如果最终用户使用 \(使用者\) 时的用户进行任何更改，则这些更改立即传输到数据存储区 \(和不能撤消。\)  
  
 实现 OLE DB `IRowsetChange`接口，从而启用中 `IRowsetChangeIRowsetChangeImpl` 现有行的列，删除行和插入新行的更新值。  
  
 OLE DB 模板实现支持所有基方法 \(`SetData`、`InsertRow`和 `DeleteRows`\)。  
  
> [!IMPORTANT]
>  强烈建议您在尝试实现提供程序读取下列文档：  
  
-   [创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)  
  
-   *OLE DB Programmer's Reference*6 的章节  
  
-   另请参见 `RUpdateRowset` 类如何在 UpdatePV 示例  
  
## 要求  
 **头文件:** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)