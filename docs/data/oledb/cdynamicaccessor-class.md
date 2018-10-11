---
title: CDynamicAccessor 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- GetColumnFlags
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b9d1982e1da6526c1c9db607062a66b163f912ce
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083666"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor 类

使您可以在不知道数据库架构（数据库的基础结构）的情况下访问数据源。  
  
## <a name="syntax"></a>语法

```cpp
class CDynamicAccessor : public CAccessorBase  
```  

## <a name="requirements"></a>要求  

**标头**：atldbcli.h  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddBindEntry](#addbindentry)|重写默认访问器时，请将绑定条目添加到输出列。|  
|[CDynamicAccessor](#cdynamicaccessor)|实例化并初始化`CDynamicAccessor`对象。|  
|[关闭](#close)|取消绑定所有列时，释放分配的内存，并释放[IAccessor](/previous-versions/windows/desktop/ms719672)类中的接口指针。|  
|[GetBlobHandling](#getblobhandling)|检索 BLOB 处理的当前行值。|  
|[GetBlobSizeLimit](#getblobsizelimit)|检索以字节为单位的最大 BLOB 大小。|  
|[GetBookmark](#getbookmark)|检索当前行的书签。|  
|[GetColumnCount](#getcolumncount)|检索行集中的列数。|  
|[GetColumnFlags](#getcolumnflags)|检索列特征。|  
|[GetColumnInfo](#getcolumninfo)|检索列元数据。|  
|[GetColumnName](#getcolumnname)|检索指定列的名称。|  
|[GetColumnType](#getcolumntype)|检索指定列的数据类型。|  
|[GetLength](#getlength)|检索以字节为单位的列的最大可取长度。|  
|[GetOrdinal](#getordinal)|检索给定列名称的列索引。|  
|[GetStatus](#getstatus)|检索指定列的状态。|  
|[GetValue](#getvalue)|从缓冲区中检索数据。|  
|[SetBlobHandling](#setblobhandling)|设置 BLOB 处理的当前行值。|  
|[SetBlobSizeLimit](#setblobsizelimit)|以字节为单位设置的最大 BLOB 大小。|  
|[SetLength](#setlength)|设置列的长度以字节为单位。|  
|[SetStatus](#setstatus)|设置指定列的状态。|  
|[SetValue](#setvalue)|将存储到缓冲区的数据。|  
  
## <a name="remarks"></a>备注  

使用`CDynamicAccessor`方法以获取列信息，例如列名、 列数、 数据类型等。 然后可以使用此列的信息来在运行时动态创建取值函数。  
  
列信息存储在缓冲区的创建和管理此类。 从缓冲区使用获取数据[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)。  
  
有关的讨论和使用动态访问器类的示例，请参阅[使用动态访问器](../../data/oledb/using-dynamic-accessors.md)。  

## <a name="addbindentry"></a> Cdynamicaccessor:: Addbindentry

将绑定条目添加到输出列。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();  
```  
  
#### <a name="parameters"></a>参数  

info<br/>
[in]一个`DBCOLUMNINFO`结构，它包含的列信息。 请参阅中的"DBCOLUMNINFO 结构" [icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704)中*OLE DB 程序员参考*。  
  
### <a name="return-value"></a>返回值  

一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  

使用此方法重写使用创建的默认访问器时`CDynamicAccessor`(请参阅[如何实现提取的数据？](../../data/oledb/fetching-data.md))。 
  
## <a name="cdynamicaccessor"></a> Cdynamicaccessor:: Cdynamicaccessor

实例化并初始化`CDynamicAccessor`对象。  
  
### <a name="syntax"></a>语法  
  
```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000);  
```  
  
#### <a name="parameters"></a>参数  

*eBlobHandling*<br/>
指定二进制大型对象 (BLOB) 数据的处理方式。 默认值为 DBBLOBHANDLING_DEFAULT。 请参阅[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) DBBLOBHANDLINGENUM 值的说明。  
  
*nBlobSize*<br/>
最大 BLOB 大小（以字节为单位）；该值之上的列数据被视为 BLOB。 默认值为 8000。 请参阅[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)有关详细信息。  
  
### <a name="remarks"></a>备注  

如果使用构造函数来初始化`CDynamicAccessor`对象，您可以指定它将如何绑定 Blob。 Blob 可以包含二进制数据，例如图形、 声音或已编译代码。 默认行为是将视为 Blob 列超过 8,000 个字节，并尝试将其绑定到`ISequentialStream`对象。 但是，可以指定不同的值为 BLOB 大小。  
  
此外可以指定如何`CDynamicAccessor`处理被称为 BLOB 数据的列数据： 它可以处理 BLOB 数据以默认方式; 可以跳过 （不绑定） BLOB 数据; 也可以将 BLOB 数据绑定中提供程序分配内存。  

## <a name="close"></a> Cdynamicaccessor:: Close

取消绑定所有列时，释放分配的内存，并释放[IAccessor](/previous-versions/windows/desktop/ms719672)类中的接口指针。  
  
### <a name="syntax"></a>语法  
  
```cpp
void Close() throw();  
```  

## <a name="getblobhandling"></a> Cdynamicaccessor:: Getblobhandling

检索 BLOB 处理的当前行值。  
  
### <a name="syntax"></a>语法  
  
```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;  
```  
  
### <a name="remarks"></a>备注  

返回处理值的 BLOB *eBlobHandling*通过设置[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)。 

## <a name="getblobsizelimit"></a> Cdynamicaccessor:: Getblobsizelimit

检索以字节为单位的最大 BLOB 大小。  
  
### <a name="syntax"></a>语法  
  
```cpp
const DBLENGTH GetBlobSizeLimit() const;  
```  
  
### <a name="remarks"></a>备注  

返回处理值的 BLOB *nBlobSize*通过设置[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)。  

## <a name="getbookmark"></a> Cdynamicaccessor:: Getbookmark

检索当前行的书签。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*pBookmark*<br/>
[out]一个指向[CBookmark](../../data/oledb/cbookmark-class.md)对象。  
  
### <a name="return-value"></a>返回值  

一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  

您需要设置`DBPROP_IRowsetLocate`为 variant_true，则检索一个书签。 

## <a name="getcolumncount"></a> Cdynamicaccessor:: Getcolumncount

检索列的数。  
  
### <a name="syntax"></a>语法  
  
```cpp
DBORDINAL GetColumnCount() const throw();  
```  
  
### <a name="return-value"></a>返回值  

检索的列数。  

## <a name="getcolumnflags"></a> Cdynamicaccessor:: Getcolumnflags

检索列特征。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool GetColumnFlags(DBORDINAL nColumn,   
   DBCOLUMNFLAGS* pFlags) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nColumn*<br/>
[in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
*pFlags*<br/>
[out]指向描述列特征的位掩码的指针。 请参阅中的"DBCOLUMNFLAGS 枚举类型" [icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704)中*OLE DB 程序员参考*。  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**如果成功检索列特征。 否则，返回 **false**。  
  
### <a name="remarks"></a>备注  

从一个偏移的列号。 列零是一种特殊情况;如果可用，则该书签。

## <a name="getcolumninfo"></a> Cdynamicaccessor:: Getcolumninfo

返回所需的大多数使用者的列元数据。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT GetColumnInfo(IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer) throw();  
```  
  
#### <a name="parameters"></a>参数  

*pRowset*<br/>
[in]一个指向[IRowset](/previous-versions/windows/desktop/ms720986)接口。  
  
*pColumns*<br/>
[out]一个指向内存中要在行集中; 返回的列数此数字包括书签列，如果有的话。  
  
*ppColumnInfo*<br/>
[out]指向内存中要返回的数组的指针`DBCOLUMNINFO`结构。 请参阅中的"DBCOLUMNINFO 结构" [icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704)中*OLE DB 程序员参考*。  
  
*ppStringsBuffer*<br/>
[out]指向在其中存储的所有字符串值返回一个指向内存的指针 (在使用名称*columnid* ; 二是*pwszName*) 单个分配块中。  
  
### <a name="return-value"></a>返回值  

一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  

请参阅[icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704)中*OLE DB 程序员参考*有关数据类型信息`DBORDINAL`， `DBCOLUMNINFO`，和`OLECHAR`。  

## <a name="getcolumnname"></a> Cdynamicaccessor:: Getcolumnname

检索指定列的名称。  
  
### <a name="syntax"></a>语法  
  
```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nColumn*<br/>
[in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
### <a name="return-value"></a>返回值  

指定列的名称。  

## <a name="getcolumntype"></a> Cdynamicaccessor:: Getcolumntype

检索指定列的数据类型。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool GetColumnType(DBORDINAL nColumn,   
   DBTYPE* pType) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nColumn*<br/>
[in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
*pType*<br/>
[out]指向指定列的数据类型的指针。  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**成功后或**false**失败。  

## <a name="getlength"></a> Cdynamicaccessor:: Getlength

检索指定列的长度。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool GetLength(DBORDINAL nColumn,   
   DBLENGTH* pLength) const throw();  

bool GetLength(const CHAR* pColumnName,   
   DBLENGTH* pLength) const throw();  

bool GetLength(const WCHAR* pColumnName,   
   DBLENGTH* pLength) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nColumn*<br/>
[in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。  
  
*pLength*<br/>
[out]指向包含以字节为单位的列的长度的整数的指针。  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**如果找到指定的列。 否则，此函数返回**false**。  
  
### <a name="remarks"></a>备注  

第一个重写使用的列号，而第二个和第三个重写 ANSI 或 Unicode 格式，使用列名称分别。 

## <a name="getordinal"></a> Cdynamicaccessor:: Getordinal

根据列名检索列号。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool GetOrdinal(const CHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  

bool GetOrdinal(const WCHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。  
  
*pOrdinal*<br/>
[out] 指向列号的指针。  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**如果找到具有指定名称的列。 否则，此函数返回**false**。

## <a name="getstatus"></a> Cdynamicaccessor:: Getstatus

检索指定列的状态。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool GetStatus(DBORDINAL nColumn,   
   DBSTATUS* pStatus) const throw();  

bool GetStatus(const CHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  

bool GetStatus(const WCHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nColumn*<br/>
[in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。  
  
*pStatus*<br/>
[out]指向包含的列状态的变量的指针。 请参阅[DBSTATUS](/previous-versions/windows/desktop/ms722617)中*OLE DB 程序员参考*有关详细信息。  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**如果找到指定的列。 否则，此函数返回**false**。  

## <a name="getvalue"></a> Cdynamicaccessor:: Getvalue

检索指定列的数据。  
  
### <a name="syntax"></a>语法  
  
```cpp
void* GetValue(DBORDINAL nColumn) const throw();  

void* GetValue(const CHAR* pColumnName) const throw();  

void* GetValue(const WCHAR* pColumnName) const throw();  

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*ctype*<br/>
[in]处理字符串类型以外的任意数据类型的模板化参数 (`CHAR*`， `WCHAR*`)，这需要特殊处理。 `GetValue` 使用基于此处指定相应的数据类型。  
  
*nColumn*<br/>
[in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
*pColumnName*<br/>
[in]列名称。  
  
*pData*<br/>
[out]指向指定列的内容的指针。  
  
### <a name="return-value"></a>返回值  

如果你想要将字符串数据传递，使用非模板化版本的`GetValue`。 此方法的非模板化版本返回`void*`，它指向包含指定的列数据的缓冲区的一部分。 如果找不到列，返回 NULL。  
  
对于所有其他数据类型，它是更易于使用的模板化版本`GetValue`。 模板化版本，会返回 **，则返回 true**成功后或**false**失败。  
  
### <a name="remarks"></a>备注  

使用非模板化版本，返回包含字符串和包含其他数据类型的列的模板化版本中的列。  
  
在调试模式下，如果您将收到一个断言的大小*pData*是为它所指向的列的大小不相等。  

## <a name="setblobhandling"></a> Cdynamicaccessor:: Setblobhandling

设置 BLOB 处理的当前行值。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);  
```  
  
#### <a name="parameters"></a>参数  

*eBlobHandling*<br/>
指定处理 BLOB 数据的方式。 它可以采用以下值：  
  
- DBBLOBHANDLING_DEFAULT： 处理列的数据大于*nBlobSize* (通过设置`SetBlobSizeLimit`) 作为 BLOB 数据，检索通过`ISequentialStream`或`IStream`对象。 此选项将尝试将每个列以包含大于数据绑定*nBlobSize*或列出为 DBTYPE_IUNKNOWN 作为 BLOB 数据。  
  
- DBBLOBHANDLING_NOSTREAMS： 处理列的数据大于*nBlobSize* (通过设置`SetBlobSizeLimit`) 作为 BLOB 数据，检索通过提供程序分配，使用者拥有的内存中的引用。 此选项可用于具有一个以上的 BLOB 列的表，该提供程序只支持一个`ISequentialStream`每个访问器的对象。  
  
- DBBLOBHANDLING_SKIP： 跳过 （不绑定） 限定为包含 Blob 的列 （访问器不能将绑定或检索列的值，但它仍将检索的列状态和长度）。  
  
### <a name="remarks"></a>备注  

在调用 `SetBlobHandling` 之前应当先调用 `Open`。  
  
构造函数方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)设置处理到 DBBLOBHANDLING_DEFAULT 值的 BLOB。

## <a name="setblobsizelimit"></a> Cdynamicaccessor:: Setblobsizelimit

以字节为单位设置的最大 BLOB 大小。  
  
### <a name="syntax"></a>语法  
  
```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);  
```  
  
#### <a name="parameters"></a>参数  

*nBlobSize*<br/>
指定的 BLOB 大小限制。  
  
### <a name="remarks"></a>备注  

以字节为单位; 设置的最大 BLOB 大小大于此值的列数据被视为 BLOB。 某些提供程序 （例如 2 GB) 的列提供极大的大小。 而不是尝试此大小的列分配内存时，您通常会尝试绑定这些列作为 Blob。 这样您无需分配所有内存，但您仍可以读取而无需担心截断的所有数据。 但是，有某些情况的下，您可能需要强制`CDynamicAccessor`以其本机数据类型绑定大的列。 若要执行此操作，调用`SetBlobSizeLimit`之前调用`Open`。  
  
构造函数方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)设置为默认值为 8000 个字节的最大 BLOB 大小。  

## <a name="setlength"></a> Cdynamicaccessor:: Setlength

设置指定列的长度。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool SetLength(DBORDINAL nColumn,   
   DBLENGTH nLength)throw();  

bool SetLength(const CHAR* pColumnName,   
   DBLENGTH nLength) throw();  

bool SetLength(const WCHAR* pColumnName,   
   DBLENGTH nLength) throw();  
```  
  
#### <a name="parameters"></a>参数  

*nColumn*<br/>
[in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
*nLength*<br/>
[in]以字节为单位的列的长度。  
  
*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**如果已成功设置指定的列长度。 否则，此函数返回**false**。  

## <a name="setstatus"></a> Cdynamicaccessor:: Setstatus

设置指定列的状态。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool SetStatus(DBORDINAL nColumn,   
   DBSTATUS status)throw();  

bool SetStatus(const CHAR* pColumnName,   
   DBSTATUS status) throw();  

bool SetStatus(const WCHAR* pColumnName,   
   DBSTATUS status) throw();  
```  
  
#### <a name="parameters"></a>参数  

*nColumn*<br/>
[in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
*status*<br/>
[in]列状态。 请参阅[DBSTATUS](/previous-versions/windows/desktop/ms722617)中*OLE DB 程序员参考*有关详细信息。  
  
*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**如果指定的列状态设置成功。 否则，此函数返回**false**。 

## <a name="setvalue"></a> Cdynamicaccessor:: Setvalue

将数据存储到指定的列。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template <class ctype>
bool SetValue(   
   DBORDINAL nColumn,   
   constctype& data) throw( );  

template <class ctype>    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data) throw( );  

template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data) throw( );  
```  
  
#### <a name="parameters"></a>参数  

*ctype*<br/>
[in]处理字符串类型以外的任意数据类型的模板化参数 (`CHAR*`， `WCHAR*`)，这需要特殊处理。 `GetValue` 使用基于此处指定相应的数据类型。  
  
*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。  
  
*data*<br/>
[in]指向包含数据的内存的指针。  
  
*nColumn*<br/>
[in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
### <a name="return-value"></a>返回值  

如果你想要设置字符串数据，使用非模板化版本的`GetValue`。 此方法的非模板化版本返回`void*`，它指向包含指定的列数据的缓冲区的一部分。 如果找不到列，返回 NULL。  
  
对于所有其他数据类型，它是更易于使用的模板化版本`GetValue`。 模板化版本，会返回 **，则返回 true**成功后或**false**失败。  

## <a name="see-also"></a>请参阅  

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 类](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)