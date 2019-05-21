---
title: 支持架构行集
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: 09af59d97ab87c66a0a7096e72cc7b92bc3a5dbf
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525273"
---
# <a name="supporting-schema-rowsets"></a>支持架构行集

使用架构行集，使用者可以在不知道数据存储的基础结构或架构的情况下，获取数据存储的相关信息。 例如，数据存储可能有采用用户定义层次结构的表，因此除了读取它之外，没有任何方法可确保了解架构。 （另一个例子是，Visual C++ 向导使用架构行集来为使用者生成取值函数。）为了允许使用者这样做，提供程序的会话对象公开 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 接口中的方法。 在 Visual C++ 应用程序中，使用 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 类来实现 `IDBSchemaRowset`。

`IDBSchemaRowsetImpl` 支持以下方法：

- [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)：针对架构行集检查限制的有效性。

- [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)：为模板参数指定的对象实现 COM 对象创建程序函数。

- [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)：指定对特定架构行集支持哪些限制。

- [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)：返回架构行集（继承自接口）。

- [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)：返回 `IDBSchemaRowsetImpl::GetRowset` 可访问的架构行集的列表（继承自接口）。

## <a name="atl-ole-db-provider-wizard-support"></a>ATL OLE DB 提供程序向导支持

::: moniker range="vs-2019"

ATL OLE DB 提供程序向导不适用于 Visual Studio 2019 及更高版本。

::: moniker-end

::: moniker range="vs-2017"

ATL OLE DB 提供程序向导在会话头文件中创建三个架构类：

- CShortNameSessionTRSchemaRowset

- CShortNameSessionColSchemaRowset

- CShortNameSessionPTSchemaRowset

这些类响应使用者对架构信息的请求；请注意，OLE DB 规范要求，必须支持这三个架构行集：

- CShortNameSessionTRSchemaRowset 处理对表信息的请求（DBSCHEMA_TABLES 架构行集）。

- CShortNameSessionColSchemaRowset 处理对列信息的请求（DBSCHEMA_COLUMNS 架构行集）。 向导提供了这些类的示例实现，它们返回 DOS 提供程序的架构信息。

- CShortNameSessionPTSchemaRowset 处理对提供程序类型的相关架构信息的请求（DBSCHEMA_PROVIDER_TYPES 架构行集）。 向导提供的默认实现返回 S_OK。

可以将这些类自定义为处理适合提供程序的架构信息：

- 在 CShortNameSessionTRSchemaRowset 中，必须填写目录、表和说明字段（`trData.m_szType`、`trData.m_szTable` 和 `trData.m_szDesc`）。 向导生成的示例仅使用一行（一个表）。 其他提供程序可能会返回多个表。

- 在 CShortNameSessionColSchemaRowset 中，将表名称作为 `DBID` 进行传递。

::: moniker-end

## <a name="setting-restrictions"></a>设置限制

与架构行集支持相关的一个重要概念是，使用 `SetRestrictions` 设置限制。 限制允许使用者只提取匹配行（例如，查找表“MyTable”中的所有列）。 限制是可选的，如果不支持任何限制（默认设置），则始终返回所有数据。 有关支持限制的提供程序示例，请参阅 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 示例。

## <a name="setting-up-the-schema-map"></a>设置架构映射

设置架构映射（如 UpdatePV 中 Session.h 内的架构映射）：

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

必须支持 DBSCHEMA_TABLES、DBSCHEMA_COLUMNS 和 DBSCHEMA_PROVIDER_TYPES，才能支持 `IDBSchemaRowset`。 可以自行添加其他架构行集。

使用 `Execute` 方法声明架构行集类（如 `UpdatePV` 中的 `CUpdateSessionTRSchemaRowset`）：

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

