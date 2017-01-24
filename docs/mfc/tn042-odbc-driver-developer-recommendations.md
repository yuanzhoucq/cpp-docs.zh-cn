---
title: "TN042：ODBC 驱动程序开发人员建议 | Microsoft Docs"
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
  - "vc.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据库 [C++], ODBC"
  - "ODBC 驱动程序 [C++], 写入"
  - "TN042"
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN042：ODBC 驱动程序开发人员建议
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明 ODBC 驱动程序编写的教程。  概述 ODBC 功能 MFC 数据库类使和各个项目通常语义详细信息的要求和过程。  支持三个必需的 `CRecordset` 打开模式驱动程序功能 \(**forwardOnly**、**快照** 和 **dynaset**\) 来描述。  
  
## ODBC 的游标库  
 MFC 数据库类当前功能。大多数情况下最多 1 级 ODBC 驱动程序提供功能的用户。  所幸，ODBC 的游标库将分层自己在数据库类和驱动程序之间并自动提供此附加功能。  
  
 例如，多数 1.0 驱动程序不支持向后滚动。  游标库在 **SQLExtendedFetch**的 FETCH\_PREV 调用无法检测此和驱动程序从缓存的行并它们按照要求。  
  
 游标库依赖关系的另一个重要示例是定位更新。  多数 1.0 驱动程序或具有定位更新，但是，游标库将生成上标识数据源的目标行基于其当前缓存数据值的更新语句，则缓存的一个时间戳值。  
  
 类库不利用多个行集合。  因此，仍 **SQLSetPos** 语句始终应用 1 行的行集合。  
  
## CDatabases  
 每个 `CDatabase` 分配唯一 **HDBC**。\(如果使用了 `CDatabase``ExecuteSQL`，**HSTMT** 函数暂时分配。\)因此，如果需要多个 entity\_CODECDatabase 的，则必须支持多个 **HDBC**。每个 **HENV**。  
  
 数据库类需要游标库。  它会在 **SQLSetConnections** 调用 **SQL\_ODBC\_CURSORS**，**SQL\_CUR\_USE\_ODBC**会反映在中。  
  
 使用 `CDatabase::Open`**SQLDriverConnect**，**SQL\_DRIVER\_COMPLETE** 建立到数据源的连接。  
  
 驱动程序必须支持 **SQLGetInfo SQL\_ODBC\_API\_CONFORMANCE** \>**SQL\_OAC\_LEVEL1SQLGetInfo SQL\_ODBC\_SQL\_CONFORMANCE** \>**SQL\_OSC\_MINIMUM**。为 \=，  
  
 为了为 `CDatabase` 及其相关的记录集中支持事务，**SQLGetInfo** 的**SQL\_CURSOR\_COMMIT\_BEHAVIOR** 和 **SQL\_CURSOR\_ROLLBACK\_BEHAVIOR** 必须具有 **SQL\_CR\_PRESERVE**。  否则，尝试执行事务控件将被忽略。  
  
 必须支持**SQLGetInfoSQL\_DATA\_SOURCE\_READ\_ONLY**。  如果返回“Y”，更新操作在数据源不会运行。  
  
 如果 `CDatabase` 中打开只读，尝试设置读取的数据源用 **SQLSetConnectOption SQL\_ACCESS\_MODE**，**SQL\_MODE\_READ\_ONLY**才进行。  
  
 如果标识符的引用，应从带有 **SQLGetInfo** 的**SQL\_IDENTIFIER\_QUOTE\_CHAR** 调用驱动程序返回此信息。  
  
 出于调试目的，**SQL\_DBMS\_NAME** 从 **SQLGetInfo SQL\_DBMS\_VER** 和驱动程序。  
  
 **SQLSetStmtOption SQL\_QUERY\_TIMEOUT** 和 **SQL\_ASYNC\_ENABLE** 可能在 `CDatabase`**HDBC**。  
  
 **SQLError** 可以调用使用的任意或所有参数为空。  
  
 当然，则必须支持、**SQLAllocEnv**、**SQLAllocConnect**、**SQLDisconnect** 和 **SQLFreeConnect**。  
  
## ExecuteSQL  
 除了分配和释放临时 **HSTMT**之外，`ExecuteSQL` 调用 **SQLExecDirect**、**SQLFetch**、**SQLNumResultCol** 和 `SQLMoreResults`。  **SQLCancel** 可以调用 **HSTMT**。  
  
