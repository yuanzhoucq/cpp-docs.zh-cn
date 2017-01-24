---
title: "记录集：动态绑定数据列 (ODBC) | Microsoft Docs"
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
  - "列 [C++], 绑定到记录集"
  - "数据绑定 [C++], 记录集内的列"
  - "数据绑定 [C++], 记录集列"
  - "ODBC 记录集 [C++], 动态绑定列"
  - "记录集 [C++], 绑定数据"
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：动态绑定数据列 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 记录集管理绑定您在设计时指定的表列，但有时可能要绑定设计时未知的列。  本主题说明：  
  
-   [可能需要将列动态绑定到记录集的场合](#_core_when_you_might_bind_columns_dynamically)。  
  
-   [运行时动态绑定列的方式](#_core_how_to_bind_columns_dynamically)。  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果正在使用批量取行，通常建议不使用所描述的技术。  有关批量取行的更多信息，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_when_you_might_bind_columns_dynamically"></a> 何时可以动态绑定列  
 在设计时，“MFC 应用程序向导”或 [MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)（“添加类”中）基于数据源上的已知表和列创建记录集类。  在设计数据库和此后应用程序在运行时使用那些表和列之间，可以更改数据库。  您或其他用户可能添加或删除表，或者从您的应用程序的记录集所依赖的表中添加或删除列。  这对所有的数据访问应用程序可能无关紧要，但如果它对您的应用程序很重要，那么除了重新设计和重新编译之外，是否有其他方法可以解决数据库架构中的更改？  本主题将要回答这个问题。  
  
 本主题描述可能动态绑定列的最常见情况：最初的记录集基于一个已知的数据库架构，而您在运行时希望处理其他的列。  本主题进一步假定其他列映射到 `CString` 字段数据成员这一最常见的情况，但也提供了帮助您管理其他数据类型的建议。  
  
 用少量的额外代码，您可以：  
  
-   [确定在运行时可用的列](#_core_to_determine_the_columns_in_a_table_at_run_time)。  
  
-   [运行时动态将附加列绑定到记录集](#_core_adding_the_columns)。  
  
 记录集仍然包含您在设计时知道的列的数据成员。  还包含动态确定是否已将任何新列添加到目标表的少量额外代码，如果已将任何新列添加到目标表，则将这些新列绑定到动态分配的存储区（而非绑定到记录集数据成员）。  
  
 本主题不包括其他动态绑定情况，如删除的表或列。  对于那些情况，您需要更直接地使用 ODBC API 调用。  有关信息，请参见 MSDN Library 光盘上的 ODBC SDK Programmer's Reference（ODBC SDK 程序员参考）。  
  
##  <a name="_core_how_to_bind_columns_dynamically"></a> 如何动态绑定列  
 若要动态绑定列，必须知道（或者能够确定）其他列的名称。  还必须分配其他字段数据成员的存储区、指定它们的名称和类型并指定要添加的列数。  
  
 下面的讨论涉及两个不同的记录集。  第一个记录集是从目标表中选择记录的主记录集。  第二个记录集是用于获得目标表的列信息的特殊列记录集。  
  
###  <a name="_core_the_general_process"></a> 一般过程  
 通常，按照下面的步骤进行操作：  
  
1.  构造主记录集对象。  
  
     （可选）将指针传递给打开的 `CDatabase` 对象，或者能够用某种其他方式将连接信息提供给列记录集。  
  
2.  采取步骤动态添加列。  
  
     请参见下面“添加列”中描述的过程。  
  
3.  打开主记录集。  
  
     记录集选择记录并使用记录字段交换 \(RFX\)，同时绑定静态列（映射到记录集字段数据成员的列）和动态列（映射到分配的其他存储区）。  
  
###  <a name="_core_adding_the_columns"></a> 添加列  
 运行时动态绑定添加的列需要完成以下步骤：  
  
1.  确定运行时目标表中的列。  从该信息中提取自设计记录集类以来已经添加到表中的列列表。  
  
     一个好的方法是使用专门用于在数据源中查询目标表的列信息（例如，列名和数据类型）的列记录集类。  
  
2.  为新字段数据成员提供存储区。  主记录集类不包含未知列的字段数据成员，因此您必须提供一个位置来存储名称、结果值和可能的数据类型信息（如果列的数据类型不同）。  
  
     一个方法是生成一个或多个动态列表，一个列表用于新列的名称，另一个列表用于列的结果值，第三个列表用于列的数据类型（如有必要）。  这些列表（特别是值列表）提供绑定的信息和必要的存储区。  下图将阐释如何生成列表。  
  
     ![生成要动态绑定的列列表](../../data/odbc/media/vc37w61.gif "vc37W61")  
生成要动态绑定的列列表  
  
3.  为每个已添加的列在主记录集的 `DoFieldExchange` 函数中添加 RFX 函数调用。  这些 RFX 调用执行获取记录（包括其他列）和将列绑定到记录集数据成员或绑定到为它们动态提供的存储区的操作。  
  
     一个方法是在主记录集的 `DoFieldExchange` 函数中添加一个依次通过新列列表的循环，该循环调用列表中每个列的相应 RFX 函数。  在每个 RFX 调用中，传递列名列表中的列名和结果值列表的相应成员中的存储位置。  
  
###  <a name="_core_lists_of_columns"></a> 列列表  
 您需要使用的四个列表在下表中显示。  
  
 [当前表列（图示中的列表 1）](#_core_illustration_dynamic)  
 数据源上表中的当前列列表。  此列表可能与记录集中当前绑定的列列表匹配。  
  
 [绑定记录集列（图示中的列表 2）](#_core_illustration_dynamic)  
 记录集中绑定的列列表。  这些列在 `DoFieldExchange` 函数中已经有 RFX 语句。  
  
 [要动态绑定的列（图示中的列表 3）](#_core_illustration_dynamic)  
 在表中但不在记录集中的列列表。  这些是要动态绑定的列。  
  
 [动态列值（图示中的列表 4）](#_core_illustration_dynamic)  
 包含从动态绑定列中检索到的值的存储列表。  此列表中的元素与“要动态绑定的列”中的元素一一对应。  
  
###  <a name="_core_building_your_lists"></a> 生成列表  
 记住了一般策略后，就可以开始了解具体步骤。  本主题其他部分中的过程向您展示了如何生成[列列表](#_core_lists_of_columns)中显示的列表。  过程将引导您完成：  
  
-   [确定不在记录集中的列名](#_core_determining_which_table_columns_are_not_in_your_recordset)。  
  
-   [为新添加到表中的列提供动态存储区](#_core_providing_storage_for_the_new_columns)。  
  
-   [为新列动态添加 RFX 调用](#_core_adding_rfx_calls_to_bind_the_columns)。  
  
###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> 确定不在记录集中的表列  
 生成包含主记录集中已经绑定的列的列表（“绑定记录集列”，如[图示](#_core_illustration_dynamic)的“列表 2”中所示）。  然后生成名为“要动态绑定的列”的列表，该列表从“当前表列”和“绑定记录集列”中派生，它包含属于数据源上的表但不属于主记录集的列的名称。  
  
##### 确定不在记录集中的列的名称（要动态绑定的列）  
  
1.  生成主记录集中已经绑定的列列表（“绑定记录集列”）。  
  
     一个方法是在设计时创建“绑定记录集列”。  可以以可视的方式检查记录集的 `DoFieldExchange` 函数中的 RFX 函数调用以获得这些名称。  然后将列表设置为用名称初始化的数组。  
  
     例如，[图示](#_core_illustration_dynamic)用三个元素显示“绑定记录集列”（列表 2）。  “绑定记录集列”现在缺少“当前表列”（列表 1）中显示的 Phone 列。  
  
2.  比较“当前表列”和“绑定记录集列”以生成主记录集中尚未绑定列的列表（“要动态绑定的列”）。  
  
     一个方法是依次比较“当前表列”和“绑定记录集列”这两个列表中的列，其中“当前表列”是运行时表中的列的列表，“绑定记录集列”是记录集中已经并行绑定列的列表。  在“要动态绑定的列”中，放入“当前表列”中未出现在“绑定记录集列”中的任何名称。  
  
     例如，[图示](#_core_illustration_dynamic)用一个元素显示“要动态绑定的列”（列表 3）：出现在“当前表列”（列表 1）中但不在“绑定记录集列”（列表 2）中的 Phone 列。  
  
3.  生成“动态列值”（如[图示](#_core_illustration_dynamic)中的“列表 4”所示）列表，在该列表中存储与要动态绑定的列（“要动态绑定的列”）列表中存储的每个列名相对应的数据值。  
  
     此列表的元素充当新记录集字段数据成员的角色。  它们是动态列被绑定到的存储位置。  有关列表的说明，请参见[列列表](#_core_lists_of_columns)。  
  
###  <a name="_core_providing_storage_for_the_new_columns"></a> 为新列提供存储区  
 下一步，设置要动态绑定的列的存储位置。  也就是提供用来存储每个列值的列表元素。  这些存储位置与记录集成员变量相对应，而记录集成员变量存储正常绑定的列。  
  
##### 为新列提供动态存储（动态列值）  
  
1.  生成与“要动态绑定的列”并行的“动态列值”以包含每个列中的数据值。  
  
     例如，[图示](#_core_illustration_dynamic)用一个元素显示“动态列值”（列表 4）：一个包含当前记录的实际电话号码的 `CString` 对象，“555\-1212”。  
  
     在最常见的情况下，“动态列值”有 `CString` 类型的元素。  如果处理的列具有不同的数据类型，则需要可以包含不同类型元素的列表。  
  
 前面的过程产生两个主列表：包含列名的“要动态绑定的列”和包含当前记录列值的“动态列值”。  
  
> [!TIP]
>  如果新列的数据类型不完全相同，则可能需要一个额外的并行列表，来包含以某种方式定义列列表中每个相应元素的类型的项。（如果希望，可以为此使用 **AFX\_RFX\_BOOL**、**AFX\_RFX\_BYTE** 等值。  在 AFXDB.H 中定义了这些常量。）根据表示列数据类型的方式选择列表类型。  
  
###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> 添加 RFX 调用以绑定列  
 最后，通过将新列的 RFX 调用放到 `DoFieldExchange` 函数中来安排要发生的动态绑定。  
  
##### 动态添加新列的 RFX 调用  
  
1.  在主记录集的 `DoFieldExchange` 成员函数中，添加依次通过新列（“要动态绑定的列”）列表的代码。  在每个循环中，从“要动态绑定的列”中提取列名并从“动态列值”中提取列的结果值。  将这些项传递给适合该列的数据类型的 RFX 函数调用。  有关列表的说明，请参见[列列表](#_core_lists_of_columns)。  
  
 通常情况下，在 `RFX_Text` 函数调用中从列表提取 `CString` 对象，如下列代码行所示，其中“要动态绑定的列”是称为 `m_listName` 的 `CStringList`，而“动态列值”是称为 `m_listValue` 的 `CStringList`：  
  
```  
RFX_Text( pFX,   
            m_listName.GetNext( posName ),   
            m_listValue.GetNext( posValue ));  
```  
  
 有关 RFX 函数的更多信息，请参见“类库引用”中的[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)。  
  
> [!TIP]
>  如果新列具有不同的数据类型，则在循环中使用 switch 语句调用适合每个类型的 RFX 函数。  
  
 当框架在 **Open** 进程中调用 `DoFieldExchange` 以将列绑定到记录集时，静态列的 RFX 调用绑定这些列。  然后循环重复调用动态列的 RFX 函数。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：处理大数据项 \(ODBC\)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)