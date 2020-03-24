---
title: OLE DB 提供程序模板宏
ms.date: 02/11/2019
f1_keywords:
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
ms.openlocfilehash: 2fda4d9f003e84247527d964685e631532d4c366
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210140"
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB 提供程序模板宏

OLE DB 模板提供程序宏提供以下类别的功能：

## <a name="property-set-map-macros"></a>属性集映射宏

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|标记属性集的开头。|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|标记属性集的开头。|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|标记可以在提供程序范围之外隐藏或定义的属性集的开头。|
|[CHAIN_PROPERTY_SET](#chain_property_set)|将属性组链接在一起。|
|[END_PROPERTY_SET](#end_property_set)|标记属性集的结尾。|
|[END_PROPSET_MAP](#end_propset_map)|标记属性集映射的结尾。|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|将属性中的特定属性设置为默认值。|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|将属性中的特定属性设置为提供的值。 还允许您设置标志和选项。|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|将属性中的特定属性设置为提供的值。|

## <a name="column-map-macros"></a>列映射宏

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|标记提供程序列映射条目的开头。|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|标记提供程序列映射项的结尾。|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|表示提供程序支持的特定列。|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|表示提供程序支持的特定列。 您可以指定列数据类型。|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|表示提供程序支持的特定列。 可以指定列的大小、数据类型、精度、小数位数和架构行集 GUID。|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|表示提供程序支持的特定列。 您可以指定列大小。|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|表示提供程序支持的特定列。 它假定列类型为字符串。|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|表示提供程序支持的特定列。 与 PROVIDER_COLUMN_ENTRY_LENGTH 一样，还允许您指定列的数据类型和大小。|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|表示提供程序支持的特定列。 它假定列类型是 Unicode 字符串。|

## <a name="schema-rowset-macros"></a>架构行集宏

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|标记架构映射的开头。|
|[END_SCHEMA_MAP](#end_schema_map)|标记架构映射的结尾。|
|[SCHEMA_ENTRY](#schema_entry)|将 GUID 与类相关联。|

## <a name="requirements"></a>要求

**标头：** atldb.h

### <a name="begin_property_set"></a><a name="begin_property_set"></a>BEGIN_PROPERTY_SET

标记属性集映射中设置的属性的开头。

#### <a name="syntax"></a>语法

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>parameters

*guid*<br/>
中属性 GUID。

#### <a name="example"></a>示例

请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a>BEGIN_PROPERTY_SET_EX

标记属性集映射中设置的属性的开头。

#### <a name="syntax"></a>语法

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>parameters

*guid*<br/>
中属性 GUID。

*flag*<br/>
中对于您不希望公开的任何属性集，或在提供程序范围外公开属性的提供程序 UPROPSET_PASSTHROUGH UPROPSET_HIDDEN。

#### <a name="example"></a>示例

请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a>BEGIN_PROPSET_MAP

标记属性集映射条目的开头。

#### <a name="syntax"></a>语法

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>parameters

*类*<br/>
中在其中指定此属性集的类。 可以在以下 OLE DB 对象中指定属性集：

- [数据源对象](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [会话对象](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [命令](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>示例

下面是一个示例属性集映射：

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a>CHAIN_PROPERTY_SET

此宏将属性组链接在一起。

#### <a name="syntax"></a>语法

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>parameters

*ChainClass*<br/>
中要链接其属性的类的名称。 这是 ATL 项目向导生成的一个类，它已经包含一个映射（如会话、命令或数据源对象类）。

#### <a name="remarks"></a>备注

可以将另一个类的属性集链接到自己的类，然后直接从类访问属性。

> [!CAUTION]
>  请慎用此宏。 使用不当会导致使用者未能 OLE DB 一致性测试。

### <a name="end_property_set"></a><a name="end_property_set"></a>END_PROPERTY_SET

标记属性集的结尾。

#### <a name="syntax"></a>语法

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>parameters

*guid*<br/>
中属性 GUID。

#### <a name="example"></a>示例

请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="end_propset_map"></a><a name="end_propset_map"></a>END_PROPSET_MAP

标记属性集映射项的结尾。

#### <a name="syntax"></a>语法

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>示例

请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="property_info_entry"></a><a name="property_info_entry"></a>PROPERTY_INFO_ENTRY

表示属性集中的特定属性。

#### <a name="syntax"></a>语法

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>parameters

*dwPropID*<br/>
[in] 一个 [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 值，该值可与属性集 GUID 一起使用以标识属性。

#### <a name="remarks"></a>备注

此宏将 `DWORD` 类型的属性值设置为 ATLDB.H 中定义的默认值。 若要将属性设置为所选的值，请使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)。 若要同时为属性设置 `VARTYPE` 和[DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) ，请使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。

#### <a name="example"></a>示例

请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a>PROPERTY_INFO_ENTRY_EX

表示属性集中的特定属性。

#### <a name="syntax"></a>语法

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>parameters

*dwPropID*<br/>
[in] 一个 [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 值，该值可与属性集 GUID 一起使用以标识属性。

*vt*<br/>
[in] 此属性项的 `VARTYPE`。 （在 wtypes 中定义）

dwFlags<br/>
[in] 一个描述此属性项的 [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) 值。

*value*<br/>
[in] `DWORD`类型的属性值。

*选项*<br/>
DBPROPOPTIONS_REQUIRED 或 DBPROPOPTIONS_SETIFCHEAP。 通常，提供程序不需要设置*选项*，因为它是由使用者设置的。

#### <a name="remarks"></a>备注

使用此宏，你可以直接指定 `DWORD` 类型的属性值以及选项和标记。 若要仅将属性设置为 ATLDB.H 中指定的默认值，请使用 [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要将属性设置为你选择的值且不要设置其上的选项或标记，请使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)。

#### <a name="example"></a>示例

请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a>PROPERTY_INFO_ENTRY_VALUE

表示属性集中的特定属性。

#### <a name="syntax"></a>语法

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>parameters

*dwPropID*<br/>
[in] 一个 [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) 值，该值可与属性集 GUID 一起使用以标识属性。

*value*<br/>
[in] `DWORD`类型的属性值。

#### <a name="remarks"></a>备注

利用此宏，你可以直接指定 `DWORD`类型的属性值。 将属性设置为为 ATLDB.H 中定义的默认值。H，使用[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要设置属性的值、标志和选项，请使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。

#### <a name="example"></a>示例

请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a>BEGIN_PROVIDER_COLUMN_MAP

标记提供程序列映射条目的开头。

#### <a name="syntax"></a>语法

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>parameters

*类*<br/>
中此映射所属的类的名称。

#### <a name="example"></a>示例

下面是一个示例提供程序列映射：

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a>END_PROVIDER_COLUMN_MAP

标记提供程序列映射项的结尾。

#### <a name="syntax"></a>语法

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>示例

请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a>PROVIDER_COLUMN_ENTRY

表示提供程序支持的特定列。

#### <a name="syntax"></a>语法

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>parameters

name<br/>
中列名称。

*序号*<br/>
[in] 列号。 除非该列为书签列，否则列号不能为0。

*member*<br/>
中对应于列 `dataClass` 中的成员变量。

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a>PROVIDER_COLUMN_ENTRY_FIXED

表示提供程序支持的特定列。

#### <a name="syntax"></a>语法

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>parameters

name<br/>
中列名称。

*序号*<br/>
[in] 列号。 除非该列为书签列，否则列号不能为0。

*dbtype*<br/>
中[DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))中的数据类型。

*member*<br/>
中用于存储数据的 `dataClass` 中的成员变量。

#### <a name="remarks"></a>备注

允许您指定列数据类型。

#### <a name="example"></a>示例

请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a>PROVIDER_COLUMN_ENTRY_GN

表示提供程序支持的特定列。

#### <a name="syntax"></a>语法

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>parameters

name<br/>
中列名称。

*序号*<br/>
[in] 列号。 除非该列为书签列，否则列号不能为0。

*flag*<br/>
中指定返回数据的方式。 请参阅[DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85))中的 `dwFlags` 说明。

*colSize*<br/>
中列大小。

*dbtype*<br/>
中指示值的数据类型。 请参阅[DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85))中的 `wType` 说明。

*精度*<br/>
中指示当*dbType*为 DBTYPE_NUMERIC 或 DBTYPE_DECIMAL 时，获取数据时要使用的精度。 请参阅[DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85))中的 `bPrecision` 说明。

*scale*<br/>
中指示在 DBTYPE_NUMERIC 或 DBTYPE_DECIMAL dbType 时获取数据时要使用的小数位数。 请参阅[DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85))中的 `bScale` 说明。

*guid*<br/>
架构行集 GUID。 有关架构行集及其 Guid 的列表，请参阅*OLE DB 程序员参考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

#### <a name="remarks"></a>备注

允许您指定列的大小、数据类型、精度、小数位数和架构行集 GUID。

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a>PROVIDER_COLUMN_ENTRY_LENGTH

表示提供程序支持的特定列。

#### <a name="syntax"></a>语法

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>parameters

name<br/>
中列名称。

*序号*<br/>
[in] 列号。 除非该列为书签列，否则列号不能为0。

size<br/>
中列大小（以字节为单位）。

*member*<br/>
中存储列数据 `dataClass` 中的成员变量。

#### <a name="remarks"></a>备注

允许您指定列大小。

#### <a name="example"></a>示例

请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a>PROVIDER_COLUMN_ENTRY_STR

表示提供程序支持的特定列。

#### <a name="syntax"></a>语法

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>parameters

name<br/>
中列名称。

*序号*<br/>
[in] 列号。 除非该列为书签列，否则列号不能为0。

*member*<br/>
中数据类中存储数据的成员变量。

#### <a name="remarks"></a>备注

当假定列数据[DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85))时，请使用此宏。

#### <a name="example"></a>示例

请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

表示提供程序支持的特定列。

#### <a name="syntax"></a>语法

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>parameters

name<br/>
中列名称。

*序号*<br/>
[in] 列号。 除非该列为书签列，否则列号不能为0。

*dbtype*<br/>
中[DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85))中的数据类型。

size<br/>
中列大小（以字节为单位）。

*member*<br/>
中数据类中存储数据的成员变量。

#### <a name="remarks"></a>备注

与[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)类似，但也可用于指定列的数据类型和大小。

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a>PROVIDER_COLUMN_ENTRY_WSTR

表示提供程序支持的特定列。

#### <a name="syntax"></a>语法

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>parameters

name<br/>
中列名称。

*序号*<br/>
[in] 列号。 除非该列为书签列，否则列号不能为0。

*member*<br/>
中数据类中存储数据的成员变量。

#### <a name="remarks"></a>备注

当列数据为以 null 结尾的 Unicode 字符串（ [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85))）时，请使用此宏。

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a>BEGIN_SCHEMA_MAP

表示架构映射的开头。

#### <a name="syntax"></a>语法

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>parameters

*SchemaClass*<br/>
包含映射的类。 通常，这将是 session 类。

#### <a name="remarks"></a>备注

有关架构行集的详细信息，请参阅 Windows SDK 中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

### <a name="end_schema_map"></a><a name="end_schema_map"></a>END_SCHEMA_MAP

表示架构映射的结尾。

#### <a name="syntax"></a>语法

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>备注

有关详细信息，请参阅[IDBSchemaRowsetImpl 类](../../data/oledb/idbschemarowsetimpl-class.md)。

### <a name="schema_entry"></a><a name="schema_entry"></a>SCHEMA_ENTRY

将 GUID 与类相关联。

#### <a name="syntax"></a>语法

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>parameters

*guid*<br/>
架构行集 GUID。 有关架构行集及其 Guid 的列表，请参阅*OLE DB 程序员参考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

*rowsetClass*<br/>
将创建用于表示架构行集的类。

#### <a name="remarks"></a>备注

然后， [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)可以在映射中查询 guid 列表，也可以在给定 guid 时创建行集。 `IDBSchemaRowsetImpl` 创建的架构行集类似于标准的 `CRowsetImpl`派生类，但它必须提供具有以下签名的 `Execute` 方法：

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

此 `Execute` 函数填充行集的数据。 ATL 项目向导按照*OLE DB 程序员参考*中的[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))中所述，在项目中为三个必需 OLE DB 架构中的每一个创建三个初始架构行集：

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

向导还在架构映射中添加了三个对应的条目。 有关使用向导创建提供程序的详细信息，请参阅[创建 OLE DB 模板提供程序](../../data/oledb/creating-an-ole-db-provider.md)。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 提供程序模板参考](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)
