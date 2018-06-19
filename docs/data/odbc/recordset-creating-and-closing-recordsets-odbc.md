---
title: 记录集： 创建和关闭记录集 (ODBC) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bbf020e12151e666aa8f88098865b1624403b828
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092097"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>记录集：创建和关闭记录集 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 若要使用记录集，构造一个记录集对象，然后调用其**打开**成员函数来运行记录集的查询和选择的记录。 当你完成使用该记录，请关闭并销毁对象。  
  
 本主题说明：  
  
-   [何时以及如何创建记录集对象](#_core_creating_recordsets_at_run_time)。  
  
-   [何时以及如何可以限定通过参数化、 筛选、 排序或锁定的记录集的行为](#_core_setting_recordset_options)。  
  
-   [何时以及如何关闭记录集对象](#_core_closing_a_recordset)。  
  
##  <a name="_core_creating_recordsets_at_run_time"></a> 在运行时创建记录集  
 你可以在程序中创建记录集对象之前，你通常编写应用程序特定的记录集类。 有关此预备步骤的详细信息，请参阅[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 当你需要从数据源选择记录时，请打开动态集或快照的对象。 要创建的对象类型取决于你需要在你的应用程序和 ODBC 驱动程序支持的数据。 有关详细信息，请参阅[动态集](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。  
  
#### <a name="to-open-a-recordset"></a>若要打开记录集  
  
1.  构造的对象你`CRecordset`-派生类。  
  
     您可以构造在堆上或函数的堆栈帧上的对象。  
  
2.  （可选） 修改默认记录集行为。 有关可用的选项，请参阅[设置记录集选项](#_core_setting_recordset_options)。  
  
3.  调用对象的[打开](../../mfc/reference/crecordset-class.md#open)成员函数。  
  
 在构造函数中，将传递指向的指针`CDatabase`对象或传递**NULL**使用一个临时数据库对象，该框架构造并打开基于返回的连接字符串[GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成员函数。 `CDatabase`对象可能已连接到数据源。  
  
 调用**打开**使用 SQL 来从数据源选择记录。 选择 （如果有） 的第一个记录是当前记录。 此记录的字段的值存储在记录集对象的字段数据成员。 如果选择了任何记录，同时`IsBOF`和`IsEOF`成员函数返回 0。  
  
 在你[打开](../../mfc/reference/crecordset-class.md#open)调用，你可以：  
  
-   指定记录集是动态集或快照。 默认情况下，作为快照打开记录集。 或者，你可以指定只进记录，这样仅向前滚动，一次一个记录集。  
  
     默认情况下，记录集使用中存储的默认类型`CRecordset`数据成员**m_nDefaultType**。 向导编写代码以初始化**m_nDefaultType**到向导中选择的记录集类型。 而不是接受该默认设置，您可以替换另一个记录集类型。  
  
-   指定要替换默认的 sql 语句的字符串**选择**记录集构造的语句。  
  
-   指定记录集是只读的还是仅限追加。 记录集允许完全更新默认情况下，但你可以仅添加新记录限制，或可以禁止所有更新。  
  
 下面的示例演示如何打开类的只读快照对象`CStudentSet`，应用程序特定的类：  
  
```  
// Construct the snapshot object  
CStudentSet rsStudent( NULL );  
// Set options if desired, then open the recordset  
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))  
    return FALSE;  
// Use the snapshot to operate on its records...  
```  
  
 调用后**打开**，使用成员函数和数据成员的对象使用的记录。 在某些情况下，你可能想要再次查询或刷新记录集以包括在数据源发生更改。 有关详细信息，请参阅[记录集： 再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。  
  
> [!TIP]
>  在开发过程中使用的连接字符串可能不是最终用户所需的连接字符串不同。 有关这方面通用化你的应用程序的建议，请参阅[数据源： 管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)。  
  
##  <a name="_core_setting_recordset_options"></a> 设置记录集选项  
 在构造记录集对象之后但在调用之前**打开**若要选择记录，你可能想要设置某些选项来控制记录集的行为。 对于所有记录集，您可以：  
  
-   指定[筛选器](../../data/odbc/recordset-filtering-records-odbc.md)若要将限制记录选择。  
  
-   指定[排序](../../data/odbc/recordset-sorting-records-odbc.md)的记录的顺序。  
  
-   指定[参数](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)让您可以选择使用获取，或在运行时计算的信息的记录。  
  
 如果条件正确，还可以设置以下选项：  
  
-   如果记录集是可更新，并支持锁定选项，指定[锁定](../../data/odbc/recordset-locking-records-odbc.md)用于更新的方法。  
  
> [!NOTE]
>  若要影响记录的选择，必须设置这些选项，然后才能调用**打开**成员函数。  
  
##  <a name="_core_closing_a_recordset"></a> 关闭记录集  
 完成记录后，必须释放类型，并释放其内存。  
  
#### <a name="to-close-a-recordset"></a>若要关闭记录集  
  
1.  调用其[关闭](../../mfc/reference/crecordset-class.md#close)成员函数。  
  
2.  记录集对象销毁。  
  
     如果声明的函数的堆栈帧上，当对象超出范围时对象将自动销毁。 否则，请使用**删除**运算符。  
  
 **关闭**释放记录集的**HSTMT**处理。 它不会销毁 c + + 对象。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)   
 [记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)