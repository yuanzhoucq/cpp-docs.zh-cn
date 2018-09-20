---
title: TN068： 使用 Microsoft Access 7 ODBC 驱动程序执行事务 |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 4006ee6953342fd55b644eeb2a8e8f30c1d80285
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395838"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068：使用 Microsoft Access 7 ODBC 驱动程序执行事务

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明介绍如何使用 MFC ODBC 数据库类和 Microsoft ODBC 桌面驱动程序软件包版本 3.0 中包括的 Microsoft 访问 7.0 ODBC 驱动程序时执行的事务。

## <a name="overview"></a>概述

如果数据库应用程序执行事务时，您必须小心以调用`CDatabase::BeginTrans`和`CRecordset::Open`在应用程序中正确的顺序。 Microsoft 访问 7.0 驱动程序将使用 Microsoft Jet 数据库引擎和 Jet 需要你的应用程序不开始已打开的游标的任何数据库上的事务。 有关 MFC ODBC 数据库类中，打开的游标相当于一种开放`CRecordset`对象。

如果您打开记录集之前调用`BeginTrans`，您可能看不到任何错误消息。 但是，任何记录集更新之后调用成为永久你应用程序利用`CRecordset::Update`，并更新将不会回滚通过调用`Rollback`。 若要避免此问题，必须调用`BeginTrans`第一个，然后打开记录集。

MFC 检查游标提交和回滚行为的驱动程序功能。 类`CDatabase`提供了两个成员函数，`GetCursorCommitBehavior`并`GetCursorRollbackBehavior`，以确定在你打开的任何事务的效果`CRecordset`对象。 对于 Microsoft Access 7.0 ODBC 驱动程序，这些成员函数返回`SQL_CB_CLOSE`因为 Access 驱动程序不支持游标保留。 因此，您必须调用`CRecordset::Requery`以下`CommitTrans`或`Rollback`操作。

当你需要一个接一个执行多个事务时，不能调用`Requery`后第一个事务，然后再启动下一个。 您必须关闭记录集在下一步对调用之前`BeginTrans`即可满足 Jet 的要求。 此技术说明介绍了处理这种情况下的两个方法：

- 每轮之后关闭 recordset`CommitTrans`或`Rollback`操作。

- 使用 ODBC API 函数`SQLFreeStmt`。

## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>每个 CommitTrans 或回滚操作后关闭记录集

在开始之前事务，请确保记录集对象已关闭。 在调用`BeginTrans`，调用记录集的`Open`成员函数。 调用后立即关闭记录集`CommitTrans`或`Rollback`。 请注意反复打开和关闭记录集可能会降低应用程序的性能。

## <a name="using-sqlfreestmt"></a>使用 SQLFreeStmt

您还可以使用 ODBC API 函数`SQLFreeStmt`以显式晚于结束事务时关闭游标。 若要启动另一个事务，调用`BeginTrans`跟`CRecordset::Requery`。 调用时`SQLFreeStmt`，则必须指定记录集的 HSTMT 作为第一个参数和*SQL_CLOSE*第二个参数。 此方法是比关闭和打开的每个事务开始时记录集。 下面的代码演示如何实现这种方法：

```cpp
CMyDatabase db;
db.Open("MYDATASOURCE");
CMyRecordset rs(&db);

// start transaction 1 and
// open the recordset
db.BeginTrans();
rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans(); // or Rollback()

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

另一种方法来实现这种方法是编写一个新的函数`RequeryWithBeginTrans`，可以调用之后，要开始下一个事务提交或回滚的第一个。 若要编写此类函数，请执行以下步骤操作：

1. 复制的代码`CRecordset::Requery( )`到新函数。

2. 将以下行添加到在调用后立即`SQLFreeStmt`:

   `m_pDatabase->BeginTrans( );`

现在可以调用之间的事务的每个对此函数：

```cpp
// start transaction 1 and
// open the recordset
db.BeginTrans();

rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans();   // or Rollback()

// close the cursor, start new transaction,
// and get the result set
rs.RequeryWithBeginTrans();

// manipulate data

// end transaction 2
db.CommitTrans();   // or Rollback()
```

> [!NOTE]
> 不要使用此方法，如果您需要更改的记录集成员变量*m_strFilter*或*m_strSort*之间的事务。 在这种情况下，应在每个后关闭记录集`CommitTrans`或`Rollback`操作。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
