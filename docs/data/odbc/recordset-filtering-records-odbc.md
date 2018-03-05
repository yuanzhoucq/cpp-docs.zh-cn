---
title: "记录集： 筛选记录 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b6d6e8b41e67c9f33d643a2f64c7bdf2d2251eff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-filtering-records-odbc"></a>记录集：筛选记录 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明如何筛选记录集，以便它选择仅可用记录的特定子集。 例如，你可能想要选择仅对特定的课程，如 MATH101 类部分。 筛选器是搜索条件的 SQL 的内容定义**其中**子句。 框架将其追加到记录集的 SQL 语句时**其中**子句限制选定内容。  
  
 构造对象之后但在调用之前，必须建立记录集对象的筛选器及其**打开**成员函数 (或你在调用之前**Requery**现有记录集的成员函数对象，其**打开**之前已调用成员函数)。  
  
#### <a name="to-specify-a-filter-for-a-recordset-object"></a>若要指定的记录集对象的筛选器  
  
1.  构造一个新的记录集对象 (或准备调用**Requery**现有对象)。  
  
2.  将对象的值设置[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)数据成员。  
  
     筛选器是一个以 null 结尾的字符串，包含 SQL 内容**其中**子句，但不是关键字**其中**。 例如，使用：  
  
    ```  
    m_pSet->m_strFilter = "CourseID = 'MATH101'";  
    ```  
  
     not  
  
    ```  
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";  
    ```  
  
    > [!NOTE]
    >  用单引号上面显示了文本字符串"MATH101"。 在 ODBC SQL 规范中，单引号用于表示字符的字符串文本。 查看在此情况下你 DBMS 的报价要求你 ODBC 驱动程序文档。 此语法还讨论了进一步接近本主题的结尾。  
  
3.  设置任何其他所需的选项，如排序顺序、 锁定模式下或参数。 指定一个参数是特别有用。 有关参数化筛选器的信息，请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
4.  调用**打开**为新的对象 (或**Requery**先前已打开的对象)。  
  
> [!TIP]
>  在你的筛选器中使用参数可能是用于检索记录的最有效方法。  
  
> [!TIP]
>  记录集筛选器可用于[联接](../../data/odbc/recordset-performing-a-join-odbc.md)表和使用[参数](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)基于信息获取，或在运行时计算。  
  
 记录集选择满足你指定的搜索条件的那些记录。 例如，若要指定课程筛选器上述 (假定变量`strCourseID`当前设置，例如，为"MATH101")，执行以下操作：  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
 记录集包含 MATH101 类的所有部分的记录。  
  
 请注意如何在以下示例中，使用一个字符串变量中设置筛选器字符串。 这是典型的用法。 但是，假设你想要指定文本值 100。 课程 id 下面的代码演示如何设置正确替换为文本值的筛选器字符串：  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
 请注意，使用单引号字符;如果设置了直接的筛选器字符串，筛选器字符串是**不**:  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
 上面显示的引号符合 ODBC 规格的但有些 Dbms 可能需要其他引号字符。 有关详细信息，请参阅[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
> [!NOTE]
>  如果你选择覆盖通过传递到你自己 SQL 字符串的记录集的默认 SQL 字符串**打开**，你不应设置筛选器，如果你自定义字符串具有**其中**子句。 有关重写默认的 sql 语句的详细信息，请参阅[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 对记录 (ODBC) 进行排序](../../data/odbc/recordset-sorting-records-odbc.md)   
 [记录集： 如何记录集选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [记录集： 如何记录集更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)