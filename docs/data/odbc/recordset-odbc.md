---
title: "记录集 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c5fc714b9c2ff0e1af679edbc3842b86d201fee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-odbc"></a>记录集 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 A [CRecordset](../../mfc/reference/crecordset-class.md)对象表示一组从数据源选择的记录。 记录可以来自：  
  
-   一个表。  
  
-   一个查询。  
  
-   一个可访问一个或多个表的存储的过程。  
  
 基于表的记录集的一个示例是"所有客户，"访问 Customer 表。 查询的一个示例是"Joe smith 的所有发票。" 基于存储过程 （有时称为预定义的查询） 的记录集的一个示例是"过期的帐户中，所有"的调用后端数据库中的存储的过程。 记录集可以加入两个或多个表从相同的数据源，但不是来自不同数据源的表。  
  
> [!NOTE]
>  有关记录集用派生类向导的信息，请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)和[数据库支持，MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)。  
  
> [!NOTE]
>  某些 ODBC 驱动程序支持数据库的视图。 在这个意义上的视图是最初创建与 SQL 的查询`CREATE VIEW`语句。 向导当前不支持视图，但是可能此支持的代码。  
  
##  <a name="_core_recordset_capabilities"></a>记录集功能  
 所有记录集对象共享的以下功能：  
  
-   如果数据源不是只读的则可以指定记录集为[可更新](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，[可追加](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，或只读的。 如果可更新记录集，你可以选择保守式或开放式[锁定](../../data/odbc/recordset-locking-records-odbc.md)方法，提供驱动程序提供适当的锁定支持。 如果数据源是只读的该记录集将是只读的。  
  
-   可以调用成员函数以[滚动](../../data/odbc/recordset-scrolling-odbc.md)通过选定的记录。  
  
-   你可以[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)来限制从这些可用选择哪些记录的记录。  
  
-   你可以[排序](../../data/odbc/recordset-sorting-records-odbc.md)按升序或降序，记录基于一个或多个列。  
  
-   你可以[参数化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)为限定在运行时的记录集选定的记录集。  
  
##  <a name="_core_snapshots_and_dynasets"></a>快照和动态集  
 有两种主要类型的记录集：[快照](../../data/odbc/snapshot.md)和[动态记录集](../../data/odbc/dynaset.md)。 类支持这两`CRecordset`。 每个共享的公共特性的所有记录集，但每个扩展自己专用的方式的常见功能。 快照提供了静态数据的视图，并且可用于报表和其他情况下，在其中您希望数据的视图在特定时间存在。 当你想要显示的记录集而无需再次查询或刷新记录集由其他用户所做的更新时，动态记录集非常有用。 快照和动态集可以是可更新或只读的。 反映记录添加或删除其他用户，通过调用[CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery)。  
  
 `CRecordset`此外允许两个其他类型的记录集： 动态记录集和只进的记录集。 动态记录集是类似于动态记录集;但是，动态记录集反映添加或删除而不调用任何记录`CRecordset::Requery`。 为此，动态记录集的相对上 DBMS，处理时间通常费用较高和许多的 ODBC 驱动程序不支持它们。 与此相反，仅向前的记录集提供不需要更新或向后滚动的记录集的数据访问的最有效方法。 例如，你可能使用只进的记录集数据在一个数据源之间迁移，其中只需通过在一个向前方向的数据移动。 若要使用只进的记录集，必须执行以下两个操作：  
  
-   传递选项**CRecordset::forwardOnly**作为`nOpenType`参数[打开](../../mfc/reference/crecordset-class.md#open)成员函数。  
  
-   指定**CRecordset::readOnly**中`dwOptions`参数**打开**。  
  
    > [!NOTE]
    >  有关动态集支持的 ODBC 驱动程序要求的信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)。 有关此版本的 Visual c + + 中包含的 ODBC 驱动程序的列表以及有关获取其他驱动程序的信息，请参阅[ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
##  <a name="_core_your_recordsets"></a>你的记录集  
 对于每个非重复表、 视图或你想要访问的存储的过程，您通常定义派生自的类`CRecordset`。 （例外情况是数据库联接，在其中一个记录集所表示的两个或多个表的列）。在派生的记录集类，你启用的记录字段交换 (RFX) 机制或批量记录字段交换 (Bulk RFX) 机制，它类似于对话框数据交换 (DDX) 机制。 RFX 和批量 RFX 简化数据源的数据的传输到记录集;RFX 此外将数据传输从记录集到数据源。 有关详细信息，请参阅[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)和[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 记录集对象访问你的所有选定的记录。 通过结合使用的多个所选记录滚动`CRecordset`成员函数，如`MoveNext`和`MovePrev`。 同时，记录集对象将表示只有一个选定的记录，当前记录。 可以通过声明与列的表或从数据库查询产生的记录相对应的类成员变量的记录集来检查当前记录的字段。 有关记录集数据成员的信息，请参阅[记录集： 体系结构 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)。  
  
 以下主题介绍使用记录集对象的详细信息。 按功能类别和自然浏览顺序，以便可以顺序阅读会列出的主题。  
  
### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>有关打开、 读取和关闭记录集的机制的主题  
  
-   [记录集：体系结构 (ODBC)](../../data/odbc/recordset-architecture-odbc.md)  
  
-   [记录集：声明表的类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)  
  
-   [记录集：创建和关闭记录集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)  
  
-   [记录集：滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)  
  
-   [记录集：书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)  
  
-   [记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)  
  
-   [记录集：对记录进行排序 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)  
  
-   [记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>有关修改记录集的技巧的主题  
  
-   [记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)  
  
-   [记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)  
  
-   [记录集：再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)  
  
### <a name="topics-about-somewhat-more-advanced-techniques"></a>有关某种程度上的主题更高级的技术  
  
-   [记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)  
  
-   [记录集：为预定义查询声明一个类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)  
  
-   [记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)  
  
-   [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)  
  
-   [记录集：处理大数据项 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)  
  
-   [记录集：获取 SUM 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)  
  
### <a name="topics-about-how-recordsets-work"></a>有关记录集的工作原理的主题  
  
-   [记录集：记录集如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)  
  
-   [记录集：记录集如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [事务 (ODBC)](../../data/odbc/transaction-odbc.md)