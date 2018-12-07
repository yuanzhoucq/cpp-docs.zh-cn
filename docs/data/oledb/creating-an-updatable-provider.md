---
title: 创建可更新的提供程序
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 04db02bc8ad4db0c669e07a0bcf1b60ffa22e8ad
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521396"
---
# <a name="creating-an-updatable-provider"></a>创建可更新的提供程序

Visual c + + 支持可更新的提供程序或可更新的提供程序 （写入） 数据存储区。 本主题讨论如何创建可更新的提供程序使用 OLE DB 模板。

本主题假定你着手工作提供程序。 有两个步骤创建可更新的提供程序。 您必须首先确定如何提供程序将对数据存储区; 进行的更改具体而言，是否更改会立即完成或者延迟，直到发出 update 命令。 部分"[使提供程序可更新](#vchowmakingprovidersupdatable)"的更改和的设置，需要在提供程序代码中执行操作。

接下来，必须确保您的提供程序包含所有功能，以支持使用者可能会请求它的任何内容。 如果使用者想要更新的数据存储区，则提供程序必须包含的数据保存到数据存储区的代码。 例如，可能会使用 MFC 的 C 运行时库来执行此类操作对数据源。 部分"[写入到数据源](#vchowwritingtothedatasource)"介绍如何将写入到数据源，处理 NULL 和默认值，并设置列标志。

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)是可更新的提供程序的示例。 UpdatePV 是相同的作为 MyProv 但对可更新的支持。

##  <a name="vchowmakingprovidersupdatable"></a> 使提供程序可更新

使提供程序可更新的关键了解您希望在提供程序对数据存储区和想要执行这些操作的提供程序如何执行哪些的操作。 具体而言，主要问题是数据存储区的更新是否要立即完成或延迟 （批处理） 发出更新命令之前。

您必须首先决定是否继承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`行集类中。 具体取决于这些所选内容来实现，三种方法的功能将会受到影响： `SetData`， `InsertRows`，和`DeleteRows`。

- 如果继承自[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)，立即调用这三种方法更改数据存储区。

- 如果继承自[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)，方法延迟到数据存储区的更改，直到你调用`Update`， `GetOriginalData`，或`Undo`。 如果更新涉及多项更改，它们在批处理模式下 （请注意，批处理更改可以添加相当大的内存开销） 执行。

请注意，`IRowsetUpdateImpl`派生自`IRowsetChangeImpl`。 因此，`IRowsetUpdateImpl`提供更改功能以及批处理功能。

### <a name="to-support-updatability-in-your-provider"></a>若要在您的提供程序中支持可更新性

1. 在行集类中，继承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`。 这些类用于更改数据存储区提供相应的接口：

   **添加 IRowsetChange**

   添加`IRowsetChangeImpl`到使用此窗体继承链：

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   此外将添加`COM_INTERFACE_ENTRY(IRowsetChange)`到`BEGIN_COM_MAP`行集类中的部分。

   **添加 IRowsetUpdate**

   添加`IRowsetUpdate`到使用此窗体继承链：

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > 应删除`IRowsetChangeImpl`继承链中的行。 如前面所述的指令的此例外必须包含的代码`IRowsetChangeImpl`。

