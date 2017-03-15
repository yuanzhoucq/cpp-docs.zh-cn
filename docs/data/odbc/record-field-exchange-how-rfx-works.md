---
title: "记录字段交换：RFX 的工作方式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据绑定 [C++], DFX"
  - "ODBC [C++], RFX"
  - "记录编辑 [C++], 使用 RFX"
  - "RFX (ODBC) [C++], 绑定字段和参数"
  - "RFX (ODBC) [C++], 更新记录集内的数据"
  - "滚动 [C++]"
  - "滚动 [C++], RFX"
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 记录字段交换：RFX 的工作方式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明 RFX 进程。  这是一个高级主题，包括：  
  
-   [RFX 和记录集](#_core_rfx_and_the_recordset)  
  
-   [RFX 进程](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的类，这些类中尚未实现批量取行。  如果使用的是批量取行，则实现批量记录字段交换 \(Bulk RFX\)。  Bulk RFX 与 RFX 类似。  若要了解其中的差别，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_rfx_and_the_recordset"></a> RFX 和记录集  
 将记录集对象的字段数据成员集合在一起组成一个编辑缓冲区，保持一条记录的选定列。  当记录集第一次打开并将读取第一个记录时，RFX 将每个选定列绑定（关联）到适当的字段数据成员的地址。  当记录集更新记录时，RFX 调用 ODBC API 函数以将 SQL **UPDATE** 或 **INSERT** 语句发送到驱动程序。  RFX 使用其有关字段数据成员的知识来指定要写的列。  
  
 框架在某些阶段备份编辑缓冲区，因此必要时它能够还原其内容。  RFX 在添加新记录之前和编辑现有记录之前备份编辑缓冲区。  某些情况下，例如紧接 `AddNew` 的 **Update** 调用之后，RFX 还原编辑缓冲区。  如果终止新更改的编辑缓冲区（例如，在调用 **Update** 之前移动到另一个记录），则编辑缓冲区不还原。  
  
 除了在数据源和记录集的字段数据成员之间交换数据以外，RFX 还管理绑定参数。  当记录集打开时，所有参数数据成员都按照 `CRecordset::Open` 构造的 SQL 语句中“？”占位符的顺序进行绑定。  有关更多信息，请参见[记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
 您的记录集类对 `DoFieldExchange` 的重写完成所有工作：双向移动数据。  与对话框数据交换 \(DDX\) 一样，RFX 也需要有关类的数据成员的信息。  基于您用向导指定的字段数据成员名称和数据类型，向导将编写记录集特定的 `DoFieldExchange` 实现，从而为您提供必要的信息。  
  
##  <a name="_core_the_record_field_exchange_process"></a> 记录字段交换过程  
 本节描述打开记录集对象时以及添加、更新和删除记录时 RFX 事件的顺序。  本主题中的[记录集打开过程中 RFX 操作的顺序](#_core_sequence_of_rfx_operations_during_recordset_open)表和[滚动过程中 RFX 操作的顺序](#_core_sequence_of_rfx_operations_during_scrolling)表显示的过程有：RFX 处理记录集中的“移动”命令时的过程，RFX 管理更新时的过程。  在这些过程中，将调用 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 来执行多种不同的操作。  [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 对象的 **m\_nOperation** 数据成员确定所请求的操作。  您会发现在阅读本资料之前先阅读[记录集：记录集如何选择记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) 和[记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 很有帮助。  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX：列和参数的初始绑定  
 当调用记录集对象的 [Open](../Topic/CRecordset::Open.md) 成员函数时，按显示的顺序发生下列 RFX 活动：  
  
-   如果记录集含有参数数据成员，则框架调用 `DoFieldExchange` 将参数绑定到记录集的 SQL 语句字符串中的参数占位符。  参数值的与数据类型相关的表示形式用于在 **SELECT** 语句中找到的每个占位符。  这在 SQL 语句准备完毕但尚未执行时发生。  有关语句准备的信息，请参见 ODBC Programmer's Reference（ODBC 程序员参考）中的 **::SQLPrepare** 函数。  
  
-   框架再次调用 `DoFieldExchange` 将选定列的值绑定到记录集中的相应字段数据成员。  此操作将该记录集对象设立为编辑缓冲区（包含第一条记录的列）。  
  
-   记录集执行 SQL 语句，而数据源选择第一条记录。  该记录的列被加载到记录集的字段数据成员中。  
  
 下表显示了打开记录集时 RFX 的操作顺序。  
  
### 记录集打开过程中 RFX 操作的顺序  
  
|您的操作|DoFieldExchange 操作|数据库\/SQL 的操作|  
|----------|------------------------|------------------|  
|1.  打开记录集。|||  
||2.  生成 SQL 语句。||  
|||3.  发送 SQL。|  
||4.  绑定参数数据成员。||  
||5.  将字段数据成员绑定到列。||  
|||6.  ODBC 执行移动并填写该数据。|  
||7.  修复 C\+\+ 数据。||  
  
 记录集使用 ODBC 的准备好的执行，从而允许用同一 SQL 语句进行快速的再次查询。  有关准备好的执行的更多信息，请参见 MSDN Library 中的 ODBC SDK *Programmer's Reference*（ODBC SDK 程序员参考）。  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX：滚动  
 当从一个记录滚动到另一个记录时，框架调用 `DoFieldExchange` 以新记录的值替换以前存储在字段数据成员中的值。  
  
 下表显示了用户在记录间移动时 RFX 操作的顺序。  
  
### 滚动过程中 RFX 操作的顺序  
  
|您的操作|DoFieldExchange 操作|数据库\/SQL 的操作|  
|----------|------------------------|------------------|  
|1.  调用 `MoveNext` 或其他 Move 函数之一。|||  
|||2.  ODBC 执行移动并填写该数据。|  
||3.  修复 C\+\+ 数据。||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX：添加新记录和编辑现有记录  
 如果添加新记录，记录集会作为编辑缓冲区运行以生成新记录的内容。  与添加记录一样，编辑记录也涉及更改记录集的字段数据成员的值。  从 RFX 的角度看，顺序如下：  
  
1.  调用记录集的 [AddNew](../Topic/CRecordset::AddNew.md) 或 [Edit](../Topic/CRecordset::Edit.md) 成员函数会使 RFX 存储当前编辑缓冲区，以便该缓冲区以后可以还原。  
  
2.  `AddNew` 或 **Edit** 准备编辑缓冲区中的字段，以便 RFX 可检测到已更改的字段数据成员。  
  
     由于新记录中没有用来与新值进行比较的以前的值，因此 `AddNew` 将每个字段数据成员的值设置为 **PSEUDO\_NULL** 值。  以后，当您调用 **Update** 时，RFX 将每个数据成员的值与 **PSEUDO\_NULL** 值进行比较。  如果存在差异，说明已设置数据成员。（**PSEUDO\_NULL** 不同于带有真正的 Null 值的记录列，而且这二者也都不同于 C\+\+ **NULL**。）  
  
     与 `AddNew` 的 **Update** 调用不同的是，**Edit** 的 **Update** 调用使用先前存储的值而不是 **PSEUDO\_NULL** 与更新后的值进行比较。  差异在于 `AddNew` 没有先前已存储的用于比较的值。  
  
3.  您直接设置要编辑其值或用来填充新记录的字段数据成员的值。  这可以包括调用 `SetFieldNull`。  
  
4.  您调用 [Update](../Topic/CRecordset::Update.md) 检查已更改的字段数据成员，详见步骤 2（请参见表[滚动过程中 RFX 操作的顺序](#_core_sequence_of_rfx_operations_during_scrolling)）。  如果没有任何更改，则 **Update** 返回 0。  如果某些字段数据成员已更改，则 **Update** 准备并执行包含记录中所有已更新字段的值的 SQL **INSERT** 语句。  
  
5.  对于 `AddNew`，**Update** 通过恢复上次存储的记录（该记录在调用 `AddNew` 前为当前记录）的值以结束整个过程。  对于 **Edit**，新的已编辑值仍留在原处。  
  
 下表显示了当添加新记录或编辑现有记录时 RFX 操作的顺序。  
  
### AddNew 和 Edit 过程中 RFX 操作的顺序  
  
|您的操作|DoFieldExchange 操作|数据库\/SQL 的操作|  
|----------|------------------------|------------------|  
|1.  调用 `AddNew` 或 **Edit**。|||  
||2.  备份编辑缓冲区。||  
||3.  对于 `AddNew`，将字段数据成员标记为“无变动”和 Null。||  
|4.  为记录集字段数据成员赋值。|||  
|5.  调用 **Update**。|||  
||6.  检查已更改的字段。||  
||7.  为 `AddNew` 生成 SQL **INSERT** 语句或为 **Edit** 生成 **UPDATE** 语句。||  
|||8.  发送 SQL。|  
||9.  对于 `AddNew`，将编辑缓冲区还原为该缓冲区的备份内容。  对于 **Edit**，删除备份。||  
  
### RFX：删除现有记录  
 当您删除记录时，RFX 将所有字段设置为 **NULL**，提醒您该记录已删除，您必须将其移走。  您不需要任何其他 RFX 序列信息。  
  
## 请参阅  
 [记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [宏、全局函数和全局变量](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md)