由于 `CUpdateSession` 继承自 `IDBSchemaRowsetImpl`，因此它包含所有限制处理方法。 使用 `CSchemaRowsetImpl` 时，声明（上面架构映射中列出的）三个子类：`CUpdateSessionTRSchemaRowset`、`CUpdateSessionColSchemaRowset` 和 `CUpdateSessionPTSchemaRowset`。 其中每个子类都有 `Execute` 方法，用于处理各自的一组限制（搜索条件）。 每个 `Execute` 方法都比较 cRestrictions 和 rgRestrictions 参数的值。 有关这些参数的说明，请参阅 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)。

若要详细了解与特定架构行集对应的限制，请参阅 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 中的架构行集 GUID 表（这篇文章收录在 Windows SDK 的“OLE DB 程序员参考”中）。

例如，如果对 DBSCHEMA_TABLES 支持了 TABLE_NAME 限制，便会执行以下操作：

首先，查找 DBSCHEMA_TABLES，并确定它是否支持以下四个限制（按顺序）。

|架构行集限制|限制值|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1（二进制 1）|
|TABLE_SCHEMA|0x2（二进制 10）|
|TABLE_NAME|0x4（二进制 100）|
|TABLE_TYPE|0x8（二进制 1000）|

接下来，每个限制有一个对应位。 由于只想要支持 TABLE_NAME，因此会在 `rgRestrictions` 元素中返回 0x4。 如果支持了 TABLE_CATALOG 和 TABLE_NAME，便会返回 0x5（二进制 101）。

默认情况下，实现对任何请求都返回 0（不支持任何限制）。 例如，UpdatePV 是支持限制的提供程序。

### <a name="example"></a>示例

此代码摘自 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 示例。 `UpdatePv` 支持三个必需架构行集：DBSCHEMA_TABLES、DBSCHEMA_COLUMNS 和 DBSCHEMA_PROVIDER_TYPES。 本主题通过逐步介绍如何实现 DBSCHEMA_TABLE 行集，举例说明了如何在提供程序中实现架构支持。

> [!NOTE]
> 示例代码可能与本文列出的代码不同；应将示例代码视为最新版本。

添加架构支持的第一步是，确定要支持哪些限制。 若要确定哪些限制可用于架构行集，请查看 OLE DB 规范中的 `IDBSchemaRowset` 定义。 主定义后面是包含架构行集名称、限制数和限制列的表。 选择要支持的架构行集，并记下限制数和限制列。 例如，DBSCHEMA_TABLES 支持四个限制（TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME 和 TABLE_TYPE）：

```cpp
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,
   ULONG* rgRestrictions)
{
    for (ULONG l=0; l<cRestrictions; l++)
    {
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
            rgRestrictions[l] = 0x0C;
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))
                 rgRestrictions[l] = 0x04;
             else if (InlineIsEqualGUID(rguidSchema[l],
                                        DBSCHEMA_PROVIDER_TYPES))
                      rgRestrictions[l] = 0x00;
   }
}
```

位表示每个限制列。 若要支持限制（即可以通过它进行查询），请将相应位设置为 1。 如果不想支持限制，请将相应位设置为 0。 在上面的代码行中，`UpdatePV` 对 DBSCHEMA_TABLES 行集支持 TABLE_NAME 和 TABLE_TYPE 限制。 这两个分别是第三个（位掩码 100）和第四个（位掩码 1000）限制。 因此，`UpdatePv` 的位掩码为 1100（或 0x0C）：

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

以下 `Execute` 函数类似于常规行集中的函数。 有三个参数：pcRowsAffected、cRestrictions 和 rgRestrictions。 pcRowsAffected 变量是提供程序可用来返回架构行集中行数的输出参数。 cRestrictions 参数是包含使用者传递给提供程序的限制数的输入参数。 rgRestrictions 参数是包含限制值的 VARIANT 值数组。

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

cRestrictions 变量基于架构行集的限制总数，无论提供程序是否支持它们。 因为 UpdatePv 支持两个限制（第三个和第四个），所以此代码仅查找大于或等于 3 的 cRestrictions 值。

TABLE_NAME 限制值存储在 rgRestrictions [2] 中（同样，从零开始的数组中的第三个限制为 2）。 检查限制是否不是 VT_EMPTY，以真正支持它。 请注意，VT_NULL 不等于 VT_EMPTY。 VT_NULL 指定有效限制值。