1. 将以下代码添加到 COM 映射 (`BEGIN_COM_MAP ... END_COM_MAP`):

   |  如果你实现   |           将添加到 COM 映射             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | 如果你实现 | 将添加到属性组映射 |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在命令中，将以下代码添加到属性集映射中 (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):

   |  如果你实现   |                                             将添加到属性组映射                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在属性集映射中，您还应包括以下设置的所有按照如下所示：

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

   您可以找到这些宏调用中，由在 Atldb.h 中查找的属性 Id 和值的值 （如果 Atldb.h 不同于联机文档，Atldb.h 取代文档）。

   > [!NOTE]
   > 许多`VARIANT_FALSE`和`VARIANT_TRUE`设置所需的 OLE DB 模板; OLE DB 规范指出，它们可以是读/写，但 OLE DB 模板仅支持一个值。

   **如果实现 IRowsetChangeImpl**

   如果你实现`IRowsetChangeImpl`，必须在您的提供程序上设置以下属性。 这些属性主要用于请求通过接口`ICommandProperties::SetProperties`。

   - `DBPROP_IRowsetChange`： 设置将自动设置`DBPROP_IRowsetChange`。

   - `DBPROP_UPDATABILITY`： 指定受支持的方法一个位掩码`IRowsetChange`: `SetData`， `DeleteRows`，或`InsertRow`。

   - `DBPROP_CHANGEINSERTEDROWS`： 使用者可以调用`IRowsetChange::DeleteRows`或`SetData`为新插入的行。

   - `DBPROP_IMMOBILEROWS`： 行集不会对插入或更新的行重新排序。

   **如果实现 IRowsetUpdateImpl**

   如果你实现了`IRowsetUpdateImpl`，必须设置以下属性上您的提供商，除了为的所有属性都设置`IRowsetChangeImpl`以前列出：

   - `DBPROP_IRowsetUpdate`。

   - `DBPROP_OWNINSERT`： 必须为 READ_ONLY 和为 VARIANT_TRUE。

   - `DBPROP_OWNUPDATEDELETE`： 必须为 READ_ONLY 和为 VARIANT_TRUE。

   - `DBPROP_OTHERINSERT`： 必须为 READ_ONLY 和为 VARIANT_TRUE。

   - `DBPROP_OTHERUPDATEDELETE`： 必须为 READ_ONLY 和为 VARIANT_TRUE。

   - `DBPROP_REMOVEDELETED`： 必须为 READ_ONLY 和为 VARIANT_TRUE。

   - `DBPROP_MAXPENDINGROWS`。

   > [!NOTE]
   > 如果支持通知，您可能还有一些其他属性;请参阅部分`IRowsetNotifyCP`为此列表。

##  <a name="vchowwritingtothedatasource"></a> 写入到数据源

若要从数据源中读取，调用`Execute`函数。 若要写入的数据源，请调用`FlushData`函数。 （在常规的意义上，刷新表示以保存对表或索引到磁盘进行的修改。）

```cpp
FlushData(HROW, HACCESSOR);
```

行句柄 (HROW) 和访问器句柄 (HACCESSOR) 参数，可以指定要写入的区域。 通常情况下，一次写入的单个数据字段。

`FlushData`方法中最初存储的格式写入数据。 如果不重写此函数，您的提供程序将正常工作，但不是会进行更改刷新到数据存储。

### <a name="when-to-flush"></a>何时刷新

