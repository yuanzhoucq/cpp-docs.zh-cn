---
title: 记录集：参数化记录集 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: df67256c54cae3e2adb054d653d3e58bb91dd631
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026157"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>记录集：参数化记录集 (ODBC)

本主题适用于 MFC ODBC 类。

有时你可能想要能够在运行时，选择记录使用计算得出的或从你的最终用户获得的信息。 记录集参数允许您实现这个目标。

本主题说明：

- [参数化记录集的目的](#_core_parameterized_recordsets)。

- [何时以及为何您可能希望参数化记录集](#_core_when_to_use_parameters)。

- [如何在记录集类中的数据成员声明参数](#_core_parameterizing_your_recordset_class)。

- [如何在运行时将参数信息传递给记录集对象](#_core_passing_parameter_values_at_run_time)。

##  <a name="_core_parameterized_recordsets"></a> 参数化记录集

参数化记录集，可以通过在运行时的参数信息。 这样做有两个重要的影响：

- 它可能会导致更好的执行速度。

- 它允许您生成查询在运行时，基于在设计时不可用的信息，例如从用户获得的或运行时计算的信息。

当您调用`Open`若要运行查询，该记录集使用的参数信息来完成其**SQL SELECT**语句。 你可以参数化任何记录集。

##  <a name="_core_when_to_use_parameters"></a> 何时使用参数

参数的典型用途包括：

- 将运行时参数传递给预定义的查询。

   若要将参数传递给存储过程，必须指定完整的自定义 ODBC**调用**语句，用参数占位符 — — 当您调用`Open`，重写记录集的默认的 SQL 语句。 有关详细信息，请参阅[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)中*类库参考*和[SQL:自定义记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)和[记录集：预定义的查询 (ODBC) 声明的类](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。

- 有效地执行大量查询与不同的参数信息。

   例如，每次你的最终用户查找信息的特定学生在学生注册数据库中，您可以指定学生的名称或 ID 作为参数从用户获取。 然后，当调用记录集的`Requery`成员函数，该查询只选择该学生的记录。

   记录集的筛选器字符串，存储在`m_strFilter`，可能如下所示：

    ```cpp
    "StudentID = ?"
    ```

   假设你获取变量中的学生 ID `strInputID`。 当将参数设置为`strInputID`变量的值绑定到所表示的参数占位符 （例如，学生 ID 为 100）"？"中的筛选器字符串。

   分配参数值，如下所示：

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   您不希望这种方式设置筛选器字符串：

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   有关如何正确的筛选器字符串使用引号引起来的讨论，请参阅[记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。

   参数值每次均不同您再次查询记录集是新学生 id。

   > [!TIP]
   > 使用一个参数是只使用筛选器比效率更高。 参数化记录集，数据库必须处理 SQL**选择**语句仅一次。 不带参数，筛选记录集**选择**必须处理语句每次`Requery`的新筛选器值。

有关筛选器的详细信息，请参阅[记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。

##  <a name="_core_parameterizing_your_recordset_class"></a> 参数化记录集类

> [!NOTE]
> 本部分适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果您使用的批量行提取，则实现参数是一个类似的过程。 有关详细信息，请参阅[记录集：(ODBC) 批量提取记录](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

创建记录集类之前，确定所需的参数、 其数据类型是什么，和记录集如何使用它们。

#### <a name="to-parameterize-a-recordset-class"></a>若要参数化记录集类

1. 运行[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)从**添加类**创建类。

1. 指定记录集的列的字段数据成员。

1. 向导会将类写入到你的项目中的文件后，转到.h 文件并手动将一个或多个参数的数据成员添加到类声明。 添加可能类似于下面的示例中，快照类的部分设计为回答查询"中有哪些学生高级类？"

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

   向导生成的字段数据成员之后添加您参数的数据成员。 约定是将单词"Param"追加到每个用户定义的参数名称。

1. 修改[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) .cpp 文件中的成员函数定义。 添加 RFX 函数调用每个参数的数据成员添加到类。 有关编写 RFX 函数的信息，请参阅[记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 请在前面的单个调用 RFX 调用的参数：

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. 在记录集类的构造函数中的参数，计数增加`m_nParams`。

   有关信息，请参阅[记录字段交换：使用向导代码](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)。

1. 当您编写代码，用于创建此类记录集对象时，在将"？"在您的 SQL 语句字符串中的每个位置，其中一个参数是要替换的 （问号） 符号。

   在运行时，"？"的占位符，按顺序填充，则通过通过参数值。 第一个参数的数据成员设置后[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)调用，将替换第一个"？"在 SQL 字符串，第二个参数的数据成员替换第二个"？"，依次类推。

> [!NOTE]
> 参数顺序非常重要： RFX 的顺序调用中的参数在`DoFieldExchange`函数必须与你的 SQL 字符串中的参数占位符的顺序匹配。

> [!TIP]
> 要使用的最有可能字符串是所指定的字符串 （如果有） 的类[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)数据成员，但某些 ODBC 驱动程序可能会允许其他 SQL 子句中的参数。

##  <a name="_core_passing_parameter_values_at_run_time"></a> 在运行时传递参数值

在调用之前，必须指定参数值`Open`（适用于新的记录集对象） 或`Requery`（适用于一个现有）。

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>在运行时将参数值传递到记录集对象

1. 构造的记录集对象。

1. 准备一个字符串或字符串，如`m_strFilter`包含 SQL 语句或其各个部分的字符串。 将"？"参数信息是其中的占位符。

1. 将运行时参数值分配给对象的每个参数的数据成员。

1. 调用`Open`成员函数 (或`Requery`，某个现有记录集)。

例如，假设你想要指定您使用在运行时获取的信息的记录集的筛选器字符串。 假定已构造的类记录集`CStudentSet`前面，名为`rsStudents`—，现在想要再次将其用于特定种类的学生信息查询。

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

记录集包含的记录符合指定筛选器，它已由运行时参数构造的条件的学生的记录。 在这种情况下，记录集包含的所有高年级学生记录。

> [!NOTE]
>  如果需要可以设置参数的数据成员的值为 Null，使用[SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull)。 同样可以检查参数数据成员是否为 Null，使用[IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull)。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[记录集：如何记录集选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)