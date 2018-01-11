---
title: "记录字段交换： RFX 的工作方式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5eac97bb87103bd72dfd721515baf58324fc851f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-how-rfx-works"></a>记录字段交换：RFX 的工作方式
本主题介绍的 RFX 过程。 这是一个高级主题，包括：  
  
-   [RFX 和记录集](#_core_rfx_and_the_recordset)  
  
-   [RFX 过程](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  本主题适用于从派生的类`CRecordset`中哪些批量行提取尚未实现。 如果你将批量行提取，实现批量记录字段交换 (Bulk RFX)。 批量 RFX 等同于 RFX。 若要了解的差别，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_rfx_and_the_recordset"></a>RFX 和记录集  
 记录集对象的字段数据成员，合起来看，构成一个编辑缓冲区，保持一条记录所选的列。 当记录集首次打开时，并将读取的第一个记录时，RFX （关联） 每个选定列绑定到相应的字段数据成员的地址。 RFX 当记录集更新记录时，调用 ODBC API 函数来发送 SQL**更新**或**插入**于驱动程序的语句。 RFX 使用的字段数据成员及其知识来指定要写入的列。  
  
 框架编辑缓冲区在备份某些阶段，因此它可以在必要时还原其内容。 RFX 备份编辑缓冲区，然后再添加一个新的记录和之前编辑现有记录。 它将在某些情况下，例如，编辑缓冲区还原后**更新**调用以下`AddNew`。 如果终止新更改的编辑缓冲区，例如，将移动到另一条记录之前调用，将不会还原编辑缓冲区**更新**。  
  
 除了交换的数据源和记录集的字段数据成员之间的数据，RFX 管理绑定参数。 当打开记录集时，任何参数数据成员将绑定顺序排列"？"中的 SQL 语句的占位符，`CRecordset::Open`构造。 有关详细信息，请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
 记录集类的重写`DoFieldExchange`执行所有工作，在两个方向移动数据。 对话框数据交换 (DDX)，如 RFX 需要有关您的类数据成员的信息。 该向导通过编写的记录集特定的实现提供所需的信息`DoFieldExchange`为你，在基于的字段数据成员的名称和数据类型，指定使用向导。  
  
##  <a name="_core_the_record_field_exchange_process"></a>记录字段交换过程  
 本部分介绍 RFX 事件的顺序，随着打开记录集对象以及你添加、 更新和删除记录。 表[序列的 RFX 操作期间记录集打开](#_core_sequence_of_rfx_operations_during_recordset_open)和表[滚动过程中 RFX 操作的序列](#_core_sequence_of_rfx_operations_during_scrolling)在本主题演示该过程作为 RFX 进程**移动**命令，在记录集，RFX 管理更新。 这些过程， [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)调用以执行许多不同的操作。 **M_nOperation**数据成员的[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象确定请求的操作。 你可能会发现有助于读取[记录集： 如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)在阅读本材料之前。  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX： 初始绑定的列和参数  
 以下 RFX 活动按所示，当调用记录集对象的顺序发生[打开](../../mfc/reference/crecordset-class.md#open)成员函数：  
  
-   如果记录集具有参数数据成员，框架将调用`DoFieldExchange`将参数绑定到记录集的 SQL 语句字符串中的参数占位符。 在中找到的数据类型相关的表示形式参数的值用于每个占位符**选择**语句。 准备 SQL 语句之后但在执行之前，将发生这种情况。 有关语句准备的信息，请参阅**:: SQLPrepare** ODBC 中的函数*程序员参考*。  
  
-   框架调用`DoFieldExchange`第二次以将所选列的值绑定到记录集内的相应字段数据成员。 这将为编辑缓冲区包含第一条记录的列确定记录集对象。  
  
-   记录集执行 SQL 语句，而数据源选择第一条记录。 记录的列都会加载到记录集的字段数据成员。  
  
 当你打开记录集时下, 表显示 RFX 操作的序列。  
  
### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>记录集打开期间 RFX 操作的顺序  
  
|您的操作|DoFieldExchange 操作|数据库/SQL 操作|  
|--------------------|-------------------------------|-----------------------------|  
|1.打开记录集。|||  
||2.生成 SQL 语句。||  
|||3.发送 SQL。|  
||4.将绑定的参数数据成员。||  
||5.绑定到列的字段数据成员。||  
|||6.ODBC 移动且填充的数据。|  
||7.C + + 中修复数据。||  
  
 记录集使用 ODBC 的准备好的执行以允许快速再次查询，使用相同的 SQL 语句。 准备好的执行有关的详细信息，请参阅 ODBC SDK*程序员参考*MSDN 库中。  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a>RFX： 滚动  
 你从一个记录滚动到另一个时，框架将调用`DoFieldExchange`以替换以前存储在具有新记录的值的字段数据成员的值。  
  
 当用户将从一个记录到另一个记录下, 表显示 RFX 操作的序列。  
  
### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a>序列的过程中滚动 RFX 操作  
  
|您的操作|DoFieldExchange 操作|数据库/SQL 操作|  
|--------------------|-------------------------------|-----------------------------|  
|1.调用`MoveNext`或其他移动函数之一。|||  
|||2.ODBC 移动且填充的数据。|  
||3.C + + 中修复数据。||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX： 添加新记录和编辑现有记录  
 如果您添加一条新记录，记录集进行操作作为编辑缓冲区以生成新的记录的内容。 与添加记录，编辑记录涉及更改的记录集的字段数据成员的值。 RFX 角度来看，从序列如下所示：  
  
1.  对记录集的调用[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数会导致 RFX 来存储当前的编辑缓冲区，因此可以稍后能还原。  
  
2.  `AddNew`或**编辑**准备编辑缓冲区中的字段，以便 RFX 可以检测已更改的字段数据成员。  
  
     因为一条新记录不具有任何以前的值进行比较，新的`AddNew`设置到每个字段数据成员的值**PSEUDO_NULL**值。 以后，当你调用**更新**，每个数据成员的值与进行比较的 RFX **PSEUDO_NULL**值。 如果没有区别，已设置的数据成员。 (**PSEUDO_NULL**不具有 Null 值 true 的记录列相同也不是任何一种方法与 c + + 相同**NULL**。)  
  
     与不同**更新**寻求`AddNew`、**更新**寻求**编辑**比较更新值使用以前存储的值，而不是使用**PSEUDO_NULL**。 差异在于`AddNew`没有以前存储的值进行比较。  
  
3.  你想要编辑其值或你想为一条新记录填入，直接设置字段数据成员的值。 这可以包括调用`SetFieldNull`。  
  
4.  对调用[更新](../../mfc/reference/crecordset-class.md#update)检查已更改的字段数据成员，如步骤 2 中所述 (请参阅表[滚动过程中 RFX 操作的序列](#_core_sequence_of_rfx_operations_during_scrolling))。 如果都未发生更改，**更新**返回 0。 如果更改了某些字段数据成员，**更新**准备并执行 SQL**插入**包含记录中的所有更新字段的值的语句。  
  
5.  有关`AddNew`，**更新**通过还原以前存储的值之前的当前的记录到结束`AddNew`调用。 有关**编辑**，新的已编辑值保持不变。  
  
 下表显示 RFX 操作的序列时添加一条新记录或编辑现有记录。  
  
### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>序列的过程中 AddNew 和编辑 RFX 操作  
  
|您的操作|DoFieldExchange 操作|数据库/SQL 操作|  
|--------------------|-------------------------------|-----------------------------|  
|1.调用`AddNew`或**编辑**。|||  
||2.备份编辑缓冲区。||  
||3.有关`AddNew`、 将标记为"清理"的字段数据成员和 Null。||  
|4.将值分配到记录集字段数据成员。|||  
|5.调用**更新**。|||  
||6.检查已更改的字段。||  
||7.生成 SQL**插入**语句`AddNew`或**更新**语句**编辑**。||  
|||8.发送 SQL。|  
||9.有关`AddNew`，将编辑缓冲区还原为其备份的内容。 有关**编辑**，删除备份。||  
  
### <a name="rfx-deleting-existing-records"></a>RFX： 删除现有记录  
 RFX 时删除记录时，将所有字段都设置为**NULL**提醒一下，删除该记录，你必须将其移走。 不需要任何其他 RFX 序列信息。  
  
## <a name="see-also"></a>请参阅  
 [记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [宏、 全局函数和全局变量](../../mfc/reference/mfc-macros-and-globals.md)  
 [CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)