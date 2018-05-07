---
title: 'TN042: ODBC 驱动程序开发人员建议 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.odbc
dev_langs:
- C++
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35c75f5c5bae3a1b56abe91340de00f373663792
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042：ODBC 驱动程序开发人员建议
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍 ODBC 驱动程序编写人员准则。 它概述了一般要求和 ODBC 的功能使 MFC 数据库类，以及各种预期语义的详细信息的假设。 所需驱动程序功能，以支持三个`CRecordset`打开模式 (**forwardOnly**，**快照**和**动态集**) 所述。  
  
## <a name="odbcs-cursor-library"></a>ODBC 的游标库  
 MFC 数据库类呈现给用户，在许多情况下超出大多数第 1 级 ODBC 驱动程序提供的功能的功能。 幸运的是，ODBC 的游标库将层本身之间的数据库类和驱动程序，并将自动提供很多此附加功能。  
  
 例如，大多数 1.0 驱动程序不支持向后滚动。 游标库可以检测到这种，和将缓存的驱动程序中的行并将它们呈现在 FETCH_PREV 调用中的要求**SQLExtendedFetch**。  
  
 游标库依赖的另一个重要的示例是定位的更新。 大多数 1.0 驱动程序还没有定位的更新，但是游标库将生成更新语句标识基于其当前的缓存的数据值或缓存的时间戳值的数据源上的目标行。  
  
 类库永远不会利用多个行集。 因此的几个**SQLSetPos**语句始终应用于行的行集的 1。  
  
## <a name="cdatabases"></a>CDatabases  
 每个`CDatabase`分配单个**HDBC**。 (如果`CDatabase`的`ExecuteSQL`函数使用， **HSTMT**暂时分配。)因此，如果多个`CDatabase`的需要，多个**HDBC**每 s **HENV**必须支持。  
  
 数据库类需要的是光标库。 这反映在**SQLSetConnections**调用**SQL_ODBC_CURSORS**， **SQL_CUR_USE_ODBC**。  
  
 **SQLDriverConnect**， **SQL_DRIVER_COMPLETE**由`CDatabase::Open`建立到数据源的连接。  
  
 该驱动程序必须支持**SQLGetInfo SQL_ODBC_API_CONFORMANCE** >= **SQL_OAC_LEVEL1**， **SQLGetInfo SQL_ODBC_SQL_CONFORMANCE**  >= **SQL_OSC_MINIMUM**。  
  
 为了使事务的支持`CDatabase`和其依赖的记录集， **SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR**和**SQL_CURSOR_ROLLBACK_BEHAVIOR**必须具有**SQL_CR_PRESERVE**。 否则，将忽略尝试执行事务控制。  
  
 **SQLGetInfo SQL_DATA_SOURCE_READ_ONLY**必须支持。 如果它返回"Y"，则将在数据源上不执行任何更新操作。  
  
 如果`CDatabase`打开 ReadOnly，尝试读取的数据源设置仅将会执行与**SQLSetConnectOption SQL_ACCESS_MODE**， **SQL_MODE_READ_ONLY**。  
  
 如果标识符需要用引号括起来，应从该驱动程序返回此信息**SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR**调用。  
  
 出于调试目的， **SQLGetInfo SQL_DBMS_VER**和**SQL_DBMS_NAME**驱动程序中检索。  
  
 **SQLSetStmtOption SQL_QUERY_TIMEOUT**和**SQL_ASYNC_ENABLE**不能对调用`CDatabase`的**HDBC**。  
  
 **SQLError**可调用使用任何或所有自变量为 NULL。  
  
 当然， **SQLAllocEnv**， **SQLAllocConnect**， **SQLDisconnect**和**SQLFreeConnect**必须支持。  
  
## <a name="executesql"></a>ExecuteSQL  
 除了分配和释放一个临时**HSTMT**，`ExecuteSQL`调用**SQLExecDirect**， **SQLFetch**， **SQLNumResultCol**和`SQLMoreResults`。 **SQLCancel**不能对调用**HSTMT**。  
  