## GetDatabaseName  
 **SQLGetInfo** 将**SQL\_DATABASE\_NAME** 调用。  
  
## CommitTrans，回滚，BeginTrans  
 如果事务，请求，**SQLSetConnectOption** 的**SQL\_AUTOCOMMIT** 和 **SQLTransact**，**SQL\_COMMIT**将 **SQL\_ROLLBACK** 和 **SQL\_AUTOCOMMIT** 调用。  
  
## CRecordsets  
 必须支持**SQLAllocStmt**，**SQLPrepare**，**SQLExecute** \(对于 **打开** 和 **再次查询**\)，**SQLExecDirect** \(对于更新操作\)，**SQLFreeStmt**。  **SQLNumResultCols** 和 **SQLDescribeCol** 在 \+ 不同 \+ 时候将设置的结果。  
  
 **SQLSetParam** 用于绑定参数数据和 **DATA\_AT\_EXEC** 功能广泛使用。  
  
 **SQLBindCol** 多地用于对输出列 ODBC 数据的存储位置。  
  
 两个 **SQLGetData** 调用来检索 **SQL\_LONG\_VARCHAR** 和一个 **SQL\_LONG\_VARBINARY** 数据。  首次调用尝试通过调用 **SQLGetData** 来查找列值的总长度与 cbMaxValue 0，但有效的 pcbValue。  如果 pcbValue 按住 **SQL\_NO\_TOTAL**，将引发异常。  否则，`HGLOBAL` 任务，并且，另一次调用 **SQLGetData** 检索整个结果。  
  
## Updating  
 如果保守式锁定请求 **SQLGetInfo**，**SQL\_LOCK\_TYPES** 将查询。  如果 **SQL\_LCK\_EXCLUSIVE** 不支持，将引发异常。  
  
 尝试更新 `CRecordset` \(**快照** 或 **dynaset**\) 将导致分配一个 **HSTMT**。  对于不支持第二 **HSTMT**的驱动程序，游标库是模拟此功能。  遗憾的是，这在某些情况下可能意味着强制在第一 **HSTMT** 的当前完成查询到在处理第二 **HSTMT** 请求之前。  
  
 在更新操作过程，**SQLFreeStmt SQL\_CLOSE**、**SQL\_RESET\_PARAMS** 和 **SQLGetCursorName** 是调用。  
  
 如果在 **outputColumns**的 **CLongBinarys**，则必须支持 **DATA\_AT\_EXEC** ODBC 的功能。  这包括从 **SQLExecDirect**返回的 **SQL\_NEED\_DATA**、**SQLParamData** 和 **SQLPutData**。  
  
 **SQLRowCount** 之后执行称为验证后 1 仅记录的 **SQLExecDirect**更新。  
  
## ForwardOnly 光标  
 仅 **SQLFetch移动**。操作是必需的。  注意 **forwardOnly** 光标不支持更新。  
  
## 快照光标  
 快照支持功能需要 **SQLExtendedFetch**。  如上所述，ODBC 游标库是检测驱动程序不支持 **SQLExtendedFetch**，而且提供必要的支持。  
  
 **SQLGetInfo**，**SQL\_SCROLL\_OPTIONS** 必须支持 **SQL\_SO\_STATIC**。  
  
## 动态集游标  
 下面所需的最低支持打开动态集：  
  
 **SQLGetInfo**，**SQL\_ODBC\_VER** 返回 \> 为“01 "  
  
 **SQLGetInfo**，**SQL\_SCROLL\_OPTIONS** 必须支持 **SQL\_SO\_KEYSET\_DRIVEN**。  
  
 **SQLGetInfo**，**SQL\_ROW\_UPDATES** 必须返回“Y”。  
  
 **SQLGetInfo**，**SQL\_POSITIONED\_UPDATES** 必须支持 **SQL\_PS\_POSITIONED\_DELETE** 和 **SQL\_PS\_POSITIONED\_UPDATE**。  
  
 此外，如果，保守式锁定请求，对 **SQLSetPos** 的调用使用 irow 错误 1，的 fRefresh 和蜂群 **SQL\_LCK\_EXCLUSIVE** 中进行。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)