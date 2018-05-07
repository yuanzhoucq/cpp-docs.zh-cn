---
title: TN068： 使用 Microsoft Access 7 ODBC 驱动程序执行事务 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data.odbc
dev_langs:
- C++
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63cce7532d93b1bd44b6a44c526310bd894d5e07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068：使用 Microsoft Access 7 ODBC 驱动程序执行事务
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍如何使用 MFC ODBC 数据库类和的 Microsoft ODBC Desktop Driver Pack 版本 3.0 中包含的 Microsoft 访问 7.0 ODBC 驱动程序时执行事务。  
  
## <a name="overview"></a>概述  
 如果数据库应用程序执行事务，您必须小心地将其调用`CDatabase::BeginTrans`和`CRecordset::Open`应用程序中正确的顺序。 Microsoft 访问 7.0 驱动程序使用 Microsoft Jet 数据库引擎，并且 Jet 需要你的应用程序不开始上的所有数据库都已打开的游标的事务。 MFC ODBC 数据库类中，打开的游标等于打开`CRecordset`对象。  
  
 如果打开之前调用的记录集**BeginTrans**，你可能看不到任何错误消息。 但是，任何记录集更新在调用后变为永久你应用程序使`CRecordset::Update`，并且更新将不会回滚通过调用**回滚**。 若要避免此问题，必须调用**BeginTrans**第一个，然后打开记录集。  
  
 MFC 检查游标提交和回滚行为的驱动程序功能。 类`CDatabase`提供两个成员函数，`GetCursorCommitBehavior`和`GetCursorRollbackBehavior`，以确定你处于打开状态的任何事务的效果`CRecordset`对象。 对于 Microsoft 访问 7.0 ODBC 驱动程序，这些成员函数返回`SQL_CB_CLOSE`因为 Access 驱动程序不支持游标保留。 因此，必须调用`CRecordset::Requery`以下**CommitTrans**或**回滚**操作。  
  
 当你需要一个接一个执行多个事务时，无法调用**Requery**后第一个事务，然后再启动下一个。 您必须关闭记录集的后续调用之前**BeginTrans**以满足 Jet 的要求。 此技术说明描述两种方法可以处理这种情况下：  
  
-   在每个后关闭记录集**CommitTrans**或**回滚**操作。  
  
-   使用 ODBC API 函数**SQLFreeStmt**。  
  
## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>每个 CommitTrans 或回滚操作后关闭记录集  
 在开始之前事务，请确保记录集对象已关闭。 在调用**BeginTrans**，调用记录集的**打开**成员函数。 在调用之后立即关闭记录集**CommitTrans**或**回滚**。 请注意重复打开和关闭记录集可能会降低应用程序的性能。  
  
## <a name="using-sqlfreestmt"></a>使用 SQLFreeStmt  
 你还可以使用 ODBC API 函数**SQLFreeStmt**以显式晚于结束事务时关闭游标。 若要启动另一个事务，调用**BeginTrans**跟`CRecordset::Requery`。 在调用时**SQLFreeStmt**，你必须指定记录集的 HSTMT 作为第一个参数和**SQL_CLOSE**第二个参数。 此方法非常快，关闭并打开每个事务开始时记录集。 下面的代码演示如何实现此方法：  
  
```  
CMyDatabase db;  
db.Open("MYDATASOURCE");

CMyRecordset rs(&db);

 
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
// close the cursor  
::SQLFreeStmt(rs.m_hstmt, SQL_CLOSE);

 
// start transaction 2  
db.BeginTrans();

 
// now get the result set  
rs.Requery();

 
// manipulate data  
 
// end transaction 2  
db.CommitTrans();

 
rs.Close();

db.Close();
```  
  
 另一种方法实现此方法是编写一个新函数**RequeryWithBeginTrans**，其可以调用以启动下一个事务之后你提交, 或回滚第一个。 若要编写此类函数，请执行以下步骤操作：  
  
1.  将代码复制**CRecordset::Requery （)** 到新函数。  
  
2.  将以下行添加到在调用后立即**SQLFreeStmt**:  
  
 `m_pDatabase->BeginTrans( );`  
  
 现在你可以调用之间的事务的每个对此函数：  
  
```  
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
// close the cursor,
    start new transaction,  
// and get the result set  
rs.RequeryWithBeginTrans();

 
// manipulate data  
 
// end transaction 2  
db.CommitTrans();
*// or Rollback()  
```  
  
> [!NOTE]
>  不要使用此方法，如果你需要更改的记录集成员变量**m_strFilter**或`m_strSort`之间的事务。 在这种情况下，你应在每个后关闭记录集**CommitTrans**或**回滚**操作。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

