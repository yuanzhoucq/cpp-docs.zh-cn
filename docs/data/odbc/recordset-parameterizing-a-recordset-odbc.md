---
title: "记录集：参数化记录集 (ODBC) | Microsoft Docs"
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
  - "ODBC 记录集, 参数化"
  - "参数化记录集"
  - "传递参数, 到运行时中的查询"
  - "记录集, 参数化"
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 记录集：参数化记录集 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 有时您可能希望能够使用通过计算得出的或从最终用户获得的信息在运行时选择记录。  记录集参数使您得以实现该目标。  
  
 本主题说明：  
  
-   [参数化记录集的目的](#_core_parameterized_recordsets)。  
  
-   [可能需要参数化记录集的场合和原因](#_core_when_to_use_parameters)。  
  
-   [在记录集类中声明参数数据成员的方式](#_core_parameterizing_your_recordset_class)。  
  
-   [在运行时向记录集传递参数信息的方式](#_core_passing_parameter_values_at_run_time)。  
  
##  <a name="_core_parameterized_recordsets"></a> 参数化记录集  
 参数化记录集使您得以在运行时传递参数信息。  它产生两个重要的影响：  
  
-   可能加快执行速度。  
  
-   它使您得以基于设计时不可用的信息（例如，在运行时从用户获得的或通过计算得出的信息）在运行时生成查询。  
  
 当您调用 **Open** 运行查询时，记录集使用参数信息来完成其 **SQL SELECT** 语句。  可以参数化任何记录集。  
  
##  <a name="_core_when_to_use_parameters"></a> 何时使用参数  
 参数的典型用途包括：  
  
-   将运行时参数传递到预定义查询。  
  
     若要将参数传递到存储过程，则必须在调用 **Open** 时指定一条完整的自定义 ODBC **CALL** 语句（带参数占位符），以便重写记录集的默认 SQL 语句。  有关更多信息，请参见 Class Library Reference（《类库参考》）中的 [CRecordset::Open](../Topic/CRecordset::Open.md)、[SQL：自定义记录集的 SQL 语句 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md) 和[记录集：声明预定义查询的类 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。  
  
-   用不同的参数信息有效地执行大量查询。  
  
     例如，最终用户每次在学生注册数据库中查阅特定学生的信息时，可以将学生的姓名或 ID 指定为从该用户获得的参数。  然后，当您调用记录集的 **Requery** 成员函数时，查询只选择该学生的记录。  
  
     存储在 **m\_strFilter** 中的记录集的筛选字符串可能类似于：  
  
    ```  
    "StudentID = ?"  
    ```  
  
     假定您在变量 `strInputID` 中获得学生 ID。  当将参数设置为 `strInputID`（例如，学生 ID 为 100）时，该变量的值即被绑定到用筛选字符串中的“?”表示的参数占位符。  
  
     如下赋参数值：  
  
    ```  
    strInputID = "100";  
    ...  
    m_strParam = strInputID;  
    ```  
  
     而不要以这种方式设置筛选器字符串：  
  
    ```  
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted  
                                       // for some drivers  
    ```  
  
     有关如何在筛选器字符串中正确使用引号的讨论，请参见[记录集：筛选记录 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
     每次在记录集中再次查询新学生的 ID 时，此参数值是不同的。  
  
    > [!TIP]
    >  使用参数比只使用筛选器更有效。  对于参数化记录集，数据库必须只处理一次 SQL **SELECT** 语句。  对于没有参数的已筛选记录集，每次用新的筛选值 **Requery** 时都必须处理 **SELECT** 语句。  
  
 有关筛选器的更多信息，请参见[记录集：筛选记录 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
##  <a name="_core_parameterizing_your_recordset_class"></a> 参数化记录集类  
  
> [!NOTE]
>  本节适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果正在使用批量取行，则实现参数的过程与此相似。  有关更多信息，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 在创建记录集类之前，确定所需的参数、参数的数据类型以及记录集使用参数的方式。  
  
#### 参数化记录集类  
  
1.  从“添加类”运行 [MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)来创建类。  
  
2.  指定记录集的列的字段数据成员。  
  
3.  当向导将类写入项目的某个文件之后，转到 .h 文件并向类声明手动添加一个或多个参数数据成员。  添加的内容可能类似于下面的示例，快照类的一部分被设计用来回答查询“哪些学生是高年级的？  
  
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
  
     在向导生成的字段数据成员后面添加参数数据成员。  约定是将字“Param”追加到每一个用户定义的参数名。  
  
4.  修改 .cpp 文件中的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 成员函数定义。  为已添加到类中的每一个参数数据成员添加 RFX 函数调用。  有关编写 RFX 函数的信息，请参见[记录字段交换：RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  在参数的 RFX 调用之前单一调用：  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
5.  在记录集类的构造函数中，增加参数 `m_nParams` 的计数。  
  
     有关信息，请参见[记录字段交换：处理向导代码](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)。  
  
6.  在编写创建此类的记录集对象的代码时，在 SQL 语句字符串中所有要替换的参数位置都放置一个“?”（问号）符号。  
  
     运行时，“?”占位符由传递的参数值按顺序填充。  在 [SetFieldType](../Topic/CFieldExchange::SetFieldType.md) 调用后设置的第一个参数数据成员替换 SQL 字符串中的第一个“?”，第二个参数数据成员替换第二个“?”，依此类推。  
  
> [!NOTE]
>  参数顺序很重要：`DoFieldExchange` 函数中参数的 RFX 调用顺序必须与 SQL 字符串中的参数占位符顺序相匹配。  
  
> [!TIP]
>  很可能使用的字符串是为类的 [m\_strFilter](../Topic/CRecordset::m_strFilter.md) 数据成员指定的字符串（如果有），但某些 ODBC 驱动程序可能允许其他 SQL 子句中的参数。  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a> 在运行时传递参数值  
 必须在调用 **Open**（对于新的记录集对象）或 **Requery**（对于现有对象）之前指定参数值。  
  
#### 运行时向记录集对象传递参数值  
  
1.  构造记录集对象。  
  
2.  准备一个或多个字符串（如 **m\_strFilter** 字符串），包含 SQL 语句或 SQL 语句的一部分。  将“?”占位符放置到参数信息将要处于的位置。  
  
3.  向该对象的每一个参数数据成员赋予一个运行时参数值。  
  
4.  调用 **Open** 成员函数（或对于现有记录集调用 **Requery**）。  
  
 例如，假定希望用运行时获得的信息为记录集指定筛选字符串。  假定此前已构造了 `CStudentSet` 类的记录集（名为 `rsStudent`s），现在想在其中再次查询某种特定学生信息。  
  
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
  
 记录集包含那些记录符合筛选器指定条件的学生的记录，而该筛选器已由运行时参数构造。  在此例中，记录集包含所有高年级学生的记录。  
  
> [!NOTE]
>  必要时，可以使用 [SetParamNull](../Topic/CRecordset::SetParamNull.md) 将参数数据成员的值设置为 Null。  同样，可以使用 [IsFieldNull](../Topic/CRecordset::IsFieldNull.md) 检查参数数据成员是否为 Null。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：添加、更新和删除记录 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [记录集：记录集如何选择记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)