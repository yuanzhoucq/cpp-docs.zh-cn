---
title: "TN068：使用 Microsoft Access 7 ODBC 驱动程序执行事务 | Microsoft Docs"
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
  - "vc.data.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN068"
  - "事务, 调用 BeginTrans"
  - "事务, Microsoft Access"
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN068：使用 Microsoft Access 7 ODBC 驱动程序执行事务
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明如何执行事务，请使用 MFC ODBC 数据库类中，在桌面 Microsoft ODBC 驱动程序中包括的 Microsoft Access ODBC 驱动 7.0 程序打包版本 3.0。  
  
## 概述  
 如果数据库应用程序执行事务，您必须注意调用 `CDatabase::BeginTrans` 和 `CRecordset::Open` 以正确的顺序应用程序中  7.0 Microsoft Access 驱动程序使用 Microsoft Jet 数据库引擎，并且，Jet 要求应用程序未启动对具有打开游标的所有数据库的事务。  对于 MFC ODBC 数据库类，一个打开游标相当于打开 `CRecordset` 对象。  
  
 如果在调用 **BeginTrans**之前打开记录集，则不会显示任何错误消息。  但是，所有记录集更新应用程序使变为如果在调用 `CRecordset::Update`后，通过调用 **回滚**更新，并将无法回滚。  若要避免此问题，您必须首先调用 **BeginTrans** 之后再打开记录集。  
  
 MFC 检查光标提交和回滚行为的驱动程序功能。  类在 `CDatabase` 打开 `CRecordset` 对象提供两个成员函数，`GetCursorCommitBehavior` 和 `GetCursorRollbackBehavior`，以确定所有事务的影响。  对于 7.0 Microsoft Access ODBC 驱动程序，因为访问驱动程序不支持游标，保存这些成员函数返回 `SQL_CB_CLOSE`。  因此，您必须调用在 **CommitTrans** 或 **回滚** 操作的 `CRecordset::Requery`。  
  
 当需要逐个时执行多个事务，在第一事务之后调用 **再次查询** 之后再启动下一个。  必须关闭记录集，则在下次调用 **BeginTrans** 才能喷气机满足的要求。  此技术说明描述处理此情况两个方法：  
  
-   关闭在每个 **CommitTrans** 或 **回滚** 操作之后的记录集。  
  
-   使用 ODBC API 函数 **SQLFreeStmt**。  
  
## 关闭在每次 CommitTrans 或回滚操作之后的记录集  
 在启动该事务之前，请决定记录集关闭对象。  在调用 **BeginTrans**后，调用记录集的 **打开** 成员函数。  关闭在调用 **CommitTrans** 或 **回滚**之前的记录集。  注意对于打开和关闭记录集可以降低应用程序的性能。  
  
## 使用 SQLFreeStmt  
 也可以使用 ODBC API 函数 **SQLFreeStmt** 之后结束事务后显式关闭光标。  若要开始另一事务，通过调用 **BeginTrans**`CRecordset::Requery`后面。  当调用 **SQLFreeStmt**时，必须指定记录集的 HSTMT 作为第一个参数和 **SQL\_CLOSE** 作为第二个参数。  此方法比结束和开始学习记录集在每个事务的启动。  下面的代码演示如何实现此技术：  
  
```  
CMyDatabase db;  
db.Open( "MYDATASOURCE" );  
CMyRecordset rs( &db );  
  
// start transaction 1 and   
// open the recordset  
db.BeginTrans( );  
rs.Open( );  
  
// manipulate data  
  
// end transaction 1  
db.CommitTrans( );  // or Rollback( )  
  
// close the cursor  
::SQLFreeStmt( rs.m_hstmt, SQL_CLOSE );  
  
// start transaction 2  
db.BeginTrans( );  
  
// now get the result set  
rs.Requery( );  
  
// manipulate data  
  
// end transaction 2  
db.CommitTrans( );  
  
rs.Close( );  
db.Close( );  
```  
  
 另一种方法实现此技术将编写新函数，**RequeryWithBeginTrans**，可以调用开始下一事务，在提交或回滚第一个后。  若要编写此类函数，请执行以下步骤：  
  
1.  复制 **CRecordset::Requery\( \)** 的代码添加到新功能。  
  
2.  添加调用之后立即调用的代码行到 **SQLFreeStmt**:  
  
     `m_pDatabase->BeginTrans( );`  
  
 现在您可以调用。每对事务之间此函数：  
  
```  
// start transaction 1 and   
// open the recordset  
db.BeginTrans( );  
rs.Open( );  
  
// manipulate data  
  
// end transaction 1  
db.CommitTrans( );  // or Rollback( )  
  
// close the cursor, start new transaction,  
// and get the result set  
rs.RequeryWithBeginTrans( );  
  
// manipulate data  
  
// end transaction 2  
db.CommitTrans( );  // or Rollback( )  
```  
  
> [!NOTE]
>  如果需要将在事务之间，的记录集成员变量 **m\_strFilter** 或 `m_strSort` 中要使用此技术。  在这种情况下，您应在每个 **CommitTrans** 或 **回滚** 操作之后关闭记录集。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)