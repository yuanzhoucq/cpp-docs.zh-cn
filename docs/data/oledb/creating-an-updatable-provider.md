---
title: 创建可更新的提供程序
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 2811cd56bdc87282b9d4395a9a79ba9b333dadee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211388"
---
# <a name="creating-an-updatable-provider"></a>创建可更新的提供程序

视觉C++对象支持可更新的提供程序或可更新数据存储的提供程序。 本主题讨论如何使用 OLE DB 模板创建可更新的提供程序。

本主题假定你开始使用的是可使用的提供程序。 创建可更新的提供程序有两个步骤。 您必须首先确定提供程序将如何对数据存储进行更改;具体而言，是立即执行更改还是推迟更改，直到发出 update 命令。 "[使提供程序可更新](#vchowmakingprovidersupdatable)" 一节描述了在提供程序代码中需要执行的更改和设置。

接下来，必须确保提供程序包含支持使用者可能请求的任何内容的所有功能。 如果使用者想要更新数据存储区，则提供程序必须包含将数据保存到数据存储的代码。 例如，您可以使用 C 运行时库或 MFC 对您的数据源执行此类操作。 "[写入数据源](#vchowwritingtothedatasource)" 一节介绍如何向数据源写入数据，如何处理 NULL 值和默认值，以及如何设置列标志。

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)是可更新的提供程序的一个示例。 UpdatePV 与 MyProv 相同，但具有可更新的支持。

##  <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>使提供程序可更新

使提供程序可更新的关键是了解你希望提供程序在数据存储中执行哪些操作，以及你希望提供程序如何执行这些操作。 具体而言，主要问题是是否立即或延迟（批处理）对数据存储进行更新，直至发出 update 命令。

首先，必须确定是否从行集类中的 `IRowsetChangeImpl` 或 `IRowsetUpdateImpl` 继承。 这三种方法的功能会受到影响，具体取决于所选的实现方式： `SetData`、`InsertRows`和 `DeleteRows`。

- 如果从[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)继承，则调用这三个方法会立即更改数据存储区。

- 如果从[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)继承，则方法将更改保存到数据存储区，直到你调用 `Update`、`GetOriginalData`或 `Undo`。 如果更新涉及多个更改，则在批处理模式下执行（请注意，批处理更改可能会增加相当多的内存开销）。

请注意，`IRowsetUpdateImpl` 派生自 `IRowsetChangeImpl`。 因此，`IRowsetUpdateImpl` 提供了更改功能和批处理功能。

### <a name="to-support-updatability-in-your-provider"></a>支持提供程序中的可更新性

1. 在行集类中，继承自 `IRowsetChangeImpl` 或 `IRowsetUpdateImpl`。 这些类提供了用于更改数据存储的相应接口：

   **添加 IRowsetChange**

   使用以下格式将 `IRowsetChangeImpl` 添加到继承链：

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   同时，将 `COM_INTERFACE_ENTRY(IRowsetChange)` 添加到行集类中的 `BEGIN_COM_MAP` 部分。

   **添加 IRowsetUpdate**

   使用以下格式将 `IRowsetUpdate` 添加到继承链：

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > 你应从继承链中删除 `IRowsetChangeImpl` 行。 前面提到的指令的这一例外必须包含用于 `IRowsetChangeImpl`的代码。