表名称的 `UpdatePv` 定义是文本文件的完全限定路径名称。 提取限制值，然后尝试打开文件，以确保文件确实存在。 如果文件不存在，返回的是 S_OK。 这看起来可能有点倒退，但代码实际上是在指示使用者，根据指定的名称找不到任何受支持的表。 返回 S_OK 表示代码已正确执行。

```cpp
USES_CONVERSION;
enum {
            sizeOfszFile = 255
};
CTABLESRow  trData;
FILE        *pFile = NULL;
TCHAR       szFile[ sizeOfszFile ];
errcode     err = 0;

// Handle any restrictions sent to us. This only handles
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04
// for a total of (0x0C)
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)
{
    CComBSTR bstrName = rgRestrictions[2].bstrVal;
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))
    {
        // Check to see if the file exists
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));
        if (szFile[0] == _T('\0') ||
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))
        {
            return S_OK;// Their restriction was invalid return no data
        }
        else
        {
            fclose(pFile);
        }
    }
}
```

支持的第四个限制 (TABLE_TYPE) 类似于第三个限制。 检查值是否不是 VT_EMPTY。 此限制仅返回表类型 TABLE。 若要确定 DBSCHEMA_TABLES 的有效值，请查看“OLE DB 程序员参考”的“附录 B”中的 TABLES 行集部分。

```cpp
// TABLE_TYPE restriction:
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)
{
    CComBSTR bstrType = rgRestrictions[3].bstrVal;
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))
    {
        // This is kind of a blind restriction.
        // This only actually supports
        // TABLES so if you get anything else,
        // just return an empty rowset.
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)
            return S_OK;
    }
}
```

这是为行集实际创建行条目的位置。 变量 `trData` 对应于 `CTABLESRow`，这是 OLE DB 提供程序模板中定义的结构。 `CTABLESRow` 对应于 OLE DB 规范的“附录 B”中的 TABLES 行集定义。 只需要添加一行，因为一次只能支持一个表。

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` 仅设置三个列：TABLE_NAME、TABLE_TYPE 和 DESCRIPTION。 记下返回其信息的列，因为在实现 `GetDBStatus` 时需要用到此类信息：

```cpp
    _ATLTRY
    {
        m_rgRowData.Add(trData);
    }
    _ATLCATCHALL()
    {
        return E_OUTOFMEMORY;
    }
    //if (!m_rgRowData.Add(trData))
    //    return E_OUTOFMEMORY;
    *pcRowsAffected = 1;
    return S_OK;
}
```

`GetDBStatus` 函数对架构行集执行正确操作非常重要。 因为不返回 TABLES 行集中每个列的数据，所以需要指定返回和不返回哪些列的数据。

```cpp
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pColInfo != NULL);

    switch(pColInfo->iOrdinal)
    {
    case 3:     // TABLE_NAME
    case 4:     // TABLE_TYPE
    case 6:     // DESCRIPTION
        return DBSTATUS_S_OK;
        break;
    default:
        return DBSTATUS_S_ISNULL;
    break;
    }
}
```

因为 `Execute` 函数从 TABLES 行集中返回 TABLE_NAME、TABLE_TYPE 和 DESCRIPTION 字段的数据，所以你可以查看 OLE DB 规范的“附录 B”，并确定（通过自上而下计数）它们是序号 3、4 和 6。 对于其中每一列，返回的是 DBSTATUS_S_OK。 对于其他所有列，返回的是 DBSTATUS_S_ISNULL。 请务必返回此状态，因为使用者可能不知道返回值是 NULL 或其他值。 同样，请注意，NULL 不相当于空。

若要详细了解 OLE DB 架构行集接口，请参阅“OLE DB 程序员参考”中的 [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) 接口。

若要了解使用者如何使用 `IDBSchemaRowset` 方法，请参阅[使用架构行集获取元数据](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)。

有关支持架构行集的提供程序示例，请参阅 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 示例。

## <a name="see-also"></a>请参阅

[高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)
