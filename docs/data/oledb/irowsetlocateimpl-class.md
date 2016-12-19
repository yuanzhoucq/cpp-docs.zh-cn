---
title: "IRowsetLocateImpl 类 | Microsoft Docs"
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
  - "IRowsetLocateImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "书签, OLE DB"
  - "IRowsetLocateImpl 类"
  - "提供程序, 书签"
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetLocateImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现 OLE DB 接口，[IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) 获取从行集合中任意行。  
  
## 语法  
  
```  
template <  
   class T,   
   class RowsetInterface,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,   
   class BookmarkKeyType = LONG,   
   class BookmarkType = LONG,   
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >  
>  
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<  
   T,   
   RowsetInterface,   
   RowClass,   
   MapClass  
>  
```  
  
#### 参数  
 `T`  
 类从 `IRowsetLocateImpl` 派生。  
  
 `RowsetInterface`  
 类从 `IRowsetImpl` 派生。  
  
 `RowClass`  
 为 **HROW** 的存储单元。  
  
 `MapClass`  
 \(提供程序\) 占用的任何行句柄的单元格。  
  
 `BookmarkKeyType`  
 书签的类型，如长或字符串。  普通的书签必须具有长度至少两个字节。\(单字节长度为 [标准书签](https://msdn.microsoft.com/en-us/library/ms712954.aspx) OLE DB **DBBMK\_FIRST**，**DBBMK\_LAST**和 **DBBMK\_INVALID**是保留的。\)  
  
 `BookmarkType`  
 维护的书签对数据关系的映射机制。  
  
 `BookmarkMapClass`  
 \(书签\) 占用的任何行句柄的单元格。  
  
## 成员  
  
### 接口方法  
  
|||  
|-|-|  
|[比较](../../data/oledb/irowsetlocateimpl-compare.md)|比较两个书签。|  
|[GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)|获取启动行与书签的偏移量指定的行。|  
|[GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)|提取与指定书签的行。|  
|[哈希](../../data/oledb/irowsetlocateimpl-hash.md)|返回指定书签的哈希值。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_rgbookmarks](../../data/oledb/irowsetlocateimpl-m-rgbookmarks.md)|一个书签。|  
  
## 备注  
 `IRowsetLocateImpl` 接口是 [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) 的 OLE DB 模板实现。  `IRowsetLocate` 用于获取从行集合中任意行。  不实现此接口的行集合是 `sequential` 行集合。  在 `IRowsetLocate` 上存在行集时，第 0 列是行的书签；读取此列将获取可用于重新定位到同一行中书签的值。  
  
 `IRowsetLocateImpl` 用于实现在提供程序的书签支持。  书签是占位符 \(对行集合的索引\) 使使用者尽快返回到行，允许对该数据的缓存联接。  提供程序确定书签可以唯一标识行。  使用 `IRowsetLocateImpl` 方法，您可以比较书签，偏移之前获取由行，由书签提取行并返回书签的哈希值。  
  
 要支持在 OLE DB 为行集合书签，以便此类使行集继承。  
  
 有关实现书签支持的信息，请参见在 *Visual C\+\+ Programmer's Guide* 中的 *OLE DB Programmer's Reference* 和 [提供程序的书签支持](../../data/oledb/provider-support-for-bookmarks.md) [书签](https://msdn.microsoft.com/en-us/library/ms709728.aspx) 在 `Platform``SDK`。  
  
## 要求  
 **头文件:**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/en-us/library/ms721190.aspx)   
 [用于书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)   
 [Bookmarks](https://msdn.microsoft.com/en-us/library/ms709728.aspx)