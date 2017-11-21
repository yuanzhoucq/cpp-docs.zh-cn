---
title: "记录集： 获取 Sum 及其他聚合结果 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f69341095e2bf6ad97e3b9c3fa0535c349c47ca3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>记录集：获取 SUM 及其他聚合结果 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明如何获取使用以下的聚合结果[SQL](../../data/odbc/sql.md)关键字：  
  
-   **SUM**计算数值数据类型列中值的总和。  
  
-   **最小值**提取数值数据类型列中的最小值。  
  
-   **最大**提取数值数据类型列中的最大值。  
  
-   **AVG**计算数值数据类型列中的所有值的平均值。  
  
-   **计数**对列中的任何数据类型的记录数进行计数。  
  
 若要获取有关数据源中的记录的统计信息而不是从数据源中提取的记录，你可以使用这些 SQL 函数。 记录集通常创建包含单个包含一个值的记录 （如果所有列都是聚合）。 (如果你使用可能是多个记录**GROUP BY**子句。)此值是由 SQL 函数执行的提取或计算的结果。  
  
> [!TIP]
>  若要添加 SQL **GROUP BY**子句 (和可能**HAVING**子句) 到 SQL 语句，请将其追加到末尾**m_strFilter**。 例如:   
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
 你可以限制使用通过筛选和排序的列，获取聚合结果的记录的数。  
  
> [!CAUTION]
>  有些聚合运算符从对其它们正在进行聚合的列返回不同的数据类型。  
  
-   **SUM**和**AVG**可能返回下一个更大的数据类型 (例如，调用`int`返回**长**或**double**)。  
  
-   **计数**通常返回**长**而不考虑目标列类型。  
  
-   **最大**和**MIN**返回相同的数据类型与它们计算的列。  
  
     例如，**添加类**向导创建`long``m_lSales`以适应销售列中，但你需要更换这一点与`double m_dblSumSales`数据成员，以容纳聚合结果。 请参见以下示例。  
  
#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>若要获取记录集的聚合结果  
  
1.  中所述创建一个记录集[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)包含你想要获取聚合结果的列。  
  
2.  修改[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)记录集的函数。 表示列名称的字符串替换 (第二个参数的[RFX](../../data/odbc/record-field-exchange-using-rfx.md)函数调用) 与一个字符串，表示在列上的聚合函数。 例如，对于替换：  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     使用：  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
3.  打开记录集。 聚合运算的结果会留在`m_dblSumSales`。  
  
> [!NOTE]
>  该向导实际上分配没有匈牙利语前缀的数据成员名称。 例如，向导将生成`m_Sales`为 Sales 列，而不是`m_lSales`前面用于图名称。  
  
 如果你使用[CRecordView](../../mfc/reference/crecordview-class.md)类来查看数据中，你必须更改 DDX 函数调用来显示新的数据成员值; 在这种情况下，将它从：  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);  
```  
  
 到:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);  
```  
  
## <a name="see-also"></a>另请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集：记录集如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)