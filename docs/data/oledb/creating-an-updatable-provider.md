---
title: 创建可更新的提供程序
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 720ceba397d17642402de4d44cbb4481852fa153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365562"
---
# <a name="creating-an-updatable-provider"></a>创建可更新的提供程序

可视C++支持可更新（写入）数据存储的可更新提供程序或提供程序。 本主题讨论如何使用 OLE DB 模板创建可更新的提供程序。

本主题假定您从可行的提供程序开始。 创建可增加提供程序有两个步骤。 您必须首先决定提供程序将如何更改数据存储;但是，您必须首先决定提供程序将如何对数据存储进行更改。具体来说，更改是立即执行还是延迟，直到发布更新命令。 "[使提供程序可上可访问](#vchowmakingprovidersupdatable)"一节描述了在提供程序代码中需要执行的更改和设置。

接下来，必须确保提供程序包含所有功能，以支持使用者可能请求的任何功能。 如果使用者想要更新数据存储，则提供程序必须包含将数据保存到数据存储的代码。 例如，您可以使用 C 运行时库或 MFC 对数据源执行此类操作。 "[写入数据源](#vchowwritingtothedatasource)"部分介绍了如何写入数据源、处理 NULL 和默认值以及设置列标志。

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)是可更新提供程序的示例。 更新PV与 MyProv 相同，但具有可更新的支持。

## <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>使提供商可上可

使提供程序正常运行的关键是了解您希望提供程序在数据存储上执行哪些操作，以及您希望提供程序如何执行这些操作。 具体而言，主要问题是，在发布更新命令之前，是否立即完成对数据存储的更新或延迟（批处理）。

您必须首先决定是否继承行`IRowsetChangeImpl`集类或`IRowsetUpdateImpl`行集类。 根据您选择实现的这些功能，三种方法的功能将受到影响： `SetData`、`InsertRows`和`DeleteRows`。

- 如果从[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)继承，调用这三种方法将立即更改数据存储。

- 如果从[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)继承，则这些方法将更改推迟到调用`Update`或`GetOriginalData`。 `Undo` 如果更新涉及多个更改，它们以批处理模式执行（请注意，批处理更改可能会增加相当大的内存开销）。

从`IRowsetUpdateImpl`派生的请注意`IRowsetChangeImpl`。 因此，`IRowsetUpdateImpl`为您提供更改功能和批处理功能。

### <a name="to-support-updatability-in-your-provider"></a>支持提供商的升数据度

1. 在行集类中，从`IRowsetChangeImpl`继承`IRowsetUpdateImpl`或 。 这些类为更改数据存储提供了适当的接口：

   **添加 IRowset 更改**

   使用此`IRowsetChangeImpl`窗体添加到继承链：

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   还要添加到`COM_INTERFACE_ENTRY(IRowsetChange)`排集`BEGIN_COM_MAP`类中的节。

   **添加 IRowset 更新**

   使用此`IRowsetUpdate`窗体添加到继承链：

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > 应从继承链`IRowsetChangeImpl`中删除该行。 前面提到的指令的例外情况必须包括 的代码`IRowsetChangeImpl`。

1. 将以下内容添加到 COM 地图`BEGIN_COM_MAP ... END_COM_MAP`（ ）

   |  如果实现   |           添加到 COM 地图             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | 如果实现 | 添加到属性集映射 |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在命令中，将以下内容添加到属性集映射 （`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`）

   |  如果实现   |                                             添加到属性集映射                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在属性集映射中，还应包括以下所有设置，如下所示：

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

   通过在 Atldb.h 中查找属性 ED 和值（如果 Atldb.h 与联机文档不同，Atldb.h 将取代文档），可以找到这些宏调用中使用的值。

   > [!NOTE]
   > OLE DB `VARIANT_FALSE` `VARIANT_TRUE`模板需要许多 和 设置;OLE DB 规范表示它们可以读取/写入，但 OLE DB 模板只能支持一个值。

   **如果实现 IRowsetChangeimpl**

   如果实现`IRowsetChangeImpl`，则必须在提供程序上设置以下属性。 这些属性主要用于通过`ICommandProperties::SetProperties`请求接口。

   - `DBPROP_IRowsetChange`：设置此自动设置`DBPROP_IRowsetChange`。

   - `DBPROP_UPDATABILITY``IRowsetChange`： 在 上`SetData`指定受支持方法的位`DeleteRows`掩码`InsertRow`， 或 。

   - `DBPROP_CHANGEINSERTEDROWS`：使用者可以调用`IRowsetChange::DeleteRows`或`SetData`用于新插入的行。

   - `DBPROP_IMMOBILEROWS`：行集不会重新排序插入或更新的行。

   **如果实现 IRowset 更新**

   如果实现`IRowsetUpdateImpl`，除了为`IRowsetChangeImpl`以前列出的设置所有属性外，还必须在提供程序上设置以下属性：

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`：必须READ_ONLY和VARIANT_TRUE。

   - `DBPROP_OWNUPDATEDELETE`：必须READ_ONLY和VARIANT_TRUE。

   - `DBPROP_OTHERINSERT`：必须READ_ONLY和VARIANT_TRUE。

   - `DBPROP_OTHERUPDATEDELETE`：必须READ_ONLY和VARIANT_TRUE。

   - `DBPROP_REMOVEDELETED`：必须READ_ONLY和VARIANT_TRUE。

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > 如果您支持通知，您可能也拥有一些其他属性;但是，如果支持通知，则可能还有其他属性。请参阅此列表的`IRowsetNotifyCP`节。

## <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>写入数据源

要从数据源读取，请调用 函数`Execute`。 要写入数据源，请调用 函数`FlushData`。 （在一般意义上说，刷新意味着将对表或索引的修改保存到磁盘。

```cpp
FlushData(HROW, HACCESSOR);
```

行句柄 （HROW） 和访问器句柄 （HACCESSOR） 参数允许您指定要写入的区域。 通常，您一次编写一个数据字段。

该方法`FlushData`以最初存储数据的格式写入数据。 如果不重写此函数，提供程序将正常运行，但不会将更改刷新到数据存储。

### <a name="when-to-flush"></a>何时刷新

每当需要将数据写入数据存储时，提供程序模板都会调用 FlushData;这通常（但并非总是）是调用以下函数的结果：

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows`（如果有要在行中插入的新数据）

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>工作原理

