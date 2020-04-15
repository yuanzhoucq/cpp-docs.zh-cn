---
title: 记录集：参数化记录集 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: 6d28471bdc44d5d75a9eeac2327f92a8e2e265c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360658"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>记录集：参数化记录集 (ODBC)

本主题适用于 MFC ODBC 类。

有时，你可能想能够使用从最终用户计算或获取的信息在运行时选择记录。 记录集参数使你能够实现此目标。

本主题介绍：

- [参数化记录集的目的](#_core_parameterized_recordsets)。

- [何时以及为何可能需要参数化记录集](#_core_when_to_use_parameters)。

- [如何在记录集类中声明参数数据成员](#_core_parameterizing_your_recordset_class)。

- [如何在运行时将参数信息传递给记录集对象](#_core_passing_parameter_values_at_run_time)。

## <a name="parameterized-recordsets"></a><a name="_core_parameterized_recordsets"></a> 参数化记录集

参数化记录集使你能够在运行时传递参数信息。 此操作将产生两个重要的影响：

- 它可能会加快执行速度。

- 它使你能够根据在设计时不可用的信息（例如从用户获取的信息或在运行时计算的信息）在运行时生成查询。

当你调用 `Open` 运行查询时，记录集将使用参数信息来完成其 SQL SELECT 语句****。 你可以参数化任何记录集。

## <a name="when-to-use-parameters"></a><a name="_core_when_to_use_parameters"></a> 何时使用参数

参数的典型用途包括：

- 将运行时参数传递给预定义的查询。

   若要将参数传递给存储过程，必须在调用 `Open` 时使用参数占位符指定完整的自定义 ODBC CALL 语句，从而替代记录集的默认 SQL 语句****。 有关详细信息，请参阅[CRecordset：：在](../../mfc/reference/crecordset-class.md#open)*类库引用*和 SQL 中打开[：自定义记录集的 SQL 语句 （ODBC）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)和[记录集：声明预定义查询 （ODBC） 的类](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。

- 使用不同的参数信息有效地执行大量再次查询。

   例如，每当最终用户在学生注册数据库中查找特定学生的信息时，你可以将学生的姓名或 ID 指定为从用户获取的参数。 然后，当你调用记录集的 `Requery` 成员函数时，查询仅会选择该学生的记录。

   记录集的筛选器字符串（存储在 `m_strFilter` 中）可能如下所示：

    ```cpp
    "StudentID = ?"
    ```

   假设你在变量 `strInputID` 中获取学生 ID。 当你将参数设置为 `strInputID` 时（例如，学生 ID 为 100），变量的值会绑定到由筛选器字符串中的“?”表示的参数占位符。

   按如下所示分配参数值：

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   你不希望以这种方式设置筛选器字符串：

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   有关如何正确使用引号对筛选器字符串的讨论，请参阅[记录集：筛选记录 （ODBC）。](../../data/odbc/recordset-filtering-records-odbc.md)

   每当再次查询新学生 ID 的记录集时，参数值都是不同的。

   > [!TIP]
   > 使用参数比使用简单的筛选器更高效。 对于参数化记录集，数据库必须只处理一次 SQL SELECT 语句****。 对于没有参数的已筛选的记录集，每次当你使用新筛选器值进行 `Requery` 时，SELECT 语句都必须被处理****。

有关筛选器的详细信息，请参阅[记录集：筛选记录 （ODBC）。](../../data/odbc/recordset-filtering-records-odbc.md)

## <a name="parameterizing-your-recordset-class"></a><a name="_core_parameterizing_your_recordset_class"></a> 参数化记录集类

> [!NOTE]
> 本部分适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果使用的是批量行提取，实现参数则是一个类似的过程。 有关详细信息，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

创建记录集类之前，请确定所需的参数、其数据类型以及记录集如何使用它们。

#### <a name="to-parameterize-a-recordset-class"></a>参数化记录集类

> [!NOTE]
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建此功能。

1. 从“添加类”运行 [MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)以创建类****。

1. 为记录集的列指定字段数据成员。

1. 当向导将类写入项目中的文件后，转到 .h 文件并手动将一个或多个参数数据成员添加到类声明中。 添加可能类似于以下示例，快照类的一部分旨在回答查询“哪些学生在高年级？”

    ```cpp
    class CStudentSet : public CRecordset
    {
    // Field/Param Data
        CString m_strFirstName;
        CString m_strLastName;
        CString m_strStudentID;
        CString m_strGradYear;

        CString m_strGradYrParam;
    };
    ```

   在向导生成的字段数据成员后面添加参数数据成员。 约定是将“Param”一词追加到每个用户定义的参数名称。

1. 修改 .cpp 文件中的 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 成员函数定义。 为添加到类中的每个参数数据成员添加 RFX 函数调用。 有关编写 RFX 函数的信息，请参阅[记录字段交换：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。 通过单个调用将针对参数的 RFX 调用置于前面：

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. 在记录集类的构造函数中，递增参数计数，`m_nParams`。

   有关详细信息，请参阅[记录字段交换：使用向导代码](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)。

1. 在编写创建此类的记录集对象的代码时，请在 SQL 语句字符串中要替换参数的每个位置中放置一个“?”（问号）符号。

   在运行时，“?”占位符是按顺序由传递的参数值填充。 在 [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) 调用之后设置的第一个参数数据成员将替换 SQL 字符串中的第一个“?”，第二个参数数据成员将替换第二个“?”，依此类推。

> [!NOTE]
> 参数顺序是非常重要的：`DoFieldExchange` 函数中针对参数的 RFX 调用的顺序必须与 SQL 字符串中参数占位符的顺序相匹配。

> [!TIP]
> 最可能使用的字符串是为类的 [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) 数据成员指定的字符串（如果有），但某些 ODBC 驱动程序可能允许其他 SQL 子句中的参数。

## <a name="passing-parameter-values-at-run-time"></a><a name="_core_passing_parameter_values_at_run_time"></a> 在运行时传递参数值

在调用 `Open`（针对新记录集对象）或 `Requery`（针对现有记录集对象）之前必须指定参数值。

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>在运行时将参数值传递给记录集对象

1. 构造记录集对象。

1. 准备一个或多个字符串，例如 `m_strFilter` 字符串，包含 SQL 语句或其中一部分。 将“?”占位符放置在参数信息要转至的位置。

1. 将运行时参数值分配给对象的每个参数数据成员。

1. 调用 `Open` 成员函数（针对现有记录集，则调用 `Requery`）。

例如，假设要使用在运行时获取的信息为记录集指定筛选器字符串。 假设你之前已构造了一个 `CStudentSet` 类的记录集（称为 `rsStudents`），现在想再次查询特定类型的学生信息。

```cpp
// Set up a filter string with
// parameter placeholders
rsStudents.m_strFilter = "GradYear <= ?";

// Obtain or calculate parameter values
// to pass--simply assigned here
CString strGradYear = GetCurrentAcademicYear( );

// Assign the values to parameter data members
rsStudents.m_strGradYrParam = strGradYear;

// Run the query
if( !rsStudents.Requery( ) )
    return FALSE;
```

记录集包含那些记录符合筛选器所指定条件的学生的记录，筛选器是根据运行时参数构造的。 在这种情况下，记录集包含所有高年级学生的记录。

> [!NOTE]
> 如果需要，可以使用 [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull) 将参数数据成员的值设置为 Null。 同样可以使用 [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) 检查参数数据成员是否为 Null。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[记录集：记录集如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
