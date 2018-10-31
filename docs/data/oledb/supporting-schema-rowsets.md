---
title: 支持架构行集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 79c02a36e0c19b0702a81281e626c60e016def32
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083276"
---
# <a name="supporting-schema-rowsets"></a>支持架构行集

架构行集允许使用者获得有关数据存储的信息，而不必知道其基础结构或架构。 例如，数据存储区可能有组织到用户定义层次结构，因此会有没有办法确保通过阅读本文了解除架构表。 （作为另一个示例中，请注意，Visual c + + 向导使用架构行集来生成使用者的访问器。）若要允许使用者执行此操作，提供程序的会话对象公开的方法上[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)接口。 在 Visual c + + 应用程序，您使用[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)类，以实现`IDBSchemaRowset`。

`IDBSchemaRowsetImpl` 支持以下方法：

- [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)检查针对架构行集的限制的有效性。

- [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)实现 COM 对象创建者函数由模板参数指定的对象。

- [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)指定特定架构行集支持哪些限制。

- [Idbschemarowset:: Getrowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)返回架构行集 （继承自接口）。

- [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)返回的架构行集的列表可供源`IDBSchemaRowsetImpl::GetRowset`（继承自接口）。

## <a name="atl-ole-db-provider-wizard-support"></a>ATL OLE DB 提供程序向导支持

在 ATL OLE DB 提供程序向导会话标头文件中创建三个架构类：

- **C**<em>短名称</em>**SessionTRSchemaRowset**

- **C**<em>短名称</em>**SessionColSchemaRowset**

- **C**<em>短名称</em>**SessionPTSchemaRowset**

这些类对架构信息; 的使用者请求做出响应请注意，OLE DB 规范要求支持这些三个架构行集：

- **C**<em>短名称</em>**SessionTRSchemaRowset**处理的表信息的请求 (`DBSCHEMA_TABLES`架构行集)。

- **C**<em>短名称</em>**SessionColSchemaRowset**处理的列信息的请求 (`DBSCHEMA_COLUMNS`架构行集)。 向导提供了这些类，它返回一个 DOS 提供程序的架构信息的示例实现。

- **C**<em>短名称</em>**SessionPTSchemaRowset**处理有关提供程序类型的架构信息的请求 (`DBSCHEMA_PROVIDER_TYPES`架构行集)。 向导提供的默认实现返回`S_OK`。

可以自定义这些类来处理适合您的提供程序的架构信息：

- 在中**C**<em>短名称</em>**SessionTRSchemaRowset**，您必须填写的目录、 表和描述字段 (`trData.m_szType`， `trData.m_szTable`，和`trData.m_szDesc`). 该向导生成的示例使用只有一个行 （表）。 其他提供程序可能会返回多个表。

- 在中**C**<em>短名称</em>**SessionColSchemaRowset**，为表的名称传递`DBID`。

## <a name="setting-restrictions"></a>设置限制

在架构行集支持的一个重要概念设置限制，您执行此操作使用`SetRestrictions`。 限制允许使用者只提取匹配行（例如，查找表“MyTable”中的所有列）。 限制是可选的，如果不支持任何限制（默认设置），则始终返回所有数据。 有关支持限制的提供程序的示例，请参阅[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)示例。

## <a name="setting-up-the-schema-map"></a>设置架构映射

设置在 UpdatePV Session.h 中这样一个架构映射：

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

若要支持`IDBSchemaRowset`，必须支持`DBSCHEMA_TABLES`， `DBSCHEMA_COLUMNS`，和`DBSCHEMA_PROVIDER_TYPES`。 您可以自行添加附加的架构行集。

声明具有的架构行集类`Execute`等方法`CUpdateSessionTRSchemaRowset`UpdatePV 中：

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

请注意，`CUpdateSession`继承`IDBSchemaRowsetImpl`，因此它处理方法的所有限制。 使用`CSchemaRowsetImpl`，声明 （在上面的架构映射中列出） 的三个子类： `CUpdateSessionTRSchemaRowset`， `CUpdateSessionColSchemaRowset`，和`CUpdateSessionPTSchemaRowset`。 每个这些子类别有`Execute`处理各自的限制 （搜索条件） 的一组方法。 每个`Execute`方法比较的值`cRestrictions`和`rgRestrictions`参数。 请参阅中的这些参数的说明[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)。

有关哪些限制对应于特定架构行集的详细信息，请查阅上表的架构行集 Guid 中[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)中*OLE DB 程序员参考*中Windows SDK。

例如，如果您支持**TABLE_NAME**限制`DBSCHEMA_TABLES`，您将执行以下操作：

首先，查找`DBSCHEMA_TABLES`并查看它支持四个限制 （按顺序）。

|架构行集限制|限制值|
|-------------------------------|-----------------------|
|**TABLE_CATALOG**|0x1 (二进制 1)|
|**TABLE_SCHEMA**|0x2 (二进制为 10)|
|**TABLE_NAME**|0x4 (二进制 100)|
|**TABLE_TYPE**|0x8 （二进制 1000 个）|

