---
title: 记录集：为预定义查询声明一个类 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: 9d19328fb82503519fd8eca083e0dd11e10883ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212948"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>记录集：为预定义查询声明一个类 (ODBC)

> [!NOTE]
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建使用者。

本主题适用于 MFC ODBC 类。

本主题介绍如何为预定义查询（有时称为存储过程，例如在 Microsoft SQL Server 中）创建记录集类。

> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果实现了批量提取行，此过程则非常相似。 若要了解实现批量行提取的记录集和不执行的记录集之间的差异，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

某些数据库管理系统 (DBMS) 使你能够创建预定义查询并从程序中像函数一样进行调用。 查询具有名称，可能会采用参数，并且可能会返回记录。 本主题中的过程描述了如何调用返回记录（可能还会采用参数）的预定义查询。

数据库类不支持更新预定义查询。 快照预定义查询和动态集预定义查询之间的差异不具有可更新性，但无论是否是其他用户（或程序中的其他记录集）所进行的更改均在记录集中可见。

> [!TIP]
>  不需要记录集即可调用不返回记录的预定义查询。 尽管可以如下所述准备 SQL 语句，但需要通过调用 `CDatabase` 成员函数 [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) 来执行它。

尽管可以创建一个单一记录集类来管理调用预定义查询，但有一些工作必须要亲自完成。 向导不支持专门为此目的创建类。

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>创建用于调用预定义查询（存储过程）的类

1. 使用“添加类”中的 [MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)为表创建一个记录集类，此表提供了查询返回的大部分列。 这使你能够为接下来的操作做好准备。

1. 手动为查询返回的但向导未创建的任何表的任何列添加字段数据成员。

   例如，如果查询从另外两个表中返回三列，则向此类添加六个字段数据成员（具有适当的数据类型）。

1. 在类的 [DoFieldExchange](../../data/odbc/record-field-exchange-rfx.md) 成员函数中手动添加 [RFX](../../mfc/reference/crecordset-class.md#dofieldexchange) 函数调用，对应每个添加的字段数据成员的数据类型。

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  必须知道结果集中返回的数据类型和列的顺序。 `DoFieldExchange` 中 RFX 函数调用的顺序必须与结果集列的顺序匹配。

1. 在记录集类构造函数中手动添加新字段数据成员的初始化。

   还必须递增 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 数据成员的初始化值。 尽管向导将编写初始化，但它仅涵盖其添加的字段数据成员。 例如：

    ```cpp
    m_nFields += 6;
    ```

   某些数据类型不应在此处进行初始化，例如，`CLongBinary` 或字节数组。

1. 如果查询会采用参数，则为每个参数添加参数数据成员、RFX 函数调用和初始化。

1. 必须为每个添加的参数递增 `m_nParams`，就像在此过程的步骤 4 中为添加的字段执行 `m_nFields` 一样。 有关详细信息，请参阅[记录集：参数化记录集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

1. 采用以下格式手动编写 SQL 语句字符串：

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   其中“CALL”是 ODBC 关键字，“proc-name”是数据源上已知的查询名称，“?”项是你在运行时提供给记录集的参数值的占位符（如果有）。 以下示例为一个参数准备占位符：

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. 在打开记录集的代码中，设置记录集的参数数据成员的值，然后调用 `Open` 成员函数，从而为 lpszSQL 参数传递你的 SQL 字符串。 或者，替换类中由 `GetDefaultSQL` 成员函数返回的字符串。

以下示例显示了调用名为 `Delinquent_Accts` 的预定义查询的过程，这将为销售地区编号采用一个参数。 此查询返回三列：`Acct_No`、`L_Name`、`Phone`。 所有列都来自“客户”表。

以下记录集指定查询返回的列的字段数据成员以及在运行时请求的销售地区编号的参数。

```cpp
class CDelinquents : public CRecordset
{
// Field/Param Data
    LONG m_lAcct_No;
    CString m_strL_Name;
    CString m_strPhone;
    LONG m_lDistParam;
    // ...
};
```

除了手动添加的 `m_lDistParam` 成员外，此类声明与向导所编写的一样。 此处不显示其他成员。

下一个示例演示了 `CDelinquents` 构造函数中数据成员的初始化。

```cpp
CDelinquents::CDelinquents(CDatabase* pdb)
   : CRecordset(pdb)
{
    // Wizard-generated params:
    m_lAcct_No = 0;
    m_strL_Name = "";
    m_strPhone = "";
    m_nFields = 3;
    // User-defined params:
    m_nParams = 1;
    m_lDistParam = 0;
}
```

请注意 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 和 [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) 的初始化。 向导将初始化 `m_nFields`；你需要初始化 `m_nParams`。

下一个示例演示了 `CDelinquents::DoFieldExchange` 中的 RFX 函数：

```cpp
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Long(pFX, "Acct_No", m_lAcct_No);
    RFX_Text(pFX, "L_Name", m_strL_Name);
    RFX_Text(pFX, "Phone", m_strPhone);
    pFX->SetFieldType(CFieldExchange::param);
    RFX_Long(pFX, "Dist_No", m_lDistParam);
}
```

除了为三个返回的列进行 RFX 调用外，此代码还管理在运行时传递的参数的绑定。 此参数与 `Dist_No`（地区编号）相匹配。

下一个示例演示了如何设置 SQL 字符串以及如何使用它来打开记录集。

```cpp
// Construct a CDelinquents recordset object
CDelinquents rsDel( NULL );
CString strSQL = "{CALL Delinquent_Accts (?)}"
// Specify a parameter value (obtained earlier from the user)
rsDel.m_lDistParam = lDistrict;
// Open the recordset and run the query
if( rsDel.Open( CRecordset::snapshot, strSQL ) )
    // Use the recordset ...
```

此代码将构造一个快照，向它传递先前从用户处获取的参数，并调用预定义查询。 查询运行时，它将返回指定销售地区的记录。 每条记录都包含帐号、客户姓氏和客户电话号码的列。

> [!TIP]
>  你可能需要处理来自存储过程的返回值（输出参数）。 有关详细信息和示例，请参阅 [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[记录集：声明表的类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)
