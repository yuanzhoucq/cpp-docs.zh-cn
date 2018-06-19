---
title: 记录集： 参数化记录集 (ODBC) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 275cd9d2ee7ccbd4c9972c00ae6fbb8f33166a0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098545"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>记录集：参数化记录集 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 有时你可能想要能够在运行时，选择记录使用计算得出的或从你的最终用户获得的信息。 记录集参数，可以实现该目标。  
  
 本主题说明：  
  
-   [参数化记录集的目的](#_core_parameterized_recordsets)。  
  
-   [何时和为何你可能想要参数化记录集](#_core_when_to_use_parameters)。  
  
-   [如何将参数声明记录集类中的数据成员](#_core_parameterizing_your_recordset_class)。  
  
-   [如何在运行时将参数信息传递到记录集对象](#_core_passing_parameter_values_at_run_time)。  
  
##  <a name="_core_parameterized_recordsets"></a> 参数化记录集  
 参数化记录集，可以通过在运行时的参数信息。 这样做有两个重要的影响：  
  
-   它可能会导致更好的执行速度。  
  
-   它允许你基于在设计时，无法对你的信息，如信息从你的用户获得的或在运行时计算在运行时，生成查询。  
  
 当调用**打开**若要运行查询，记录集使用参数的信息来完成其**SQL SELECT**语句。 你可以参数化任何记录集。  
  
##  <a name="_core_when_to_use_parameters"></a> 何时使用参数  
 参数的典型用途包括：  
  
-   将运行时自变量传递给预定义的查询。  
  
     若要将参数传递给存储过程，必须指定完整的自定义 ODBC**调用**语句-用参数占位符 — 当您调用**打开**，重写记录集的默认 SQL 语句。 有关详细信息，请参阅[CRecordset::Open](../../mfc/reference/crecordset-class.md#open)中*类库参考*和[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)和[记录集： 为预定义的查询 (ODBC) 声明一个类](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。  

  
-   有效地执行大量查询使用不同的参数信息。  
  
     例如，每次你的最终用户查找有关特定学生在学生注册数据库中，你可以指定学生的名称或 ID 作为参数从用户获取。 然后，当调用记录集的**Requery**成员函数时，查询只选择该学生的记录。  
  
     存储在中的记录集的筛选器字符串**m_strFilter**，可能如下所示：  
  
    ```  
    "StudentID = ?"  
    ```  
  
     假设你获取变量中的学生 ID `strInputID`。 当将参数设置为`strInputID`（例如，学生 ID 为 100） 的变量的值绑定到由参数占位符"？"筛选器字符串中。  
  
     分配参数值，如下所示：  
  
    ```  
    strInputID = "100";  
    ...  
    m_strParam = strInputID;  
    ```  
  
     你不想要设置筛选器字符串这种方式：  
  
    ```  
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted  
                                       // for some drivers  
    ```  
  
     有关如何正确使用引号，筛选器字符串的讨论，请参阅[记录集： 筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
     参数值的次均不同，每个新的学生 id requery 记录集  
  
    > [!TIP]
    >  使用一个参数是只使用筛选器比效率更高。 参数化记录集，数据库必须处理 SQL**选择**语句仅一次。 为不带参数，筛选记录集**选择**必须处理语句在每次时**Requery**使用新的筛选器值。  
  
 有关筛选器的详细信息，请参阅[记录集： 筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
##  <a name="_core_parameterizing_your_recordset_class"></a> 参数化记录集类  
  
> [!NOTE]
>  本部分适用于对象派生自`CRecordset`中哪些批量行提取尚未实现。 如果你使用的批量行提取，则实现参数是一个类似的过程。 有关详细信息，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 创建记录集类之前，确定需要哪些参数、 其数据类型是什么，和记录集如何使用它们。  
  
#### <a name="to-parameterize-a-recordset-class"></a>若要参数化记录集类  
  
1.  运行[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)从**添加类**创建类。  
  
2.  指定记录集的列的字段数据的成员。  
  
3.  向导会将类写入到你的项目中的文件后，转到的.h 文件，并手动将一个或多个参数数据成员添加到类声明。 添加可能看起来类似下面的示例中，但快照类的一部分设计为回答查询"中有哪些学生年级？"  
  
    ```  
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
  
     向导生成的字段数据成员之后添加你的参数数据成员。 约定是将 word"Param"追加到每个用户定义的参数名称。  
  
4.  修改[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) .cpp 文件中的成员函数定义。 每个参数数据成员添加到类中添加的 RFX 函数调用。 有关编写 RFX 函数的信息，请参阅[记录字段交换： RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。 请在前面的参数到一次调用 RFX 调用：  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
5.  记录集类的构造函数中的参数，计数增加`m_nParams`。  
  
     有关信息，请参阅[记录字段交换： 处理向导代码](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)。  
  
6.  当你编写的代码： 创建此类的记录集对象时，将"？"在您的 SQL 语句字符串中的每个位置，其中一个参数是要替换的 （问号） 符号。  
  
     在运行时，"？"占位符，按顺序填充，则你传递的参数值。 之后的第一个参数数据成员设置[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)调用将替换第一个"？"在 SQL 字符串的第二个参数数据成员替换第二个"？"，依次类推。  
  
> [!NOTE]
>  参数顺序非常重要： RFX 的顺序调用中的参数你`DoFieldExchange`函数必须与你的 SQL 字符串中的参数占位符的顺序一致。  
  
> [!TIP]

>  要使用的最可能的字符串是所指定的字符串 （如果有） 的类的[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)数据成员，但某些 ODBC 驱动程序可能会允许其他 SQL 子句中的参数。  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a> 在运行时传递参数值  
 必须指定参数值，然后才能调用**打开**（适用于新的记录集对象） 或**Requery** （对于一个现有）。  
  
#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>若要在运行时将参数值传递到记录集对象  
  
1.  构造的记录集对象。  
  
2.  准备一个字符串或字符串，如**m_strFilter**包含 SQL 语句或其中的部分的字符串。 将"？"参数信息所在转的占位符。  
  
3.  将运行时参数值分配到每个参数数据成员的对象。  
  
4.  调用**打开**成员函数 (或**Requery**，某个现有记录集)。  
  
 例如，假设你想要指定你使用在运行时获取的信息的记录集的筛选器字符串。 假定已构造的类的记录集`CStudentSet`前面-调用`rsStudents`-，现在想要再次查询特定种类的学生信息。  
  
```  
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
  
 记录集包含记录这些学生版其记录满足指定筛选器，已由运行时参数构造的条件。 在这种情况下，记录集包含记录所有高级学生版。  
  
> [!NOTE]
>  如果需要你可以将参数数据成员的值设置为 Null，使用[SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull)。 你可以同样检查参数数据成员是否为 Null，使用[IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [记录集：记录集如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)