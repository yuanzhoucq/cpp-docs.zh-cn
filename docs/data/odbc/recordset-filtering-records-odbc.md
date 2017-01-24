---
title: "记录集：筛选记录 (ODBC) | Microsoft Docs"
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
  - "数据 [MFC], 筛选"
  - "筛选记录集"
  - "筛选器 [C++], 记录集对象"
  - "ODBC 记录集 [C++], 筛选记录"
  - "记录集 [C++], 筛选"
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：筛选记录 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本主题演示如何筛选记录集，使它只选择可用记录的特定子集。  例如，您可能想只选择特定课程（如 MATH101）的课时。  筛选器是由 SQL **WHERE** 子句的内容定义的搜索条件。  当框架将筛选器追加到记录集的 SQL 语句后，**WHERE** 子句限制选定内容。  
  
 必须在构造对象之后但尚未调用对象的 **Open** 成员函数之前（或在调用某个现有记录集对象的 **Requery** 成员函数之前，而该记录集的 **Open** 成员函数先前已被调用过）建立记录集对象的筛选器。  
  
#### 为记录集对象指定筛选器  
  
1.  构造新的记录集对象（或准备为现有对象调用 **Requery**）。  
  
2.  设置该对象的 [m\_strFilter](../Topic/CRecordset::m_strFilter.md) 数据成员的值。  
  
     筛选器是以 NULL 结尾的字符串，包含 SQL **WHERE** 子句的内容但不包含关键字 **WHERE**。  例如，使用：  
  
    ```  
    m_pSet->m_strFilter = "CourseID = 'MATH101'";  
    ```  
  
     not  
  
    ```  
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";  
    ```  
  
    > [!NOTE]
    >  上面的示例用单引号显示文本字符串“MATH101”。  在 ODBC SQL 规范中，单引号用于表示一个字符串。  查看 ODBC 驱动程序文档，了解您的 DBMS 在此情况下的引用要求。  该语法在接近本主题结尾部分还有进一步的讨论。  
  
3.  设置所需的任何其他选项，如排序顺序、锁定模式或参数。  指定参数特别有用。  有关参数化筛选器的信息，请参见[记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
4.  为新对象调用 **Open**（或为先前已打开的对象调用 **Requery**）。  
  
> [!TIP]
>  在筛选器中使用参数可能是检索记录的最有效方法。  
  
> [!TIP]
>  记录集筛选器在使用[联接](../../data/odbc/recordset-performing-a-join-odbc.md)表和基于在运行时获取或计算出的信息的[参数](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)时，十分有用。  
  
 记录集只选择那些符合指定搜索条件的记录。  例如，若要指定上述课程筛选器（假定当前已将一个变量 `strCourseID` 设置为“MATH101”），请执行下列操作：  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
 记录集包含 MATH101 所有课时的记录。  
  
 注意上面的示例中如何使用字符串变量设置筛选器字符串。  这是典型用法。  但假设您想为课程 ID 指定文本值 100。  下面的代码显示如何用常值正确设置筛选器字符串：  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
 注意单引号字符的使用；如果直接设置筛选器字符串，则筛选器字符串**不**是：  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
 上面显示的引号符合 ODBC 规范，但某些 DBMS 可能要求其他引号字符。  有关更多信息，请参见 [SQL：自定义记录集的 SQL 语句 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
> [!NOTE]
>  如果选择通过将自己的 SQL 字符串传递给 **Open** 来重写记录集的默认 SQL 字符串，则当自定义字符串有 **WHERE** 子句时不应设置筛选器。  有关重写默认 SQL 的更多信息，请参见 [SQL：自定义记录集的 SQL 语句 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：对记录进行排序 \(ODBC\)](../../data/odbc/recordset-sorting-records-odbc.md)   
 [记录集：记录集如何选择记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [记录集：锁定记录 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)