---
title: CDynamicAccessor 类
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
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
ms.openlocfilehash: 6182d66b49647758bf17ab160d536e39b97b8c0f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216474"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor 类

使您可以在不知道数据库架构（数据库的基础结构）的情况下访问数据源。

## <a name="syntax"></a>语法

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>要求

**标头**： atldbcli。h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[AddBindEntry](#addbindentry)|重写默认访问器时，向输出列添加绑定项。|
|[CDynamicAccessor](#cdynamicaccessor)|实例化并初始化 `CDynamicAccessor` 对象。|
|[关闭](#close)|取消绑定所有列，释放已分配的内存，并释放类中的[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))接口指针。|
|[GetBlobHandling](#getblobhandling)|检索当前行的 BLOB 处理值。|
|[GetBlobSizeLimit](#getblobsizelimit)|检索最大 BLOB 大小（以字节为单位）。|
|[GetBookmark](#getbookmark)|检索当前行的书签。|
|[GetColumnCount](#getcolumncount)|检索行集中的列数。|
|[GetColumnFlags](#getcolumnflags)|检索列特性。|
|[GetColumnInfo](#getcolumninfo)|检索列元数据。|
|[GetColumnName](#getcolumnname)|检索指定列的名称。|
|[GetColumnType](#getcolumntype)|检索指定列的数据类型。|
|[GetLength](#getlength)|检索列的可能的最大长度（以字节为单位）。|
|[GetOrdinal](#getordinal)|根据给定的列名称检索列索引。|
|[GetStatus](#getstatus)|检索指定列的状态。|
|[GetValue](#getvalue)|从缓冲区中检索数据。|
|[SetBlobHandling](#setblobhandling)|设置当前行的 BLOB 处理值。|
|[SetBlobSizeLimit](#setblobsizelimit)|设置最大 BLOB 大小（以字节为单位）。|
|[SetLength](#setlength)|设置列的长度（以字节为单位）。|
|[SetStatus](#setstatus)|设置指定列的状态。|
|[SetValue](#setvalue)|将数据存储到缓冲区。|

## <a name="remarks"></a>备注

使用 `CDynamicAccessor` 方法来获取列信息，如列名称、列计数、数据类型等。 然后，使用此列信息在运行时动态创建访问器。

列信息存储在由此类创建和管理的缓冲区中。 使用[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)从缓冲区中获取数据。

有关使用动态访问器类的讨论和示例，请参阅[使用动态访问器](../../data/oledb/using-dynamic-accessors.md)。

## <a name="cdynamicaccessoraddbindentry"></a><a name="addbindentry"></a>CDynamicAccessor：： AddBindEntry

向输出列添加绑定项。

### <a name="syntax"></a>语法

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>参数

*信息*<br/>
中`DBCOLUMNINFO`包含列信息的结构。 请参阅*OLE DB 程序员参考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中的 "DBCOLUMNINFO 结构"。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

重写使用创建的默认访问器时，请使用此方法 `CDynamicAccessor` （请参阅[如何获取数据？](../../data/oledb/fetching-data.md)）。

## <a name="cdynamicaccessorcdynamicaccessor"></a><a name="cdynamicaccessor"></a>CDynamicAccessor：： CDynamicAccessor

实例化并初始化 `CDynamicAccessor` 对象。

### <a name="syntax"></a>语法

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>参数

*eBlobHandling*<br/>
指定二进制大型对象（BLOB）数据的处理方式。 默认值为 DBBLOBHANDLING_DEFAULT。 有关 DBBLOBHANDLINGENUM 值的说明，请参阅[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) 。

*nBlobSize*<br/>
最大 BLOB 大小（以字节为单位）；该值之上的列数据被视为 BLOB。 默认值为8000。 有关详细信息，请参阅[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) 。

### <a name="remarks"></a>备注

如果使用构造函数初始化 `CDynamicAccessor` 对象，则可以指定它将如何绑定 blob。 Blob 可以包含二进制数据（如图形、声音或编译的代码）。 默认行为是将大于8000字节的列视为 Blob，并尝试将其绑定到 `ISequentialStream` 对象。 但是，您可以将不同的值指定为 BLOB 大小。

还可以指定如何 `CDynamicAccessor` 处理限定为 blob 数据的列数据：它可以采用默认方式处理 blob 数据; 它可以跳过（不绑定） blob 数据; 也可以在提供程序分配的内存中绑定 blob 数据。

## <a name="cdynamicaccessorclose"></a><a name="close"></a>CDynamicAccessor：： Close

取消绑定所有列，释放已分配的内存，并释放类中的[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))接口指针。

### <a name="syntax"></a>语法

```cpp
void Close() throw();
```

## <a name="cdynamicaccessorgetblobhandling"></a><a name="getblobhandling"></a>CDynamicAccessor：： GetBlobHandling

检索当前行的 BLOB 处理值。

### <a name="syntax"></a>语法

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>备注

返回由[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)设置的 BLOB 处理值*eBlobHandling* 。

## <a name="cdynamicaccessorgetblobsizelimit"></a><a name="getblobsizelimit"></a>CDynamicAccessor：： GetBlobSizeLimit

检索最大 BLOB 大小（以字节为单位）。

### <a name="syntax"></a>语法

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>备注

返回由[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)设置的 BLOB 处理值*nBlobSize* 。

## <a name="cdynamicaccessorgetbookmark"></a><a name="getbookmark"></a>CDynamicAccessor：： GetBookmark

检索当前行的书签。

### <a name="syntax"></a>语法

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>参数

*pBookmark*<br/>
弄指向[CBookmark](../../data/oledb/cbookmark-class.md)对象的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

需要将设置 `DBPROP_IRowsetLocate` 为 VARIANT_TRUE 才能检索书签。

## <a name="cdynamicaccessorgetcolumncount"></a><a name="getcolumncount"></a>CDynamicAccessor：： GetColumnCount

检索列数。

### <a name="syntax"></a>语法

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>返回值

检索的列数。

## <a name="cdynamicaccessorgetcolumnflags"></a><a name="getcolumnflags"></a>CDynamicAccessor：： GetColumnFlags

检索列特性。

### <a name="syntax"></a>语法

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>参数

*nColumn*<br/>
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

*pFlags*<br/>
弄指向描述列特征的位掩码的指针。 请参阅*OLE DB 程序员参考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中的 "DBCOLUMNFLAGS 枚举类型"。

### <a name="return-value"></a>返回值

**`true`** 如果成功检索列特征，则返回。 否则，它将返回 **`false`** 。

### <a name="remarks"></a>备注

列号是从1开始的偏移量。 列零是一种特殊情况;如果可用，则为书签。

## <a name="cdynamicaccessorgetcolumninfo"></a><a name="getcolumninfo"></a>CDynamicAccessor：： GetColumnInfo

返回大多数使用方需要的列元数据。

### <a name="syntax"></a>语法

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>参数

*pRowset*<br/>
中指向[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))接口的指针。

*pColumns*<br/>
弄一个指向内存的指针，该内存用于返回行集中的列数;此数字包含书签列（如果有）。

*ppColumnInfo*<br/>
弄一个指向内存的指针，该内存用于返回结构的数组 `DBCOLUMNINFO` 。 请参阅*OLE DB 程序员参考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中的 "DBCOLUMNINFO 结构"。

*ppStringsBuffer*<br/>
弄一个指向内存的指针，该内存用于返回一个指针，该指针指向用于单个分配块内的所有字符串值（在*columnid*或*pwszName*中使用的名称）的存储区。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

有关数据类型、和的信息，请参阅*OLE DB 程序员参考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) `DBORDINAL` `DBCOLUMNINFO` `OLECHAR` 。

## <a name="cdynamicaccessorgetcolumnname"></a><a name="getcolumnname"></a>CDynamicAccessor：： GetColumnName

检索指定列的名称。

### <a name="syntax"></a>语法

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>参数

*nColumn*<br/>
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

### <a name="return-value"></a>返回值

指定列的名称。

## <a name="cdynamicaccessorgetcolumntype"></a><a name="getcolumntype"></a>CDynamicAccessor：： GetColumnType

检索指定列的数据类型。

### <a name="syntax"></a>语法

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>参数

*nColumn*<br/>
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

*pType*<br/>
弄指向指定列的数据类型的指针。

### <a name="return-value"></a>返回值

**`true`** 成功或失败时返回 **`false`** 。

## <a name="cdynamicaccessorgetlength"></a><a name="getlength"></a>CDynamicAccessor：： GetLength

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
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。

*pLength*<br/>
弄指向包含列长度（以字节为单位）的整数的指针。

### <a name="return-value"></a>返回值

**`true`** 如果找到指定列，则返回。 否则，此函数返回 **`false`** 。

### <a name="remarks"></a>备注

第一个重写采用列号，第二个和第三个重写分别采用 ANSI 或 Unicode 格式的列名。

## <a name="cdynamicaccessorgetordinal"></a><a name="getordinal"></a>CDynamicAccessor：： GetOrdinal

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

**`true`** 如果找到具有指定名称的列，则返回。 否则，此函数返回 **`false`** 。

## <a name="cdynamicaccessorgetstatus"></a><a name="getstatus"></a>CDynamicAccessor：： GetStatus

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
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。

*pStatus*<br/>
弄指向包含列状态的变量的指针。 有关详细信息，请参阅*OLE DB 程序员参考*中的[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) 。

### <a name="return-value"></a>返回值

**`true`** 如果找到指定列，则返回。 否则，此函数返回 **`false`** 。

## <a name="cdynamicaccessorgetvalue"></a><a name="getvalue"></a>CDynamicAccessor：： GetValue

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
中处理除字符串类型（，）以外的任何数据类型的模板化参数 `CHAR*` `WCHAR*` ，这需要特殊处理。 `GetValue`根据你在此处指定的内容使用适当的数据类型。

*nColumn*<br/>
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

*pColumnName*<br/>
中列名称。

*pData*<br/>
弄指向指定列的内容的指针。

### <a name="return-value"></a>返回值

如果要传递字符串数据，请使用的非模板化版本 `GetValue` 。 此方法的非模板化版本返回 **`void*`** ，指向包含指定列数据的缓冲区部分。 如果找不到该列，则返回 NULL。

对于所有其他数据类型，使用的模板化版本更为简单 `GetValue` 。 模板化版本会 **`true`** 在成功或 **`false`** 失败时返回。

### <a name="remarks"></a>备注

使用非模板化版本返回包含字符串的列以及包含其他数据类型的列的模板化版本。

在调试模式下，如果*pData*的大小与它所指向的列的大小不相等，则将获得一个断言。

## <a name="cdynamicaccessorsetblobhandling"></a><a name="setblobhandling"></a>CDynamicAccessor：： SetBlobHandling

设置当前行的 BLOB 处理值。

### <a name="syntax"></a>语法

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>参数

*eBlobHandling*<br/>
指定处理 BLOB 数据的方式。 该参数采用以下值：

- DBBLOBHANDLING_DEFAULT：将大于*nBlobSize*的列数据（由设置 `SetBlobSizeLimit` ）作为 BLOB 数据处理，并通过 `ISequentialStream` 或对象进行检索 `IStream` 。 此选项将尝试将包含大于*nBlobSize*的数据的每个列绑定到作为 BLOB 数据 DBTYPE_IUNKNOWN 列出的列。

- DBBLOBHANDLING_NOSTREAMS：将大于*nBlobSize*的列数据（由设置 `SetBlobSizeLimit` ）处理为 BLOB 数据，并在提供程序分配的、使用者拥有的内存中通过引用来检索它。 对于具有多个 BLOB 列的表，此选项非常有用，并且访问接口仅支持 `ISequentialStream` 每个访问器一个对象。

- DBBLOBHANDLING_SKIP： Skip （不要绑定）限定为包含 Blob 的列（该访问器不会绑定或检索列值，但它仍将检索列状态和长度）。

### <a name="remarks"></a>备注

在调用 `SetBlobHandling` 之前应当先调用 `Open`。

构造函数方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)将 BLOB 处理值设置为 DBBLOBHANDLING_DEFAULT。

## <a name="cdynamicaccessorsetblobsizelimit"></a><a name="setblobsizelimit"></a>CDynamicAccessor：： SetBlobSizeLimit

设置最大 BLOB 大小（以字节为单位）。

### <a name="syntax"></a>语法

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>参数

*nBlobSize*<br/>
指定 BLOB 大小限制。

### <a name="remarks"></a>备注

设置最大 BLOB 大小（以字节为单位）;大于此值的列数据将被视为 BLOB。 某些提供程序为列提供极大的大小（如 2 GB）。 你通常会尝试将这些列绑定为 Blob，而不是尝试为这种大小的列分配内存。 这样一来，就不需要分配所有内存，但仍可在不影响截断的情况下读取所有数据。 但是，在某些情况下，你可能想要强制 `CDynamicAccessor` 在其本机数据类型中绑定大列。 为此，请 `SetBlobSizeLimit` 在调用前调用 `Open` 。

构造函数方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)将最大 BLOB 大小设置为默认值8000字节。

## <a name="cdynamicaccessorsetlength"></a><a name="setlength"></a>CDynamicAccessor：： SetLength

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
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

*nLength*<br/>
中列的长度（以字节为单位）。

*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。

### <a name="return-value"></a>返回值

**`true`** 如果已成功设置指定的列长度，则返回。 否则，此函数返回 **`false`** 。

## <a name="cdynamicaccessorsetstatus"></a><a name="setstatus"></a>CDynamicAccessor：： SetStatus

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
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

*status*<br/>
中列状态。 有关详细信息，请参阅*OLE DB 程序员参考*中的[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) 。

*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。

### <a name="return-value"></a>返回值

**`true`** 如果指定的列状态设置成功，则返回。 否则，此函数返回 **`false`** 。

## <a name="cdynamicaccessorsetvalue"></a><a name="setvalue"></a>CDynamicAccessor：： SetValue

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
中处理除字符串类型（，）以外的任何数据类型的模板化参数 `CHAR*` `WCHAR*` ，这需要特殊处理。 `GetValue`根据你在此处指定的内容使用适当的数据类型。

*pColumnName*<br/>
[in] 指向包含列名的字符串的指针。

*data*<br/>
中指向包含数据的内存的指针。

*nColumn*<br/>
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

### <a name="return-value"></a>返回值

如果要设置字符串数据，请使用的非模板化版本 `GetValue` 。 此方法的非模板化版本返回 **`void*`** ，指向包含指定列数据的缓冲区部分。 如果找不到该列，则返回 NULL。

对于所有其他数据类型，使用的模板化版本更为简单 `GetValue` 。 模板化版本会 **`true`** 在成功或 **`false`** 失败时返回。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 类](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)