1. 将以下内容添加到 COM 映射（`BEGIN_COM_MAP ... END_COM_MAP`）：

   |  如果实现   |           添加到 COM 映射             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | 如果实现 | 添加到属性集映射 |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在命令中，将以下内容添加到属性集映射（`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`）：

   |  如果实现   |                                             添加到属性集映射                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在属性集映射中，还应包括下面显示的所有设置：

    ```cpp
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)

    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)
    ```

   通过在为 atldb.h 中查找属性 Id 和值（如果为 atldb.h 与联机文档不同，为 atldb.h 将取代文档），可以查找这些宏调用中使用的值。

   > [!NOTE]
   > OLE DB 模板需要许多 `VARIANT_FALSE` 和 `VARIANT_TRUE` 设置;OLE DB 规范指示它们可以是可读/写的，但 OLE DB 模板只能支持一个值。

   **如果实现 IRowsetChangeImpl**

   如果实现 `IRowsetChangeImpl`，则必须在提供程序上设置以下属性。 这些属性主要用于通过 `ICommandProperties::SetProperties`来请求接口。

   - `DBPROP_IRowsetChange`：设置此操作会自动设置 `DBPROP_IRowsetChange`。

   - `DBPROP_UPDATABILITY`：指定 `IRowsetChange`上支持的方法的位掩码： `SetData`、`DeleteRows`或 `InsertRow`。

   - `DBPROP_CHANGEINSERTEDROWS`：使用者可以为新插入的行调用 `IRowsetChange::DeleteRows` 或 `SetData`。

   - `DBPROP_IMMOBILEROWS`：行集不会对插入行或更新的行重新排序。

   **如果实现 IRowsetUpdateImpl**

   如果实现 `IRowsetUpdateImpl`，则除了设置前面列出的 `IRowsetChangeImpl` 的所有属性外，还必须在提供程序上设置以下属性：

   - `DBPROP_IRowsetUpdate` 列中的一个值匹配。

   - `DBPROP_OWNINSERT`：必须 READ_ONLY 并 VARIANT_TRUE。

   - `DBPROP_OWNUPDATEDELETE`：必须 READ_ONLY 并 VARIANT_TRUE。

   - `DBPROP_OTHERINSERT`：必须 READ_ONLY 并 VARIANT_TRUE。

   - `DBPROP_OTHERUPDATEDELETE`：必须 READ_ONLY 并 VARIANT_TRUE。

   - `DBPROP_REMOVEDELETED`：必须 READ_ONLY 并 VARIANT_TRUE。

   - `DBPROP_MAXPENDINGROWS` 列中的一个值匹配。

   > [!NOTE]
   > 如果支持通知，还可以使用其他一些属性;请参阅此列表 `IRowsetNotifyCP` 的部分。

##  <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>写入数据源

若要从数据源读取数据，请调用 `Execute` 函数。 若要写入数据源，请调用 `FlushData` 函数。 （一般意义上，flush 是指将对表或索引所做的修改保存到磁盘。）

```cpp
FlushData(HROW, HACCESSOR);
```

行句柄（HROW）和取值函数句柄（HACCESSOR）参数允许指定要写入的区域。 通常，一次写入一个数据字段。

`FlushData` 方法以最初存储数据的格式写入数据。 如果不重写此函数，则提供程序将正常工作，但不会将更改刷新到数据存储区。

### <a name="when-to-flush"></a>何时刷新