使用者发出需要刷新（如更新）的呼叫，并且此调用将传递给提供程序，提供程序始终执行以下操作：

- 每当`SetDBStatus`您绑定了状态值时，都会调用。

- 检查列标志。

- 调用 `IsUpdateAllowed`。

这三个步骤有助于提供安全。 然后提供程序调用`FlushData`。

### <a name="how-to-implement-flushdata"></a>如何实现刷新数据

要实现`FlushData`，您需要考虑几个问题：

确保数据存储可以处理更改。

处理 NULL 值。

### <a name="handling-default-values"></a>处理默认值。

要实现自己的`FlushData`方法，您需要：

- 转到排设置类。

- 在行集类中，将 声明放在：

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- 提供 的`FlushData`实现。

良好的实现仅`FlushData`存储实际更新的行和列。 您可以使用 HROW 和 HACCESSOR 参数来确定要存储的当前行和列以进行优化。

通常，最大的挑战是使用您自己的本机数据存储。 如果可能，请尝试：

- 尽可能简单地将写入数据存储的方法保留。

- 处理 NULL 值（可选但建议）。

- 处理默认值（可选但建议）。

最好的办法是在数据存储中为 NULL 和默认值设置实际指定值。 最好可以推断此数据。 如果没有，建议您不要允许 NULL 和默认值。

下面的示例显示了`FlushData``RUpdateRowset``UpdatePV`如何在示例中的类中实现（请参阅示例代码中的 Rowset.h）：

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

要使提供商处理更改，首先需要确保数据存储（如文本文件或视频文件）具有允许您对其进行更改的设施。 如果没有，则应与提供程序项目分开创建该代码。

### <a name="handling-null-data"></a>处理空数据

最终用户可能会发送 NULL 数据。 将 NULL 值写入数据源中的字段时，可能存在问题。 想象一下，接受城市和邮政编码值的订单受理应用程序;它可以接受任一或两个值，但不能两者，因为在这种情况下，交付是不可能的。 因此，您必须限制字段中某些对应用程序有意义的 NULL 值组合。

作为提供程序开发人员，您必须考虑如何存储该数据、如何从数据存储中读取数据以及如何向用户指定这些数据。 具体而言，您必须考虑如何更改数据源中排组数据的数据状态（例如，数据状态 = NULL）。 当使用者访问包含 NULL 值的字段时，您可以决定返回什么值。

查看 UpdatePV 示例中的代码;它说明了提供程序如何处理 NULL 数据。 在 UpdatePV 中，提供程序通过在数据存储中写入字符串"NULL"来存储 NULL 数据。 当它从数据存储中读取 NULL 数据时，它会看到该字符串，然后清空缓冲区，创建 NULL 字符串。 如果数据值为空，`IRowsetImpl::GetDBStatus`它还可以覆盖该值DBSTATUS_S_ISNULL返回。

### <a name="marking-nullable-columns"></a>标记可标记列

如果还实现架构行集（请参阅`IDBSchemaRowsetImpl`），则实现应在DBSCHEMA_COLUMNS行集（通常由 CxxxSchemaColSchemaRowset 在提供程序中标记）中指定该列为空。

您还需要指定所有可空列在 版本的 中`GetColumnInfo`包含DBCOLUMNFLAGS_ISNULLABLE值。

在 OLE DB 模板实现中，如果无法将列标记为空，提供程序将假定它们必须包含值，并且不允许使用者将其发送为 null 值。

下面的示例演示如何在 UpdatePV 中的 CUpdate 命令（请参阅 UpProvRS.cpp） 中实现`CommonGetColInfo`该函数。 请注意列如何对空列DBCOLUMNFLAGS_ISNULLABLE。

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

与 NULL 数据一样，您有责任处理更改的默认值。

的默认值`FlushData``Execute`是返回S_OK。 因此，如果不重写此函数，更改似乎成功（S_OK将返回），但它们不会传输到数据存储。

在`UpdatePV`示例（在 Rowset.h 中`SetDBStatus`），该方法处理默认值的方式如下：

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

如果支持列上的默认值，则需要使用提供程序类\<\>SchemaRowset 类中的元数据设置该值。 设置 `m_bColumnHasDefault = VARIANT_TRUE`。

您还负责设置列标志，这些标志是使用 DBCOLUMNFLAGS 枚举类型指定的。 列标志描述列特征。

例如，在`CUpdateSessionColSchemaRowset`（在`UpdatePV`Session.h 中）中的类中，第一列的设置方式是这样的：

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

此代码指定列支持默认值 0、可写入以及列中的所有数据具有相同的长度。 如果希望列中的数据具有可变长度，则不会设置此标志。

## <a name="see-also"></a>另请参阅

[创建 OLE DB 提供程序](creating-an-ole-db-provider.md)