提供程序模板调用 FlushData，每当数据需要写入到数据存储区;这通常 （但并非总是如此），将发生以下函数调用：

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` （如果没有要插入的行中的新数据）

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>其工作原理

使用者发出要求 （如更新） 刷新的调用而此调用传递给提供程序，始终将执行以下操作：

- 调用`SetDBStatus`每当有绑定的状态值。

- 检查列标志。

- 调用 `IsUpdateAllowed`。

这三个步骤帮助提供安全。 然后在提供程序调用`FlushData`。

### <a name="how-to-implement-flushdata"></a>如何实现 FlushData

若要实现`FlushData`，您需要考虑的几个问题：

确保数据存储区可以处理的更改。

处理 NULL 值。

### <a name="handling-default-values"></a>处理默认值。

若要实现您自己`FlushData`方法中，你需要：

- 请转到行集类。

- 在行集类中，放置的声明：

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- 提供的实现`FlushData`。

好实现的`FlushData`存储的行和列的实际更新。 HROW 和 HACCESSOR 参数可用于确定当前行和列存储的优化。

通常，最大的挑战如何使用你自己的本机数据存储。 如果可能，请尝试：

- 保留写入到数据存储区一样简单的方法。

- 处理 NULL 值 （可选但建议）。

- 处理默认值 （可选但建议）。

最佳办法就是能够实际指定的值为 NULL 和默认值在数据存储区中。 最好可以运用此数据。 如果没有，则建议不允许空值和默认值。

下面的示例演示如何`FlushData`中实现`RUpdateRowset`类中`UpdatePV`示例 （在示例代码，请参阅 Rowset.h）：

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

为提供者来处理更改，首先需要确保数据存储区 （如文本文件或视频文件中） 具有使您能够对它进行更改的功能。 如果不是，应从提供程序项目单独创建该代码。

### <a name="handling-null-data"></a>处理 NULL 数据

有可能，最终用户将会发送 NULL 数据。 当数据源中的字段中写入 NULL 值时，可能会有潜在问题。 假设接受表示城市和邮政编码; 值的顺序进行应用程序它能接受一个或两个值，但不是既不，因为在这种情况下传递就不可能。 因此需要限制对你的应用程序有意义的字段中的 NULL 值的某些组合。

作为提供程序开发人员，您必须考虑如何将存储此数据、 如何将数据存储中读取该数据和如何为用户指定的。 具体而言，必须考虑如何更改数据源中的行集数据的数据状态 (例如，DataStatus = NULL)。 您决定要使用者访问包含 NULL 值的字段时返回的值。

看一下 UpdatePV 示例; 中的代码它演示了一个提供程序如何处理 NULL 的数据。 在 UpdatePV，提供程序数据存储中存储通过编写在字符串"NULL"NULL 数据。 当它从数据存储区中读取 NULL 数据时，它将会看到该字符串，然后清空缓冲区，以创建空字符串。 它还具有的重写`IRowsetImpl::GetDBStatus`在它返回 DBSTATUS_S_ISNULL 该数据值是否为空。

### <a name="marking-nullable-columns"></a>将标记为 Null 的列

如果还实现架构行集 (请参阅`IDBSchemaRowsetImpl`)，您的实现应指定 DBSCHEMA_COLUMNS 行集 （通常标记提供程序中通过 CxxxSchemaColSchemaRowset） 中的列可以为 null。

此外需要指定可以为 null 的所有列都包含你的版本中的 DBCOLUMNFLAGS_ISNULLABLE 值`GetColumnInfo`。

在 OLE DB 模板实现中，如果您不能将标记为可为 null，列提供程序将假定它们必须包含一个值，并且将不允许使用者将其发送 null 值。

下面的示例演示如何将`CommonGetColInfo`在 CUpdateCommand 中实现函数 （请参阅 UpProvRS.cpp） UpdatePV 中。 请注意如何列具有此 DBCOLUMNFLAGS_ISNULLABLE 为 null 的列。

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

与 NULL 数据一样，您有责任处理如何更改默认值。

默认值为`FlushData`和`Execute`将返回 S_OK。 因此，如果不重写此函数，所做的更改看起来是成功 （返回 S_OK），但它们不能传输到数据存储。

在中`UpdatePV`示例 （在 Rowset.h)，`SetDBStatus`方法处理默认值，如下所示：

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

如果在列上支持默认值，则需要将其使用中的元数据设置\<提供程序类\>SchemaRowset 类。 设置`m_bColumnHasDefault = VARIANT_TRUE`。

您也有责任设置指定使用 DBCOLUMNFLAGS 枚举类型的列标志。 列标志描述列特征。

例如，在`CUpdateSessionColSchemaRowset`类中`UpdatePV`（在 Session.h)，第一列将设置这种方式：

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

此代码指定，除此之外，列支持默认值为 0，它是可写，并且列中的所有数据都具有相同的长度。 如果你想要具有可变长度的列中的数据，则不要设置此标志。

## <a name="see-also"></a>请参阅

[创建 OLE DB 提供程序](creating-an-ole-db-provider.md)