每当需要将数据写入数据存储时，提供程序模板就会调用 FlushData;这通常（但不总是）会由于调用以下函数而发生：

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` （如果有新的数据要插入到行中）

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>工作原理

使用者发出要求刷新（例如更新）的调用，并将此调用传递到提供程序，这将始终执行以下操作：

- 只要有一个状态值，就 `SetDBStatus` 调用。

- 检查列标志。

- 调用 `IsUpdateAllowed`。

这三个步骤有助于提供安全性。 然后，提供程序调用 `FlushData`。

### <a name="how-to-implement-flushdata"></a>如何实现 FlushData

若要实现 `FlushData`，需要考虑几个问题：

确保数据存储可以处理更改。

处理 NULL 值。

### <a name="handling-default-values"></a>处理默认值。

若要实现您自己的 `FlushData` 方法，您需要：

- 中转到行集类。

- 在行集类中放置的声明：

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- 提供 `FlushData`的实现。

`FlushData` 的良好实现仅存储实际更新的行和列。 您可以使用 HROW 和 HACCESSOR 参数来确定当前要存储以进行优化的行和列。

通常，最大的挑战是使用自己的本机数据存储。 如果可能，请尝试执行以下操作：

- 使写入数据存储区的方法尽可能简单。

- 处理 NULL 值（可选，但建议这样做）。

- 处理默认值（可选，但建议这样做）。

最好的做法是将数据存储中的实际指定值指定为 NULL 值和默认值。 最好是将此数据外推。 如果不允许，则建议您不要允许空值和默认值。

下面的示例演示如何在 `UpdatePV` 示例的 `RUpdateRowset` 类中实现 `FlushData` （请参阅示例代码中的 Rowset）：

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)
...
HRESULT FlushData(HROW, HACCESSOR)
{
    ATLTRACE2(atlTraceDBProvider, 0, "RUpdateRowset::FlushData\n");

    USES_CONVERSION;
    enum {
        sizeOfString = 256,
        sizeOfFileName = MAX_PATH
    };
    FILE*    pFile = NULL;
    TCHAR    szString[sizeOfString];
    TCHAR    szFile[sizeOfFileName];
    errcode  err = 0;

    ObjectLock lock(this);

    // From a filename, passed in as a command text,
    // scan the file placing data in the data array.
    if (m_strCommandText == (BSTR)NULL)
    {
        ATLTRACE( "RRowsetUpdate::FlushData -- "
                  "No filename specified\n");
        return E_FAIL;
    }

    // Open the file
    _tcscpy_s(szFile, sizeOfFileName, OLE2T(m_strCommandText));
    if ((szFile[0] == _T('\0')) ||
        ((err = _tfopen_s(&pFile, &szFile[0], _T("w"))) != 0))
    {
        ATLTRACE("RUpdateRowset::FlushData -- Could not open file\n");
        return DB_E_NOTABLE;
    }

    // Iterate through the row data and store it.
    for (long l=0; l<m_rgRowData.GetSize(); l++)
    {
        CAgentMan am = m_rgRowData[l];

        _putw((int)am.dwFixed, pFile);

        if (_tcscmp(&am.szCommand[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szCommand2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);
    }

    if (fflush(pFile) == EOF || fclose(pFile) == EOF)
    {
        ATLTRACE("RRowsetUpdate::FlushData -- "
                 "Couldn't flush or close file\n");
    }

    return S_OK;
}
```

### <a name="handling-changes"></a>处理更改

为了使提供程序能够处理更改，您首先需要确保您的数据存储区（例如文本文件或视频文件）的功能使您能够对其进行更改。 如果不是，则应将该代码与提供程序项目分开创建。

### <a name="handling-null-data"></a>处理 NULL 数据

最终用户可能会发送 NULL 数据。 向数据源中的字段写入空值时，可能会出现潜在问题。 假设有一个按顺序排列的应用程序，接受城市和邮政编码的值;它可以接受或同时接受两个值，但不能同时接受这两个值，因为在这种情况下不可能进行传递。 因此，必须在对应用程序有意义的字段中限制某些 NULL 值组合。

作为提供者开发人员，您必须考虑如何存储该数据，如何从数据存储中读取数据，以及如何将该数据指定给用户。 具体来说，您必须考虑如何更改数据源中行集数据的数据状态（例如，DataStatus = NULL）。 当使用者访问包含 NULL 值的字段时，可以决定返回什么值。

查看 UpdatePV 示例中的代码;它说明了提供程序如何处理 NULL 数据。 在 UpdatePV 中，提供程序通过将字符串 "NULL" 写入数据存储区来存储空数据。 在从数据存储区中读取 NULL 数据时，它会看到该字符串，然后清空缓冲区，从而创建一个 NULL 字符串。 它还覆盖了 `IRowsetImpl::GetDBStatus`，如果该数据值为空，则它会在其中返回 DBSTATUS_S_ISNULL。

### <a name="marking-nullable-columns"></a>标记可为空的列

如果还实现架构行集（请参阅 `IDBSchemaRowsetImpl`），则实现应在 DBSCHEMA_COLUMNS 行集中指定（通常由 CxxxSchemaColSchemaRowset 在提供程序中标记），该列可为 null。

还需要指定所有可为 null 的列都包含您的 `GetColumnInfo`版本中的 DBCOLUMNFLAGS_ISNULLABLE 值。

在 OLE DB 模板实现中，如果无法将列标记为可以为 null，则提供程序会假定它们必须包含一个值，并且不允许使用者向其发送 null 值。

