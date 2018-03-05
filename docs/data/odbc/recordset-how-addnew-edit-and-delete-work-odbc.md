---
title: "记录集： AddNew、 Edit 和 Delete 如何 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dbbf224797bd7d2eed2b085a6a7dd8eb1865de1c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明如何`AddNew`，**编辑**，和**删除**类的成员函数`CRecordset`工作。 涉及主题包括：  
  
-   [如何添加记录的工作机制](#_core_adding_a_record)  
  
-   [添加记录的可见性](#_core_visibility_of_added_records)  
  
-   [编辑记录的工作原理](#_core_editing_an_existing_record)  
  
-   [如何删除记录的工作机制](#_core_deleting_a_record)  
  
> [!NOTE]
>  本主题适用于派生自`CRecordset`中哪些批量行提取尚未实现。 如果你将批量行提取，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 作为补充，你可能想要读取[记录字段交换： RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)，用于描述 RFX 更新操作中的相应角色。  
  
##  <a name="_core_adding_a_record"></a>添加记录  

 将一条新记录添加到记录集涉及调用记录集的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成员函数，设置的值将新记录的字段数据成员，以及调用[更新](../../mfc/reference/crecordset-class.md#update)成员函数可以编写到数据源记录。  
  
 作为调用的前提条件`AddNew`，记录集必须具有尚未打开以只读方式。 `CanUpdate`和`CanAppend`成员函数让你能够确定这些条件。  
  
 当调用`AddNew`:  
  
-   编辑缓冲区中的记录被存储，因此可以还原其内容，如果将取消该操作。  
  
-   因此可以以更高版本中这些检测更改标记的字段数据成员。 字段数据成员也会标记清除 （未更改） 并将设置为 Null。  
  
 调用后`AddNew`、 编辑缓冲区表示新、 准备好空记录，以使用值填充。 若要执行此操作，手动应通过将分配给这些设置的值。 你可以指定字段的实际数据值，而不调用`SetFieldNull`指定 Null 值。  
  
 若要提交所做的更改，请调用**更新**。 当调用**更新**新记录：  
  
-   如果 ODBC 驱动程序支持**:: SQLSetPos** ODBC API 函数时，MFC 使用函数对数据源添加记录。 与**:: SQLSetPos**，MFC 可以更有效地地添加一条记录，因为它没有构造和处理的 SQL 语句。  
  
-   如果**:: SQLSetPos**不能使用，MFC 有如下：  
  
    1.  如果检测不到任何更改，**更新**不执行任何操作并返回 0。  
  
    2.  如果有更改，**更新**构造 SQL**插入**语句。 由所有已更新字段数据成员所表示的列中列出**插入**语句。 若要强制将包含一个列，请调用[SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty)成员函数：  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **更新**提交新记录-**插入**执行语句并将该记录是提交到数据源 （如果不是快照，该记录集） 上的表，除非在事务正在进行。  
  
    4.  已存储的记录将还原到编辑缓冲区。 之前的当前记录`AddNew`调用是当前再次而不管是否**插入**成功执行语句。  
  
    > [!TIP]
    >  一条新记录的完全控制，采用以下方法： 将所有字段，将具有值，然后显式设置将为 Null，调用任何字段的值设置`SetFieldNull`用一个指针指向字段并使用参数**TRUE** （默认值）。 如果你想要确保字段不写入数据源，调用`SetFieldDirty`用一个指针指向字段并使用参数**FALSE**，并且不会修改字段的值。 若要确定是否允许字段为 Null，调用`IsFieldNullable`。  
  
    > [!TIP]
    >  若要检测记录集数据成员更改值时，MFC 使用**PSEUDO_NULL**适合于每个可以存储在记录集中的数据类型的值。 如果你必须显式将字段设置为**PSEUDO_NULL**值和字段恰好已被标记为 Null，你还必须调用`SetFieldNull`，传递的第一个参数中的字段的地址和**FALSE**中第二个参数。  
  
##  <a name="_core_visibility_of_added_records"></a>添加记录的可见性  
 可见到记录集时添加的记录？ 已添加的记录有时显示，有时不可见，具体取决于以下两项操作：  
  
-   支持的驱动程序。  
  
-   框架可以充分利用。  
  
 如果 ODBC 驱动程序支持**:: SQLSetPos** ODBC API 函数时，MFC 使用函数添加的记录。 与**:: SQLSetPos**，添加记录都可见的任何可更新的 MFC 记录集。 若不支持该函数，添加记录不可见，必须调用**Requery**才能看到它们。 使用**:: SQLSetPos**来说也是更高效。  
  
##  <a name="_core_editing_an_existing_record"></a>编辑现有记录  
 编辑在记录集中的现有记录涉及到该记录，调用记录集的滚动[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数，设置的值将新记录的字段数据成员，以及调用[更新](../../mfc/reference/crecordset-class.md#update)成员函数以将更改的记录写入到数据源。  
  
 作为调用的前提条件**编辑**，记录集必须是可更新和上一条记录。 `CanUpdate`和`IsDeleted`成员函数让你能够确定这些条件。 当前记录还必须已尚未删除，且必须记录在会记录集 (同时`IsBOF`和`IsEOF`返回 0)。  
  
 当调用**编辑**，存储编辑缓冲区 （当前记录） 中的记录。 已存储的记录值更高版本用于检测是否已更改任何字段。  
  
 调用后**编辑**，编辑缓冲区仍表示当前记录，但现在已准备好接受对字段数据成员的更改。 若要更改的记录，手动设置你想要编辑的任何字段数据成员的值。 你可以指定字段的实际数据值，而不调用`SetFieldNull`指定 Null 值。 若要提交所做的更改，调用**更新**。  
  
> [!TIP]
>  若要获取外`AddNew`或**编辑**模式，请调用**移动**与参数**AFX_MOVE_REFRESH**。  
  
 作为调用的前提条件**更新**、 记录集不能为空，并且必须尚未删除当前记录。 `IsBOF``IsEOF`，和`IsDeleted`都应返回 0。  
  
 当调用**更新**的已编辑的记录：  
  
-   如果 ODBC 驱动程序支持**:: SQLSetPos** ODBC API 函数时，MFC 使用函数来更新数据源上的记录。 与**:: SQLSetPos**，驱动程序与相应的记录在服务器上，如果两个不同更新服务器上的记录将编辑缓冲区进行比较。 与**:: SQLSetPos**，MFC 可以高效地更新的记录，因为它没有构造和处理的 SQL 语句。  
  
     或  
  
-   如果**:: SQLSetPos**不能使用，MFC 有如下：  
  
    1.  如果进行不了任何更改，**更新**不执行任何操作并返回 0。  
  
    2.  如果有更改，**更新**构造 SQL**更新**语句。 中列出的列**更新**语句基于已更改的字段数据成员。  
  
    3.  **更新**提交所做的更改 — 执行**更新**语句-和记录更改对数据源，但不是提交的事务，如果正在进行中 (请参阅[事务： 执行中的事务记录集 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)事务如何影响更新有关的信息)。 ODBC 保留副本的记录，这样也会更改。  
  
    4.  与不同的过程`AddNew`、**编辑**过程不会还原已存储的记录。 已编辑的记录仍保持为当前记录。  
  
    > [!CAUTION]
    >  当你准备更新记录集通过调用**更新**，请注意你记录集包括所有列组成的表的主键 （或表或足够列上的任何唯一的列的所有唯一索引确定行）。 在某些情况下，该框架还可以使用仅选定记录集中的列来标识表中要更新的记录。 不包含所有必要的列，可能会在表中更新多个记录。 在这种情况下，框架会引发异常时调用**更新**。  
  
    > [!TIP]
    >  如果调用`AddNew`或**编辑**后又调用任一函数之前但在之前调用**更新**，编辑缓冲区刷新与存储的记录，并替换中的新建或编辑记录进度。 此行为提供了一种方法中止`AddNew`或**编辑**并开始一个新： 如果你确定记录正在进行了故障，只需调用**编辑**或`AddNew`试。  
  
##  <a name="_core_deleting_a_record"></a>删除记录  
 从记录集中删除一条记录包括滚动到该记录及调用记录集的[删除](../../mfc/reference/crecordset-class.md#delete)成员函数。 与不同`AddNew`和**编辑**，**删除**不需要匹配调用**更新**。  
  
 作为调用的前提条件**删除**，记录集必须可更新，并且它必须位于一条记录。 `CanUpdate`， `IsBOF`， `IsEOF`，和`IsDeleted`成员函数让你能够确定这些条件。  
  
 当调用**删除**:  
  
-   如果 ODBC 驱动程序支持**:: SQLSetPos** ODBC API 函数时，MFC 使用函数来删除数据源上的记录。 使用**:: SQLSetPos**通常比使用 SQL 更高效。  
  
     或  
  
-   如果**:: SQLSetPos**不能使用，MFC 有如下：  
  
    1.  编辑缓冲区中的当前记录不会备份作为 in`AddNew`和**编辑**。  
  
    2.  **删除**构造 SQL**删除**中删除记录的语句。  
  
         编辑缓冲区中的当前记录不会存储为在`AddNew`和**编辑**。  
  
    3.  **删除**提交删除-执行**删除**语句。 记录被标记为已删除数据源上并且该记录是快照，则在 ODBC。  
  
    4.  已删除的记录的值仍中的记录集的字段数据成员但 Null 和记录集的标记的字段数据成员`IsDeleted`成员函数将返回一个非零值。  
  
    > [!NOTE]
    >  删除的记录后, 应滚动到另一条记录来重新填充具有新记录的数据的编辑缓冲区。 它是错误调用**删除**再次或要调用**编辑**。  
  
 有关更新操作中使用的 SQL 语句的信息，请参阅[SQL](../../data/odbc/sql.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 有关更新的更多信息 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)