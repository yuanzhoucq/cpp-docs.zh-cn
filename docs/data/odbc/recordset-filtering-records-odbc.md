---
title: 记录集： 筛选记录 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1196bc41022a3202a55ad1ba5c208b8a8fdbbcc5
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340607"
---
# <a name="recordset-filtering-records-odbc"></a>记录集：筛选记录 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明如何筛选记录集，以便它选择仅可用记录的特定子集。 例如，你可能想要选择仅对特定的课程，如 MATH101 类部分。 筛选器是由 SQL 的内容定义的搜索条件**其中**子句。 该框架将其追加到记录集的 SQL 语句时**其中**子句限制选定内容。  
  
 构造对象后，但在调用之前，必须建立记录集对象的筛选器及其`Open`成员函数 (或在调用之前`Requery`成员函数的现有记录集对象，其`Open`成员函数具有被调用过）。  
  
#### <a name="to-specify-a-filter-for-a-recordset-object"></a>若要指定记录集对象的筛选器  
  
1.  构造一个新的记录集对象 (或准备调用`Requery`现有对象)。  
  
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
    >  用单引号上面显示了文本字符串"MATH101"。 在 ODBC SQL 规范中，使用单引号来表示字符的字符串文字。 查看在此情况下所使用的 DBMS 的引号要求您 ODBC 驱动程序文档。 此语法还讨论了进一步接近本主题的结尾。  
  
3.  设置任何其他所需的选项，如排序顺序、 锁定模式或参数。 指定一个参数是特别有用。 有关参数化筛选器的信息，请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
4.  调用`Open`为新的对象 (或`Requery`以前打开的对象)。  
  
> [!TIP]
>  在你的筛选器中使用参数可能是用于检索记录的最有效方法。  
  
> [!TIP]
>  记录集筛选器的作用[加入](../../data/odbc/recordset-performing-a-join-odbc.md)表，而用于[参数](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)基于信息获取，或运行时计算的。  
  
 记录集选择满足你指定的搜索条件的记录。 例如，若要指定课程筛选器上面所述 (假定变量`strCourseID`当前设置，例如，为"MATH101")，执行以下操作：  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
 记录集包含 MATH101 类的所有部分的记录。  
  
 请注意，上面的示例中使用字符串变量中如何设置筛选器字符串。 这是典型的用法。 但是，假设你想要指定文字值 100 的课程 id。 下面的代码演示如何设置文本值与正确的筛选器字符串：  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
 请注意，使用单引号字符;如果直接设置的筛选器字符串，则筛选器字符串**不**:  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
 上面显示的引号符合 ODBC 规范，但某些 Dbms 可能需要其他引号字符。 有关详细信息，请参阅[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
> [!NOTE]
>  如果你选择覆盖通过将传递到你自己的 SQL 字符串的记录集的默认 SQL 字符串`Open`，如果具有自定义的字符串，不应设置筛选器**其中**子句。 有关重写默认的 sql 语句的详细信息，请参阅[SQL： 自定义您记录集的 SQL 语句 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 对记录 (ODBC) 进行排序](../../data/odbc/recordset-sorting-records-odbc.md)   
 [记录集： 如何记录集选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [记录集： 如何记录集更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)