## <a name="getdatabasename"></a>GetDatabaseName  
 **SQLGetInfo SQL_DATABASE_NAME**将调用。  
  
## <a name="begintrans-committrans-rollback"></a>BeginTrans，CommitTrans，回滚  
 **SQLSetConnectOption SQL_AUTOCOMMIT**和**SQLTransact SQL_COMMIT**， **SQL_ROLLBACK**和**SQL_AUTOCOMMIT**事务请求将会调用进行。  
  
## <a name="crecordsets"></a>CRecordsets  
 **SQLAllocStmt**， **SQLPrepare**， **SQLExecute** (有关**打开**和**Requery**)， **SQLExecDirect** （对于更新操作）， **SQLFreeStmt**必须支持。 **SQLNumResultCols**和**SQLDescribeCol**将对结果集在不同时间调用。  
  
 **SQLSetParam**广泛用于参数将数据绑定和**DATA_AT_EXEC**功能。  
  
 **SQLBindCol**广泛用于注册输出列使用 ODBC 的数据存储位置。  
  
 两个**SQLGetData**调用用于检索**SQL_LONG_VARCHAR**和**SQL_LONG_VARBINARY**数据。 第一次调用尝试通过调用查找列的值的总长度**SQLGetData**与 cbMaxValue 0，但有效 pcbValue。 如果 pcbValue 持有**SQL_NO_TOTAL**，将引发异常。 否则为`HGLOBAL`已分配，以及另一个**SQLGetData**可检索整个结果的调用。  
  
## <a name="updating"></a>Updating  
 如果请求悲观锁定，则**SQLGetInfo SQL_LOCK_TYPES**将查询。 如果**SQL_LCK_EXCLUSIVE**是不受支持，就将引发异常。  
  
 尝试更新`CRecordset`(**快照**或**动态集**) 将导致第二个**HSTMT**要分配。 为驱动程序不支持第二个**HSTMT**，光标库将模拟此功能。 遗憾的是，这可能并有时意味着强制当前查询的第一天**HSTMT**在处理第二个之前完成**HSTMT**的请求。  
  
 **SQLFreeStmt SQL_CLOSE**和**SQL_RESET_PARAMS**和**SQLGetCursorName**将在更新操作过程中调用。  
  
 如果有**CLongBinarys**中**outputColumns**，ODBC 的**DATA_AT_EXEC**必须支持功能。 这包括返回**SQL_NEED_DATA**从**SQLExecDirect**， **SQLParamData**和**SQLPutData**。  
  
 **SQLRowCount**执行以验证是否只有 1 记录已由更新后，将调用**SQLExecDirect**。  
  
## <a name="forwardonly-cursors"></a>ForwardOnly 游标  
 仅**SQLFetch**需要**移动**操作。 请注意， **forwardOnly**游标不支持更新。  
  
## <a name="snapshot-cursors"></a>快照游标  
 快照功能需要**SQLExtendedFetch**支持。 如上所述，如果驱动程序不支持将检测 ODBC 游标库**SQLExtendedFetch**，并提供必要的支持本身。  
  
 **SQLGetInfo**， **SQL_SCROLL_OPTIONS**必须支持**SQL_SO_STATIC**。  
  
## <a name="dynaset-cursors"></a>动态集游标  
 下面是打开动态集所需的最小支持：  
  
 **SQLGetInfo**， **SQL_ODBC_VER**必须返回 >"01"。  
  
 **SQLGetInfo**， **SQL_SCROLL_OPTIONS**必须支持**SQL_SO_KEYSET_DRIVEN**。  
  
 **SQLGetInfo**， **SQL_ROW_UPDATES**必须返回"Y"。  
  
 **SQLGetInfo**， **SQL_POSITIONED_UPDATES**必须支持**SQL_PS_POSITIONED_DELETE**和**SQL_PS_POSITIONED_UPDATE**。  
  
 此外，如果请求悲观锁定，则调用**SQLSetPos** irow 1、 fRefresh FALSE 与 fLock **SQL_LCK_EXCLUSIVE**将进行。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

