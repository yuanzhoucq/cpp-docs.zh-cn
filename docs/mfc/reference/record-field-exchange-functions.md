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
ms.openlocfilehash: 491b00fe65634acf7c8805dd471fa6e3cc62acf0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426605"
---
# <a name="record-field-exchange-functions"></a>记录字段交换函数

本主题列出了记录字段交换（RFX、Bulk RFX 和 DFX）函数，这些函数用于在记录集对象与其数据源之间自动传输数据以及对数据执行其他操作。

如果正在使用基于 ODBC 的类，并且已实现批量行提取，则必须为与数据源列对应的每个数据成员调用批量 RFX 函数，以便手动重写 `DoBulkFieldExchange` 的 `CRecordset` 成员函数。

如果未在基于 ODBC 的类中实现批量提取，或者使用基于 DAO 的类（已过时），则 ClassWizard 将通过为记录集中的每个字段数据成员调用 RFX 函数（对于 ODBC 类）或 DFX 函数（对于 DAO 类）来重写 `CRecordset` 或 `CDaoRecordset` 的 `DoFieldExchange` 成员函数。

记录字段交换函数在框架每次调用 `DoFieldExchange` 或 `DoBulkFieldExchange`时传输数据。 每个函数传输一种特定的数据类型。

有关如何使用这些函数的详细信息，请参阅 [记录字段交换：RFX 的工作方式 (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md)一文。 有关批量行提取的详细信息，请参阅 [记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

对于动态绑定的数据列，你还可以自行调用 RFX 或 DFX 函数，如 [记录集：动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)一文中所述。 此外，你还可以编写自己的自定义 RFX 或 DFX 例程，如技术说明 [43](../../mfc/tn043-rfx-routines.md) （针对 ODBC）和技术说明 [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) （针对 DAO）中所述。

有关在 `DoFieldExchange` 和 `DoBulkFieldExchange` 函数中出现 RFX 和批量 RFX 函数的示例，请参阅[RFX_Text](#rfx_text)和 [RFX_Text_Bulk] #rfx_text_bulk）。 DFX 函数与 RFX 函数非常类似。

### <a name="rfx-functions-odbc"></a>RFX 函数 (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|传输 [CByteArray](cbytearray-class.md)类型的字节数组。|
|[RFX_Bool](#rfx_bool)|传输布尔数据。|
|[RFX_Byte](#rfx_byte)|传输单字节数据。|
|[RFX_Date](#rfx_date)|使用[CTime](../../atl-mfc-shared/reference/ctime-class.md)或 TIMESTAMP_STRUCT 传输时间和日期数据。|
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

## <a name="rfx_binary"></a>  RFX_Binary

在 `CRecordset` 对象的字段数据成员和 ODBC 类型的数据源上的记录列之间传输字节数组 SQL_BINARY、SQL_VARBINARY 或 SQL_LONGVARBINARY。

### <a name="syntax"></a>语法

```
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取[CByteArray](cbytearray-class.md)类型的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*nMaxLength*<br/>
所传输的字符串或数组的最大允许长度。 *NMaxLength*的默认值为255。 合法值是1到 INT_MAX。 框架为数据分配此空间量。 为了获得最佳性能，传递一个足够大的值以容纳所需的最大数据项。

### <a name="remarks"></a>备注

这些类型的数据源中的数据映射到记录集的类型 `CByteArray`。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_bool"></a>  RFX_Bool

在 `CRecordset` 对象的字段数据成员和 ODBC 类型 SQL_BIT 的数据源上的记录列之间传输布尔数据。

### <a name="syntax"></a>语法

```
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，将从指定的数据成员中获取类型为 BOOL 的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_byte"></a>  RFX_Byte

在 `CRecordset` 对象的字段数据成员和 ODBC 类型 SQL_TINYINT 的数据源上的记录列之间传输单个字节。

### <a name="syntax"></a>语法

```
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，将从指定数据成员中提取 BYTE 类型的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_date"></a>  RFX_Date

在 `CRecordset` 对象的字段数据成员和 ODBC 类型的数据源上的记录列之间传输 `CTime` 或 TIMESTAMP_STRUCT 数据 SQL_DATE、SQL_TIME 或 SQL_TIMESTAMP。

### <a name="syntax"></a>语法

```
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

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
在指示的数据成员中存储的值;要传输的值。 函数的各种版本采用不同的数据类型作为值：

函数的第一个版本采用对[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。 对于从记录集到数据源的传输，此值取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

函数的第二个版本采用对 `TIMESTAMP_STRUCT` 结构的引用。 在调用之前，必须自行设置此结构。 在此版本中，不支持对话框数据交换（DDX）支持或代码向导支持。 函数的第三个版本的工作方式类似于第一个版本，只不过它采用对[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用。

### <a name="remarks"></a>备注

函数的 `CTime` 版本会对某些中间处理的开销产生一定的开销。 如果发现其中一个因素太有限，请使用第二个版本的函数。 但请注意，缺少代码向导和 DDX 支持以及自行设置结构的要求。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_double"></a>  RFX_Double

在 `CRecordset` 对象的字段数据成员和 ODBC 类型 SQL_DOUBLE 的数据源上的记录列之间传输**双精度浮点**数据。

### <a name="syntax"></a>语法

```
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取类型为**double**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_int"></a>  RFX_Int

在 `CRecordset` 对象的字段数据成员和 ODBC 类型 SQL_SMALLINT 的数据源中记录的列之间传输整数数据。

### <a name="syntax"></a>语法

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取值（类型为**int**）。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_long"></a>  RFX_Long

在 `CRecordset` 对象的字段数据成员和 ODBC 类型 SQL_INTEGER 的数据源中记录的列之间传输长整数数据。

### <a name="syntax"></a>语法

```
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，会从指定的数据成员获取类型为**long**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_longbinary"></a>  RFX_LongBinary

使用类[CLongBinary](clongbinary-class.md)传输二进制大型对象（BLOB）数据在 `CRecordset` 对象的字段数据成员和 ODBC 类型的数据源上的记录列 SQL_LONGVARBINARY 或 SQL_LONGVARCHAR。

### <a name="syntax"></a>语法

```
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，会从指定的数据成员获取类型 `CLongBinary`的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_single"></a>  RFX_Single

在 `CRecordset` 对象的字段数据成员和 ODBC 类型 SQL_REAL 的数据源中记录的列之间传输浮点数据。

### <a name="syntax"></a>语法

```
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取类型为**float**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_text"></a>  RFX_Text

传输 `CRecordset` 对象的字段数据成员与 ODBC 类型 SQL_LONGVARCHAR、SQL_CHAR、SQL_VARCHAR、SQL_DECIMAL 或 SQL_NUMERIC 的数据源中记录的列之间 `CString` 数据。

### <a name="syntax"></a>语法

```
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向 `CFieldExchange`类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，会从指定的数据成员获取类型 `CString`的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*nMaxLength*<br/>
所传输的字符串或数组的最大允许长度。 *NMaxLength*的默认值为255。 合法值为1到 INT_MAX）。 框架为数据分配此空间量。 为了获得最佳性能，传递一个足够大的值以容纳所需的最大数据项。

*nColumnType*<br/>
主要用于参数。 一个整数，指示参数的数据类型。 类型是**SQL_XXX**格式的 ODBC 数据类型。

*nScale*<br/>
指定 ODBC 类型 SQL_DECIMAL 或 SQL_NUMERIC 的值的小数位数。 *nScale*仅在设置参数值时才有用。 有关详细信息，请参阅*ODBC SDK 程序员参考*的附录 D 中的 "精度、小数位数、长度和显示大小" 主题。

### <a name="remarks"></a>备注

所有这些类型的数据源中的数据都将映射到记录集中的 `CString`。

### <a name="example"></a>示例

此示例演示对 `RFX_Text`的多个调用。 另请注意对 `CFieldExchange::SetFieldType`的两次调用。 对于参数，必须将调用写入 `SetFieldType` 及其 RFX 调用。 输出列调用及其关联 RFX 调用通常由代码向导编写。

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

**标头：** afxdb

## <a name="rfx_binary_bulk"></a>  RFX_Binary_Bulk

将 ODBC 数据源的列中的多行数据传输到 `CRecordset`派生对象中的相应数组。

### <a name="syntax"></a>语法

```
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*prgByteVals*<br/>
指向字节值的数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prgLengths*<br/>
指向长整数数组的指针。 此数组将存储*prgByteVals*所指向的数组中每个值的长度（以字节为单位）。 请注意，如果对应数据项包含 Null 值，则将存储 SQL_NULL_DATA 的值。 有关更多详细信息，请参阅*ODBC SDK 程序员参考*中的 odbc API 函数 `SQLBindCol`。

*nMaxLength*<br/>
*PrgByteVals*所指向的数组中存储的值的最大允许长度。 若要确保不会截断数据，请传递一个足够大的值以容纳所需的最大数据项。

### <a name="remarks"></a>备注

数据源列可以具有 ODBC 类型的 SQL_BINARY、SQL_VARBINARY 或 SQL_LONGVARBINARY。 记录集必须将类型为指针的字段数据成员定义为 BYTE。

如果将*prgByteVals*和*PRGLENGTHS*初始化为 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
>  大容量记录字段交换仅将数据从数据源传输到 recordset 对象。 为了使记录集可更新，必须使用 ODBC API 函数 `SQLSetPos`。

有关详细信息，请参阅文章[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_bool_bulk"></a>  RFX_Bool_Bulk

将 ODBC 数据源的列中的多行数据传输到 `CRecordset`派生对象中的相应数组。

### <a name="syntax"></a>语法

```
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*prgBoolVals*<br/>
指向布尔值的数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prgLengths*<br/>
指向长整数数组的指针。 此数组将存储*prgBoolVals*所指向的数组中每个值的长度（以字节为单位）。 请注意，如果对应数据项包含 Null 值，则将存储 SQL_NULL_DATA 的值。 有关更多详细信息，请参阅*ODBC SDK 程序员参考*中的 odbc API 函数 `SQLBindCol`。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的 SQL_BIT。 记录集必须将类型指针的字段数据成员定义为 BOOL。

如果将*prgBoolVals*和*PRGLENGTHS*初始化为 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
>  大容量记录字段交换仅将数据从数据源传输到 recordset 对象。 若要使记录集可更新，必须使用 ODBC API 函数 `SQLSetPos`。

有关详细信息，请参阅文章[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_byte_bulk"></a>  RFX_Byte_Bulk

将 ODBC 数据源的列中的多行传输到 `CRecordset`派生对象中的相应数组。

### <a name="syntax"></a>语法

```
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*prgByteVals*<br/>
指向字节值的数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prgLengths*<br/>
指向长整数数组的指针。 此数组将存储*prgByteVals*所指向的数组中每个值的长度（以字节为单位）。 请注意，如果对应数据项包含 Null 值，则将存储 SQL_NULL_DATA 的值。 有关更多详细信息，请参阅*ODBC SDK 程序员参考*中的 odbc API 函数 `SQLBindCol`。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的 SQL_TINYINT。 记录集必须将类型为指针的字段数据成员定义为 BYTE。

如果将*prgByteVals*和*PRGLENGTHS*初始化为 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
>  大容量记录字段交换仅将数据从数据源传输到 recordset 对象。 若要使记录集可更新，必须使用 ODBC API 函数 `SQLSetPos`。

有关详细信息，请参阅文章[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_date_bulk"></a>  RFX_Date_Bulk

将从 ODBC 数据源的列 TIMESTAMP_STRUCT 数据的多行传输到 `CRecordset`派生对象中的相应数组。

### <a name="syntax"></a>语法

```
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*prgTSVals*<br/>
指向 TIMESTAMP_STRUCT 值的数组的指针。 此数组将存储要从数据源传输到记录集的数据。 有关 TIMESTAMP_STRUCT 数据类型的详细信息，请参阅*ODBC SDK 程序员参考*的附录 D 中的 "C 数据类型" 主题。

*prgLengths*<br/>
指向长整数数组的指针。 此数组将存储*prgTSVals*所指向的数组中每个值的长度（以字节为单位）。 请注意，如果对应数据项包含 Null 值，则将存储 SQL_NULL_DATA 的值。 有关更多详细信息，请参阅*ODBC SDK 程序员参考*中的 odbc API 函数 `SQLBindCol`。

### <a name="remarks"></a>备注

数据源列可以具有 ODBC 类型的 SQL_DATE、SQL_TIME 或 SQL_TIMESTAMP。 记录集必须定义指向 TIMESTAMP_STRUCT 的类型指针的字段数据成员。

如果将*prgTSVals*和*PRGLENGTHS*初始化为 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
>  大容量记录字段交换仅将数据从数据源传输到 recordset 对象。 若要使记录集可更新，必须使用 ODBC API 函数 `SQLSetPos`。

有关详细信息，请参阅文章[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_double_bulk"></a>  RFX_Double_Bulk

将来自 ODBC 数据源的列的多个双精度浮点数据行传输到 `CRecordset`派生对象中的相应数组。

### <a name="syntax"></a>语法

```
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*prgDblVals*<br/>
指向**双精度**值的数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prgLengths*<br/>
指向长整数数组的指针。 此数组将存储*prgDblVals*所指向的数组中每个值的长度（以字节为单位）。 请注意，如果对应数据项包含 Null 值，则将存储 SQL_NULL_DATA 的值。 有关更多详细信息，请参阅*ODBC SDK 程序员参考*中的 odbc API 函数 `SQLBindCol`。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的 SQL_DOUBLE。 记录集必须将类型指针的字段数据成员定义为**double**。

如果将*prgDblVals*和*PRGLENGTHS*初始化为 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
>  大容量记录字段交换仅将数据从数据源传输到 recordset 对象。 若要使记录集可更新，必须使用 ODBC API 函数 `SQLSetPos`。

有关详细信息，请参阅文章[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_int_bulk"></a>  RFX_Int_Bulk

在 `CRecordset` 对象的字段数据成员和 ODBC 类型 SQL_SMALLINT 的数据源中记录的列之间传输整数数据。

### <a name="syntax"></a>语法

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关 `CFieldExchange` 对象可以指定的操作的详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取值（类型为**int**）。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

### <a name="example"></a>示例

请参阅[RFX_Text](#rfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_long_bulk"></a>  RFX_Long_Bulk

将来自 ODBC 数据源的列的多个长整数数据行传输到 `CRecordset`派生对象中的相应数组。

### <a name="syntax"></a>语法

```
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*prgLongVals*<br/>
指向长整数数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prgLengths*<br/>
指向长整数数组的指针。 此数组将存储*prgLongVals*所指向的数组中每个值的长度（以字节为单位）。 请注意，如果对应数据项包含 Null 值，则将存储 SQL_NULL_DATA 的值。 有关更多详细信息，请参阅*ODBC SDK 程序员参考*中的 odbc API 函数 `SQLBindCol`。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的 SQL_INTEGER。 记录集必须将类型为指针的字段数据成员定义为**long**。

如果将*prgLongVals*和*PRGLENGTHS*初始化为 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
>  大容量记录字段交换仅将数据从数据源传输到 recordset 对象。 若要使记录集可更新，必须使用 ODBC API 函数 `SQLSetPos`。

有关详细信息，请参阅文章[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_single_bulk"></a>  RFX_Single_Bulk

将 ODBC 数据源的列中的多行浮点数据传输到 `CRecordset`派生对象中的相应数组。

### <a name="syntax"></a>语法

```
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*prgFltVals*<br/>
指向**浮点**值的数组的指针。 此数组将存储要从数据源传输到记录集的数据。

*prgLengths*<br/>
指向长整数数组的指针。 此数组将存储*prgFltVals*所指向的数组中每个值的长度（以字节为单位）。 请注意，如果对应数据项包含 Null 值，则将存储 SQL_NULL_DATA 的值。 有关更多详细信息，请参阅*ODBC SDK 程序员参考*中的 odbc API 函数 `SQLBindCol`。

### <a name="remarks"></a>备注

数据源列必须具有 ODBC 类型的 SQL_REAL。 记录集必须将类型指针的字段数据成员定义为**float**。

如果将*prgFltVals*和*PRGLENGTHS*初始化为 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
>  大容量记录字段交换仅将数据从数据源传输到 recordset 对象。 若要使记录集可更新，必须使用 ODBC API 函数 `SQLSetPos`。

有关详细信息，请参阅文章[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

请参阅[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>要求

**标头：** afxdb

## <a name="rfx_text_bulk"></a>  RFX_Text_Bulk

将多行字符数据从 ODBC 数据源的列传输到 `CRecordset`派生对象中的相应数组。

### <a name="syntax"></a>语法

```
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)对象的指针。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
数据列的名称。

*prgStrVals*<br/>
指向 LPSTR 值数组的指针。 此数组将存储要从数据源传输到记录集的数据。 请注意，对于当前版本的 ODBC，这些值不能为 Unicode。

*prgLengths*<br/>
指向长整数数组的指针。 此数组将存储*prgStrVals*所指向的数组中每个值的长度（以字节为单位）。 此长度不包括 null 终止字符。 请注意，如果对应数据项包含 Null 值，则将存储 SQL_NULL_DATA 的值。 有关更多详细信息，请参阅*ODBC SDK 程序员参考*中的 odbc API 函数 `SQLBindCol`。

*nMaxLength*<br/>
*PrgStrVals*所指向的数组中存储的值的最大允许长度，包括 null 终止字符。 若要确保不会截断数据，请传递一个足够大的值以容纳所需的最大数据项。

### <a name="remarks"></a>备注

数据源列可以有 SQL_LONGVARCHAR、SQL_CHAR、SQL_VARCHAR、SQL_DECIMAL 或 SQL_NUMERIC 的 ODBC 类型。 记录集必须定义 LPSTR 类型的字段数据成员。

如果将*prgStrVals*和*PRGLENGTHS*初始化为 NULL，则它们指向的数组将自动分配，大小等于行集大小。

> [!NOTE]
>  大容量记录字段交换仅将数据从数据源传输到 recordset 对象。 若要使记录集可更新，必须使用 ODBC API 函数 `SQLSetPos`。

有关详细信息，请参阅文章[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>示例

你必须在 `DoBulkFieldExchange` 重写中手动编写调用。 此示例演示对数据传输的 `RFX_Text_Bulk`调用，以及对 `RFX_Long_Bulk`的调用。 这些调用前面有一个对[CFieldExchange：： SetFieldType](CFieldExchange::SetFieldType.md)的调用。 请注意，对于参数，必须调用 RFX 函数，而不是 Bulk RFX 函数。

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

**标头：** afxdb

## <a name="dfx_binary"></a>  DFX_Binary

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上的记录列之间传输字节数组。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取[CByteArray](cbytearray-class.md)类型的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*nPreAllocSize*<br/>
框架预分配此内存量。 如果数据较大，则框架将根据需要分配更多空间。 为了获得更好的性能，请将此大小设置为一个足够大的值，以防止重新分配。 默认大小是在 AFXDAO 中定义的。H 文件作为 AFX_DAO_BINARY_DEFAULT_SIZE。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_DISABLE_FIELD_CACHE 不使用双缓冲，你必须自行调用[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull](cdaorecordset-class.md#setfieldnull) 。 其他可能的值（AFX_DAO_ENABLE_FIELD_CACHE）使用双缓冲，无需执行额外的工作来将字段标记为 "已更新" 或 "Null"。 出于性能和内存原因，请避免此值，除非您的二进制数据相对较小。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否为所有字段按默认方式缓存数据。

### <a name="remarks"></a>备注

数据在 DAO 的类型 DAO_BYTES 之间进行映射，并在记录集中[CByteArray](cbytearray-class.md)类型。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_bool"></a>  DFX_Bool

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员和数据源上的记录列之间传输布尔数据。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，将从指定的数据成员中获取类型为 BOOL 的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_ENABLE_FIELD_CACHE 使用双缓冲。 其他可能的值为 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

数据在 DAO 的类型 DAO_BOOL 和记录集中的类型为 BOOL 之间进行映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_byte"></a>  DFX_Byte

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员与数据源上的记录列之间传输单个字节。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，将从指定数据成员中提取 BYTE 类型的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_ENABLE_FIELD_CACHE 使用双缓冲。 其他可能的值为 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

数据在 DAO 中的类型 DAO_BYTES 和记录集中的类型 BYTE 之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_currency"></a>  DFX_Currency

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员与数据源上的记录列之间传输货币数据。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，此值取自类型为[COleCurrency](colecurrency-class.md)的指定数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_ENABLE_FIELD_CACHE 使用双缓冲。 其他可能的值为 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

数据在 DAO 的类型 DAO_CURRENCY 之间进行映射，并在记录集中[COleCurrency](colecurrency-class.md)类型。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_datetime"></a>  DFX_DateTime

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员与数据源上的记录列之间传输时间和日期数据。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 函数获取对[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用。 对于从记录集到数据源的传输，此值取自指定的数据成员。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_ENABLE_FIELD_CACHE 使用双缓冲。 其他可能的值为 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

数据在 DAO 的类型 DAO_DATE 之间进行映射，并在记录集中[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)类型。

> [!NOTE]
>  `COleDateTime` 将在 DAO 类中替换[CTime](../../atl-mfc-shared/reference/ctime-class.md)和 TIMESTAMP_STRUCT。 `CTime` 和 TIMESTAMP_STRUCT 仍用于基于 ODBC 的数据访问类。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_double"></a>  DFX_Double

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员与数据源上的记录列之间传输**双精度浮点**数据。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取类型为**double**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_ENABLE_FIELD_CACHE 使用双缓冲。 其他可能的值为 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

数据在 DAO 的类型 DAO_R8 之间进行映射，并在记录集中键入**double float** 。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_long"></a>  DFX_Long

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员与数据源上的记录列之间传输长整型数据。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，会从指定的数据成员获取类型为**long**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_ENABLE_FIELD_CACHE 使用双缓冲。 其他可能的值为 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

数据在 DAO 中的类型 DAO_I4 和记录集中的**long**类型之间映射。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_longbinary"></a>  DFX_LongBinary

**重要提示**建议使用[DFX_Binary](#dfx_binary)而不是此函数。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取[CLongBinary](clongbinary-class.md)类型的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwPreAllocSize*<br/>
框架预分配此内存量。 如果数据较大，则框架将根据需要分配更多空间。 为了获得更好的性能，请将此大小设置为一个足够大的值，以防止重新分配。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DISABLE_FIELD_CACHE 不使用双缓冲。 其他可能的值为 AFX_DAO_ENABLE_FIELD_CACHE。 使用双缓冲，无需执行额外工作来将字段标记为脏或 Null。 出于性能和内存原因，请避免此值，除非您的二进制数据相对较小。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

提供 `DFX_LongBinary` 是为了与 MFC ODBC 类兼容。 `DFX_LongBinary` 函数在 `CLongBinary`CDaoRecordset[ 对象的字段数据成员和数据源上的记录列之间使用](cdaorecordset-class.md)类传输二进制大型对象（BLOB）数据。 数据在 DAO 的类型 DAO_BYTES 之间进行映射，并在记录集中[CLongBinary](clongbinary-class.md)类型。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_short"></a>  DFX_Short

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员与数据源上的记录列之间传输短整型数据。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，会从指定的数据成员获取值（类型为**short**）。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_ENABLE_FIELD_CACHE 使用双缓冲。 其他可能的值为 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

数据在 DAO 的类型 DAO_I2 之间进行映射，并在记录集中键入**short** 。

> [!NOTE]
>  `DFX_Short` 等效于基于 ODBC 的类的[RFX_Int](#rfx_int) 。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_single"></a>  DFX_Single

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员与数据源上的记录列之间传输浮点数据。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取类型为**float**的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_ENABLE_FIELD_CACHE 使用双缓冲。 其他可能的值为 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

数据在 DAO 的类型 DAO_R4 之间进行映射，并在记录集中键入**float** 。

### <a name="example"></a>示例

请参阅[DFX_Text](#dfx_text)。

### <a name="requirements"></a>要求

**标头：** afxdao

## <a name="dfx_text"></a>  DFX_Text

在[CDaoRecordset](cdaorecordset-class.md)对象的字段数据成员与数据源上的记录列之间传输 `CString` 数据。

### <a name="syntax"></a>语法

```
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
指向[CDaoFieldExchange](cdaofieldexchange-class.md)类的对象的指针。 此对象包含用于定义每次函数时的上下文的信息。

*szName*<br/>
数据列的名称。

*value*<br/>
存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，从指定的数据成员获取类型为[CString](../../atl-mfc-shared/reference/cstringt-class.md)的值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。

*nPreAllocSize*<br/>
框架预分配此内存量。 如果数据较大，则框架将根据需要分配更多空间。 为了获得更好的性能，请将此大小设置为一个足够大的值，以防止重新分配。

*dwBindOptions*<br/>
一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下，AFX_DAO_ENABLE_FIELD_CACHE 使用双缓冲。 其他可能的值为 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 将不对此字段执行检查。 您必须自行调用[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull](cdaorecordset-class.md#setfieldnull) 。

> [!NOTE]
>  可以通过设置[CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)来控制是否默认情况下对数据进行双缓冲处理。

### <a name="remarks"></a>备注

数据在 DAO 中的类型 DAO_CHAR 之间映射（或者，如果定义了符号 _UNICODE，则 DAO_WCHAR）并在记录集中键入[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。  n

### <a name="example"></a>示例

此示例演示对 `DFX_Text`的多个调用。 另请注意两个对[CDaoFieldExchange：： SetFieldType](cdaofieldexchange-class.md#setfieldtype)的调用。 必须编写对 `SetFieldType` 及其**DFX**调用的第一次调用。 第二次调用及其关联的**DFX**调用通常由生成类的代码向导编写。

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

**标头：** afxdao

## <a name="see-also"></a>另请参阅

[宏和全局](mfc-macros-and-globals.md)<br/>
[CRecordset：:D oFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset：:D oBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset：:D oFieldExchange](cdaorecordset-class.md#dofieldexchange)
