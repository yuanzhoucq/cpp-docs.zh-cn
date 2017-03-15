---
title: "命令和表 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessorRowset 类, 命令类和表类"
  - "CCommand 类, OLE DB 使用者模板"
  - "命令 [C++], OLE DB 使用者模板"
  - "CTable 类"
  - "OLE DB 使用者模板, 命令支持"
  - "OLE DB 使用者模板, 表支持"
  - "行集合, 访问"
  - "表 [C++], OLE DB 使用者模板"
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 命令和表
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用命令和表可以访问行集合（即打开行集合、执行命令和绑定列）。  [CCommand](../../data/oledb/ccommand-class.md) 和 [CTable](../../data/oledb/ctable-class.md) 类分别实例化命令对象和表对象。  这些类从 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) 派生，如下图所示。  
  
 ![CCommand 和 CTable](../../data/oledb/media/vccommandstables.gif "vcCommandsTables")  
命令类和表类  
  
 在前面的表中，`TAccessor` 可以是在[访问器类型](../../data/oledb/accessors-and-rowsets.md)中列出的任何访问器类型。  *TRowset* 可以是在[行集合类型](../../data/oledb/accessors-and-rowsets.md)中列出的任何行集合类型。  *TMultiple* 指定结果类型（即单结果集或多结果集）。  
  
 [ATL OLE DB 使用者向导](../../atl/reference/atl-ole-db-consumer-wizard.md)使您可以指定是否需要命令或表对象。  
  
-   对于不带命令的数据源，可以使用 `CTable` 类。  通常将此类用于未指定任何参数并且不需要多个结果的简单行集合。  此简单类使用所指定的表名打开数据源中的一个表。  
  
-   对于支持命令的数据源，可以改用 `CCommand` 类。  若要执行命令，请调用此类上的 [Open](../../data/oledb/ccommand-open.md)。  也可以调用 `Prepare` 准备需要执行一次以上的命令。  
  
     **CCommand** 具有三个模板参数：访问器类型、行集合类型和结果类型（默认情况下为 `CNoMultipleResults` 或 `CMultipleResults`）。  如果指定 `CMultipleResults`，`CCommand` 类则支持 **IMultipleResults** 接口并支持处理多个行集合。  [DBVIEWER](http://msdn.microsoft.com/zh-cn/07620f99-c347-4d09-9ebc-2459e8049832) 示例显示如何处理多个结果。  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)