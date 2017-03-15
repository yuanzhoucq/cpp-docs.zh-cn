---
title: "记录集：对记录进行排序 (ODBC) | Microsoft Docs"
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
  - "ODBC 记录集, 排序"
  - "记录集, 排序"
  - "对数据进行排序, 记录集数据"
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 记录集：对记录进行排序 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本主题说明如何对记录集排序。  可以指定一列或多列作为排序的依据，并且可以为每一指定的列指定升序或降序（`ASC` 或 **DESC**；`ASC` 为默认值）。  例如，如果指定两列，则首先对第一个命名列的记录进行排序，然后对第二个命名列的记录进行排序。  SQL **ORDER BY** 子句定义排序。  框架向记录集的 SQL 查询追加 **ORDER BY** 子句后，该子句控制选定内容的排序。  
  
 必须在构造对象之后但尚未调用对象的 **Open** 成员函数之前（或在调用某个现有记录集对象的 **Requery** 成员函数之前，而该记录集的 **Open** 成员函数先前已被调用过）建立记录集的排序顺序。  
  
#### 为记录集对象指定排序顺序  
  
1.  构造一个新的记录集对象（或准备为现有对象调用 **Requery**）。  
  
2.  设置该对象的 [m\_strSort](../Topic/CRecordset::m_strSort.md) 数据成员的值。  
  
     排序是以 NULL 结尾的字符串。  它包含 **ORDER BY** 子句的内容，但不包含关键字 **ORDER BY**。  例如，使用：  
  
    ```  
    recordset.m_strSort = "LastName DESC, FirstName DESC";  
    ```  
  
     not  
  
    ```  
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";  
    ```  
  
3.  设置所需的任何其他选项，如筛选器、锁定模式或参数。  
  
4.  为新对象调用 **Open**（或为现有对象调用 **Requery**）。  
  
 选定的记录按指定要求排序。  例如，若要以降序对一组学生记录按姓进行排序，然后按名进行排序，请执行下列操作：  
  
```  
// Construct the recordset  
CStudentSet rsStudent( NULL );  
// Set the sort  
rsStudent.m_strSort = "LastName DESC, FirstName DESC";  
// Run the query with the sort in place  
rsStudent.Open( );  
```  
  
 记录集包含所有的学生记录，以降序（Z 到 A）先按姓排序，然后按名排序。  
  
> [!NOTE]
>  如果您选择通过将自己的 SQL 字符串传递给 **Open** 来重写记录集的默认 SQL 字符串，则当自定义字符串有 **ORDER BY** 子句时不应设置排序。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [记录集：筛选记录 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)