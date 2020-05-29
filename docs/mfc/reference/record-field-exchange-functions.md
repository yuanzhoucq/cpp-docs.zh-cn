---
title: 记录字段交换函数
ms.date: 09/17/2019
f1_keywords:
- AFXDB/RFX_Binary
- AFXDB/RFX_Bool
- AFXDB/RFX_Byte
- AFXDB/RFX_Date
- AFXDB/RFX_Double
- AFXDB/RFX_Int
- AFXDB/RFX_Long
- AFXDB/RFX_LongBinary
- AFXDB/RFX_Single
- AFXDB/RFX_Text
- AFXDB/RFX_Binary_Bulk
- AFXDB/RFX_Bool_Bulk
- AFXDB/RFX_Byte_Bulk
- AFXDB/RFX_Date_Bulk
- AFXDB/RFX_Double_Bulk
- AFXDB/RFX_Int_Bulk
- AFXDB/RFX_Long_Bulk
- AFXDB/RFX_Single_Bulk
- AFXDB/RFX_Text_Bulk
- AFXDB/DFX_Binary
- AFXDB/DFX_Bool
- AFXDB/DFX_Byte
- AFXDB/DFX_Currency
- AFXDB/DFX_DateTime
- AFXDB/DFX_Double
- AFXDB/DFX_Long
- AFXDB/DFX_LongBinary
- AFXDB/DFX_Short
- AFXDB/DFX_Single
- AFXDB/DFX_Text
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions [MFC]
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions [MFC]
- DFX functions [MFC]
- bulk RFX functions [MFC]
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions [MFC]
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
ms.openlocfilehash: bfd3ba64a33547b8a27e0f3bc896f39c94486464
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372976"
---
# <a name="record-field-exchange-functions"></a>记录字段交换函数

本主题列出了记录字段交换（RFX、Bulk RFX 和 DFX）函数，这些函数用于在记录集对象与其数据源之间自动传输数据以及对数据执行其他操作。

如果正在使用基于 ODBC 的类，并且已实现批量行提取，则必须为与数据源列对应的每个数据成员调用批量 RFX 函数，以便手动重写 `DoBulkFieldExchange` 的 `CRecordset` 成员函数。

如果您尚未在基于 ODBC 的类中实现批量行提取，或者如果您使用的是基于 DAO 的类（已过时），则 ClassWizard 将覆盖`DoFieldExchange``CRecordset`或`CDaoRecordset`通过为记录集中的每个字段数据成员调用 RFX 函数（对于 ODBC 类）或 DFX 函数（用于 DAO 类）来覆盖其成员函数。

记录字段交换函数在框架每次调用 `DoFieldExchange` 或 `DoBulkFieldExchange`时传输数据。 每个函数传输一种特定的数据类型。

