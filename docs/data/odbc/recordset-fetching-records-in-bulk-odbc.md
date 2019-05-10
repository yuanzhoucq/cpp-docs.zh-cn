---
title: 记录集：提取记录大容量 (ODBC)
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
ms.openlocfilehash: 2fdcbf18fcb0d97ba7b2a39aa9bbbd79e65a4112
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397843"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>记录集：提取记录大容量 (ODBC)

本主题适用于 MFC ODBC 类。

类`CRecordset`提供了有关批量行提取，这意味着，多个记录可以检索在一次在一次获取，而不是检索一条记录一次从数据源的支持。 您可以实现批量行提取仅在派生`CRecordset`类。 将数据从数据源传输到记录集对象的过程称为批量记录字段交换 (Bulk RFX)。 请注意，如果不使用中的批量行提取`CRecordset`的派生的类中，数据传输通过记录字段交换 (RFX)。 有关详细信息，请参阅[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。

本主题说明：

- [CRecordset 如何支持批量行提取](#_core_how_crecordset_supports_bulk_row_fetching)。

- [使用时的特殊注意事项批量取行](#_core_special_considerations)。

- [如何实现批量记录字段交换](#_core_how_to_implement_bulk_record_field_exchange)。

##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> CRecordset 如何支持大容量行提取

然后再打开记录集对象，可以定义具有的行集大小`SetRowsetSize`成员函数。 行集大小指定应在单个提取期间检索多少条记录。 实现批量行提取时，默认行集大小为 25。 如果未实现批量行提取，在 1 保持固定的行集大小。

初始化行集大小之后，请调用[打开](../../mfc/reference/crecordset-class.md#open)成员函数。 此处，必须指定`CRecordset::useMultiRowFetch`的选项*dwOptions*实现批量行提取的参数。 此外，可以设置`CRecordset::userAllocMultiRowBuffers`选项。 批量记录字段交换机制使用数组存储的数据在提取过程中检索多个行。 可以通过该框架自动分配这些存储缓冲区也可以手动分配它们。 指定`CRecordset::userAllocMultiRowBuffers`选项意味着，将执行此分配。

下表列出了提供的成员函数`CRecordset`以支持批量取行。

|成员函数|描述|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|处理提取过程中发生任何错误的虚拟函数。|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|实现批量记录字段交换。 名为自动传输到多行数据从数据源的记录集对象。|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|检索行集大小的当前设置。|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|指示给定提取后实际检索行数。 在大多数情况下，这是行集大小，除非不完整行集提取。|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|返回一个行集内的特定行提取状态。|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|刷新的数据和状态的行集内的特定行。|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|将光标移到行集内的特定行。|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|为指定的值更改的行集大小的设置的虚拟函数。|

##  <a name="_core_special_considerations"></a> 特别注意的事项

尽管批量行提取是性能提升，但某些功能的操作以不同的方式。 你决定实现批量行提取之前，请考虑以下方面：

- 框架将自动调用`DoBulkFieldExchange`成员函数将数据从数据源传输到记录集对象。 但是，数据不会传输从记录集返回到数据源。 调用`AddNew`， `Edit`， `Delete`，或`Update`成员函数导致失败的断言。 尽管`CRecordset`目前不提供一种机制，用于更新的数据大容量行，可以编写您自己的函数，通过使用 ODBC API 函数`SQLSetPos`。 有关详细信息`SQLSetPos`，请参阅*ODBC SDK 程序员参考*MSDN 文档中。

- 成员函数`IsDeleted`， `IsFieldDirty`， `IsFieldNull`， `IsFieldNullable`， `SetFieldDirty`，并`SetFieldNull`不能实现批量行提取的记录集上使用。 但是，可以调用`GetRowStatus`来代替`IsDeleted`，并`GetODBCFieldInfo`来代替`IsFieldNullable`。

- `Move`操作按行集重新定位在记录集。 例如，假设您打开包含初始行集大小为 10 的 100 条记录的记录集。 `Open` 提取行 1 到 10，与当前记录位于第 1 行。 调用`MoveNext`提取下一个行集，不是下一步的行。 此行集的行 11 到 20，与当前记录位于第 11 行组成。 请注意，`MoveNext`和`Move( 1 )`实现批量行提取时不等效。 `Move( 1 )` 提取当前记录的第 1 行开始的行集。 在此示例中，调用`Move( 1 )`后调用`Open`提取的行 2 至第 11，包括与位于第 2 行的当前记录的行集合。 有关详细信息，请参阅[移动](../../mfc/reference/crecordset-class.md#move)成员函数。

- 与不同的记录字段交换，向导不支持批量记录字段交换。 这意味着您必须手动声明字段数据成员和手动重写`DoBulkFieldExchange`通过编写对批量 RFX 函数的调用。 有关详细信息，请参阅[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)中*类库参考*。

##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> 如何实现批量记录字段交换

批量记录字段交换将行集的数据从数据源传输到记录集对象。 批量 RFX 函数使用数组来存储此数据，以及数组来存储在行集中的每个数据项的长度。 在类定义中，您必须作为指针来访问数据数组定义将字段数据成员。 此外，必须定义一组的指针访问数组的长度。 不应将任何参数的数据成员声明为指针;使用大容量记录字段交换时声明参数数据成员是作为声明它们时使用记录字段交换相同的。 下面的代码演示一个简单的示例：

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

可以手动分配这些存储缓冲区或框架完成分配。 若要自行分配缓冲区，必须指定`CRecordset::userAllocMultiRowBuffers`的选项*dwOptions*中的参数`Open`成员函数。 请确保将数组的大小设置为至少等于行集大小。 如果你想要具有框架完成分配，则应初始化为 NULL 指针。 这通常是记录集对象的构造函数中：

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

最后，您必须重写`DoBulkFieldExchange`成员函数。 对于字段数据成员调用批量 RFX 函数;对于任何参数的数据成员调用 RFX 函数。 如果通过将 SQL 语句或存储的过程，以打开记录集`Open`，在进行批量 RFX 调用的顺序必须与在记录集中的列的顺序; 同样，RFX 的顺序调用的参数必须与相对应顺序中的 SQL 语句或存储的过程的参数。

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
>  必须调用`Close`成员函数之前将派生`CRecordset`类超出作用域。 这可确保释放由框架分配任何内存。 它是一个良好的编程做法始终显式调用`Close`，无论是否已实现批量行提取。

记录字段交换 (RFX) 有关详细信息，请参阅[记录字段交换：RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关使用参数的详细信息，请参阅[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)和[记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

