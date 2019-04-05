---
title: 记录集：获取 Sum 及其他聚合结果 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
ms.openlocfilehash: e10f2e1574dae234d98d210784d4a8ddef3bb57e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025317"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>记录集：获取 Sum 及其他聚合结果 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明了如何获取聚合的结果，使用以下[SQL](../../data/odbc/sql.md)关键字：

- **SUM**计算数值数据类型列中值的总计。

- **最小值**提取数值数据类型列中的最小值。

- **最大**提取数值数据类型列中的最大值。

- **AVG**计算数值数据类型列中的所有值的平均值。

- **计数**对任何数据类型的列中的记录数进行计数。

若要获取有关数据源中的记录的统计信息而不是从数据源中提取记录使用这些 SQL 函数。 通常创建记录集包含单个记录 （如果所有列都是聚合），其中包含一个值。 (如果您使用过可能是多个记录**GROUP BY**子句。)此值是计算或执行的 SQL 函数提取的结果。

> [!TIP]
>  若要添加 SQL **GROUP BY**子句 (和可能**HAVING**子句) 到 SQL 语句，请将其追加到末尾`m_strFilter`。 例如：

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

可以限制用于获取聚合结果进行筛选和对列进行排序的记录数。

> [!CAUTION]
>  某些聚合运算符从它们正在进行聚合的列将返回不同的数据类型。

- **总和**和**AVG**可能会返回下一个较大的数据类型 (例如，使用调用`int`返回**长**或**double**)。

- **计数**通常返回**长**而不考虑目标列类型。

- **最大**并**MIN**返回它们计算的列的数据类型相同。

     例如，**添加类**向导将创建`long``m_lSales`若要容纳 Sales 列，但您需要将此替换`double m_dblSumSales`数据成员，以适应聚合结果。 请参见以下示例。

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>若要获取记录集的聚合结果

1. 创建记录集，如中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)包含你想要获取聚合结果的列。

1. 修改[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)记录集的函数。 表示列名称的字符串替换为 (第二个参数[RFX](../../data/odbc/record-field-exchange-using-rfx.md)函数调用) 与一个字符串，表示列的聚合函数。 例如，将为：

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     替换为：

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. 打开记录集。 聚合运算的结果会留在`m_dblSumSales`。

> [!NOTE]
>  该向导实际上分配没有匈牙利语前缀的数据成员名称。 例如，该向导将生成`m_Sales`Sales 列，而不是`m_lSales`早前用于图的名称。

如果使用的[CRecordView](../../mfc/reference/crecordview-class.md)类来查看数据，则必须更改 DDX 函数调用来显示新的数据成员值; 在这种情况下，将它从：

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

到:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：如何记录集选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)