---
title: 记录集：获取 SUM 及其他聚合结果 (ODBC)
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
ms.openlocfilehash: b9e70716ad90a14bbed552d47f48d5a3317e5a62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225704"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>记录集：获取 SUM 及其他聚合结果 (ODBC)

> [!NOTE]
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建使用者。

本主题适用于 MFC ODBC 类。

本主题介绍如何使用以下 [SQL](../../data/odbc/sql.md) 关键字来获取聚合结果：

- **SUM** 计算数值数据类型列中的值的总和。

- **MIN** 提取数值数据类型列中的最小值。

- **MAX** 提取数值数据类型列中的最大值。

- **AVG** 计算数值数据类型列中所有值的平均值。

- **COUNT** 计算任何数据类型列中的记录数。

可以使用这些 SQL 函数来获取有关数据源中记录的统计信息，而不是用于从数据源中提取记录。 创建的记录集通常由包含值的单个记录（如果所有列为聚合）组成。 （如果使用了**GROUP by**子句，则可能有多个记录。）此值是由 SQL 函数执行的计算或提取的结果。

> [!TIP]
> 若要在 SQL 语句中添加 SQL GROUP BY 子句（可能还有“HAVING”子句），请将其附加到 `m_strFilter` 的末尾********。 例如：

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

可以通过对列进行筛选和排序来限制用于获取聚合结果的记录数。

> [!CAUTION]
> 某些聚合运算符将从其聚合的列返回不同的数据类型。

- **SUM**和**AVG**可能返回下一个较大的数据类型（例如，通过调用， **`int`** 返回**LONG**或 **`double`** ）。

- 不管目标列的类型是什么，“COUNT”通常会返回“LONG”********。

- “MAX”和“MIN”返回与其计算列相同的数据类型********。

     例如，**添加类**向导创建 **`long`** `m_lSales` 以容纳销售列，但需要将其替换为 `double m_dblSumSales` 数据成员以容纳聚合结果。 请参阅以下示例。

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>获取记录集的聚合结果

1. 创建记录集，如[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述，其中包含要从中获取聚合结果的列。

1. 修改记录集的 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 函数。 将表示列名称的字符串（[RFX](../../data/odbc/record-field-exchange-using-rfx.md) 函数调用的第二个参数）替换为表示列的聚合函数的字符串。 例如，将：

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     替换为：

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. 打开记录集。 聚合操作的结果保留在 `m_dblSumSales` 中。

> [!NOTE]
> 向导实际将分配没有匈牙利语前缀的数据成员名称。 例如，向导将为“Sales”列生成 `m_Sales`，而不是之前用于图中的 `m_lSales` 名称。

如果使用 [CRecordView](../../mfc/reference/crecordview-class.md) 类来查看数据，则必须更改 DDX 函数调用以显示新的数据成员值；在这种情况下，更改：

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

到:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：记录集如何选择记录（ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
