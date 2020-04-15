---
title: TN042：ODBC 驱动程序开发人员建议
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 67f7a86a247b60be66dabb0a89f04d39ce76222b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372140"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042：ODBC 驱动程序开发人员建议

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明介绍了 ODBC 驱动程序编写器的指南。 它概述了 MFC 数据库类对 ODBC 功能的一般要求和假设，以及各种预期的语义详细信息。 介绍了支持`CRecordset`三种打开模式（**仅转发**、**快照**和**动态集**）所需的驱动程序功能。

## <a name="odbcs-cursor-library"></a>ODBC 的光标库

MFC 数据库类向用户提供的功能在许多情况下超过了大多数级别 1 ODBC 驱动程序提供的功能。 幸运的是，ODBC 的光标库将在数据库类和驱动程序之间分层，并自动提供大部分附加功能。

例如，大多数 1.0 驱动程序不支持向后滚动。 游标库可以检测到这一点，并将缓存驱动程序中的行，并在 中的`SQLExtendedFetch`FETCH_PREV调用时根据需要显示它们。

游标库依赖的另一个重要示例是定位更新。 大多数 1.0 驱动程序也没有定位更新，但游标库将生成更新语句，这些语句根据数据源的当前缓存数据值或缓存的时间戳值标识目标行。

类库从不使用多个行集。 因此，少数`SQLSetPos`语句始终应用于行集的第 1 行。

## <a name="cdatabases"></a>C数据库

每个`CDatabase`分配一个**HDBC。** （如果使用`CDatabase`'s 函数`ExecuteSQL`，则临时分配**HSTMT。** 因此，如果需要`CDatabase`多个 HDBC，则必须支持每个**HENV**的多个**HDBC。**

数据库类需要游标库。 这反映在`SQLSetConnections`**电话SQL_ODBC_CURSORS，SQL_CUR_USE_ODBC。** **SQL_CUR_USE_ODBC**

`SQLDriverConnect`**SQL_DRIVER_COMPLETE**用于`CDatabase::Open`建立与数据源的连接。

司机`SQLGetInfo SQL_ODBC_API_CONFORMANCE` >= 必须支持**SQL_OAC_LEVEL1，SQL_OSC_MINIMUM。** `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**

`CDatabase`为了支持 及其从属记录集的`SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR`事务 **，SQL_CURSOR_ROLLBACK_BEHAVIOR**必须具有**SQL_CR_PRESERVE**。 否则，将忽略执行事务控件的尝试。

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY`必须支持。 如果它返回"Y"，则对数据源不执行任何更新操作。

如果`CDatabase`打开 ReadOnly，则尝试设置仅读的数据源将使用`SQLSetConnectOption SQL_ACCESS_MODE`**SQL_MODE_READ_ONLY**。

如果标识符需要报价，则应从`SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR`具有呼叫的驱动程序返回此信息。

出于调试目的，`SQLGetInfo SQL_DBMS_VER`并从驱动程序中检索**SQL_DBMS_NAME。**

`SQLSetStmtOption SQL_QUERY_TIMEOUT`**和SQL_ASYNC_ENABLE**可以调用的`CDatabase`**HDBC。**

`SQLError`可以使用任何或所有参数 NULL 调用。

`SQLAllocEnv`当然，`SQLAllocConnect`和`SQLDisconnect``SQLFreeConnect`必须支持。

## <a name="executesql"></a>ExecuteSQL

除了分配和释放临时**HSTMT**`ExecuteSQL`外，`SQLExecDirect``SQLFetch`调用`SQLNumResultCol`和`SQLMoreResults`。 `SQLCancel`可调用**HSTMT**。

## <a name="getdatabasename"></a>获取数据库名称

`SQLGetInfo SQL_DATABASE_NAME`将被调用。

## <a name="begintrans-committrans-rollback"></a>开始转换、提交转换、回滚

`SQLSetConnectOption SQL_AUTOCOMMIT`和`SQLTransact SQL_COMMIT`，如果发出事务请求，将调用**SQL_ROLLBACK**和**SQL_AUTOCOMMIT。**

## <a name="crecordsets"></a>C记录集

`SQLAllocStmt``SQLPrepare` `Requery` `SQLExecDirect` （对于`Open`更新操作）`SQLFreeStmt`必须支持。 `SQLExecute` `SQLNumResultCols`并将`SQLDescribeCol`调用不同时间设置的结果。

`SQLSetParam`广泛用于绑定参数数据和**DATA_AT_EXEC**功能。

`SQLBindCol`广泛用于将输出列数据存储位置与 ODBC 注册。

两`SQLGetData`个调用用于检索**SQL_LONG_VARCHAR**和**SQL_LONG_VARBINARY**数据。 第一个调用尝试通过使用 cbMaxValue 0 调用`SQLGetData`，但使用有效的 pcbValue 来查找列值的总长度。 如果 pcbValue 持有**SQL_NO_TOTAL**，则引发异常。 否则，将分配**HGLOBAL，** 并调用`SQLGetData`另一个调用来检索整个结果。

## <a name="updating"></a>正在更新

如果请求悲观锁定，`SQLGetInfo SQL_LOCK_TYPES`将查询。 如果**不支持SQL_LCK_EXCLUSIVE，** 将引发异常。

`CRecordset`尝试更新 （**快照**或**动态集**） 将导致分配第二个**HSTMT。** 对于不支持第二个**HSTMT**的驱动程序，光标库将模拟此功能。 遗憾的是，这有时可能意味着在处理第二个**HSTMT**请求之前强制第一个**HSTMT**上的当前查询完成。

`SQLFreeStmt SQL_CLOSE`**和SQL_RESET_PARAMS，** 将在`SQLGetCursorName`更新操作期间调用。

如果**输出列**中有**CLongBinarys，** 则必须支持 ODBC **DATA_AT_EXEC**功能。 这包括从`SQLExecDirect`返回`SQLParamData`**SQL_NEED_DATA** `SQLPutData`和 。

`SQLRowCount`在执行后调用，以验证 只有`SQLExecDirect`1 条记录由 更新。

## <a name="forwardonly-cursors"></a>仅转发光标

操作`SQLFetch`仅是必需的`Move`。 请注意，**仅转发**游标不支持更新。

## <a name="snapshot-cursors"></a>快照光标

快照功能需要`SQLExtendedFetch`支持。 如上所述，ODBC 游标库将检测驱动程序何时不支持`SQLExtendedFetch`，并本身提供必要的支持。

`SQLGetInfo`**，SQL_SCROLL_OPTIONS**必须支持**SQL_SO_STATIC**。

## <a name="dynaset-cursors"></a>发电机光标

以下是打开动态集所需的最低支持：

`SQLGetInfo`**，SQL_ODBC_VER**必须返回>"01"。

`SQLGetInfo`**，SQL_SCROLL_OPTIONS**必须支持**SQL_SO_KEYSET_DRIVEN。**

`SQLGetInfo`**，SQL_ROW_UPDATES**必须返回"Y"。

`SQLGetInfo`**，SQL_POSITIONED_UPDATES**必须支持**SQL_PS_POSITIONED_DELETE**和**SQL_PS_POSITIONED_UPDATE。**

此外，如果请求悲观锁定，将调用`SQLSetPos`irow 1、fRefresh FALSE 和 fLock **SQL_LCK_EXCLUSIVE。**

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
