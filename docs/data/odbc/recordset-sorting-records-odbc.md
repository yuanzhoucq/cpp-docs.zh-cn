---
title: "记录集： 对记录 (ODBC) 进行排序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 846b3cfd4d5abe6d0eb76cfb12840f094564c926
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-sorting-records-odbc"></a>记录集：对记录进行排序 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明如何对记录集进行排序。 还可以指定要作为排序依据的一个或多个列，并可以指定按升序或降序 (`ASC`或**DESC**;`ASC`是默认值) 为每个指定列。 例如，如果你指定两个列，记录进行排序首先在名为的第一列，然后在名为的第二个列。 SQL **ORDER BY**子句定义排序。 当框架追加**ORDER BY**子句对记录集的 SQL 查询，所选内容的排序子句则控制。  
  
 构造对象之后但在调用之前，必须建立记录集的排序顺序其**打开**成员函数 (或你在调用之前**Requery**现有记录集对象的成员函数其**打开**之前已调用成员函数)。  
  
#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>若要指定记录集对象的排序顺序  
  
1.  构造一个新的记录集对象 (或准备调用**Requery**一个现有的)。  
  
2.  将对象的值设置[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)数据成员。  
  
     排序是以 null 结尾的字符串。 它包含的内容**ORDER BY**子句，但不是关键字**ORDER BY**。 例如，使用：  
  
    ```  
    recordset.m_strSort = "LastName DESC, FirstName DESC";  
    ```  
  
     not  
  
    ```  
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";  
    ```  
  
3.  设置任何其他所需的选项，如筛选器、 锁定模式下或参数。  
  
4.  调用**打开**为新的对象 (或**Requery**现有对象)。  
  
 选择的记录进行排序所指定。 例如，要排序的一组按姓氏，则名字降序学生记录，请执行以下操作：  
  
```  
// Construct the recordset  
CStudentSet rsStudent( NULL );  
// Set the sort  
rsStudent.m_strSort = "LastName DESC, FirstName DESC";  
// Run the query with the sort in place  
rsStudent.Open( );  
```  
  
 记录集包含所有的学生记录，以降序顺序 (从 Z 到 A) 按姓氏排序，然后按名字。  
  
> [!NOTE]
>  如果你选择覆盖通过传递到你自己 SQL 字符串的记录集的默认 SQL 字符串**打开**，如果你自定义字符串具有未设置排序**ORDER BY**子句。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)