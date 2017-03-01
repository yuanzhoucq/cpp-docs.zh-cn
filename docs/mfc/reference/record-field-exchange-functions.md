---
title: "记录字段交换函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions
- DFX functions
- bulk RFX functions
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 87b658cab22ad1aa5db17a00d1d3817e55ff4fc7
ms.lasthandoff: 02/24/2017

---
# <a name="record-field-exchange-functions"></a>记录字段交换函数
本主题列出了记录字段交换 （RFX、 Bulk RFX 和 DFX） 使用自动完成记录集对象和它的数据源之间传输数据以及对数据执行其他操作的函数。  
  
 如果正在使用基于 ODBC 的类，并且已实现批量行提取，则必须为与数据源列对应的每个数据成员调用批量 RFX 函数，以便手动重写 `DoBulkFieldExchange` 的 `CRecordset` 成员函数。  
  
 如果尚未在基于 ODBC 的类中实现批量行提取，或者如果正在使用基于 DAO 的类，ClassWizard 将通过为记录集中的每个字段数据成员调用 RFX 函数（对于 ODBC 类）或 DFX 函数（对于 DAO 类），来重写 `DoFieldExchange` 或 `CRecordset` 的 `CDaoRecordset` 成员函数。  
  
 记录字段交换函数在框架每次调用 `DoFieldExchange` 或 `DoBulkFieldExchange`时传输数据。 每个函数传输一种特定的数据类型。  
  
 有关如何使用这些函数的详细信息，请参阅文章[记录字段交换︰ 如何 RFX 的工作原理 (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有关批量取行的详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 对于动态绑定的数据的列，您还可以调用 RFX 或 DFX 函数自己，如文章中所述[记录集︰ 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。 此外，您可以编写您自己自定义的 RFX 或 DFX 例程，技术说明中所述[43](../../mfc/tn043-rfx-routines.md) （对于 ODBC) 和技术说明[53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) （对于 DAO)。  
  
 以举例说明 RFX 和 Bulk RFX 函数按它们出现在`DoFieldExchange`和`DoBulkFieldExchange`函数，请参见[RFX_Text](#rfx_text)和 [RFX_Text_Bulk] #rfx_text_bulk)。 DFX 函数与 RFX 函数非常类似。  
  
### <a name="rfx-functions-odbc"></a>RFX 函数 (ODBC)  
  
|||  
|-|-|  
|[RFX_Binary](#rfx_binary)|传输类型的字节的数组[CByteArray](cbytearray-class.md)。|  
|[RFX_Bool](#rfx_bool)|传输布尔数据。|  
|[RFX_Byte](#rfx_byte)|传输单字节数据。|  
|[RFX_Date](#rfx_date)|传输时间和日期的数据使用[CTime](../../atl-mfc-shared/reference/ctime-class.md)或**TIMESTAMP_STRUCT**。|  
|[RFX_Double](#rfx_double)|传输双精度浮点数据。|  
|[RFX_Int](#rfx_int)|传输整型数据。|  
|[RFX_Long](#rfx_long)|传输长整型数据。|  
|[RFX_LongBinary](#rfx_longbinary)|将使用对象的二进制大型对象 (BLOB) 数据传输[CLongBinary](clongbinary-class.md)类。|  
|[RFX_Single](#rfx_single)|传输浮点数据。|  
|[RFX_Text](#rfx_text)|传输字符串数据。|  
  
### <a name="bulk-rfx-functions-odbc"></a>批量 RFX 函数 (ODBC)  
  
|||  
|-|-|  
|[RFX_Binary_Bulk](#rfx_binary_bulk)|传输字节数据数组。|  
|[RFX_Bool_Bulk](#rfx_bool_bulk)|传输布尔数据数组。|  
|[RFX_Byte_Bulk](#rfx_byte_bulk)|传输单字节数组。|  
|[RFX_Date_Bulk](#rfx_date_bulk)|传输 **TIMESTAMP_STRUCT**类型的数据数组。|  
|[RFX_Double_Bulk](#rfx_double_bulk)|传输双精度浮点数据数组。|  
|[RFX_Int_Bulk](#rfx_int_bulk)|传输整型数据数组。|  
|[RFX_Long_Bulk](#rfx_long_bulk)|传输长整型数据数组。|  
|[RFX_Single_Bulk](#rfx_single_bulk)|传输浮点数据数组。|  
|[RFX_Text_Bulk](#rfx_text_bulk)|传输 **LPSTR**类型的数据数组。|  
  
### <a name="dfx-functions-dao"></a>DFX 函数 (DAO)  
  
|||
|-|-|  
|[DFX_Binary](#dfx_binary)|传输类型的字节的数组[CByteArray](cbytearray-class.md)。|  
|[DFX_Bool](#dfx_bool)|传输布尔数据。|  
|[DFX_Byte](#dfx_byte)|传输单字节数据。|  
|[DFX_Currency](#dfx_currency)|传输类型的货币数据[COleCurrency](colecurrency-class.md)。|  
|[DFX_DateTime](#dfx_datetime)|将日期和时间数据类型的传输[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。|  
|[DFX_Double](#dfx_double)|传输双精度浮点数据。|  
|[DFX_Long](#dfx_long)|传输长整型数据。|  
|[DFX_LongBinary](#dfx_longbinary)|使用 `CLongBinary` 类的对象传输二进制大型对象 (BLOB) 数据。 对于 DAO，建议你使用[DFX_Binary](#dfx_binary)相反。|  
|[DFX_Short](#dfx_short)|传输短整型数据。|  
|[DFX_Single](#dfx_single)|传输浮点数据。|  
|[DFX_Text](#dfx_text)|传输字符串数据。|  

 =============================================

## <a name="a-namerfxbinarya--rfxbinary"></a><a name="rfx_binary"></a>RFX_Binary
字段数据成员之间传输的字节数组`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_BINARY**， **SQL_VARBINARY**，或**SQL_LONGVARBINARY**。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Binary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CByteArray& value,  
   int nMaxLength = 255);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输[CByteArray](cbytearray-class.md)，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `nMaxLength`  
 允许的最大的字符串或正在传输的数组的长度。 默认值为`nMaxLength`为 255。 合法值是 1 到`INT_MAX`。 框架将为数据分配空间的量。 为了获得最佳性能，将传递一个足够大以容纳您预期的最大数据项目的值。  
  
### <a name="remarks"></a>备注  
 这些类型的数据源中的数据将映射与类型`CByteArray`在记录集中。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxboola--rfxbool"></a><a name="rfx_bool"></a>RFX_Bool
将布尔值的数据传输之间的字段数据成员`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_BIT**。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Bool(  
   CFieldExchange* pFX,  
   const char* szName,  
   BOOL& value);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**BOOL**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxbytea--rfxbyte"></a><a name="rfx_byte"></a>RFX_Byte
字段数据成员之间传输单字节`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_TINYINT**。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Byte(  
   CFieldExchange* pFX,  
   const char* szName,  
   BYTE& value);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**字节**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxdatea--rfxdate"></a><a name="rfx_date"></a>RFX_Date
传输`CTime`或**TIMESTAMP_STRUCT**之间的字段数据成员的数据`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_DATE**， **SQL_TIME**，或**SQL_TIMESTAMP**。  
  
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
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 指定的数据成员; 中存储的值要传输的值。 各种版本的函数执行值的不同的数据类型︰  
  
 该函数的第一个版本采用指向的引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。 对于从记录集到数据源的传输，从指定的数据成员中提取此值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 第二个版本的函数将对引用**TIMESTAMP_STRUCT**结构。 您必须设置此结构自己在调用之前。 既没有对话框数据交换 (DDX) 支持，也可用于此版本代码的向导支持。 该函数的第三版工作方式类似于第一个版本，但前者将对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。  
  
### <a name="remarks"></a>备注  
 `CTime`该函数的版本会产生的某些中间的处理开销，并且具有一定的限制的范围。 如果您发现极大地限制这些因素之一，则使用第二个版本的函数。 但请注意它没有代码向导和 DDX 支持以及您设置结构您自己的要求。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxdoublea--rfxdouble"></a><a name="rfx_double"></a>RFX_Double
传输**双精度浮点**之间的字段数据成员的数据`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_DOUBLE**。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Double(  
   CFieldExchange* pFX,  
   const char* szName,  
   double& value);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**double**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxinta--rfxint"></a><a name="RFX_Int"></a>RFX_Int
将整数数据传输之间的字段数据成员`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_SMALLINT**。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输`int`，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxlonga--rfxlong"></a><a name="RFX_Long"></a>RFX_Long
将长整型数据传输之间的字段数据成员`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_INTEGER**。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Long(  
   CFieldExchange* pFX,  
   const char* szName,  
   LONG&   
value );  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**长**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  
  
## <a name="a-namerfxlongbinarya--rfxlongbinary"></a><a name="RFX_LongBinary"></a>RFX_LongBinary
将使用类的二进制大型对象 (BLOB) 数据传输[CLongBinary](clongbinary-class.md)之间的字段数据成员`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_LONGVARBINARY**或**SQL_LONGVARCHAR**。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_LongBinary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CLongBinary& value);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输`CLongBinary`，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxsinglea--rfxsingle"></a><a name="rfx_single"></a>RFX_Single
将浮点数据传输之间的字段数据成员`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_REAL**。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Single(  
   CFieldExchange* pFX,  
   const char* szName,  
   float& value);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**float**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  
  

## <a name="a-namerfxtexta--rfxtext"></a><a name="rfx_text"></a>RFX_Text
传输`CString`之间的字段数据成员的数据`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_LONGVARCHAR**， **SQL_CHAR**， **SQL_VARCHAR**， **SQL_DECIMAL**，或**SQL_NUMERIC**。  
  
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
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针`CFieldExchange`。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输`CString`，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `nMaxLength`  
 允许的最大的字符串或正在传输的数组的长度。 默认值为`nMaxLength`为 255。 合法值是 1 到`INT_MAX`)。 框架将为数据分配空间的量。 为了获得最佳性能，将传递一个足够大以容纳您预期的最大数据项目的值。  
  
 *nColumnType*  
 主要用于参数。 一个整数，指示该参数的数据类型。 类型为 ODBC 数据类型的窗体**SQL_XXX**。  
  
 `nScale`  
 指定 ODBC 类型的值的小数位数**SQL_DECIMAL**或**SQL_NUMERIC**。 `nScale`有用时才设置参数值。 详细信息，请参阅主题"精度、 小数位数、 长度和显示大小"中的附录 D *ODBC SDK 程序员参考*。  
  
### <a name="remarks"></a>备注  
 所有这些类型的数据源中的数据映射间来回`CString`在记录集中。  
  
### <a name="example"></a>示例  
 此示例演示多次调用`RFX_Text`。 请注意两次调用也`CFieldExchange::SetFieldType`。 您必须为参数编写调用`SetFieldType`和其 RFX 调用。 代码向导通常写入的输出列调用并其相关联的 RFX 调用。  
  
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
 **标头︰** afxdb.h  


## <a name="a-namerfxbinarybulka--rfxbinarybulk"></a><a name="rfx_binary_Bulk"></a>RFX_Binary_Bulk
将字节数据的多个行从 ODBC 数据源的列传输到相应数组`CRecordset`-派生的对象。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Binary_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths,  
   int nMaxLength);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](cfieldexchange-class.md)对象。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 `prgByteVals`  
 指向数组的指针**字节**值。 此数组将存储数据以便从数据源传输到记录集。  
  
 `prgLengths`  
 指向一个长整数数组的指针。 此数组将以字节为单位由指向数组中每个值的存储长度`prgByteVals`。 请注意，值**SQL_NULL_DATA**相应数据项都包含一个 Null 值的情况下存储。 有关详细信息，请参阅 ODBC API 函数**SQLBindCol**中*ODBC SDK 程序员参考*。  
  
 `nMaxLength`  
 允许的最大长度为指向数组中存储的值`prgByteVals`。 若要确保数据不会被截断，传递值足够大以容纳您预期的最大数据项目。  
  
### <a name="remarks"></a>备注  
 数据源列可以具有的 ODBC 类型**SQL_BINARY**， **SQL_VARBINARY**，或**SQL_LONGVARBINARY**。 记录集必须定义的字段数据成员的指针类型的**字节**。  
  
 如果初始化`prgByteVals`和`prgLengths`到**NULL**，则它们指向的数组将自动分配给具有大小等于行集大小。  
  
> [!NOTE]
>  批量记录字段交换只将数据传输从数据源到记录集对象。 为了使您的记录集可更新，您必须使用 ODBC API 函数**SQLSetPos**。  
  
 有关详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxboolbulka--rfxboolbulk"></a><a name="rfx_bool_Bulk"></a>RFX_Bool_Bulk
将布尔型数据的多个行从 ODBC 数据源的列传输到相应数组`CRecordset`-派生的对象。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Bool_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL** prgBoolVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](cfieldexchange-class.md)对象。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 `prgBoolVals`  
 指向数组的指针**BOOL**值。 此数组将存储数据以便从数据源传输到记录集。  
  
 `prgLengths`  
 指向一个长整数数组的指针。 此数组将以字节为单位由指向数组中每个值的存储长度`prgBoolVals`。 请注意，值**SQL_NULL_DATA**相应数据项都包含一个 Null 值的情况下存储。 有关详细信息，请参阅 ODBC API 函数**SQLBindCol**中*ODBC SDK 程序员参考*。  
  
### <a name="remarks"></a>备注  
 数据源列都必须有的 ODBC 类型**SQL_BIT**。 记录集必须定义的字段数据成员的指针类型的**BOOL**。  
  
 如果初始化`prgBoolVals`和`prgLengths`到**NULL**，则它们指向的数组将自动分配给具有大小等于行集大小。  
  
> [!NOTE]
>  批量记录字段交换只将数据传输从数据源到记录集对象。 若要使您的记录集可更新，必须使用 ODBC API 函数**SQLSetPos**。  
  
 有关详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxbytebulka--rfxbytebulk"></a><a name="rfx_byte_Bulk"></a>RFX_Byte_Bulk
将单字节的多个行从 ODBC 数据源的列传输到相应数组`CRecordset`-派生的对象。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Byte_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](cfieldexchange-class.md)对象。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 `prgByteVals`  
 指向数组的指针**字节**值。 此数组将存储数据以便从数据源传输到记录集。  
  
 `prgLengths`  
 指向一个长整数数组的指针。 此数组将以字节为单位由指向数组中每个值的存储长度`prgByteVals`。 请注意，值**SQL_NULL_DATA**相应数据项都包含一个 Null 值的情况下存储。 有关详细信息，请参阅 ODBC API 函数**SQLBindCol**中*ODBC SDK 程序员参考*。  
  
### <a name="remarks"></a>备注  
 数据源列都必须有的 ODBC 类型**SQL_TINYINT**。 记录集必须定义的字段数据成员的指针类型的**字节**。  
  
 如果初始化`prgByteVals`和`prgLengths`到**NULL**，则它们指向的数组将自动分配给具有大小等于行集大小。  
  
> [!NOTE]
>  批量记录字段交换只将数据传输从数据源到记录集对象。 若要使您的记录集可更新，必须使用 ODBC API 函数**SQLSetPos**。  
  
 有关详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  
  
## <a name="a-namerfxdatebulka--rfxdatebulk"></a><a name="rfx_date_Bulk"></a>RFX_Date_Bulk
将传输的多个行**TIMESTAMP_STRUCT**数据从 ODBC 数据源的列中的相应数组到`CRecordset`-派生的对象。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Date_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   TIMESTAMP_STRUCT** prgTSVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](cfieldexchange-class.md)对象。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 `prgTSVals`  
 指向数组的指针**TIMESTAMP_STRUCT**值。 此数组将存储数据以便从数据源传输到记录集。 有关详细信息**TIMESTAMP_STRUCT**数据类型，请参阅主题"C 数据类型"中的附录 D 的*ODBC SDK 程序员参考*。  
  
 `prgLengths`  
 指向一个长整数数组的指针。 此数组将以字节为单位由指向数组中每个值的存储长度`prgTSVals`。 请注意，值**SQL_NULL_DATA**相应数据项都包含一个 Null 值的情况下存储。 有关详细信息，请参阅 ODBC API 函数**SQLBindCol**中*ODBC SDK 程序员参考*。  
  
### <a name="remarks"></a>备注  
 数据源列可以具有的 ODBC 类型**SQL_DATE**， **SQL_TIME**，或**SQL_TIMESTAMP**。 记录集必须定义的字段数据成员的指针类型的**TIMESTAMP_STRUCT**。  
  
 如果初始化`prgTSVals`和`prgLengths`到**NULL**，则它们指向的数组将自动分配给具有大小等于行集大小。  
  
> [!NOTE]
>  批量记录字段交换只将数据传输从数据源到记录集对象。 若要使您的记录集可更新，必须使用 ODBC API 函数**SQLSetPos**。  
  
 有关详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxdoublebulka--rfxdoublebulk"></a><a name="rfx_double_Bulk"></a>RFX_Double_Bulk
将从 ODBC 数据源的列的多个行的双精度浮点数据传输到相应数组中`CRecordset`-派生的对象。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Double_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   double** prgDblVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](cfieldexchange-class.md)对象。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 `prgDblVals`  
 指向数组的指针**double**值。 此数组将存储数据以便从数据源传输到记录集。  
  
 `prgLengths`  
 指向一个长整数数组的指针。 此数组将以字节为单位由指向数组中每个值的存储长度`prgDblVals`。 请注意，值**SQL_NULL_DATA**相应数据项都包含一个 Null 值的情况下存储。 有关详细信息，请参阅 ODBC API 函数**SQLBindCol**中*ODBC SDK 程序员参考*。  
  
### <a name="remarks"></a>备注  
 数据源列都必须有的 ODBC 类型**SQL_DOUBLE**。 记录集必须定义的字段数据成员的指针类型的**double**。  
  
 如果初始化`prgDblVals`和`prgLengths`到**NULL**，则它们指向的数组将自动分配给具有大小等于行集大小。  
  
> [!NOTE]
>  批量记录字段交换只将数据传输从数据源到记录集对象。 若要使您的记录集可更新，必须使用 ODBC API 函数**SQLSetPos**。  
  
 有关详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxintbulka--rfxintbulk"></a><a name="RFX_Int_Bulk"></a>RFX_Int_Bulk
将整数数据传输之间的字段数据成员`CRecordset`对象和列上的数据源的 ODBC 类型的记录**SQL_SMALLINT**。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CFieldExchange](cfieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息有关的各种操作`CFieldExchange`可以指定对象，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输`int`，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxlongbulka--rfxlongbulk"></a><a name="RFX_Long_Bulk"></a>RFX_Long_Bulk
将从 ODBC 数据源的列的多行的长整型数据传输到相应数组中`CRecordset`-派生的对象。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Long_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   long** prgLongVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](cfieldexchange-class.md)对象。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 `prgLongVals`  
 指向一个长整数数组的指针。 此数组将存储数据以便从数据源传输到记录集。  
  
 `prgLengths`  
 指向一个长整数数组的指针。 此数组将以字节为单位由指向数组中每个值的存储长度`prgLongVals`。 请注意，值**SQL_NULL_DATA**相应数据项都包含一个 Null 值的情况下存储。 有关详细信息，请参阅 ODBC API 函数**SQLBindCol**中*ODBC SDK 程序员参考*。  
  
### <a name="remarks"></a>备注  
 数据源列都必须有的 ODBC 类型**SQL_INTEGER**。 记录集必须定义的字段数据成员的指针类型的**长**。  
  
 如果初始化`prgLongVals`和`prgLengths`到**NULL**，则它们指向的数组将自动分配给具有大小等于行集大小。  
  
> [!NOTE]
>  批量记录字段交换只将数据传输从数据源到记录集对象。 若要使您的记录集可更新，必须使用 ODBC API 函数**SQLSetPos**。  
  
 有关详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  

## <a name="a-namerfxsinglebulka--rfxsinglebulk"></a><a name="rfx_single_Bulk"></a>RFX_Single_Bulk
将浮点型数据的多个行从 ODBC 数据源的列传输到相应数组`CRecordset`-派生的对象。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Single_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   float** prgFltVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](cfieldexchange-class.md)对象。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 `prgFltVals`  
 指向数组的指针**float**值。 此数组将存储数据以便从数据源传输到记录集。  
  
 `prgLengths`  
 指向一个长整数数组的指针。 此数组将以字节为单位由指向数组中每个值的存储长度`prgFltVals`。 请注意，值**SQL_NULL_DATA**相应数据项都包含一个 Null 值的情况下存储。 有关详细信息，请参阅 ODBC API 函数**SQLBindCol**中*ODBC SDK 程序员参考*。  
  
### <a name="remarks"></a>备注  
 数据源列都必须有的 ODBC 类型**SQL_REAL**。 记录集必须定义的字段数据成员的指针类型的**float**。  
  
 如果初始化`prgFltVals`和`prgLengths`到**NULL**，则它们指向的数组将自动分配给具有大小等于行集大小。  
  
> [!NOTE]
>  批量记录字段交换只将数据传输从数据源到记录集对象。 若要使您的记录集可更新，必须使用 ODBC API 函数**SQLSetPos**。  
  
 有关详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>示例  
 请参阅[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdb.h  
  

## <a name="a-namerfxtextbulka--rfxtextbulk"></a><a name="rfx_text_Bulk"></a>RFX_Text_Bulk
将字符数据的多个行从 ODBC 数据源的列传输到相应数组`CRecordset`-派生的对象。  
  
### <a name="syntax"></a>语法  
  
```
void RFX_Text_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   LPSTR* prgStrVals,  
   long** prgLengths,  
   int nMaxLength);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 一个指向[CFieldExchange](cfieldexchange-class.md)对象。 此对象包含用于定义每次函数时的上下文的信息。 有关详细信息，请参阅文章[记录字段交换︰ RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 数据列的名称。  
  
 `prgStrVals`  
 指向数组的指针**LPSTR**值。 此数组将存储数据以便从数据源传输到记录集。 请注意，与 ODBC 的当前版本，这些值不能为 Unicode。  
  
 `prgLengths`  
 指向一个长整数数组的指针。 此数组将以字节为单位由指向数组中每个值的存储长度`prgStrVals`。 这种长度不包括 null 终止字符。 请注意，值**SQL_NULL_DATA**相应数据项都包含一个 Null 值的情况下存储。 有关详细信息，请参阅 ODBC API 函数**SQLBindCol**中*ODBC SDK 程序员参考*。  
  
 `nMaxLength`  
 允许的最大长度为指向数组中存储的值`prgStrVals`，包括 null 终止字符。 若要确保数据不会被截断，传递值足够大以容纳您预期的最大数据项目。  
  
### <a name="remarks"></a>备注  
 数据源列可以具有的 ODBC 类型**SQL_LONGVARCHAR**， **SQL_CHAR**， **SQL_VARCHAR**， **SQL_DECIMAL**，或**SQL_NUMERIC**。 记录集必须定义类型的字段数据成员**LPSTR**。  
  
 如果初始化`prgStrVals`和`prgLengths`到**NULL**，则它们指向的数组将自动分配给具有大小等于行集大小。  
  
> [!NOTE]
>  批量记录字段交换只将数据传输从数据源到记录集对象。 若要使您的记录集可更新，必须使用 ODBC API 函数**SQLSetPos**。  
  
 有关详细信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>示例  
 您必须手动编写调用，您`DoBulkFieldExchange`重写。 此示例演示如何调用`RFX_Text_Bulk`，以及调用`RFX_Long_Bulk`，数据传输。 通过调用前面带有这些调用[CFieldExchange::SetFieldType](CFieldExchange::SetFieldType.md)。 请注意，对于参数，则必须调用 RFX 函数而不是批量 RFX 函数。  
  
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
 **标头︰** afxdb.h  

## <a name="a-namedfxbinarya--dfxbinary"></a><a name="dfx_binary"></a>DFX_Binary
字段数据成员之间传输的字节数组[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_Binary(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CByteArray& value,  
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,  
   DWORD dwBindOptions = 0);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输[CByteArray](cbytearray-class.md)，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `nPreAllocSize`  
 框架预先分配内存的量。 如果您的数据大小，该框架将分配所需的更多的空间。 为了提高性能，此大小设置为足够大，以防止重新分配的值。 AFXDAO 中定义的默认大小。H 文件作为**AFX_DAO_BINARY_DEFAULT_SIZE**。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下， `AFX_DAO_DISABLE_FIELD_CACHE`，不会不使用双缓冲，并必须调用[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull](cdaorecordset-class.md#setfieldnull)自己。 其他可能的值， `AFX_DAO_ENABLE_FIELD_CACHE`，使用双缓冲，并且您不需要做一些额外工作来标记字段变脏或 Null。 性能和内存的原因，为避免此值，除非是相对较小的二进制数据。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲的所有字段默认情况下通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_BYTES** DAO 以及类型[CByteArray](cbytearray-class.md)在记录集中。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  

## <a name="a-namedfxboola--dfxbool"></a><a name="dfx_bool"></a>DFX_Bool
将布尔值的数据传输之间的字段数据成员[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_Bool(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**BOOL**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 `AFX_DAO_ENABLE_FIELD_CACHE` 使用双缓冲。 另一个可能的值为 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_BOOL** DAO 以及类型**BOOL**在记录集中。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  

## <a name="a-namedfxbytea--dfxbyte"></a><a name="dfx_byte"></a>DFX_Byte
字段数据成员之间传输单字节[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_Byte(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**字节**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 `AFX_DAO_ENABLE_FIELD_CACHE` 使用双缓冲。 另一个可能的值为 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_BYTES** DAO 以及类型**字节**在记录集中。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  

## <a name="a-namedfxcurrencya--dfxcurrency"></a><a name="dfx_currency"></a>DFX_Currency
将货币数据传输之间的字段数据成员[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_Currency(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleCurrency& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源的传输，此值来自类型的指定的数据成员， [COleCurrency](colecurrency-class.md)。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 `AFX_DAO_ENABLE_FIELD_CACHE` 使用双缓冲。 另一个可能的值为 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_CURRENCY** DAO 以及类型[COleCurrency](colecurrency-class.md)在记录集中。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  

## <a name="a-namedfxdatetimea--dfxdatetime"></a><a name="dfx_datetime"></a>DFX_DateTime
将日期和时间数据传输之间的字段数据成员[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_DateTime(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleDateTime& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 该函数采用对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。 对于从记录集到数据源的传输，从指定的数据成员中提取此值。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 `AFX_DAO_ENABLE_FIELD_CACHE` 使用双缓冲。 另一个可能的值为 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_DATE** DAO 以及类型[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)在记录集中。  
  
> [!NOTE]
>  `COleDateTime`将替换[CTime](../../atl-mfc-shared/reference/ctime-class.md)和**TIMESTAMP_STRUCT**为此目的在 DAO 类。 `CTime`和**TIMESTAMP_STRUCT**仍然是用于基于 ODBC 的数据访问类。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  

## <a name="a-namedfxdoublea--dfxdouble"></a><a name="dfx_double"></a>DFX_Double
传输**双精度浮点**之间的字段数据成员的数据[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_Double(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   double& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**double**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 `AFX_DAO_ENABLE_FIELD_CACHE` 使用双缓冲。 另一个可能的值为 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_R8** DAO 以及类型**双精度浮点**在记录集中。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  

## <a name="a-namedfxlonga--dfxlong"></a><a name="dfx_long"></a>DFX_Long
将长整型数据传输之间的字段数据成员[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_Long(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   long& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**长**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 `AFX_DAO_ENABLE_FIELD_CACHE` 使用双缓冲。 另一个可能的值为 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_I4** DAO 以及类型**长**在记录集中。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  

## <a name="a-namedfxlongbinarya--dfxlongbinary"></a><a name="dfx_longbinary"></a>DFX_LongBinary
**重要**建议你使用[DFX_Binary](#dfx_binary)而不是此函数。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_LongBinary(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CLongBinary& value,  
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,  
   DWORD dwBindOptions = 0);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输[CLongBinary](clongbinary-class.md)，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 *dwPreAllocSize*  
 框架预先分配内存的量。 如果您的数据大小，该框架将分配所需的更多的空间。 为了提高性能，此大小设置为足够大，以防止重新分配的值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认情况下， **AFX_DISABLE_FIELD_CACHE**，不使用双缓冲。 另一个可能的值为 `AFX_DAO_ENABLE_FIELD_CACHE`。 使用双缓冲，并且您不需要做一些额外工作来标记字段变脏或 Null。 性能和内存的原因，为避免此值，除非是相对较小的二进制数据。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 `DFX_LongBinary`提供与 MFC ODBC 类的兼容性。 `DFX_LongBinary`函数将使用类的二进制大型对象 (BLOB) 数据传输`CLongBinary`之间的字段数据成员[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。 数据类型之间的映射**DAO_BYTES** DAO 以及类型[CLongBinary](clongbinary-class.md)在记录集中。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  

## <a name="a-namedfxshorta--dfxshort"></a><a name="dfx_short"></a>DFX_Short
传输短的字段数据成员之间的整数数据[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_Short(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   short& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**短**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 `AFX_DAO_ENABLE_FIELD_CACHE` 使用双缓冲。 另一个可能的值为 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_I2** DAO 以及类型**短**在记录集中。  
  
> [!NOTE]
>  `DFX_Short`等效于[RFX_Int](#rfx_int)基于 ODBC 的类。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  
  

## <a name="a-namedfxsinglea--dfxsingle"></a><a name="dfx_single"></a>DFX_Single
将浮点数据传输之间的字段数据成员[CDaoRecordset](cdaorecordset-class.md)对象和数据源上的记录的列。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_Single(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   float& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输**float**，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 `AFX_DAO_ENABLE_FIELD_CACHE` 使用双缓冲。 另一个可能的值为 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 将不对此字段执行检查。 您必须调用 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_R4** DAO 以及类型**float**在记录集中。  
  
### <a name="example"></a>示例  
 请参阅[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  

## <a name="a-namedfxtexta--dfxtext"></a><a name="dfx_text"></a>DFX_Text
传输`CString`之间的字段数据成员的数据[CDaoRecordset](cdaorecordset-class.md)对象和列的数据源上的记录。  
  
### <a name="syntax"></a>语法  
  
```
void AFXAPI DFX_Text(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CString& value,  
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 指向类的对象的指针[CDaoFieldExchange](cdaofieldexchange-class.md)。 此对象包含用于定义每次函数时的上下文的信息。  
  
 `szName`  
 数据列的名称。  
  
 *值*  
 存储在指定的数据成员中的值（要传输的值）。 对于从记录集到数据源类型的值的传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)，从指定的数据成员中提取。 对于从数据源得到记录集的传输，将在指定的数据成员中存储值。  
  
 `nPreAllocSize`  
 框架预先分配内存的量。 如果您的数据大小，该框架将分配所需的更多的空间。 为了提高性能，此大小设置为足够大，以防止重新分配的值。  
  
 `dwBindOptions`  
 一个选项，用来支持您利用 MFC 的双缓冲机制来检测已更改的字段记录集。 默认值 `AFX_DAO_ENABLE_FIELD_CACHE` 使用双缓冲。 另一个可能的值为 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 将不对此字段执行检查。 必须调用[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull](cdaorecordset-class.md#setfieldnull)自己。  
  
> [!NOTE]
>  您可以控制是否对数据进行双缓冲默认情况下，通过设置[cdaorecordset:: M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>备注  
 数据类型之间的映射**DAO_CHAR**在 DAO 中 (或者，如果该符号**_UNICODE**定义，则**DAO_WCHAR**) 和类型[CString](../../atl-mfc-shared/reference/cstringt-class.md)在记录集中。  n
  
### <a name="example"></a>示例  
 此示例演示多次调用`DFX_Text`。 请注意两次调用也[CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype)。 您必须编写首次调用`SetFieldType`并将其**DFX**调用。 第二个调用和及其关联**DFX**调用通常由生成的类中的代码向导编写的。  
  
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
 **标头︰** afxdao.h  
  
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)   
 [CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)   
 [CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)


