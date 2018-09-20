---
title: 'TN042: ODBC 驱动程序开发人员建议 |Microsoft Docs'
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
ms.openlocfilehash: 87e31fa0884adc78d3f1026afc59dd0b46ac7602
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375250"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042：ODBC 驱动程序开发人员建议

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此说明描述的 ODBC 驱动程序编写人员的指导原则。 它概述了一般要求和假设的 ODBC 的功能使 MFC 数据库类，以及各种预期语义的详细信息。 所需驱动程序的功能以支持三种`CRecordset`打开模式 (**forwardOnly**，**快照**并**动态集**) 所述。

## <a name="odbcs-cursor-library"></a>ODBC 的游标库

MFC 数据库类呈现给用户，在许多情况下超越了大多数的 1 级 ODBC 驱动程序提供的功能的功能。 幸运的是，ODBC 的游标库将层本身之间的数据库类和驱动程序，并将自动提供了很多此附加功能。

例如，大多数 1.0 驱动程序不支持向后滚动。 游标库可以检测到这，并将缓存从驱动程序的行并将其呈现 FETCH_PREV 调用中的请求`SQLExtendedFetch`。

游标库依赖关系的另一个重要的示例是定位的更新。 大多数 1.0 驱动程序还没有定位的更新，但该游标库将生成标识目标行根据其当前的缓存的数据值或缓存时间戳值的数据源上的 update 语句。

类库永远不会使用多个行集。 因此，一些`SQLSetPos`语句始终应用第 1 行集的行。

## <a name="cdatabases"></a>CDatabases

每个`CDatabase`分配单个**HDBC**。 (如果`CDatabase`的`ExecuteSQL`使用函数，则**HSTMT**暂时分配。)因此，如果多个`CDatabase`的要求，多个**HDBC**每个秒**HENV**必须支持。

数据库类需要游标库。 这反映在`SQLSetConnections`调用**SQL_ODBC_CURSORS**， **SQL_CUR_USE_ODBC**。

`SQLDriverConnect`**SQL_DRIVER_COMPLETE**由`CDatabase::Open`来建立与数据源的连接。

该驱动程序必须支持`SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >=  **SQL_OAC_LEVEL1**， `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**。

为要支持的事务的顺序`CDatabase`及其依赖的记录集，`SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR`并**SQL_CURSOR_ROLLBACK_BEHAVIOR**必须具有**SQL_CR_PRESERVE**。 否则，将忽略尝试执行事务控制。

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY` 必须支持。 如果它返回"Y"，则将数据源上不执行任何更新操作。

如果`CDatabase`打开只读的、 已尝试设置数据源读取仅将使用来进行`SQLSetConnectOption SQL_ACCESS_MODE`， **SQL_MODE_READ_ONLY**。

如果标识符需要用引号括起来，应从驱动程序返回此信息`SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR`调用。

出于调试目的，`SQLGetInfo SQL_DBMS_VER`并**SQL_DBMS_NAME**检索来自驱动程序。

`SQLSetStmtOption SQL_QUERY_TIMEOUT` 并**SQL_ASYNC_ENABLE**不能对调用`CDatabase`的**HDBC**。

`SQLError` 不能调用使用任何或所有参数为 NULL。

当然`SQLAllocEnv`， `SQLAllocConnect`，`SQLDisconnect`和`SQLFreeConnect`必须支持。

## <a name="executesql"></a>ExecuteSQL

除了分配和释放一个临时**HSTMT**，`ExecuteSQL`调用`SQLExecDirect`， `SQLFetch`，`SQLNumResultCol`和`SQLMoreResults`。 `SQLCancel` 不能对调用**HSTMT**。

## <a name="getdatabasename"></a>GetDatabaseName

`SQLGetInfo SQL_DATABASE_NAME` 将调用。

## <a name="begintrans-committrans-rollback"></a>BeginTrans、 CommitTrans 回滚

`SQLSetConnectOption SQL_AUTOCOMMIT` 并`SQLTransact SQL_COMMIT`， **SQL_ROLLBACK**并**SQL_AUTOCOMMIT**事务请求的情况下调用。

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt``SQLPrepare`， `SQLExecute` (对于`Open`并`Requery`)， `SQLExecDirect` （以执行更新操作），`SQLFreeStmt`必须支持。 `SQLNumResultCols` 和`SQLDescribeCol`将对结果集在不同时间调用。

`SQLSetParam` 绑定参数数据的广泛使用并**DATA_AT_EXEC**功能。

`SQLBindCol` 广泛用于注册输出列使用 ODBC 的数据存储位置。

两个`SQLGetData`调用用于检索**SQL_LONG_VARCHAR**并**SQL_LONG_VARBINARY**数据。 第一次调用会尝试通过调用查找列的值的总长度`SQLGetData`cbMaxValue 0，但有效 pcbValue。 如果 pcbValue 持有**SQL_NO_TOTAL**，将引发异常。 否则为**HGLOBAL**分配和另一个`SQLGetData`调用以检索全部结果。

## <a name="updating"></a>Updating

如果请求悲观锁定，则`SQLGetInfo SQL_LOCK_TYPES`进行查询。 如果**SQL_LCK_EXCLUSIVE**是不受支持，就会引发异常。

尝试更新`CRecordset`(**快照**或**动态集**) 将导致第二个**HSTMT**并将其分配。 不支持的驱动程序的第二个**HSTMT**，游标库将模拟此功能。 遗憾的是，这可能有时意味着，在第一个强制当前查询**HSTMT**完毕之后处理第二个, **HSTMT**的请求。

`SQLFreeStmt SQL_CLOSE` 并**SQL_RESET_PARAMS**和`SQLGetCursorName`将在更新操作过程中调用。

如果有**CLongBinarys**中**outputColumns**，ODBC 的**DATA_AT_EXEC**必须支持功能。 这包括返回**SQL_NEED_DATA**从`SQLExecDirect`，`SQLParamData`和`SQLPutData`。

`SQLRowCount` 若要验证是否仅 1 条记录已通过更新在执行后调用`SQLExecDirect`。

## <a name="forwardonly-cursors"></a>ForwardOnly 游标

仅`SQLFetch`是所必需的`Move`操作。 请注意， **forwardOnly**游标不支持更新。

## <a name="snapshot-cursors"></a>快照游标

快照功能需要`SQLExtendedFetch`支持。 如上文所述，当驱动程序不支持将检测 ODBC 游标库`SQLExtendedFetch`，并提供必要的支持本身。

`SQLGetInfo`**SQL_SCROLL_OPTIONS**必须支持**SQL_SO_STATIC**。

## <a name="dynaset-cursors"></a>动态集游标

以下是打开动态集所需的最低支持：

`SQLGetInfo`**SQL_ODBC_VER**必须返回 >"01"。

`SQLGetInfo`**SQL_SCROLL_OPTIONS**必须支持**SQL_SO_KEYSET_DRIVEN**。

`SQLGetInfo`**SQL_ROW_UPDATES**必须返回"Y"。

`SQLGetInfo`**SQL_POSITIONED_UPDATES**必须支持**SQL_PS_POSITIONED_DELETE**并**SQL_PS_POSITIONED_UPDATE**。

此外，如果请求悲观锁定，则调用`SQLSetPos`irow 1、 fRefresh FALSE 与纷纷采用**SQL_LCK_EXCLUSIVE**都能。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)

