---
title: "记录集：获取 SUM 及其他聚合结果 (ODBC) | Microsoft Docs"
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
  - "ODBC 记录集, 检索 SQL 聚合值"
  - "记录集, 检索 SQL 聚合值"
  - "从记录集中检索 SQL 合计值"
  - "SQL 聚合值"
  - "SQL 聚合值, 从记录集中检索"
  - "SQL Server 项目, 从记录集中检索聚合值"
  - "SQL, 从记录集中检索聚合值"
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：获取 SUM 及其他聚合结果 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本文解释如何使用下列 [SQL](../../data/odbc/sql.md) 关键字获取聚合结果：  
  
-   **SUM** 计算数字数据类型列中值的总和。  
  
-   **MIN** 提取数字数据类型列中的最小值。  
  
-   **MAX** 提取数字数据类型列中的最大值。  
  
-   **AVG** 计算数字数据类型列中所有值的平均值。  
  
-   **COUNT** 计算任何数据类型列中的记录数。  
  
 使用这些 SQL 函数获取数据源中有关记录的统计信息，而不是从数据源中提取记录。  已创建的记录集通常由包含值的单个记录（如果所有列都是聚合的）构成。（如果使用 **GROUP BY** 子句，则记录中集可能会有多个记录。）该值为 SQL 函数执行的计算或提取的结果。  
  
> [!TIP]
>  若要将 SQL **GROUP BY** 子句（还可能包括 **HAVING** 子句）添加到 SQL 语句，请将其追加到 **m\_strFilter** 的结尾处。  例如：  
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
 可通过筛选和排序列来限制用于获取聚合结果的记录数。  
  
> [!CAUTION]
>  某些聚合运算符会从它们正在进行聚合的列中返回一个不同的数据类型。  
  
-   **SUM** 和 **AVG** 可能返回下一个更大的数据类型（例如，使用 `int` 的调用返回 **LONG** 或 **double**）。  
  
-   **COUNT** 通常忽略目标列的类型，返回 **LONG**。  
  
-   **MAX** 与 **MIN** 返回的数据类型与它们计算的列的数据类型相同。  
  
     例如，“添加类”向导创建 `long` `m_lSales` 以提供一个 Sales 列，但您需要将其替换为 `double m_dblSumSales` 数据成员以提供聚合结果。  请参见下面的示例。  
  
#### 获取记录集的聚合结果  
  
1.  创建一个包含要从中获取聚合结果的列的记录集，如[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述。  
  
2.  修改该记录集的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 函数。  在列中用表示聚合函数的字符串替换表示列名（[RFX](../../data/odbc/record-field-exchange-using-rfx.md) 函数调用的第二个参数）的字符串。  例如，替换：  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     为：  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
3.  打开记录集。  聚合操作的结果将保留在 `m_dblSumSales` 中。  
  
> [!NOTE]
>  实际上该向导分配没有匈牙利语前缀的数据成员名称。  例如，该向导为 Sales 列产生 `m_Sales` 而不是前面用于图解的 `m_lSales` 名称。  
  
 如果正使用 [CRecordView](../../mfc/reference/crecordview-class.md) 类查看数据，则必须更改 DDX 函数调用以显示新的数据成员值；这种情况下，将：  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);  
```  
  
 更改为：  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);  
```  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：记录集如何选择记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)