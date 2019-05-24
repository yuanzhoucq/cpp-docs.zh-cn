---
title: 记录集：动态绑定数据列 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: bde61348bbfb33eef42e36bd75830c23e5b2a5f5
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707937"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>记录集：动态绑定数据列 (ODBC)

本主题适用于 MFC ODBC 类。

记录集将管理你在设计时指定的绑定表列，但在某些情况下，你可能需要绑定在设计时未知的列。 本主题介绍：

- [当你可能需要将列动态绑定到记录集时](#_core_when_you_might_bind_columns_dynamically)。

- [如何在运行时动态绑定列](#_core_how_to_bind_columns_dynamically)。

> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果使用的是批量提取行，则通常不建议使用所述的技术。 有关批量提取行的详细信息，请参阅[记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="_core_when_you_might_bind_columns_dynamically"></a> 当可能动态绑定列时

> [!NOTE] 
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建使用者。

在设计时，MFC 应用程序向导或 [MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)（来自“添加类”）将根据数据源上的已知表和列创建记录集类。 你可以在设计数据库时更改数据库，也可以稍后当你的应用程序在运行时使用这些表和列时进行更改。 你或其他用户可能会添加或删除表，或者从应用程序的记录集所依赖的表中添加或删除列。 尽管这可能不是所有数据访问应用程序的问题，但如果是你的问题，除了重新设计和重新编译之外，你会如何处理数据库架构的更改？ 本主题的目的是回答此问题。

本主题介绍了最常见的情况，在这种情况下，你可能会动态绑定所需的列（已经从基于已知数据库架构的记录集开始进行动态绑定了）以在运行时处理附加列。 本主题进一步假设附加列将映射到 `CString` 字段数据成员，这是最常见的情况，但我们也提供了建议来帮助你管理其他数据类型。

凭借少量的额外代码，你就可以：

- [确定在运行时可用的列](#_core_how_to_bind_columns_dynamically)。

- [在运行时将附加列动态绑定到记录集](#_core_adding_the_columns)。

记录集仍包含在设计时所知的列的数据成员。 它还包含少量的额外代码，这些代码用于动态确定是否已向目标表添加了任何新列，如果是，则将这些新列绑定到动态分配的存储（而不是记录集数据成员）。

本主题不涵盖其他动态绑定情况，例如删除的表或列。 对于这些情况，需要更直接地使用 ODBC API 调用。 有关信息，请参阅 MSDN 库 CD 上的 ODBC SDK 程序员参考。

##  <a name="_core_how_to_bind_columns_dynamically"></a> 如何动态绑定列

若要动态绑定列，必须知道（或能够确定）附加列的名称。 还必须为附加的字段数据成员分配存储、指定其名称及其类型，并指定要添加的列数。

以下讨论提到了两种不同的记录集。 首先是从目标表中选择记录的主记录集。 其次是特殊的列记录集，用于获取有关目标表中列的信息。

###  <a name="_core_the_general_process"></a> 常规过程

从最普遍的意义上讲，请遵循以下步骤：

1. 构造主记录集对象。

   （可选）将指针传递给打开的 `CDatabase` 对象，或者能够以其他方式向列记录集提供连接信息。

1. 按步骤进行操作以动态添加列。

   请参阅以下“添加列”中所述的过程。

1. 打开主记录集。

   记录集将选择记录并使用记录字段交换 (RFX) 来绑定静态列（映射到记录集字段数据成员的列）和动态列（映射到你所分配的额外存储）。

###  <a name="_core_adding_the_columns"></a> 添加列

在运行时动态绑定添加的列需要以下步骤：

1. 在运行时确定目标表中的列。 从此信息中提取自设计出记录集类以来已添加到表中的列的列表。

   使用列记录集类是一个不错的方法，此类设计用于查询数据源以获取目标表的列信息（例如列名和数据类型）。

1. 为新的字段数据成员提供存储。 因为主记录集类没有未知列的字段数据成员，因此必须提供一个存储名称、结果值和可能的数据类型信息的位置（如果列是不同的数据类型）。

   一种方法是生成一个或多个动态列表，一个列表用于存储新列的名称，另一个列表用于存储其结果值，第三个列表用于存储其数据类型（如有必要）。 这些列表（特别是值列表）提供了用于绑定的信息和必要的存储空间。 下图阐述了如何生成列表。

   ![生成要动态绑定的列的列表](../../data/odbc/media/vc37w61.gif "Building lists of columns to bind dynamically")<br/>
   生成要动态绑定的列列表

1. 在主记录集的 `DoFieldExchange` 函数中为每个添加的列添加 RFX 函数调用。 这些 RFX 调用执行提取记录（包括附加列）的工作，并将这些列绑定到记录集数据成员或动态提供的存储中。

   一种方法是在主记录集的 `DoFieldExchange` 函数中添加一个循环，用于循环遍历新列的列表，从而为列表中的每列调用相应的 RFX 函数。 在每次 RFX 调用时，从列名称列表中传递一个列名称，并在结果值列表的对应成员中传递存储位置。

###  <a name="_core_lists_of_columns"></a> 列的列表

需要使用的四个列表如下表所示。

|||
|-|-|
|**Current-Table-Columns**| （图中的列表 1）数据源上的表中当前列的列表。 此列表可能与记录集中当前绑定的列的列表匹配。|
|**Bound-Recordset-Columns**| （图中的列表 2）记录集中绑定的列的列表。 这些列已在 `DoFieldExchange` 函数中包含了 RFX 语句。|
|**Columns-To-Bind-Dynamically**| （图中的列表 3）位于表中但不在记录集中的列的列表。 这些列表是你想要动态绑定的列表。|
|**Dynamic-Column-Values**| （图中的列表 4）包含从动态绑定的列中检索到的值的存储空间的列表。 此列表的元素与“Columns-to-Bind-Dynamically”中的元素一一对应。|

###  <a name="_core_building_your_lists"></a> 生成你的列表

对于一般策略而言，你可以查看相关的详细信息。 本主题其余部分中的过程展示了如何生成[列的列表](#_core_lists_of_columns)中显示的列表。 这些过程将指导你完成：

- [确定不在记录集中的列的名称](#_core_determining_which_table_columns_are_not_in_your_recordset)。

- [为新添加到表中的列提供动态存储](#_core_providing_storage_for_the_new_columns)。

- [动态添加新列的 RFX 调用](#_core_adding_rfx_calls_to_bind_the_columns)。

###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> 确定哪些表列没有在记录集中

生成一个列表（Bound-Recordset-Columns，如图中的列表 2 所示），其中包含已在主记录集中绑定的列的列表。 然后生成一个列表（Columns-to-Bind-Dynamically，派生自 Current-Table-Columns 和 Bound-Recordset-Columns），其中包含在数据源上的表中但不在主记录集中的列名称。

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>确定不在记录集中的列的名称 (Columns-to-Bind-Dynamically)

1. 生成已绑定在主记录集中的列的列表 (Bound-Recordset-Columns)。

   一种方法是在设计时创建 Bound-Recordset-Columns。 你可以直观地检查记录集的 `DoFieldExchange` 函数中的 RFX 函数调用以获取这些名称。 然后，将列表设置为使用名称初始化的数组。

   例如，图中显示了带有三个元素的 Bound-Recordset-Columns（列表 2）。 Bound-Recordset-Columns 缺少 Current-Table-Columns（列表 1）中显示的“Phone”列。

1. 比较 Current-Table-Columns 和 Bound-Recordset-Columns 以生成未绑定在主记录集中的列的列表 (Columns-to-Bind-Dynamically)。

   一种方法是在运行时 (Current-Table-Columns) 以并行的方式循环遍历表中的列的列表，以及已绑定在记录集 (Bound-Recordset-Columns) 中的列的列表。 在 Columns-to-Bind-Dynamically 中放置任何 Current-Table-Columns 中的名称（这些名称未在 Bound-Recordset-Columns 中未出现）。

   例如，图中显示了具有一个元素的 Columns-to-Bind-Dynamically（列表 3）：在 Current-Table-Columns（列表 1）中找到的但在 Bound-Recordset-Columns（列表 2）中未找到的“Phone”列。

1. 生成 Dynamic-Column-Values 的列表（如图中的列表 4 所示），其中存储与列的列表中存储的每个列名称相对应的数据值来动态进行绑定 (Columns-to-Bind-Dynamically)。

   此列表的元素扮演新记录集字段数据成员的角色。 它们是动态列绑定到的存储位置。 有关列表的说明，请参阅[列的列表](#_core_lists_of_columns)。

###  <a name="_core_providing_storage_for_the_new_columns"></a> 为新列提供存储

接下来，为要动态绑定的列设置存储位置。 目的是提供一个列表元素，用于存储每列的值。 这些存储位置与记录集成员变量并行，后者存储正常绑定的列。

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>为新列提供动态存储 (Dynamic-Column-Values)

1. 生成 Dynamic-Column-Values（与 Columns-to-Bind-Dynamically 并行）以包含每列中数据的值。

   例如，图中显示了带有一个元素的 Dynamic-Column-Values（列表 4）：包含当前记录的实际电话号码的 `CString` 对象：“555-1212”。

   在最常见的情况下，Dynamic-Column-Values 具有 `CString` 类型的元素。 如果要处理不同数据类型的列，则需要可以包含各种类型元素的列表。

上述过程的结果将生成两个主要列表：Columns-to-Bind-Dynamically，包含列的名称；Dynamic-Column-Values，包含当前记录的列中的值。

> [!TIP]
> 如果新列不全是相同的数据类型，则可能需要一个额外的并行列表，其中包含以某种方式定义列列表中每个对应元素的类型的项。 （为此，如有需要，可以使用值 AFX_RFX_BOOL、AFX_RFX_BYTE 等。 这些常量是在 AFXDB.H 中定义的。）基于你表示列数据类型的方式选择列表类型。

###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> 添加 RFX 调用以绑定列

最后，通过在 `DoFieldExchange` 函数中为新列放置 RFX 调用来安排进行动态绑定。

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>为新列动态添加 RFX 调用

1. 在主记录集的 `DoFieldExchange` 成员函数中，添加循环遍历新列 (Columns-to-Bind-Dynamically) 列表的代码。 在每个循环中，从 Columns-to-Bind-Dynamically 中提取列名称，并从 Dynamic-Column-Values 中提取此列的结果值。 将这些项传递给适用于列的数据类型的 RFX 函数调用。 有关列表的说明，请参阅[列的列表](#_core_lists_of_columns)。

通常情况下，在 `RFX_Text` 函数调用中，需要从列表中提取 `CString` 对象，如以下代码行所示，其中 Columns-to-Bind-Dynamically 为 `CStringList`，称为 `m_listName`Dynamic-Column-Values 为 `CStringList`，称为 `m_listValue`：

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

有关 RFX 函数的详细信息，请参阅类库参考中的[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)。

> [!TIP]
> 如果新列是不同的数据类型，请在循环中使用 switch 语句为每种类型调用相应的 RFX 函数。

当框架在 `Open` 过程中调用 `DoFieldExchange` 将列绑定到记录集时，RFX 将调用静态列绑定这些列。 然后循环将反复调用动态列的 RFX 函数。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：处理大数据项 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)