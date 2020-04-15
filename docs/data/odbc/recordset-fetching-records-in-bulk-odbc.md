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
ms.openlocfilehash: ec4d83481f6335d4c40ffb8f004b617f2ee09c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367031"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>记录集：批量获取记录 (ODBC)

本主题适用于 MFC ODBC 类。

类`CRecordset`支持批量行提取，这意味着在单个提取期间可以同时检索多个记录，而不是一次从数据源检索一条记录。 只能在派生`CRecordset`类中实现批量行提取。 将数据从数据源传输到记录集对象的过程称为批量记录字段交换 （Bulk RFX）。 请注意，如果不在`CRecordset`派生类中使用批量行提取，则数据将通过记录字段交换 （RFX） 传输。 有关详细信息，请参阅[记录字段交换 （RFX）。](../../data/odbc/record-field-exchange-rfx.md)

本主题介绍：

- [CRecordset 如何支持批量行提取](#_core_how_crecordset_supports_bulk_row_fetching)。

- [使用批量行提取时，有一些特殊注意事项](#_core_special_considerations)。

- [如何实现批量记录字段交换](#_core_how_to_implement_bulk_record_field_exchange)。

## <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>CRecordset 如何支持批量行提取

在打开记录集对象之前，可以使用`SetRowsetSize`成员函数定义行集大小。 行集大小指定在单个提取期间应检索的记录数。 实现批量行提取时，默认行集大小为 25。 如果未实现批量行提取，则行集大小将保持为 1。

初始化行集大小后，调用[Open](../../mfc/reference/crecordset-class.md#open)成员函数。 在这里，`CRecordset::useMultiRowFetch`必须指定*dwOptions*参数的选项，以实现批量行提取。 您还可以另外设置该`CRecordset::userAllocMultiRowBuffers`选项。 批量记录字段交换机制使用数组来存储在提取期间检索的多行数据。 这些存储缓冲区可以由框架自动分配，也可以手动分配它们。 指定该`CRecordset::userAllocMultiRowBuffers`选项意味着您将执行分配。

下表列出了 为支持批量行提取而`CRecordset`提供的成员函数。

|成员函数|说明|
|---------------------|-----------------|
|[检查罗塞特错误](../../mfc/reference/crecordset-class.md#checkrowseterror)|处理提取过程中发生的任何错误的虚拟函数。|
|[多布尔菲尔德交易所](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|实现批量记录字段交换。 自动调用以将数据源传输到记录集对象的多行数据。|
|[获取罗塞特大小](../../mfc/reference/crecordset-class.md#getrowsetsize)|检索行集大小的当前设置。|
|[获取行](../../mfc/reference/crecordset-class.md#getrowsfetched)|告诉给定提取后实际检索的行数。 在大多数情况下，这是行集大小，除非提取不完整的行集。|
|[获取罗维状态](../../mfc/reference/crecordset-class.md#getrowstatus)|返回行集中特定行的提取状态。|
|[刷新罗塞特](../../mfc/reference/crecordset-class.md#refreshrowset)|刷新行集中特定行的数据和状态。|
|[设置罗塞特游标位置](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|将光标移动到行集中的特定行。|
|[设置罗塞特大小](../../mfc/reference/crecordset-class.md#setrowsetsize)|将排组大小的设置更改为指定值的虚拟函数。|

## <a name="special-considerations"></a><a name="_core_special_considerations"></a>特殊注意事项

尽管批量行提取是性能提升，但某些功能的操作方式不同。 在决定实现批量行提取之前，请考虑以下事项：

- 框架自动调用`DoBulkFieldExchange`成员函数将数据从数据源传输到记录集对象。 但是，数据不会从记录集传输回数据源。 调用`AddNew``Edit`、、`Delete`或`Update`成员函数会导致断言失败。 尽管`CRecordset`目前不提供更新批量数据行的机制，但您可以使用 ODBC API 函数编写自己的函数`SQLSetPos`。 有关 的详细信息`SQLSetPos`，请参阅 MSDN 文档中*的 ODBC SDK 程序员参考*。

- 成员函数`IsDeleted` `IsFieldDirty`、 `IsFieldNull` `IsFieldNullable`、`SetFieldDirty`和`SetFieldNull`不能用于实现批量行提取的记录集。 但是，您可以调用`GetRowStatus`代替 和`GetODBCFieldInfo``IsFieldNullable``IsDeleted`

- 操作`Move`按行集重新定位记录集。 例如，假设您打开一个记录集，该记录集具有 100 条记录，初始行集大小为 10。 `Open`获取行 1 到 10，当前记录位于第 1 行。 获取`MoveNext`下一行集的调用，而不是下一行。 此行集由行 11 到 20 组成，当前记录位于第 11 行上。 请注意，`MoveNext`当`Move( 1 )`实现批量行提取时，并不等效。 `Move( 1 )`从当前记录获取 1 行开始的行集。 在此示例中，调用`Open`后调用`Move( 1 )`获取由行 2 到 11 组成的行集，当前记录位于第 2 行。 有关详细信息，请参阅[移动](../../mfc/reference/crecordset-class.md#move)成员函数。

- 与记录字段交换不同，向导不支持批量记录字段交换。 这意味着您必须手动声明字段数据成员，并通过编写对大容量 RFX`DoBulkFieldExchange`函数的调用来手动覆盖。 有关详细信息，请参阅*类库参考*中的[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

## <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>如何实现批量记录字段交换

批量记录字段交换将一排数据从数据源传输到记录集对象。 Bulk RFX 函数使用数组来存储此数据，以及数组来存储行集中中每个数据项的长度。 在类定义中，必须将字段数据成员定义为访问数据数组的指针。 此外，必须定义一组指针才能访问长度数组。 不应将任何参数数据成员声明为指针;使用批量记录字段交换时声明参数数据成员与使用记录字段交换时声明参数数据成员相同。 以下代码显示了一个简单的示例：

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

您可以手动分配这些存储缓冲区，也可以让框架执行分配。 要自己分配缓冲区，必须在`CRecordset::userAllocMultiRowBuffers``Open`成员函数中指定*dwOptions*参数的选项。 请确保设置数组的大小至少等于行集大小。 如果要让框架进行分配，则应初始化指向 NULL 的指针。 这通常在记录集对象的构造函数中完成：

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

最后，必须重写`DoBulkFieldExchange`成员函数。 对于现场数据成员，调用批量 RFX 函数;对于任何参数数据成员，调用 RFX 函数。 如果通过将 SQL 语句或存储过程`Open`传递给 来打开记录集，则进行批量 RFX 调用的顺序必须对应于记录集中列的顺序;否则，对 批量 RFX 调用的顺序必须与同样，RFX 调用参数的顺序必须对应于 SQL 语句或存储过程中参数的顺序。

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
> 在派生`CRecordset`类超出`Close`范围之前，必须调用成员函数。 这可确保释放框架分配的任何内存。 无论是否已实现批量行提取，始终显式调用`Close`都是良好的编程实践。

有关记录字段交换 （RFX） 的详细信息，请参阅[记录字段交换：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关使用参数的详细信息，请参阅[CFieldExchange：SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)和[记录集：参数化记录集 （ODBC）。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset：m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset：m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
