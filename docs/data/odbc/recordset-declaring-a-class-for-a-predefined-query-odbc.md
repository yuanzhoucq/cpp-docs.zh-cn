---
title: 记录集：为预定义查询声明一个类 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: e83bf2ecb24a9abfd8dc9800a3a10d2d65025336
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611258"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>记录集：为预定义查询声明一个类 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明如何创建用于预定义的查询 （有时称为存储的过程，如 Microsoft SQL Server 中所示） 的记录集类。

> [!NOTE]
>  本主题适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果已实现批量行提取，过程也是非常相似。 若要了解和一些未实现批量行提取的记录集之间的差异，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

某些数据库管理系统 (Dbms)，可创建一个预定义的查询，如某个函数在程序中调用它。 查询有一个名称，可能不带参数，并可能会返回记录。 本主题中的过程介绍如何调用返回的记录 （也可能采用参数） 的预定义的查询。

数据库类不支持更新预定义的查询。 快照预定义的查询和动态集预定义的查询之间的差异不是可更新性，而其他用户 （或其他程序中的记录集） 所做的更改是否为记录集中可见。

> [!TIP]
>  不需要调用预定义的查询不返回记录的记录集。 准备 SQL 语句，如下所述，但通过调用执行`CDatabase`成员函数[ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)。

可以创建一个单一记录集类来管理调用预定义的查询，但您必须亲自做一些工作。 向导不支持专门为此目的创建的类。

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>若要创建一个类，用于调用预定义的查询 （存储过程）

1. 使用[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)从**添加类**创建提供的大部分查询所返回的列的表的记录集类。 这将提供一个良好的开端。

1. 手动添加的任何表的查询将返回，但向导未为你创建的任何列的字段数据成员。

   例如，如果查询从另外两个表返回三列，请将 （的相应数据类型） 的六个字段数据成员添加到类中。

1. 手动添加[RFX](../../data/odbc/record-field-exchange-rfx.md)函数调用[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)类，一个对应的数据类型的每个成员函数添加字段数据成员。

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  您必须知道数据类型和设置在结果中返回的列的顺序。 RFX 函数的顺序调用中`DoFieldExchange`必须与结果集列的顺序匹配。

1. 在记录集类构造函数中手动添加新字段数据成员的初始化。

   你还必须递增的初始化值[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)数据成员。 向导会将写入初始化，但它仅涵盖它为您添加的字段数据成员。 例如：

    ```cpp
    m_nFields += 6;
    ```

   某些数据类型不应对进行初始化，例如，`CLongBinary`或字节数组。

1. 如果查询采用参数，添加每个参数、 RFX 函数调用和每个初始化的参数数据成员。

1. 必须递增`m_nParams`每个已添加参数，就像`m_nFields`对于此过程的步骤 4 中添加字段。 有关详细信息，请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

1. 手动编写 SQL 语句字符串具有以下形式：

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   其中**调用**是 ODBC 关键字**进程名称**已知数据源，是查询的名称和"？"项是你提供到记录集在运行时 （如果有） 的参数值的占位符. 下面的示例准备一个参数的占位符：

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. 在代码中，打开记录集，设置记录集的参数的值的数据成员，然后调用`Open`成员函数，传递 SQL 字符串*lpszSQL*参数。 相反，将为返回的字符串或`GetDefaultSQL`在类中的成员函数。

下面的示例演示调用名为的预定义的查询的过程`Delinquent_Accts`，后者采用一个参数的销售区域号。 此查询返回三列： `Acct_No`， `L_Name`， `Phone`。 所有列都都来自客户表。

下面的记录集指定该查询将返回和销售的参数区域号在运行时所请求的列的字段数据成员。

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

此类声明是因为向导编写它，除`m_lDistParam`手动添加的成员。 此处不显示其他成员。

下面的示例演示中的数据成员初始化`CDelinquents`构造函数。

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

请注意用于初始化[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)并[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)。 该向导初始化`m_nFields`; 您初始化`m_nParams`。

下面的示例演示中的 RFX 函数`CDelinquents::DoFieldExchange`:

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

除了生成三个返回的列的 RFX 调用，此代码还管理绑定在运行时传递的参数。 该参数进行键控到`Dist_No`（学区编号） 列。

下面的示例演示如何设置 SQL 字符串以及如何使用它来打开记录集。

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

此代码构造快照、 将其传递用户，从前面获取的参数，调用预定义的查询。 当查询运行时，它返回指定销售区域的记录。 每个记录包含的帐户数、 客户的姓氏和客户的电话号码的列。

> [!TIP]
>  你可能想要处理来自存储过程的返回值 （输出参数）。 有关详细信息和示例，请参阅[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[记录集：声明表的类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)