接下来，请注意，没有为每个限制的一位。 因为你想要支持**TABLE_NAME** ，将返回在 0x4`rgRestrictions`元素。 如果您支持**TABLE_CATALOG**并**TABLE_NAME**，将返回 0x5 (二进制 101)。

默认情况下，实现返回的 0 （不支持任何限制） 的任何请求。 UpdatePV 是支持限制的提供程序的示例。

### <a name="example"></a>示例

此代码摘自[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)示例。 UpdatePv 支持三个所需的架构行集： `DBSCHEMA_TABLES`， `DBSCHEMA_COLUMNS`，和`DBSCHEMA_PROVIDER_TYPES`。 为了举例说明如何在您的提供程序中实现架构支持，本主题逐步讲解如何完成实现`DBSCHEMA_TABLE`行集。

> [!NOTE]
> 示例代码可能不同于此处; 列出示例代码应视为较新版本。

添加架构支持的第一步是确定想要支持哪些限制。 若要确定哪些限制可用于架构行集，请查看的定义的 OLE DB 规范`IDBSchemaRowset`。 以下主定义，您将看到一个包含架构行集名称、 限制数目和限制列的表。 选择你想要支持并记下数的限制和限制列的架构行集。 例如，`DBSCHEMA_TABLES`支持四个限制 (**TABLE_CATALOG**， **TABLE_SCHEMA**， **TABLE_NAME**，并且**TABLE_TYPE**):

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

位表示每个限制列。 如果你想要支持限制 （即，可以通过它查询），将该位设置为 1。 如果您不想要支持限制，请将此位设置为零。 从上面的代码行，支持 UpdatePV **TABLE_NAME**并**TABLE_TYPE**限制`DBSCHEMA_TABLES`行集。 这些是第三个 （位掩码 100） 和第四个 （位掩码 1000年） 限制。 因此，UpdatePv 的位掩码是 1100年 （或 0x0C）：

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

以下`Execute`函数是类似的正则行集。 有三个参数： *pcRowsAffected*， *cRestrictions*，并*rgRestrictions*。 *PcRowsAffected*变量是输出参数，提供程序可以在架构行集中返回的行数。 *CRestrictions*参数是包含由使用者传递给提供程序的限制数目的输入的参数。 *RgRestrictions*参数是一个数组`VARIANT`包含限制值的值。

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

`cRestrictions`变量根据总数的限制的架构行集，无论该提供程序是否支持它们。 由于 UpdatePv 支持两个限制 （第三和第四个），此代码仅查找`cRestrictions`大于或等于三个值。

值**TABLE_NAME**限制存储在`rgRestrictions[2]`（同样，从零开始的数组中的第三个限制为 2）。 您需要检查的限制不是 VT_EMPTY 使其真正支持它。 请注意 VT_NULL 不等于 VT_EMPTY。 VT_NULL 指定一个有效限制值。

表名的 UpdatePv 定义是到文本文件的完全限定的路径名称。 提取的限制值，然后尝试打开该文件以确保该文件实际上确实存在。 如果该文件不存在，则返回 S_OK。 这看起来可能有点背道而驰，但代码实际上告诉使用者是由指定的名称没有任何受支持的表。 返回 S_OK 表示执行正确的代码。

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

支持的第四个限制 (**TABLE_TYPE**) 类似于第三个限制。 检查的值不是 VT_EMPTY。 此限制仅返回表的类型，**表**。 若要确定为有效值`DBSCHEMA_TABLES`，参阅的附录 B *OLE DB 程序员参考*中**表**行集部分。

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

这是实际创建行集的行项。 在变量`trData`对应于`CTABLESRow`，OLE DB 提供程序模板中定义的结构。 `CTABLESRow` 对应于**表**OLE DB 规范的附录 B 中的行集定义。 只能有一个要添加，因为一次仅支持一个表的行。

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

UpdatePV 设置只有三个列： **TABLE_NAME**， **TABLE_TYPE**，并**说明**。 你应记下为其返回信息的列，因为在实现时需要此信息`GetDBStatus`:

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

`GetDBStatus`函数是对架构行集的正确操作非常重要。 因为不会返回每个列中的数据**表**行集，您需要指定哪些列返回的数据和未执行此操作。

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

因为你`Execute`函数返回的数据**TABLE_NAME**， **TABLE_TYPE**，并且**说明**字段从**表**行集，您可以在 OLE DB 规范的附录 B 中查找并确定 （通过从顶部倒） 它们是 3、 4 和 6 的序号。 对于每个这些列，返回 DBSTATUS_S_OK。 对于所有其他列，返回 DBSTATUS_S_ISNULL。 务必返回此状态，因为使用者可能无法理解返回的值为 NULL 或其他内容。 同样，请注意，NULL 不等效于空。

有关 OLE DB 架构行集接口的详细信息，请参阅[IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md)接口中的 OLE DB 程序员参考。

有关如何使用使用者信息`IDBSchemaRowset`方法，请参阅[用架构行集获取元数据](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)。

有关支持架构行集的提供程序的示例，请参阅 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 示例。

## <a name="see-also"></a>请参阅

[高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)
