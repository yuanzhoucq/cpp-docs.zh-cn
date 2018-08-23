---
title: OLE DB 提供程序模板宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 747f54e4ae37fe31eeea7540c1531b988d692427
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42573319"
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB 提供程序模板宏
OLE DB 模板 Provider 宏提供了以下类别中的功能：  
  
## <a name="property-set-map-macros"></a>属性设置映射宏  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](#begin_property_set)|表示属性集的开头。|  
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|表示属性集的开头。|  
|[BEGIN_PROPSET_MAP](#begin_propset_map)|可以隐藏或提供程序的作用域之外定义的属性的开头设置的标记。|  
|[CHAIN_PROPERTY_SET](#chain_property_set)|属性组链接在一起。|  
|[END_PROPERTY_SET](#end_property_set)|将标记属性集的末尾。|  
|[END_PROPSET_MAP](#end_propset_map)|将标记属性集映射的结尾。|  
|[PROPERTY_INFO_ENTRY](#property_info_entry)|设置特定属性中的属性设置为默认值。|  
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|设置特定属性中的属性设置为您提供的值。 此外可以设置标志和选项。|  
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|设置特定属性中的属性设置为您提供的值。|  
  
## <a name="column-map-macros"></a>列映射宏  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|表示提供程序的列映射条目的开头。|  
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|标记提供程序的列映射项的末尾。|  
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|表示提供程序支持的特定列。|  
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|表示提供程序支持的特定列。 可以指定列数据类型。|  
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|表示提供程序支持的特定列。 您可以指定列的大小、 数据类型、 精度、 小数位数和架构行集 GUID。|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|表示提供程序支持的特定列。 可以指定列大小。|  
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|表示提供程序支持的特定列。 它假定列类型为字符串。|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|表示提供程序支持的特定列。 PROVIDER_COLUMN_ENTRY_LENGTH，但还可以指定列的数据类型，以及大小。|  
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|表示提供程序支持的特定列。 它假定列类型为 Unicode 字符串。|  
  
## <a name="schema-rowset-macros"></a>架构行集宏  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|表示架构映射的开头。|  
|[END_SCHEMA_MAP](#end_schema_map)|将架构映射的结尾标记。|  
|[SCHEMA_ENTRY](#schema_entry)|将 GUID 与类相关联。|  

## <a name="requirements"></a>要求  
 **标头：** atldb.h  

### <a name="begin_property_set"></a> BEGIN_PROPERTY_SET
在属性中设置属性的开头的标记集映射。  
  
#### <a name="syntax"></a>语法  
  
```cpp
BEGIN_PROPERTY_SET(guid)  
```  
  
#### <a name="parameters"></a>参数  
 *guid*  
 [in]该属性的 GUID。  
  
#### <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX
在属性中设置属性的开头的标记集映射。  
  
#### <a name="syntax"></a>语法  
  
```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)  
```  
  
#### <a name="parameters"></a>参数  
 *guid*  
 [in]该属性的 GUID。  
  
 *flags*  
 [in]针对不想要公开，任何属性集或提供程序公开的提供程序的讨论范围内定义的属性的 UPROPSET_PASSTHROUGH UPROPSET_HIDDEN。  
  
#### <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="begin_propset_map"></a> BEGIN_PROPSET_MAP
标记属性的开头设置的映射条目。  
  
#### <a name="syntax"></a>语法  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
```  
  
#### <a name="parameters"></a>参数  
 *类*  
 [in]指定设置此属性的类。 可以在以下 OLE DB 对象中指定属性集：  
  
-   [数据源对象](/previous-versions/windows/desktop/ms721278\(v=vs.85\))  
  
-   [会话对象](/previous-versions/windows/desktop/ms711572\(v=vs.85\))  
  
-   [命令](/previous-versions/windows/desktop/ms724608\(v=vs.85\))  
  
#### <a name="example"></a>示例  
 下面是示例属性集映射：  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  

### <a name="chain_property_set"></a> CHAIN_PROPERTY_SET
此宏链接属性组在一起。  
  
#### <a name="syntax"></a>语法  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
```  
  
#### <a name="parameters"></a>参数  
 *ChainClass*  
 [in]要为其链属性类的名称。 这是由已包含一个映射 （如会话、 命令或数据源对象类） ATL 项目向导生成的类。  
  
#### <a name="remarks"></a>备注  
 你可以链接在从另一个类属性设置为你自己的类，然后直接从您的类访问这些属性。  
  
> [!CAUTION]
>  谨慎使用此宏。 使用不当可能会导致使用者，以 OLE DB 一致性测试失败。  

### <a name="end_property_set"></a> END_PROPERTY_SET
将标记属性集的末尾。  
  
#### <a name="syntax"></a>语法  
  
```cpp
END_PROPERTY_SET(guid)  
```  
  
#### <a name="parameters"></a>参数  
 *guid*  
 [in]该属性的 GUID。  
  
#### <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="end_propset_map"></a> END_PROPSET_MAP
标记属性的结尾设置映射条目。  
  
#### <a name="syntax"></a>语法  
  
```cpp
END_PROPSET_MAP()  
```  
  
#### <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="property_info_entry"></a> PROPERTY_INFO_ENTRY
表示属性集中的特定属性。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROPERTY_INFO_ENTRY(dwPropID)  
```  
  
#### <a name="parameters"></a>参数  
 *dwPropID*  
 [in]一个[DBPROPID](/previous-versions/windows/desktop/ms723882\(v=vs.85\))可以与属性结合使用的值设置标识属性的 GUID。  
  
#### <a name="remarks"></a>备注  
 此宏将 `DWORD` 类型的属性值设置为 ATLDB.H 中定义的默认值。 若要将属性设置为所选的值，请使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)。 若要设置[VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4)并[DBPROPFLAGS](/previous-versions/windows/desktop/ms724342\(v=vs.85\))对于在同一时间属性，使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。  
  
#### <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX
表示属性集中的特定属性。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)  
```  
  
#### <a name="parameters"></a>参数  
 *dwPropID*  
 [in]一个[DBPROPID](/previous-versions/windows/desktop/ms723882\(v=vs.85\))可以与属性结合使用的值设置标识属性的 GUID。  
  
 *vt*  
 [in][VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4)此属性项。  
  
 *dwFlags*  
 [in]一个[DBPROPFLAGS](/previous-versions/windows/desktop/ms724342\(v=vs.85\))描述此属性项的值。  
  
 *值*  
 [in] `DWORD`类型的属性值。  
  
 *options*  
 DBPROPOPTIONS_REQUIRED 或 DBPROPOPTIONS_SETIFCHEAP。 通常情况下，提供程序不需要设置*选项*由于使用者设置。  
  
#### <a name="remarks"></a>备注  
 使用此宏，你可以直接指定 `DWORD` 类型的属性值以及选项和标记。 若要仅将属性设置为 ATLDB.H 中指定的默认值，请使用 [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要将属性设置为你选择的值且不要设置其上的选项或标记，请使用 [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)。  
  
#### <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE
表示属性集中的特定属性。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)  
```  
  
#### <a name="parameters"></a>参数  
 *dwPropID*  
 [in]一个[DBPROPID](/previous-versions/windows/desktop/ms723882\(v=vs.85\))可以与属性结合使用的值设置标识属性的 GUID。  
  
 *value*  
 [in] `DWORD`类型的属性值。  
  
#### <a name="remarks"></a>备注  
 使用此宏，你可以直接指定类型的属性值`DWORD`。 若要将属性设置为 ATLDB 中定义的默认值。H，使用[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)。 若要设置的值、 标志和属性的选项，请使用[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)。  
  
#### <a name="example"></a>示例  
 请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  

### <a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP
表示提供程序的列映射条目的开头。  
  
#### <a name="syntax"></a>语法  
  
```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)  
```  
  
#### <a name="parameters"></a>参数  
 *类*  
 [in]此映射所属的类的名称。  
  
#### <a name="example"></a>示例  
 下面是示例提供程序列映射：  
  
 [!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]  

### <a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP
标记提供程序的列映射项的末尾。  
  
#### <a name="syntax"></a>语法  
  
```cpp
END_PROVIDER_COLUMN_MAP()  
```  
  
#### <a name="example"></a>示例  
 请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。  

### <a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY
表示提供程序支持的特定列。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 *序号*  
 [in] 列号。 除非列为书签列，列数必须不为 0。  
  
 *成员*  
 [in]中的成员变量`dataClass`的列相对应。  

### <a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED
表示提供程序支持的特定列。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 *序号*  
 [in] 列号。 除非列为书签列，列数必须不为 0。  
  
 *dbtype*  
 [in]中的数据类型[DBTYPE](/previous-versions/windows/desktop/ms711251\(v=vs.85\))。  
  
 *成员*  
 [in]中的成员变量`dataClass`存储的数据。  
  
#### <a name="remarks"></a>备注  
 可以指定列数据类型。  
  
#### <a name="example"></a>示例  
 请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。  

### <a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN
表示提供程序支持的特定列。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 *序号*  
 [in] 列号。 除非列为书签列，列数必须不为 0。  
  
 *flags*  
 [in]指定如何返回数据。 请参阅`dwFlags`中的说明[DBBINDING 结构](/previous-versions/windows/desktop/ms716845\(v=vs.85\))。  
  
 *colSize*  
 [in]列的大小。  
  
 *dbtype*  
 [in]指示值的数据类型。 请参阅`wType`中的说明[DBBINDING 结构](/previous-versions/windows/desktop/ms716845\(v=vs.85\))。  
  
 *precision*  
 [in]指示如果获取数据时要使用的精度*dbType* DBTYPE_NUMERIC 或 DBTYPE_DECIMAL。 请参阅`bPrecision`中的说明[DBBINDING 结构](/previous-versions/windows/desktop/ms716845\(v=vs.85\))。  
  
 *缩放*  
 [in]指示要使用 dbType 是否 DBTYPE_NUMERIC 或 DBTYPE_DECIMAL 获取数据时的比例。 请参阅`bScale`中的说明[DBBINDING 结构](/previous-versions/windows/desktop/ms716845\(v=vs.85\))。  
  
 *guid*  
 架构行集 GUID。 请参阅[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))中*OLE DB 程序员参考*有关架构行集及其 Guid 的列表。  
  
#### <a name="remarks"></a>备注  
 可以指定列的大小、 数据类型、 精度、 小数位数和架构行集 GUID。  

### <a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH
表示提供程序支持的特定列。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 *序号*  
 [in] 列号。 除非列为书签列，列数必须不为 0。  
  
 *size*  
 [in]列大小 （字节）。  
  
 *成员*  
 [in]中的成员变量`dataClass`存储列数据。  
  
#### <a name="remarks"></a>备注  
 可以指定列大小。  
  
#### <a name="example"></a>示例  
 请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。 

### <a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR
表示提供程序支持的特定列。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 *序号*  
 [in] 列号。 除非列为书签列，列数必须不为 0。  
  
 *成员*  
 [in]将数据存储的数据类中的成员变量。  
  
#### <a name="remarks"></a>备注  
 当列数据被假定为使用此宏[DBTYPE_STR](/previous-versions/windows/desktop/ms711251\(v=vs.85\))。  
  
#### <a name="example"></a>示例  
 请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。   

### <a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
表示提供程序支持的特定列。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 *序号*  
 [in] 列号。 除非列为书签列，列数必须不为 0。  
  
 *dbtype*  
 [in]中的数据类型[DBTYPE](/previous-versions/windows/desktop/ms711251\(v=vs.85\))。  
  
 *size*  
 [in]列大小 （字节）。  
  
 *成员*  
 [in]将数据存储的数据类中的成员变量。  
  
#### <a name="remarks"></a>备注  
 类似于[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)但还允许您指定列的数据类型，以及大小。  

### <a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR
表示提供程序支持的特定列。  
  
#### <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 *序号*  
 [in] 列号。 除非列为书签列，列数必须不为 0。  
  
 *成员*  
 [in]将数据存储的数据类中的成员变量。  
  
#### <a name="remarks"></a>备注  
 当列数据是以 null 结尾的 Unicode 字符串，使用此宏[DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251\(v=vs.85\))。  

### <a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP
表示架构映射的开头。  
  
#### <a name="syntax"></a>语法  
  
```cpp
BEGIN_SCHEMA_MAP(SchemaClass);  
```  
  
#### <a name="parameters"></a>参数  
 *SchemaClass*  
 包含地图的类。 通常，这将在会话类。  
  
#### <a name="remarks"></a>备注  
 请参阅[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) Windows SDK for 有关架构行集的详细信息中。  

### <a name="end_schema_map"></a> END_SCHEMA_MAP
表示架构映射的结尾。  
  
#### <a name="syntax"></a>语法  
  
```cpp
END_SCHEMA_MAP()  
```  
  
#### <a name="see-also"></a>请参阅  
 [IDBSchemaRowsetImpl 类](../../data/oledb/idbschemarowsetimpl-class.md)

### <a name="schema_entry"></a> SCHEMA_ENTRY
将 GUID 与类相关联。  
  
#### <a name="syntax"></a>语法  
  
```cpp
SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>参数  
 *guid*  
 架构行集 GUID。 请参阅[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))中*OLE DB 程序员参考*有关架构行集及其 Guid 的列表。  
  
 *rowsetClass*  
 将创建来表示架构行集类。  
  
#### <a name="remarks"></a>备注  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)然后可以查询的映射的一系列 Guid，或如果其给定一个 GUID，它可以创建行集。 架构行集`IDBSchemaRowsetImpl`创建类似于标准`CRowsetImpl`-派生的类，但它必须提供`Execute`具有以下签名的方法：  
  
```cpp  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
 这`Execute`函数填充行集的数据。 ATL 项目向导创建，如中所述[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))中*OLE DB 程序员参考*，三个的三个必需的 OLE DB 架构的每个初始项目中的架构行集：  
  
-   DBSCHEMA_TABLES  
  
-   DBSCHEMA_COLUMNS  
  
-   DBSCHEMA_PROVIDER_TYPES  
  
 向导还会在架构映射中添加三个相应的条目。 请参阅[创建 OLE DB 模板提供程序](../../data/oledb/creating-an-ole-db-provider.md)有关使用向导创建提供程序的详细信息。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB 提供程序模板参考](../../data/oledb/ole-db-provider-templates-reference.md)    
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   