下面的示例演示如何在 CUpdateCommand 中实现 `CommonGetColInfo` 函数（请参阅 UpProvRS）。 请注意，这些列对可以为 null 的列提供此 DBCOLUMNFLAGS_ISNULLABLE 的方式。

```cpp
/////////////////////////////////////////////////////////////////////////////
// CUpdateCommand (in UpProvRS.cpp)

ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols, bool bBookmark)
{
    static ATLCOLUMNINFO _rgColumns[6];
    ULONG ulCols = 0;

    if (bBookmark)
    {
        ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                            sizeof(DWORD), DBTYPE_BYTES,
                            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                            DBCOLUMNFLAGS_ISBOOKMARK)
        ulCols++;
    }

    // Next set the other columns up.
    // Add a fixed length entry for OLE DB conformance testing purposes
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Fixed"), 1, 4, DBTYPE_UI4,
                        10, 255, GUID_NULL, CAgentMan, dwFixed,
                        DBCOLUMNFLAGS_WRITE |
                        DBCOLUMNFLAGS_ISFIXEDLENGTH)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command"), 2, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text"), 3, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command2"), 4, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text2"), 5, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    if (pcCols != NULL)
    {
        *pcCols = ulCols;
    }

    return _rgColumns;
}
```

### <a name="default-values"></a>默认值

与 NULL 数据一样，你有责任处理更改默认值。

`FlushData` 和 `Execute` 的默认值是返回 S_OK。 因此，如果不重写此函数，则更改看起来是成功的（将返回 S_OK），但不会将这些更改传输到数据存储区。

在 `UpdatePV` 示例（位于 Rowset）中，`SetDBStatus` 方法处理默认值，如下所示：

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* pdbStatus, CSimpleRow* pRow,
                            ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pRow != NULL && pColInfo != NULL && pdbStatus != NULL);

    void* pData = NULL;
    char* pDefaultData = NULL;
    DWORD* pFixedData = NULL;

    switch (*pdbStatus)
    {
        case DBSTATUS_S_DEFAULT:
            pData = (void*)&m_rgRowData[pRow->m_iRowset];
            if (pColInfo->wType == DBTYPE_STR)
            {
                pDefaultData = (char*)pData + pColInfo->cbOffset;
                strcpy_s(pDefaultData, "Default");
            }
            else
            {
                pFixedData = (DWORD*)((BYTE*)pData +
                                          pColInfo->cbOffset);
                *pFixedData = 0;
                return S_OK;
            }
            break;
        case DBSTATUS_S_ISNULL:
        default:
            break;
    }
    return S_OK;
}
```

### <a name="column-flags"></a>列标志

如果支持列的默认值，则需要使用 \<提供程序类\>t 类中的元数据对其进行设置。 设置 `m_bColumnHasDefault = VARIANT_TRUE`。

您还有责任设置列标志，这些列标志是使用 DBCOLUMNFLAGS 枚举类型指定的。 列标志说明列特性。

例如，在 `UpdatePV` （位于 `CUpdateSessionColSchemaRowset` 类中）中，第一列按以下方式设置：

```cpp
// Set up column 1
trData[0].m_ulOrdinalPosition = 1;
trData[0].m_bIsNullable = VARIANT_FALSE;
trData[0].m_bColumnHasDefault = VARIANT_TRUE;
trData[0].m_nDataType = DBTYPE_UI4;
trData[0].m_nNumericPrecision = 10;
trData[0].m_ulColumnFlags = DBCOLUMNFLAGS_WRITE |
                            DBCOLUMNFLAGS_ISFIXEDLENGTH;
lstrcpyW(trData[0].m_szColumnDefault, OLESTR("0"));
m_rgRowData.Add(trData[0]);
```

此代码指定列是否支持默认值0、可写且列中的所有数据都具有相同的长度。 如果希望列中的数据具有可变长度，则不会设置此标志。

## <a name="see-also"></a>另请参阅

[创建 OLE DB 提供程序](creating-an-ole-db-provider.md)