有关如何使用这些函数的详细信息，请参阅 [记录字段交换：RFX 的工作方式 (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md)一文。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

对于动态绑定的数据列，你还可以自行调用 RFX 或 DFX 函数，如 [记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)一文中所述。 此外，你还可以编写自己的自定义 RFX 或 DFX 例程，如技术说明 [43](../../mfc/tn043-rfx-routines.md) （针对 ODBC）和技术说明 [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) （针对 DAO）中所述。

有关 RFX 和批量 RFX 函数在`DoFieldExchange`和`DoBulkFieldExchange`函数中显示的示例，请参阅[RFX_Text](#rfx_text)和 [RFX_Text_Bulk]#rfx_text_bulk）。 DFX 函数与 RFX 函数非常类似。

### <a name="rfx-functions-odbc"></a>RFX 函数 (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|传输 [CByteArray](cbytearray-class.md)类型的字节数组。|
|[RFX_Bool](#rfx_bool)|传输布尔数据。|
|[RFX_Byte](#rfx_byte)|传输单字节数据。|
|[RFX_Date](#rfx_date)|使用[CTime](../../atl-mfc-shared/reference/ctime-class.md)或 TIMESTAMP_STRUCT传输时间和日期数据。|
|[RFX_Double](#rfx_double)|传输双精度浮点数据。|
|[RFX_Int](#rfx_int)|传输整型数据。|
|[RFX_Long](#rfx_long)|传输长整型数据。|
|[RFX_LongBinary](#rfx_longbinary)|使用 [CLongBinary](clongbinary-class.md) 类的对象传输二进制大型对象 (BLOB) 数据。|
|[RFX_Single](#rfx_single)|传输浮点数据。|
|[RFX_Text](#rfx_text)|传输字符串数据。|

### <a name="bulk-rfx-functions-odbc"></a>批量 RFX 函数 (ODBC)

|||
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|传输字节数据数组。|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|传输布尔数据数组。|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|传输单字节数组。|
|[RFX_Date_Bulk](#rfx_date_bulk)|传输 TIMESTAMP_STRUCT 类型的数据数组。|
|[RFX_Double_Bulk](#rfx_double_bulk)|传输双精度浮点数据数组。|
|[RFX_Int_Bulk](#rfx_int_bulk)|传输整型数据数组。|
|[RFX_Long_Bulk](#rfx_long_bulk)|传输长整型数据数组。|
|[RFX_Single_Bulk](#rfx_single_bulk)|传输浮点数据数组。|
|[RFX_Text_Bulk](#rfx_text_bulk)|传输 LPSTR 类型的数据数组。|

### <a name="dfx-functions-dao"></a>DFX 函数 (DAO)

|||
|-|-|
|[DFX_Binary](#dfx_binary)|传输 [CByteArray](cbytearray-class.md)类型的字节数组。|
|[DFX_Bool](#dfx_bool)|传输布尔数据。|
|[DFX_Byte](#dfx_byte)|传输单字节数据。|
|[DFX_Currency](#dfx_currency)|传输 [COleCurrency](colecurrency-class.md)类型的货币数据。|
|[DFX_DateTime](#dfx_datetime)|传输 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)类型的时间和日期数据。|
|[DFX_Double](#dfx_double)|传输双精度浮点数据。|
|[DFX_Long](#dfx_long)|传输长整型数据。|
|[DFX_LongBinary](#dfx_longbinary)|使用 `CLongBinary` 类的对象传输二进制大型对象 (BLOB) 数据。 对于 DAO，建议改用 [DFX_Binary](#dfx_binary) 。|
|[DFX_Short](#dfx_short)|传输短整型数据。|
|[DFX_Single](#dfx_single)|传输浮点数据。|
|[DFX_Text](#dfx_text)|传输字符串数据。|

=============================================

## <a name="rfx_binary"></a><a name="rfx_binary"></a>RFX_Binary

在`CRecordset`对象的字段数据成员和 ODBC 类型SQL_BINARY、SQL_VARBINARY或SQL_LONGVARBINARY数据源上的记录列之间传输字节数组。

### <a name="syntax"></a>语法

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源[，CByteArray](cbytearray-class.md)类型的值取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*n 最大长度*<br/>
要传输的字符串或数组的最大允许长度。 *nMaxLength 的*默认值为 255。 法律价值为 1 到 INT_MAX。 框架为数据分配此空间量。 为了获得最佳性能，传递足够大的值以容纳您期望的最大数据项。

### <a name="remarks"></a>备注

这些类型的数据源中的数据映射到记录集中`CByteArray`的类型和类型。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_bool"></a><a name="rfx_bool"></a>RFX_Bool

在`CRecordset`对象的字段数据成员和 ODBC 类型数据源上的记录列之间传输布尔数据SQL_BIT。

### <a name="syntax"></a>语法

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，BOOL 类型的值取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_byte"></a><a name="rfx_byte"></a>RFX_Byte

在`CRecordset`对象的字段数据成员和 ODBC 类型数据源上的记录列之间传输单个字节SQL_TINYINT。

### <a name="syntax"></a>语法

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，将从指定数据成员中提取 BYTE 类型的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_date"></a><a name="rfx_date"></a>RFX_Date

在对象的字段数据成员与 ODBC 类型SQL_DATE、SQL_TIME或SQL_TIMESTAMP的数据源上的记录列之间传输`CTime`或TIMESTAMP_STRUCT数据。 `CRecordset`

### <a name="syntax"></a>语法

```cpp
void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   CTime& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   TIMESTAMP_STRUCT& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   COleDateTime& value);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定数据成员中的值;要传输的值。 函数的不同版本为值使用不同的数据类型：

函数的第一个版本用于引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。 对于从记录集传输到数据源，此值从指定的数据成员获取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

函数的第二个版本引用结构`TIMESTAMP_STRUCT`。 您必须在调用之前自己设置此结构。 此版本不支持对话数据交换 （DDX） 或代码向导支持。 函数的第三个版本的工作方式与第一个版本类似，只不过它引用了[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。

### <a name="remarks"></a>备注

函数`CTime`的版本施加了某些中间处理的开销，并且范围有限。 如果发现其中任一因素过于限制，请使用 函数的第二个版本。 但请注意，它缺乏代码向导和 DDX 支持，以及您自己设置结构的要求。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_double"></a><a name="rfx_double"></a>RFX_Double

在`CRecordset`对象的字段数据成员和 ODBC 类型数据源上的记录列之间传输**双浮点**数据SQL_DOUBLE。

### <a name="syntax"></a>语法

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，值（类型**为 double）** 取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_int"></a><a name="rfx_int"></a>RFX_Int

在`CRecordset`对象的字段数据成员和 ODBC 类型数据源上的记录列之间传输SQL_SMALLINT整数数据。

### <a name="syntax"></a>语法

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，从指定的数据成员获取**类型 int**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_long"></a><a name="rfx_long"></a>RFX_Long

在`CRecordset`对象的字段数据成员和 ODBC 类型数据源上的记录列之间传输长整数数据，SQL_INTEGER。

### <a name="syntax"></a>语法

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，值（类型**长**）取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a>RFX_LongBinary

使用类[CLongBinary](clongbinary-class.md)在`CRecordset`对象的字段数据成员和 ODBC 类型数据源上的记录列之间传输二进制大型对象 （BLOB） 数据，SQL_LONGVARBINARY或SQL_LONGVARCHAR。

### <a name="syntax"></a>语法

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，值类型`CLongBinary`从指定的数据成员获取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_single"></a><a name="rfx_single"></a>RFX_Single

在`CRecordset`对象的字段数据成员和 ODBC 类型数据源上的记录列之间传输浮点数据SQL_REAL。

### <a name="syntax"></a>语法

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，从指定的数据成员获取类型**float**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_text"></a><a name="rfx_text"></a>RFX_Text

在`CString``CRecordset`对象字段数据成员和 ODBC 类型数据源上SQL_LONGVARCHAR、SQL_CHAR、SQL_VARCHAR、SQL_DECIMAL或SQL_NUMERIC的数据源上记录列之间传输数据。

### <a name="syntax"></a>语法

```cpp
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类`CFieldExchange`对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，值类型`CString`从指定的数据成员获取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*n 最大长度*<br/>
要传输的字符串或数组的最大允许长度。 *nMaxLength 的*默认值为 255。 法律价值为 1 到 INT_MAX）。 框架为数据分配此空间量。 为了获得最佳性能，传递足够大的值以容纳您期望的最大数据项。

*nColumn 类型*<br/>
主要用于参数。 指示参数数据类型的整数。 该类型是窗体**SQL_XXX**的 ODBC 数据类型。

*n标尺*<br/>
指定 ODBC 类型值SQL_DECIMAL或SQL_NUMERIC的值的比例。 *nScale*仅在设置参数值时有用。 有关详细信息，请参阅*ODBC SDK 程序员参考*附录 D 中的主题"精度、比例、长度和显示大小"。

### <a name="remarks"></a>备注

所有这些类型的数据源中的数据都映射到记录集中的和记录中`CString`。

### <a name="example"></a>示例

此示例显示对`RFX_Text`的多个调用。 另请注意，两个`CFieldExchange::SetFieldType`调用 。 对于参数，您必须将调用写入`SetFieldType`其 RFX 调用。 输出列调用及其关联的 RFX 调用通常由代码向导编写。

```cpp
void CCustomer::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   // Macros such as RFX_Text() and RFX_Int() are dependent on the
   // type of the member variable, not the type of the field in the database.
   // ODBC will try to automatically convert the column value to the requested type
   RFX_Long(pFX, _T("[CustomerID]"), m_CustomerID);
   RFX_Text(pFX, _T("[ContactFirstName]"), m_ContactFirstName);
   RFX_Text(pFX, _T("[PostalCode]"), m_PostalCode);
   RFX_Text(pFX, _T("[L_Name]"), m_L_Name);
   RFX_Long(pFX, _T("[BillingID]"), m_BillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a>RFX_Binary_Bulk

将多行字节数据从 ODBC 数据源的列传输到`CRecordset`派生对象的相应数组。

### <a name="syntax"></a>语法

```cpp
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*普吉特瓦尔斯*<br/>
指向 BYTE 值数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prg 长度*<br/>
指向长整数数组的指针。 此数组将存储*prgByteVals*指向的数组中每个值的长度（ 请注意，如果相应的数据项包含 Null 值，则将存储SQL_NULL_DATA值。 有关详细信息，请参阅`SQLBindCol`*ODBC SDK 程序员参考中的 ODBC*API 函数。

*n 最大长度*<br/>
*prgByteVals*指向的数组中存储的值的最大允许长度。 为确保数据不会被截断，传递足够大的值以容纳预期的最大数据项。

### <a name="remarks"></a>备注

数据源列可以具有 ODBC 类型的SQL_BINARY、SQL_VARBINARY或SQL_LONGVARBINARY。 记录集必须定义指向 BYTE 的类型指针的字段数据成员。

如果将*prgByteVals*和*prgLengths*初始化到 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
> 批量记录字段交换仅将数据从数据源传输到记录集对象。 为了使记录集可更新，必须使用 ODBC API 函数`SQLSetPos`。

有关详细信息，请参阅[记录集：批量提取记录 （ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 （RFX） 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a>RFX_Bool_Bulk

将多行布尔数据从 ODBC 数据源的列传输到`CRecordset`派生对象的相应数组。

### <a name="syntax"></a>语法

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*普格布尔瓦尔茨*<br/>
指向 BOOL 值数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prg 长度*<br/>
指向长整数数组的指针。 此数组将存储*prgBoolVals*指向的数组中每个值的长度（ 请注意，如果相应的数据项包含 Null 值，则将存储SQL_NULL_DATA值。 有关详细信息，请参阅`SQLBindCol`*ODBC SDK 程序员参考中的 ODBC*API 函数。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的SQL_BIT。 记录集必须定义指向 BOOL 的类型数据成员。

如果将*prgBoolVals*和*prgLengths*初始化到 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
> 批量记录字段交换仅将数据从数据源传输到记录集对象。 要使记录集可更新，必须使用 ODBC API 函数`SQLSetPos`。

有关详细信息，请参阅[记录集：批量提取记录 （ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 （RFX） 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a>RFX_Byte_Bulk

将多行单字节从 ODBC 数据源的列传输到`CRecordset`派生对象中的相应数组。

### <a name="syntax"></a>语法

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*普吉特瓦尔斯*<br/>
指向 BYTE 值数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prg 长度*<br/>
指向长整数数组的指针。 此数组将存储*prgByteVals*指向的数组中每个值的长度（ 请注意，如果相应的数据项包含 Null 值，则将存储SQL_NULL_DATA值。 有关详细信息，请参阅`SQLBindCol`*ODBC SDK 程序员参考中的 ODBC*API 函数。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的SQL_TINYINT。 记录集必须定义指向 BYTE 的类型指针的字段数据成员。

如果将*prgByteVals*和*prgLengths*初始化到 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
> 批量记录字段交换仅将数据从数据源传输到记录集对象。 要使记录集可更新，必须使用 ODBC API 函数`SQLSetPos`。

有关详细信息，请参阅[记录集：批量提取记录 （ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 （RFX） 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a>RFX_Date_Bulk

将多行TIMESTAMP_STRUCT数据从 ODBC 数据源的列传输到`CRecordset`派生对象的相应数组。

### <a name="syntax"></a>语法

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*普格茨瓦尔斯*<br/>
指向TIMESTAMP_STRUCT值数组的指针。 此数组将存储要从数据源传输到记录集的数据。 有关TIMESTAMP_STRUCT数据类型的详细信息，请参阅*ODBC SDK 程序员参考*附录 D 中的"C 数据类型"主题。

*prg 长度*<br/>
指向长整数数组的指针。 此数组将存储*prgTSVals*指向的数组中每个值的长度（ 请注意，如果相应的数据项包含 Null 值，则将存储SQL_NULL_DATA值。 有关详细信息，请参阅`SQLBindCol`*ODBC SDK 程序员参考中的 ODBC*API 函数。

### <a name="remarks"></a>备注

数据源列可以具有 ODBC 类型的SQL_DATE、SQL_TIME或SQL_TIMESTAMP。 记录集必须定义指向TIMESTAMP_STRUCT的类型指针的字段数据成员。

如果将*prgTSVals*和*prgLengths*初始化到 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
> 批量记录字段交换仅将数据从数据源传输到记录集对象。 要使记录集可更新，必须使用 ODBC API 函数`SQLSetPos`。

有关详细信息，请参阅[记录集：批量提取记录 （ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 （RFX） 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a>RFX_Double_Bulk

将多行双精度浮点数据从 ODBC 数据源的列传输到`CRecordset`派生对象的相应数组。

### <a name="syntax"></a>语法

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*普格德瓦尔斯*<br/>
指向**双**值数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prg 长度*<br/>
指向长整数数组的指针。 此数组将存储*prgDblVals*指向的数组中每个值的长度（ 请注意，如果相应的数据项包含 Null 值，则将存储SQL_NULL_DATA值。 有关详细信息，请参阅`SQLBindCol`*ODBC SDK 程序员参考中的 ODBC*API 函数。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的SQL_DOUBLE。 记录集必须定义类型指针为**double**的字段数据成员。

如果将*prgDblVals*和*prgLengths*初始化到 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
> 批量记录字段交换仅将数据从数据源传输到记录集对象。 要使记录集可更新，必须使用 ODBC API 函数`SQLSetPos`。

有关详细信息，请参阅[记录集：批量提取记录 （ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 （RFX） 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a>RFX_Int_Bulk

在`CRecordset`对象的字段数据成员和 ODBC 类型数据源上的记录列之间传输SQL_SMALLINT整数数据。

### <a name="syntax"></a>语法

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关`CFieldExchange`对象可以指定的操作的详细信息，请参阅[记录字段交换的文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，从指定的数据成员获取**类型 int**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a>RFX_Long_Bulk

将多行长整数数据从 ODBC 数据源的列传输到`CRecordset`派生对象的相应数组。

### <a name="syntax"></a>语法

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*普龙瓦尔斯*<br/>
指向长整数数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prg 长度*<br/>
指向长整数数组的指针。 此数组将存储*prgLongVals*指向的数组中每个值的长度（ 以字节为单位）。 请注意，如果相应的数据项包含 Null 值，则将存储SQL_NULL_DATA值。 有关详细信息，请参阅`SQLBindCol`*ODBC SDK 程序员参考中的 ODBC*API 函数。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的SQL_INTEGER。 记录集必须定义指向**long**的类型指针的字段数据成员。

如果将*prgLongVals*和*prgLengths*初始化到 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
> 批量记录字段交换仅将数据从数据源传输到记录集对象。 要使记录集可更新，必须使用 ODBC API 函数`SQLSetPos`。

有关详细信息，请参阅[记录集：批量提取记录 （ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 （RFX） 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a>RFX_Single_Bulk

将多行浮点数据从 ODBC 数据源的列传输到`CRecordset`派生对象的相应数组。

### <a name="syntax"></a>语法

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*prgFltVals*<br/>
指向**浮点**值数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prg 长度*<br/>
指向长整数数组的指针。 此数组将存储*prgFltVals*指向的数组中每个值的长度（ 请注意，如果相应的数据项包含 Null 值，则将存储SQL_NULL_DATA值。 有关详细信息，请参阅`SQLBindCol`*ODBC SDK 程序员参考中的 ODBC*API 函数。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的SQL_REAL。 记录集必须定义要**浮动**的类型指针的字段数据成员。

如果将*prgFltVals*和*prgLengths*初始化到 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
> 批量记录字段交换仅将数据从数据源传输到记录集对象。 要使记录集可更新，必须使用 ODBC API 函数`SQLSetPos`。

有关详细信息，请参阅[记录集：批量提取记录 （ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 （RFX） 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a>RFX_Text_Bulk

将多行字符数据从 ODBC 数据源的列传输到`CRecordset`派生对象的相应数组。

### <a name="syntax"></a>语法

```cpp
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换文章：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*sz名称*<br/>
数据列的名称。

*普格斯特瓦尔斯*<br/>
指向 LPSTR 值数组的指针。 此数组将存储要从数据源传输到记录集的数据。 请注意，使用当前版本的 ODBC 时，这些值不能为 Unicode。

*prg 长度*<br/>
指向长整数数组的指针。 此数组将存储*prgStrVals*指向的数组中每个值的长度（ 此长度不包括空终止字符。 请注意，如果相应的数据项包含 Null 值，则将存储SQL_NULL_DATA值。 有关详细信息，请参阅`SQLBindCol`*ODBC SDK 程序员参考中的 ODBC*API 函数。

*n 最大长度*<br/>
*prgStrVals*指向的数组中存储的值的最大允许长度，包括空终止字符。 为确保数据不会被截断，传递足够大的值以容纳预期的最大数据项。

### <a name="remarks"></a>备注

数据源列可以具有 ODBC 类型的SQL_LONGVARCHAR、SQL_CHAR、SQL_VARCHAR、SQL_DECIMAL或SQL_NUMERIC。 记录集必须定义 LPSTR 类型的字段数据成员。

如果将*prgStrVals*和*prgLengths*初始化到 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
> 批量记录字段交换仅将数据从数据源传输到记录集对象。 要使记录集可更新，必须使用 ODBC API 函数`SQLSetPos`。

有关详细信息，请参阅[记录集：批量提取记录 （ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 （RFX） 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

您必须在`DoBulkFieldExchange`重写中手动写入调用。 此示例显示对`RFX_Text_Bulk`的调用，以及对`RFX_Long_Bulk`的数据传输的调用。 这些调用之前先调用[CFieldExchange：：SetFieldType](cfieldexchange-class.md#setfieldtype)。 请注意，对于参数，必须调用 RFX 函数，而不是批量 RFX 函数。

```cpp
void CMultiCustomer::DoBulkFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Long_Bulk(pFX, _T("[CustomerID]"), &m_pCustomerID, &m_pcCustomerID);
   RFX_Text_Bulk(pFX, _T("[ContactFirstName]"), &m_pContactFirstName, &m_pcContactFirstName, 50);
   RFX_Text_Bulk(pFX, _T("[PostalCode]"), &m_pPostalCode, &m_pcPostalCode, 50);
   RFX_Text_Bulk(pFX, _T("[L_Name]"), &m_pL_Name, &m_pcL_Name, 50);
   RFX_Long_Bulk(pFX, _T("[BillingID]"), &m_pBillingID, &m_pcBillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="dfx_binary"></a><a name="dfx_binary"></a>DFX_Binary

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录的列之间传输字节数组。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源[，CByteArray](cbytearray-class.md)类型的值取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*nPreAllocsize*<br/>
框架预分配此内存量。 如果数据较大，框架将根据需要分配更多空间。 为了更好的性能，将此大小设置为足够大的值，以防止重新分配。 默认大小在 AFXDAO 中定义。H 文件为AFX_DAO_BINARY_DEFAULT_SIZE。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_DISABLE_FIELD_CACHE不使用双重缓冲，您必须自己调用[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull。](cdaorecordset-class.md#setfieldnull) 另一个可能的值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲，您不必执行额外的工作来标记字段脏或 Null。 出于性能和内存原因，请避免此值，除非您的二进制数据相对较小。

> [!NOTE]
> 通过设置[CDaoRecordset：：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对所有字段双缓冲数据。

### <a name="remarks"></a>备注

数据在 DAO 中的DAO_BYTES类型和记录集中的[CByteArray](cbytearray-class.md)类型之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_bool"></a><a name="dfx_bool"></a>DFX_Bool

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录的列之间传输布尔数据。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，BOOL 类型的值取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲。 另一个可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

数据在 DAO 中的类型DAO_BOOL和记录集中的 BOOL 类型之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_byte"></a><a name="dfx_byte"></a>DFX_Byte

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录的列之间传输单个字节。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，将从指定数据成员中提取 BYTE 类型的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲。 另一个可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

数据在 DAO 中的类型 DAO_BYTES 和记录集中的类型 BYTE 之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_currency"></a><a name="dfx_currency"></a>DFX_Currency

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录的列之间传输货币数据。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，此值取自[COleCurrency](colecurrency-class.md)类型的指定数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲。 另一个可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

数据在 DAO 中的DAO_CURRENCY类型和记录集中的[COleCurrency](colecurrency-class.md)类型之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a>DFX_DateTime

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录的列之间传输时间和日期数据。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 该函数引用[COleDateTime 对象](../../atl-mfc-shared/reference/coledatetime-class.md)。 对于从记录集传输到数据源，此值从指定的数据成员获取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲。 另一个可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

数据在 DAO 中的类型DAO_DATE和记录集中的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)类型之间映射。

> [!NOTE]
> `COleDateTime`在 DAO 类中替换[CTime](../../atl-mfc-shared/reference/ctime-class.md)和 TIMESTAMP_STRUCT。 `CTime`并且TIMESTAMP_STRUCT仍用于基于 ODBC 的数据访问类。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_double"></a><a name="dfx_double"></a>DFX_Double

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录的列之间传输**双浮点**数据。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，值（类型**为 double）** 取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲。 另一个可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

数据在 DAO 中的类型DAO_R8和记录集中的双**浮点**类型之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_long"></a><a name="dfx_long"></a>DFX_Long

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录的列之间传输长整数数据。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，值（类型**长**）取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲。 另一个可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

数据在 DAO 中的类型DAO_I4和记录集中的类型**长**之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a>DFX_LongBinary

**重要**建议您使用[DFX_Binary](#dfx_binary)而不是此功能。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源[，CLongBinary](clongbinary-class.md)类型的值取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwPreAllocsize*<br/>
框架预分配此内存量。 如果数据较大，框架将根据需要分配更多空间。 为了更好的性能，将此大小设置为足够大的值，以防止重新分配。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 AFX_DISABLE_FIELD_CACHE 不使用双重缓冲。 另一个可能的值是AFX_DAO_ENABLE_FIELD_CACHE。 使用双重缓冲，您不必执行额外的工作来标记字段脏或 Null。 出于性能和内存原因，请避免此值，除非您的二进制数据相对较小。

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

`DFX_LongBinary`提供与 MFC ODBC 类兼容。 `DFX_LongBinary` 函数在 [CDaoRecordset](cdaorecordset-class.md) 对象的字段数据成员和数据源上的记录列之间使用`CLongBinary`类传输二进制大型对象（BLOB）数据。   数据在 DAO 中的类型DAO_BYTES和记录集中的[CLongBinary](clongbinary-class.md)类型之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_short"></a><a name="dfx_short"></a>DFX_Short

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录的列之间传输短整数数据。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，从指定的数据成员获取类型为**short**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲。 另一个可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

数据在 DAO 中的类型DAO_I2和记录集中的**短**类型之间映射。

> [!NOTE]
> `DFX_Short`等效于基于 ODBC 的类[RFX_Int。](#rfx_int)

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_single"></a><a name="dfx_single"></a>DFX_Single

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录的列之间传输浮点数据。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源，从指定的数据成员获取类型**float**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲。 另一个可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

数据在 DAO 中的类型DAO_R4和记录集中的**浮点**类型之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="dfx_text"></a><a name="dfx_text"></a>DFX_Text

在`CString` [CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上记录列之间传输数据。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>参数

*pFX*<br/>
指向类[CDaoFieldExchange](cdaofieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*sz名称*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集传输到数据源[，CString](../../atl-mfc-shared/reference/cstringt-class.md)类型的值取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*nPreAllocsize*<br/>
框架预分配此内存量。 如果数据较大，框架将根据需要分配更多空间。 为了更好的性能，将此大小设置为足够大的值，以防止重新分配。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值AFX_DAO_ENABLE_FIELD_CACHE使用双缓冲。 另一个可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须亲自致电[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull。](cdaorecordset-class.md#setfieldnull)

> [!NOTE]
> 通过设置[CDaoRecordset：：m_bCheckCacheForDirtyFields，](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制默认情况下是否对数据进行双重缓冲。

### <a name="remarks"></a>备注

数据在 DAO 中的类型DAO_CHAR（或者，如果定义了符号_UNICODE，DAO_WCHAR）和记录集中的[CString](../../atl-mfc-shared/reference/cstringt-class.md)类型之间映射。  n

### <a name="example"></a>示例

此示例显示对`DFX_Text`的多个调用。 另请注意，两个呼叫到[CDaoFieldExchange：setFieldType](cdaofieldexchange-class.md#setfieldtype)。 您必须将第一个调用`SetFieldType`写入其**DFX**调用。 第二个调用及其关联的**DFX**调用通常由生成类的代码向导编写。

```cpp
void CCustSet::DoFieldExchange(CDaoFieldExchange* pFX)
{
   pFX->SetFieldType(CDaoFieldExchange::param);
   DFX_Text(pFX, _T("Param"), m_strParam);
   pFX->SetFieldType(CDaoFieldExchange::outputColumn);
   DFX_Short(pFX, _T("EmployeeID"), m_EmployeeID);
   DFX_Text(pFX, _T("LastName"), m_LastName);
   DFX_Short(pFX, _T("Age"), m_Age);
   DFX_DateTime(pFX, _T("hire_date"), m_hire_date);
   DFX_DateTime(pFX, _T("termination_date"), m_termination_date);

   CDaoRecordset::DoFieldExchange(pFX);
}
```

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
[CRecordset：:DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[C记录集：:DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDao记录集：:DoFieldExchange](cdaorecordset-class.md#dofieldexchange)
