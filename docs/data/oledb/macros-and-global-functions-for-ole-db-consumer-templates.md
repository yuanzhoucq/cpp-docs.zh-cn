---
title: OLE DB 使用者模板的宏和全局函数
ms.date: 11/04/2016
f1_keywords:
- vc.templates.ole
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: 95d39b6068405a88a20b311a5851e593591a24db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445495"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>OLE DB 使用者模板的宏和全局函数

OLE DB 使用者模板包括以下宏和全局函数：

## <a name="global-functions"></a>全局函数

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|如果返回错误，转储到转储设备的 OLE DB 错误记录信息。|

## <a name="accessor-map-macros"></a>取值函数映射宏

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|表示一个访问器条目的开头。|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|标记取值函数映射条目的开始。|
|[END_ACCESSOR](#end_accessor)|标记的末尾的访问器条目。|
|[END_ACCESSOR_MAP](#end_accessor_map)|标记取值函数映射条目的末尾。|

## <a name="column-map-macros"></a>列映射宏

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|表示用户记录类中的列映射条目的开头。|
|[BLOB_ENTRY](#blob_entry)|用于绑定二进制大型对象 (BLOB)。|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|报告的 BLOB 数据列的长度。|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|报告的长度和 BLOB 数据列的状态。|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|BLOB 数据列的状态报告。|
|[BLOB_NAME](#blob_name)|用于将二进制大型对象绑定的列名称。|
|[BLOB_NAME_LENGTH](#blob_name_length)|报告的 BLOB 数据列的长度。|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|报告的长度和 BLOB 数据列的状态。|
|[BLOB_NAME_STATUS](#blob_name_status)|BLOB 数据列的状态报告。|
|[BOOKMARK_ENTRY](#bookmark_entry)|表示行集上的书签条目。 书签项是一种特殊的列条目。|
|[COLUMN_ENTRY](#column_entry)|表示与数据库中的特定列的绑定。|
|[COLUMN_ENTRY_EX](#column_entry_ex)|表示与数据库中的特定列的绑定。 支持*类型*，*长度*，*精度*，*规模*，并*状态*参数。|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|表示与数据库中的特定列的绑定。 支持*长度*变量。|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|表示与数据库中的特定列的绑定。 支持*状态*并*长度*参数。|
|[COLUMN_ENTRY_PS](#column_entry_ps)|表示与数据库中的特定列的绑定。 支持*精度*并*规模*参数。|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|表示与数据库中的特定列的绑定。 支持*长度*变量*精度*并*规模*参数。|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|表示与数据库中的特定列的绑定。 支持*状态*并*长度*变量*精度*并*规模*参数。|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|表示与数据库中的特定列的绑定。 支持*状态*变量*精度*并*规模*参数。|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|表示与数据库中的特定列的绑定。 支持*状态*变量。|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|表示与数据库中的特定列的绑定。 支持*类型*参数。|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|表示与数据库中的特定列的绑定。 支持*类型*并*大小*参数。|
|[COLUMN_NAME](#column_name)|按名称表示与数据库中的特定列的绑定。|
|[COLUMN_NAME_EX](#column_name_ex)|按名称表示与数据库中的特定列的绑定。 支持数据类型、 大小、 精度、 小数位数、 列长度和列状态的规范。|
|[COLUMN_NAME_LENGTH](#column_name_length)|按名称表示与数据库中的特定列的绑定。 支持列长度的规范。|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|按名称表示与数据库中的特定列的绑定。 支持的列长度和状态的规范。|
|[COLUMN_NAME_PS](#column_name_ps)|按名称表示与数据库中的特定列的绑定。 支持的精度和小数位数的规范。|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|按名称表示与数据库中的特定列的绑定。 支持精度、 小数位数和列长度的规范。|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|按名称表示与数据库中的特定列的绑定。 支持精度、 小数位数、 列长度和列状态的规范。|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|按名称表示与数据库中的特定列的绑定。 支持指定的精度、 小数位数和列的状态。|
|[COLUMN_NAME_STATUS](#column_name_status)|按名称表示与数据库中的特定列的绑定。 支持列状态的规范。|
|[COLUMN_NAME_TYPE](#column_name_type)|按名称表示与数据库中的特定列的绑定。 支持数据类型的规范。|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|按名称表示与数据库中的特定列的绑定。 支持的数据类型、 精度和小数位数的规范。|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|按名称表示与数据库中的特定列的绑定。 支持数据类型和大小的规范。|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|按名称表示与数据库中的特定列的绑定。 支持数据类型和列状态的规范。|
|[END_COLUMN_MAP](#end_column_map)|标记列映射项的末尾。|

## <a name="command-macros"></a>命令宏

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|指定将用于创建行集时使用的命令[CCommand](../../data/oledb/ccommand-class.md)类。 仅接受字符串类型指定的应用程序类型 （ANSI 或 Unicode） 相匹配。 建议你使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是 DEFINE_COMMAND。|
|[DEFINE_COMMAND_EX](#define_command_ex)|指定将用于创建行集时使用的命令[CCommand](../../data/oledb/ccommand-class.md)类。 支持 ANSI 和 Unicode 应用程序。|

## <a name="parameter-map-macros"></a>参数映射宏

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|表示用户记录类中的参数映射条目的开头。|
|[END_PARAM_MAP](#end_param_map)|标记参数映射项的末尾。|
|[SET_PARAM_TYPE](#set_param_type)|指定作为输入、 输出或输入/输出执行 SET_PARAM_TYPE 宏 COLUMN_ENTRY 宏。|

### <a name="atltraceerrorrecords"></a> AtlTraceErrorRecords

如果返回错误，转储到转储设备的 OLE DB 错误记录信息。

#### <a name="syntax"></a>语法

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>参数

*hErr*<br/>
[in]OLE DB 使用者模板成员函数返回的 HRESULT。

#### <a name="remarks"></a>备注

如果*hErr*不是，则为 S_OK，`AtlTraceErrorRecords`转储到转储设备的 OLE DB 错误记录信息 (**调试**选项卡的输出窗口或文件)。 错误记录信息，可从提供程序获取，对于每个错误记录条目包括行号、 源、 说明、 帮助文件、 上下文和 GUID。 `AtlTraceErrorRecords` 转储仅在调试生成此信息。 在发布版本，它是空的存根进行了优化掉。

#### <a name="see-also"></a>请参阅

[CDBErrorInfo 类](../../data/oledb/cdberrorinfo-class.md)

### <a name="begin_accessor"></a> BEGIN_ACCESSOR

表示一个访问器条目的开头。

#### <a name="syntax"></a>语法

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>参数

*num*<br/>
[in]此取值函数映射中的访问器零偏移量。

*bAuto*<br/>
[in]指定此访问器是否为自动访问器或手动访问器。 如果 **，则返回 true**，访问器是自动; 如果**false**，访问器是否为手动。 自动取值函数意味着为你在移动操作提取数据。

#### <a name="remarks"></a>备注

如果行集的多个访问器，则需要指定 BEGIN_ACCESSOR_MAP，并为每个单独的取值函数使用 BEGIN_ACCESSOR 宏。 BEGIN_ACCESSOR 宏是已完成，但 END_ACCESSOR 宏。 BEGIN_ACCESSOR_MAP 宏是已完成，但 END_ACCESSOR_MAP 宏。

#### <a name="example"></a>示例

请参阅[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP

标记取值函数映射条目的开始。

#### <a name="syntax"></a>语法

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>参数

*x*<br/>
[in] 用户记录类的名称。

*num*<br/>
[in] 此取值函数映射中的取值函数数目。

#### <a name="remarks"></a>备注

如果行集的多个访问器，则需要在开头指定 BEGIN_ACCESSOR_MAP，并为每个单独的取值函数使用 BEGIN_ACCESSOR 宏。 BEGIN_ACCESSOR 宏是已完成，但 END_ACCESSOR 宏。 取值函数映射是已完成，但 END_ACCESSOR_MAP 宏。

如果在用户记录中只有一个取值函数，则使用宏 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)。

#### <a name="example"></a>示例

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a> END_ACCESSOR

标记的末尾的访问器条目。

#### <a name="syntax"></a>语法

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>备注

对于行集的多个访问器，您需要指定 BEGIN_ACCESSOR_MAP，并为每个单独的取值函数使用 BEGIN_ACCESSOR 宏。 BEGIN_ACCESSOR 宏是已完成，但 END_ACCESSOR 宏。 BEGIN_ACCESSOR_MAP 宏是已完成，但 END_ACCESSOR_MAP 宏。

#### <a name="example"></a>示例

请参阅[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="end_accessor_map"></a> END_ACCESSOR_MAP

标记取值函数映射条目的末尾。

#### <a name="syntax"></a>语法

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>备注

对于行集的多个访问器，您需要指定 BEGIN_ACCESSOR_MAP，并为每个单独的取值函数使用 BEGIN_ACCESSOR 宏。 BEGIN_ACCESSOR 宏是已完成，但 END_ACCESSOR 宏。 BEGIN_ACCESSOR_MAP 宏是已完成，但 END_ACCESSOR_MAP 宏。

#### <a name="example"></a>示例

请参阅[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="begin_column_map"></a> BEGIN_COLUMN_MAP

标记列映射条目的开头。

#### <a name="syntax"></a>语法

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>参数

*x*<br/>
[in] 派生自 `CAccessor`的用户记录类的名称。

#### <a name="remarks"></a>备注

在行集上存在单个访问器的情况下使用此宏。 如果行集上有多个访问器，则使用 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

BEGIN_COLUMN_MAP 宏是已完成，但 END_COLUMN_MAP 宏。 当用户记录中只需要一个访问器时才使用此宏。

列对应行集中你希望绑定的字段。

#### <a name="example"></a>示例

以下是示例列和参数映射：

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a> BLOB_ENTRY

BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 用于绑定的二进制大型对象 ([BLOB](/previous-versions/windows/desktop/ms711511))。

#### <a name="syntax"></a>语法

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*IID*<br/>
[in]接口的 GUID，如`IDD_ISequentialStream`，用于检索 BLOB。

*flags*<br/>
[in]定义由 OLE 结构化存储模型的存储模式标志 (例如， `STGM_READ`)。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="example"></a>示例

请参阅[如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH

BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 用于绑定的二进制大型对象 ([BLOB](/previous-versions/windows/desktop/ms711511))。 类似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不过此宏还获取以字节为单位的 BLOB 列的长度。

#### <a name="syntax"></a>语法

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*IID*<br/>
[in]接口的 GUID，如`IDD_ISequentialStream`，用于检索 BLOB。

*flags*<br/>
[in]定义由 OLE 结构化存储模型的存储模式标志 (例如， `STGM_READ`)。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[out]以字节为单位的 BLOB 列 （实际） 长度。

#### <a name="example"></a>示例

请参阅[如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS

BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 用于绑定的二进制大型对象 ([BLOB](/previous-versions/windows/desktop/ms711511))。 类似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不过此宏还可获取的长度和 BLOB 列的状态。

#### <a name="syntax"></a>语法

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*IID*<br/>
[in]接口的 GUID，如`IDD_ISequentialStream`，用于检索 BLOB。

*flags*<br/>
[in]定义由 OLE 结构化存储模型的存储模式标志 (例如， `STGM_READ`)。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[out]以字节为单位的 BLOB 列 （实际） 长度。

*status*<br/>
[out]BLOB 数据列的状态。

#### <a name="example"></a>示例

请参阅[如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_status"></a> BLOB_ENTRY_STATUS

BEGIN_COLUMN_MAP 或 BEGIN_ACCESSOR_MAP 用于绑定的二进制大型对象 ([BLOB](/previous-versions/windows/desktop/ms711511))。 类似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不过此宏还可获取 BLOB 列的状态。

#### <a name="syntax"></a>语法

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*IID*<br/>
[in]接口的 GUID，如`IDD_ISequentialStream`，用于检索 BLOB。

*flags*<br/>
[in]定义由 OLE 结构化存储模型的存储模式标志 (例如， `STGM_READ`)。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[out]该 BLOB 字段的状态。

#### <a name="example"></a>示例

请参阅[如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_name"></a> BLOB_NAME

BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 用于绑定的二进制大型对象 ([BLOB](/previous-versions/windows/desktop/ms711511))。 类似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不过此宏采用而不是列号的列名称。

#### <a name="syntax"></a>语法

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*IID*<br/>
[in]接口的 GUID，如`IDD_ISequentialStream`，用于检索 BLOB。

*flags*<br/>
[in]定义由 OLE 结构化存储模型的存储模式标志 (例如， `STGM_READ`)。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="example"></a>示例

请参阅[如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_name_length"></a> BLOB_NAME_LENGTH

BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 用于绑定的二进制大型对象 ([BLOB](/previous-versions/windows/desktop/ms711511))。 类似于[BLOB_NAME](../../data/oledb/blob-name.md)，只不过此宏还可获取长度以字节为单位的 BLOB 数据列。

#### <a name="syntax"></a>语法

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*IID*<br/>
[in]接口的 GUID，如`IDD_ISequentialStream`，用于检索 BLOB。

*flags*<br/>
[in]定义由 OLE 结构化存储模型的存储模式标志 (例如， `STGM_READ`)。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[out]以字节为单位的 BLOB 列 （实际） 长度。

### <a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS

BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 用于绑定的二进制大型对象 ([BLOB](/previous-versions/windows/desktop/ms711511))。 类似于[BLOB_NAME](../../data/oledb/blob-name.md)，只不过此宏还可获取的长度和 BLOB 数据列的状态。

#### <a name="syntax"></a>语法

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*IID*<br/>
[in]接口的 GUID，如`IDD_ISequentialStream`，用于检索 BLOB。

*flags*<br/>
[in]定义由 OLE 结构化存储模型的存储模式标志 (例如， `STGM_READ`)。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[out]以字节为单位的 BLOB 列 （实际） 长度。

*status*<br/>
[out]该 BLOB 字段的状态。

### <a name="blob_name_status"></a> BLOB_NAME_STATUS

BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 用于绑定的二进制大型对象 ([BLOB](/previous-versions/windows/desktop/ms711511))。 类似于[BLOB_NAME](../../data/oledb/blob-name.md)，只不过此宏还可获取 BLOB 数据列的状态。

#### <a name="syntax"></a>语法

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*IID*<br/>
[in]接口的 GUID，如`IDD_ISequentialStream`，用于检索 BLOB。

*flags*<br/>
[in]定义由 OLE 结构化存储模型的存储模式标志 (例如， `STGM_READ`)。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[out]该 BLOB 字段的状态。

### <a name="bookmark_entry"></a> BOOKMARK_ENTRY

将绑定书签列。

#### <a name="syntax"></a>语法

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>参数

*变量*<br/>
[in]要绑定到书签列的变量。

#### <a name="example"></a>示例

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

#### <a name="see-also"></a>请参阅

[CBookmark 类](../../data/oledb/cbookmark-class.md)<br/>
[DBPROP_BOOKMARKS](/previous-versions/windows/desktop/ms709728)

### <a name="column_entry"></a> COLUMN_ENTRY

在行集中的特定列表示行集上的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>参数

请参阅[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*。

*nOrdinal*<br/>
[in] 列号。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

COLUMN_ENTRY 宏可在以下位置：

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

#### <a name="example"></a>示例

请参阅中的宏主题中，示例[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="column_entry_ex"></a> COLUMN_ENTRY_EX

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>参数

请参阅[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*。

*nOrdinal*<br/>
[in] 列号。

*wType*<br/>
[in]数据类型。

*nLength*<br/>
[in]数据大小 （字节）。

*nPrecision*<br/>
[in]获取数据时要使用的最大精度和*wType*是`DBTYPE_NUMERIC`。 否则，将忽略此参数。

*nScale*<br/>
[in]要获取数据时使用的比例并*wType*是`DBTYPE_NUMERIC`或`DBTYPE_DECIMAL`。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

COLUMN_ENTRY_EX 宏可在以下位置：

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

#### <a name="example"></a>示例

请参阅[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>参数

请参阅[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*。

*nOrdinal*<br/>
[in]列号，从一开始。 书签对应于列零。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

#### <a name="remarks"></a>备注

此宏支持*长度*变量。 它在以下位置中使用：

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

### <a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>参数

请参阅[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*。

*nOrdinal*<br/>
[in] 列号。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

当您要支持长度和状态变量时，请使用此宏。 它在以下位置中使用：

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

### <a name="column_entry_ps"></a> COLUMN_ENTRY_PS

在行集中的特定列表示行集上的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>参数

请参阅[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*。

*nOrdinal*<br/>
[in] 列号。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

允许您指定要绑定的列的精度和小数位数。 它在以下位置中使用：

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

### <a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>参数

请参阅[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*。

*nOrdinal*<br/>
[in]列号，从一开始。 书签对应于列零。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

#### <a name="remarks"></a>备注

允许您指定要绑定的列的精度和小数位数。 此宏支持*长度*变量。 它在以下位置中使用：

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

### <a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>参数

请参阅[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*。

*nOrdinal*<br/>
[in] 列号。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

允许您指定要绑定的列的精度和小数位数。 当您要支持长度和状态变量时，请使用此宏。 它在以下位置中使用：

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

### <a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>参数

请参阅[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*。

*nOrdinal*<br/>
[in] 列号。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

允许您指定要绑定的列的精度和小数位数。 此宏支持*状态*变量。 它在以下位置中使用：

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

### <a name="column_entry_status"></a> COLUMN_ENTRY_STATUS

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>参数

请参阅[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*。

*nOrdinal*<br/>
[in] 列号。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

此宏支持*状态*变量。 它在以下位置中使用：

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

### <a name="column_entry_type"></a> COLUMN_ENTRY_TYPE

表示与数据库中的特定列的绑定。 支持*类型*参数。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*wType*<br/>
[in]数据类型列条目。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

此宏是专用的变体[COLUMN_ENTRY](../../data/oledb/column-entry.md)宏来提供指定数据类型的方式。

### <a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE

表示与数据库中的特定列的绑定。 支持*类型*并*大小*参数。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*wType*<br/>
[in]数据类型列条目。

*nLength*<br/>
[in]以字节为单位的列项的大小。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

此宏是专用的变体[COLUMN_ENTRY](../../data/oledb/column-entry.md)宏来提供指定数据大小和类型的方式。

### <a name="column_name"></a> COLUMN_NAME

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_ENTRY](../../data/oledb/column-entry.md)，只不过此宏采用而不是列号的列名称。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

为在相同位置使用 COLUMN_NAME_ * 宏，则[COLUMN_ENTRY](../../data/oledb/column-entry.md):

- 之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)并[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。

- 之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

- 之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)并[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。

### <a name="column_name_ex"></a> COLUMN_NAME_EX

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过该宏还包含数据类型、 大小、 精度、 小数位数、 列长度和列状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*wType*<br/>
[in]数据类型。

*nLength*<br/>
[in]数据大小 （字节）。

*nPrecision*<br/>
[in]获取数据时要使用的最大精度和*wType*是`DBTYPE_NUMERIC`。 否则，将忽略此参数。

*nScale*<br/>
[in]要获取数据时使用的比例并*wType*是`DBTYPE_NUMERIC`或`DBTYPE_DECIMAL`。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_length"></a> COLUMN_NAME_LENGTH

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过该宏还包含列的长度。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过该宏还包含列的长度和列状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_ps"></a> COLUMN_NAME_PS

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过此宏还采用精度和小数位数。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过此宏还采用精度、 小数位数和列的长度。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过此宏还采用精度、 小数位数、 列长度和列的状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过此宏还采用精度、 小数位数和列的状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_status"></a> COLUMN_NAME_STATUS

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过该宏还包含列状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_type"></a> COLUMN_NAME_TYPE

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过此宏还将数据类型。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*wType*<br/>
[in]数据类型。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过该宏还包含数据类型、 精度和小数位数。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*wType*<br/>
[in]数据类型。

*nPrecision*<br/>
[in]获取数据时要使用的最大精度和*wType*是`DBTYPE_NUMERIC`。 否则，将忽略此参数。

*nScale*<br/>
[in]要获取数据时使用的比例并*wType*是`DBTYPE_NUMERIC`或`DBTYPE_DECIMAL`。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过该宏还包含数据类型和大小。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*wType*<br/>
[in]数据类型。

*nLength*<br/>
[in]数据大小 （字节）。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS

在行集中的特定列表示行集上的绑定。 类似于[COLUMN_NAME](../../data/oledb/column-name.md)，只不过该宏还包含数据类型和列的状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
[in]指向列名称的指针。 名称必须是 Unicode 字符串。 您可以完成此操作通过将置于 L 的所有引用，例如： `L"MyColumn"`。

*wType*<br/>
[in]数据类型。

*status*<br/>
[in] 要绑定到列变量的状态。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>备注

请参阅[COLUMN_NAME](../../data/oledb/column-name.md)使用 COLUMN_NAME_ * 宏的信息。

### <a name="end_column_map"></a> END_COLUMN_MAP

标记列映射项的末尾。

#### <a name="syntax"></a>语法

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>备注

它用于单个访问器行集上。 BEGIN_COLUMN_MAP 宏是已完成，但 END_COLUMN_MAP 宏。

#### <a name="example"></a>示例

请参阅[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)。

### <a name="define_command"></a> DEFINE_COMMAND

指定将用于创建行集时使用的命令[CCommand](../../data/oledb/ccommand-class.md)类。 仅接受字符串类型指定的应用程序类型 （ANSI 或 Unicode） 相匹配。

> [!NOTE]
>  建议你使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是 DEFINE_COMMAND。

#### <a name="syntax"></a>语法

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>参数

*x*<br/>
[in]用户记录 （命令） 类的名称。

*szCommand*<br/>
[in]将用于创建行集时使用的命令字符串[CCommand](../../data/oledb/ccommand-class.md)。

#### <a name="remarks"></a>备注

如果未指定命令文本中的，将为默认使用您指定的命令字符串[ccommand:: Open](../../data/oledb/ccommand-open.md)方法。

如果生成为 Unicode 应用程序，此宏接受 ANSI 字符串，如果您生成应用程序为 ANSI 或 Unicode 字符串。 建议你使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是 DEFINE_COMMAND，因为前者接受 Unicode 字符串，而不考虑 ANSI 或 Unicode 应用程序类型。

#### <a name="example"></a>示例

请参阅[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="define_command_ex"></a> DEFINE_COMMAND_EX

指定将用于创建行集时使用的命令[CCommand](../../data/oledb/ccommand-class.md)类。 支持 Unicode 和 ANSI 应用程序。

#### <a name="syntax"></a>语法

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>参数

*x*<br/>
[in]用户记录 （命令） 类的名称。

*wszCommand*<br/>
[in]将用于创建行集时使用的命令字符串[CCommand](../../data/oledb/ccommand-class.md)。

#### <a name="remarks"></a>备注

如果未指定命令文本中的，将为默认使用您指定的命令字符串[ccommand:: Open](../../data/oledb/ccommand-open.md)方法。

此宏接受 Unicode 字符串，而不考虑应用程序类型。 此宏是通过首选[DEFINE_COMMAND](../../data/oledb/define-command.md)因为它支持 Unicode 和 ANSI 应用程序。

#### <a name="example"></a>示例

请参阅[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="begin_param_map"></a> BEGIN_PARAM_MAP

标记参数映射项的开始。

#### <a name="syntax"></a>语法

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>参数

*x*<br/>
[in] 用户记录类的名称。

#### <a name="remarks"></a>备注

使用参数[命令](/previous-versions/windows/desktop/ms724608)。

#### <a name="example"></a>示例

有关示例，请参阅[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)宏。

### <a name="end_param_map"></a> END_PARAM_MAP

标记参数映射项的末尾。

#### <a name="syntax"></a>语法

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>示例

有关示例，请参阅[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)宏。

### <a name="set_param_type"></a> SET_PARAM_TYPE

指定 COLUMN_ENTRY 宏，请按照 SET_PARAM_TYPE 宏输入、 输出或输入/输出。

#### <a name="syntax"></a>语法

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>参数

*type*<br/>
[in] 要为参数设置的类型。

#### <a name="remarks"></a>备注

提供程序仅支持基础数据源支持的参数输入/输出类型。 类型是一个或多个组合`DBPARAMIO`值 (请参阅[DBBINDING 结构](/previous-versions/windows/desktop/ms716845)中*OLE DB 程序员参考*):

- `DBPARAMIO_NOTPARAM` 访问器没有任何参数。 通常情况下，设置`eParamIO`为行访问器，以提醒用户将忽略参数中此值。

- `DBPARAMIO_INPUT` 一个输入的参数。

- `DBPARAMIO_OUTPUT` 输出参数。

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` 参数是输入和输出参数。

#### <a name="example"></a>示例

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)