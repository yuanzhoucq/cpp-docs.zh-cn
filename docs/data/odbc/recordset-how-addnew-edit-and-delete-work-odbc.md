---
title: "记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddNew 方法"
  - "记录集中的数据 [C++]"
  - "ODBC 记录集 [C++], 添加记录"
  - "ODBC 记录集 [C++], 删除记录"
  - "ODBC 记录集 [C++], 编辑记录"
  - "记录编辑 [C++], 在记录集中"
  - "记录 [C++], 添加"
  - "记录 [C++], 在记录集中删除"
  - "记录 [C++], 编辑"
  - "记录 [C++], 更新"
  - "记录集 [C++], 添加记录"
  - "记录集 [C++], 删除记录"
  - "记录集 [C++], 编辑记录"
  - "记录集 [C++], 更新"
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本主题解释 `CRecordset` 类的 `AddNew`、**Edit** 和 **Delete** 成员函数的工作机制。  所涵盖的主题包括：  
  
-   [添加记录的工作机制](#_core_adding_a_record)  
  
-   [已添加记录的可见性](#_core_visibility_of_added_records)  
  
-   [编辑记录的工作机制](#_core_editing_an_existing_record)  
  
-   [删除记录的工作机制](#_core_deleting_a_record)  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果正在使用批量取行，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 作为补充，您可能需要阅读 [记录字段交换：RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)，该主题描述了 RFX 在更新操作中的相应作用。  
  
##  <a name="_core_adding_a_record"></a> 添加记录  
 向记录集添加新记录包括以下操作：调用记录集的 [AddNew](../Topic/CRecordset::AddNew.md) 成员函数，设置新记录的字段数据成员的值，以及调用将记录写入数据源的 [Update](../Topic/CRecordset::Update.md) 成员函数。  
  
 作为调用 `AddNew` 的前提条件，一定不能以只读方式打开记录集。  使用 `CanUpdate` 和 `CanAppend` 成员函数可确定这些条件。  
  
 调用 `AddNew` 时：  
  
-   编辑缓冲区中的记录被存储，因此如果取消操作，则可以还原其内容。  
  
-   字段数据成员已做标记，因此以后可检测到其中发生的更改。  字段数据成员同时被标记为“无变动”（未更改）并设置为 Null。  
  
 在您调用了 `AddNew` 之后，编辑缓冲区表示一个新的空记录随时供填写值之用。  若要完成该操作，可通过为它们赋值来手动设置值。  可调用 `SetFieldNull` 将值指定为 Null，而不必指定字段的实际数据值。  
  
 若要提交更改，请调用 **Update**。  为新记录调用 **Update** 时：  
  
-   如果 ODBC 驱动程序支持 **::SQLSetPos** ODBC API 函数，则 MFC 使用该函数在数据源中添加记录。  使用 **::SQLSetPos**，MFC 能够更有效的添加记录，因为 MFC 不必构造和处理 SQL 语句。  
  
-   如果无法使用 **::SQLSetPos**，MFC 会执行以下操作：  
  
    1.  如果未检测到更改，则 **Update** 不进行任何操作并返回 0。  
  
    2.  如果发生更改，则 **Update** 构造 SQL **INSERT** 语句。  **INSERT** 语句中将列出由所有已更新字段数据成员所表示的列。  若要强制包含某列，请调用 [SetFieldDirty](../Topic/CRecordset::SetFieldDirty.md) 成员函数：  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **Update** 提交新记录，即除非正在进行事务操作，否则将执行 **INSERT** 语句并将该记录提交到数据源（若不是快照，则为记录集）中的表。  
  
    4.  已存储的记录被还原到编辑缓冲区。  不论 **INSERT** 语句是否成功执行，`AddNew` 调用之前的当前记录都再次成为当前记录。  
  
    > [!TIP]
    >  为完全控制新记录，请采取以下方法：设置将具有值的所有字段的值，然后通过用指向字段及参数 **TRUE**（默认值）的指针调用 `SetFieldNull` 来显式设置将保持为 Null 的所有字段。  如果要确保字段不被写入数据源，则用指向该字段及参数 **FALSE** 的指针调用 `SetFieldDirty`，且不要修改字段的值。  若要确定字段是否允许为 Null，请调用 `IsFieldNullable`。  
  
    > [!TIP]
    >  为检测记录集数据成员更改值的时间，MFC 使用与存储在记录集中的每个数据类型相对应的 **PSEUDO\_NULL** 值。  如果必须将某字段显式设置为 **PSEUDO\_NULL** 值而该字段恰好已被标记为 Null，则仍必须调用 `SetFieldNull`，在第一个参数中传递字段的地址并在第二个参数中传递 **FALSE**。  
  
##  <a name="_core_visibility_of_added_records"></a> 已添加记录的可见性  
 已添加记录何时在记录集中可见？  已添加记录有时可见，有时不可见，具体取决于两点：  
  
-   驱动程序的能力。  
  
-   框架可利用的功能。  
  
 如果 ODBC 驱动程序支持 **::SQLSetPos** ODBC API 函数，则 MFC 使用该函数添加记录。  若使用 **::SQLSetPos**，则已添加记录对于任何可更新的 MFC 记录集都可见。  若不支持该函数，则已添加记录不可见，必须调用 **Requery** 才能看到它们。  使用 **::SQLSetPos** 会更有效。  
  
##  <a name="_core_editing_an_existing_record"></a> 编辑现有记录  
 编辑记录集中的现有记录包括以下操作：滚动到该记录，调用记录集的 [Edit](../Topic/CRecordset::Edit.md) 成员函数，设置新记录的字段数据成员值，以及调用将已更改的记录写入数据源的 [Update](../Topic/CRecordset::Update.md) 成员函数。  
  
 作为调用 **Edit** 的前提条件，记录集必须可更新并且有记录。  使用 `CanUpdate` 和 `IsDeleted` 成员函数可确定这些条件。  并且当前记录一定不能已被删除，且记录集中必须存在记录（`IsBOF` 和 `IsEOF` 都返回 0）。  
  
 调用 **Edit** 时，编辑缓冲区中的记录（当前记录）被存储。  已存储的记录的值将来用于检测是否有字段发生更改。  
  
 调用 **Edit** 之后，编辑缓冲区仍表示当前记录，但现在可以接受对字段数据成员的更改。  若要更改记录，请手动设置要编辑的所有字段数据成员的值。  可调用 `SetFieldNull` 将值指定为 Null，而不必指定字段的实际数据值。  若要提交更改，请调用 **Update**。  
  
> [!TIP]
>  若要退出 `AddNew` 或 **Edit** 模式，请使用参数 **AFX\_MOVE\_REFRESH** 调用 **Move**。  
  
 作为调用 **Update** 的前提条件，记录集一定不能为空且当前记录一定不能已被删除。  `IsBOF`、`IsEOF` 与 `IsDeleted` 都应返回 0。  
  
 当为已编辑的记录调用 **Update** 时：  
  
-   如果 ODBC 驱动程序支持 **::SQLSetPos** ODBC API 函数，则 MFC 使用该函数更新数据源中的记录。  驱动程序使用 **::SQLSetPos** 将编辑缓冲区与服务器上相应的记录进行比较，如果两者不同则更新服务器上的记录。  使用 **::SQLSetPos**，MFC 能够更有效地更新记录，因为它不必构造和处理 SQL 语句。  
  
     \- 或 \-  
  
-   如果无法使用 **::SQLSetPos**，MFC 会执行以下操作：  
  
    1.  如果未发生更改，则 **Update** 不进行任何操作并返回 0。  
  
    2.  如果发生更改，则 **Update** 构造 SQL **UPDATE** 语句。  **UPDATE** 语句中列出的列基于已发生更改的字段数据成员。  
  
    3.  **Update** 提交更改，即执行 **UPDATE** 语句并且记录在数据源中发生更改，但如果此时正在处理事务，则不提交记录（有关事务如何影响更新的信息，请参见 [事务：在记录集中执行事务 \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)）。  ODBC 保留记录的副本，该副本也发生更改。  
  
    4.  与 `AddNew` 的进程不同，**Edit** 进程不还原已存储的记录。  已编辑的记录仍保持为当前记录。  
  
    > [!CAUTION]
    >  当准备通过调用 **Update** 更新记录集时，请注意记录集包括组成表主键的所有列（或表上任何唯一索引的列，或可唯一标识行的足够多的列）。  某些情况下，框架只能使用记录集中选定用来标识表中要更新的记录的列。  若没有全部所需的列，表中的多项记录可能会更新。  在此情况下，调用 **Update** 时框架将引发异常。  
  
    > [!TIP]
    >  如果在调用 **Update** 之前，在以前已调用过 `AddNew` 或 **Edit** 后又调用两者之一，则编辑缓冲区由已存储的记录刷新，替换正在进行中的新记录或已编辑的记录。  这个行为提供了中止 `AddNew` 或 **Edit** 并开始新记录的方法：如果您确定进行中的记录存在错误，只需再次调用 **Edit** 或 `AddNew` 即可。  
  
##  <a name="_core_deleting_a_record"></a> 删除记录  
 从记录集中删除记录包括滚动到该记录及调用记录集的 [Delete](../Topic/CRecordset::Delete.md) 成员函数。  与 `AddNew` 和 **Edit** 不同，**Delete** 不要求对 **Update** 的匹配调用。  
  
 作为调用 **Delete** 的前提条件，记录集必须可更新并且有记录。  通过 `CanUpdate`、`IsBOF`、`IsEOF` 及 `IsDeleted` 成员函数可确定这些条件。  
  
 调用 **Delete** 时：  
  
-   如果 ODBC 驱动程序支持 **::SQLSetPos** ODBC API 函数，则 MFC 使用该函数删除数据源中的记录。  使用 **::SQLSetPos** 通常比使用 SQL 更有效。  
  
     \- 或 \-  
  
-   如果无法使用 **::SQLSetPos**，MFC 会执行以下操作：  
  
    1.  编辑缓冲区中的当前记录不像 `AddNew` 与 **Edit** 中的记录那样被备份。  
  
    2.  **Delete** 构造一个 SQL **DELETE** 语句以移除记录。  
  
         编辑缓冲区中的当前记录不像 `AddNew` 与 **Edit** 中的记录那样被存储。  
  
    3.  **Delete** 提交删除，即执行 **DELETE** 语句。  记录在数据源中（如果记录为快照，则在 ODBC 中）被标记为已删除。  
  
    4.  已删除记录的值仍位于记录集的字段数据成员中，但字段数据成员被标记为 Null 且记录集的 `IsDeleted` 成员函数将返回一个非零值。  
  
    > [!NOTE]
    >  删除记录之后，应滚动到另一个记录以用新记录的数据再次填充编辑缓冲区。  再次调用 **Delete** 或调用 **Edit** 是错误的。  
  
 有关更新操作中使用的 SQL 语句的信息，请参见 [SQL](../../data/odbc/sql.md)。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：有关更新的更多信息 \(ODBC\)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)