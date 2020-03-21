---
title: 记录集：批量获取记录 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
ms.openlocfilehash: cd9597da7ab4c405f90a145182d63945cef48c53
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079826"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>记录集：批量获取记录 (ODBC)

本主题适用于 MFC ODBC 类。

类 `CRecordset` 提供对批量行提取的支持，这意味着可以在单个提取过程中一次检索多条记录，而不是一次从数据源检索一条记录。 只能在派生的 `CRecordset` 类中实现批量行提取。 将数据从数据源传输到记录集对象的过程称为 "批量记录字段交换（Bulk RFX）"。 请注意，如果未在 `CRecordset`派生类中使用批量取行，则通过记录字段交换（RFX）传输数据。 有关详细信息，请参阅[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

本主题介绍：

- [CRecordset 如何支持批量提取行](#_core_how_crecordset_supports_bulk_row_fetching)。

- [使用批量行提取时的一些特殊注意事项](#_core_special_considerations)。

- [如何实现批量记录字段交换](#_core_how_to_implement_bulk_record_field_exchange)。

##  <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>CRecordset 如何支持批量提取行

在打开 recordset 对象之前，可以使用 `SetRowsetSize` 成员函数定义行集大小。 行集大小指定在单个提取过程中应检索多少条记录。 实现批量行提取时，默认行集大小为25。 如果未实现批量行提取，则行集大小仍固定为1。

初始化行集大小后，调用[Open](../../mfc/reference/crecordset-class.md#open)成员函数。 在此，你必须指定*dwOptions*参数的 `CRecordset::useMultiRowFetch` 选项才能实现批量提取行。 您还可以设置 `CRecordset::userAllocMultiRowBuffers` 选项。 大容量记录字段交换机制使用数组在提取过程中存储检索到的多行数据。 这些存储缓冲区可由框架自动分配，也可手动分配。 指定 `CRecordset::userAllocMultiRowBuffers` 选项意味着将进行分配。

下表列出了 `CRecordset` 提供的成员函数，以支持批量提取行。

|成员函数|说明|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|处理在提取过程中发生的任何错误的虚拟函数。|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|实现批量记录字段交换。 自动调用以将多行数据从数据源传输到记录集对象。|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|检索行集大小的当前设置。|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|指示给定提取后实际检索了多少行。 在大多数情况下，这是行集大小，除非提取了不完整的行集。|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|返回行集中特定行的提取状态。|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|刷新行集中特定行的数据和状态。|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|将光标移动到行集中的特定行。|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|将行集大小的设置更改为指定值的虚函数。|

##  <a name="special-considerations"></a><a name="_core_special_considerations"></a>特别注意事项

尽管批量取行是性能提升，但某些功能的操作方式有所不同。 在决定实现批量提取行之前，请考虑以下事项：

- 框架自动调用 `DoBulkFieldExchange` 成员函数将数据从数据源传输到 recordset 对象。 但是，数据不会从记录集传输回数据源。 调用 `AddNew`、`Edit`、`Delete`或 `Update` 成员函数将导致断言失败。 尽管 `CRecordset` 当前不提供用于更新批量数据行的机制，但你可以使用 ODBC API 函数 `SQLSetPos`来编写你自己的函数。 有关 `SQLSetPos`的详细信息，请参阅 MSDN 文档中的*ODBC SDK 程序员参考*。

- 不能对实现批量取行的记录集使用成员函数 `IsDeleted`、`IsFieldDirty`、`IsFieldNull`、`IsFieldNullable`、`SetFieldDirty`和 `SetFieldNull`。 不过，您可以调用 `GetRowStatus` 来代替 `IsDeleted`，并 `GetODBCFieldInfo` 以取代 `IsFieldNullable`。

- `Move` 操作按行集重新定位记录集。 例如，假设您打开的记录集包含100行初始行集大小为10的记录。 `Open` 提取行1到10，当前记录位于第1行。 对 `MoveNext` 的调用提取下一个行集，而不是下一行。 此行集包含第11行到第20行，当前记录位于第11行。 请注意，当实现批量提取行时，`MoveNext` 和 `Move( 1 )` 不等效。 `Move( 1 )` 提取从当前记录开始1行的行集。 在此示例中，调用 `Open` 后调用 `Move( 1 )` 将提取由第2到第11行组成的行集，当前记录位于第2行。 有关详细信息，请参阅[移动](../../mfc/reference/crecordset-class.md#move)成员函数。

- 与记录字段交换不同，向导不支持批量记录字段交换。 这意味着必须手动声明字段数据成员，并通过编写对大容量 RFX 函数的调用来手动重写 `DoBulkFieldExchange`。 有关详细信息，请参阅类库*参考*中的[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

##  <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>如何实现批量记录字段交换

大容量记录字段交换将数据源中的行集传输到记录集对象。 大容量 RFX 函数使用数组来存储此数据，以及用于存储行集中每个数据项的长度的数组。 在类定义中，必须将字段数据成员定义为指针才能访问数据数组。 此外，必须定义一组用于访问长度数组的指针。 任何参数数据成员不应声明为指针;使用大容量记录字段交换时声明参数数据成员与在使用记录字段交换时声明参数数据成员的方式相同。 下面的代码演示了一个简单的示例：

```cpp
class MultiRowSet : public CRecordset
{
public:
   // Field/Param Data
      // field data members
      long* m_rgID;
      LPSTR m_rgName;

      // pointers for the lengths
      // of the field data
      long* m_rgIDLengths;
      long* m_rgNameLengths;

      // input parameter data member
      CString m_strNameParam;

   .
   .
   .
}
```

可以手动分配这些存储缓冲区，也可以让框架执行分配。 若要自行分配缓冲区，必须在 `Open` 成员函数中指定*dwOptions*参数的 `CRecordset::userAllocMultiRowBuffers` 选项。 请确保将数组的大小至少设置为等于行集大小。 如果希望框架执行分配，应将指针初始化为 NULL。 通常在 recordset 对象的构造函数中执行此操作：

```cpp
MultiRowSet::MultiRowSet( CDatabase* pDB )
   : CRecordset( pDB )
{
   m_rgID = NULL;
   m_rgName = NULL;
   m_rgIDLengths = NULL;
   m_rgNameLengths = NULL;
   m_strNameParam = "";

   m_nFields = 2;
   m_nParams = 1;

   .
   .
   .
}
```

最后，必须重写 `DoBulkFieldExchange` 成员函数。 对于字段数据成员，请调用批量 RFX 函数;对于任何参数数据成员，请调用 RFX 函数。 如果通过将 SQL 语句或存储过程传递给 `Open`打开了记录集，则执行批量 RFX 调用的顺序必须与记录集中列的顺序相对应：同样，参数 RFX 调用的顺序必须与 SQL 语句或存储过程中的参数顺序对应。

```cpp
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )
{
   // call the Bulk RFX functions
   // for field data members
   pFX->SetFieldType( CFieldExchange::outputColumn );
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),
                  &m_rgID, &m_rgIDLengths );
   RFX_Text_Bulk( pFX, _T( "[colName]" ),
                  &m_rgName, &m_rgNameLengths, 30 );

   // call the RFX functions for
   // for parameter data members
   pFX->SetFieldType( CFieldExchange::inputParam );
   RFX_Text( pFX, "NameParam", m_strNameParam );
}
```

> [!NOTE]
>  在派生 `CRecordset` 类超出范围之前，必须调用 `Close` 成员函数。 这确保了框架分配的任何内存都已释放。 不管是否已实现批量行提取，都应始终显式调用 `Close`，这是一种良好的编程做法。

有关记录字段交换（RFX）的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关使用参数的详细信息，请参阅[CFieldExchange：： SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)和[recordset：参数化记录集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset：： m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset：： m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
