---
title: "创建可更新的提供程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通知, 在提供程序中支持"
  - "OLE DB 提供程序, 创建"
  - "OLE DB 提供程序, 可更新的"
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 创建可更新的提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 6.0 只支持只读提供程序。  Visual C\+\+ .NET 支持可更新的提供程序，或者可以更新（写入）数据存储区的提供程序。  本主题讨论如何使用 OLE DB 模板创建可更新的提供程序。  
  
 本主题假设从工作提供程序开始。  创建可更新的提供程序有两步。  必须先决定提供程序将如何更改数据存储区，具体说来就是更改是立即完成还是推迟到发出更新命令时。  “[使提供程序可更新](#vchowmakingprovidersupdatable)”一节描述需要在提供程序代码中进行的更改和设置。  
  
 下一步，必须确保提供程序包含支持使用者可能请求的任何内容的所有功能。  如果使用者要更新数据存储区，则提供程序必须包含将数据保持到数据存储区的代码。  例如，可以使用 C 运行库或 MFC 在数据源上执行这些操作。  “[写入数据源](#vchowwritingtothedatasource)”一节描述了如何写入数据源，如何处理 **NULL** 和默认值以及如何设置列标志。  
  
> [!NOTE]
>  UpdatePV 就属于可更新的提供程序。  UpdatePV 和 MyProv 相同，但是具有可更新支持。  
  
##  <a name="vchowmakingprovidersupdatable"></a> 使提供程序可更新  
 使提供程序可更新的关键是了解希望提供程序对数据存储区执行哪些操作和希望提供程序如何执行那些操作。  具体说来，主要问题是数据存储区的更新是立即完成还是推迟（批处理）到发出更新命令时。  
  
 必须先决定在行集合类中是从 `IRowsetChangeImpl` 继承还是从 `IRowsetUpdateImpl` 继承。  根据您选择实现它们中的哪一个，将影响三个方法的功能：`SetData`、**InsertRows** 和 `DeleteRows`。  
  
-   如果从 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md) 继承，调用这三个方法将立即更改数据存储区。  
  
-   如果从 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md) 继承，这些方法将数据存储区的更改推迟到调用 **Update**、`GetOriginalData` 或 **Undo** 时。  如果更新涉及若干更改，则它们以批处理模式执行（注意批处理更改会增加相当大的内存开销）。  
  
 注意 `IRowsetUpdateImpl` 从 `IRowsetChangeImpl` 导出。  因此，`IRowsetUpdateImpl` 提供了更改功能和批处理功能。  
  
#### 支持提供程序中的可更新性  
  
1.  在行集合类中，从 `IRowsetChangeImpl` 或 `IRowsetUpdateImpl` 继承。  这些类为更改数据存储区提供适当的接口：  
  
     **添加 IRowsetChange**  
  
     使用此格式将 `IRowsetChangeImpl` 添加到继承链：  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     另外将 `COM_INTERFACE_ENTRY(IRowsetChange)` 添加到行集合类中的 `BEGIN_COM_MAP` 节。  
  
     **添加 IRowsetUpdate**  
  
     使用此格式将 `IRowsetUpdate` 添加到继承链：  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  应该从继承链中移除 `IRowsetChangeImpl` 行。  这是前面提到的指令的一个特例，必须包括 `IRowsetChangeImpl` 的代码。  
  
2.  将以下内容添加到 COM 映射 \(**BEGIN\_COM\_MAP ...END\_COM\_MAP**\)：  
  
    |如果实现|添加到 COM 映射|  
    |----------|----------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  在命令中，将以下内容添加到属性集映射 \(**BEGIN\_PROPSET\_MAP ...END\_PROPSET\_MAP**\)：  
  
    |如果实现|添加到属性集映射|  
    |----------|--------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  在属性集映射中，还应该包括所有以下设置，如下所示：  
  
    ```  
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
  
     在 Atldb.h 中查找属性 ID 和值（如果 Atldb.h 与联机文档不同，则 Atldb.h 取代文档），可以找到这些宏调用中使用的值。  
  
    > [!NOTE]
    >  许多 **VARIANT\_FALSE** 和 `VARIANT_TRUE` 设置都是 OLE DB 模板必需的；OLE DB 规范声称它们可以读\/写，但是 OLE DB 模板只能支持一个值。  
  
     **如果实现 IRowsetChangeImpl**  
  
     如果实现 `IRowsetChangeImpl`，则必须在提供程序上设置以下属性。  这些属性主要用于通过 **ICommandProperties::SetProperties** 请求接口。  
  
    -   `DBPROP_IRowsetChange`：设置它会自动设置 **DBPROP\_IRowsetChange**。  
  
    -   `DBPROP_UPDATABILITY`：一个指定 `IRowsetChange` 上所支持方法（`SetData`、`DeleteRows` 或 `InsertRow`）的位掩码。  
  
    -   `DBPROP_CHANGEINSERTEDROWS`：使用者可以对新插入的行调用 **IRowsetChange::DeleteRows** 或 `SetData`。  
  
    -   `DBPROP_IMMOBILEROWS`：行集合不重新排序插入或更新的行。  
  
     **如果实现 IRowsetUpdateImpl**  
  
     如果实现 `IRowsetUpdateImpl`，则除了设置前面列出的 `IRowsetChangeImpl` 的所有属性外，还必须设置提供程序的以下属性：  
  
    -   `DBPROP_IRowsetUpdate`.  
  
    -   `DBPROP_OWNINSERT`：必须是 READ\_ONLY 和 VARIANT\_TRUE。  
  
    -   `DBPROP_OWNUPDATEDELETE`：必须是 READ\_ONLY 和 VARIANT\_TRUE。  
  
    -   `DBPROP_OTHERINSERT`：必须是 READ\_ONLY 和 VARIANT\_TRUE。  
  
    -   `DBPROP_OTHERUPDATEDELETE`：必须是 READ\_ONLY 和 VARIANT\_TRUE。  
  
    -   `DBPROP_REMOVEDELETED`：必须是 READ\_ONLY 和 VARIANT\_TRUE。  
  
    -   `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  如果支持通知，也可能具有其他一些属性；有关此列表的内容，请参见 `IRowsetNotifyCP` 中的相应部分。  
  
     有关属性如何设置的示例，请参见 [UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f) 中 **CUpdateCommand**（在 Rowset.h 中）中的属性集映射。  
  
##  <a name="vchowwritingtothedatasource"></a> 写入数据源  
 若要从数据源读取，请调用 **Execute** 函数。  若要写入数据源，请调用 `FlushData` 函数。（从一般意义上讲，“刷新”表示将表或索引的修改保存到磁盘。）  
  
```  
FlushData(HROW, HACCESSOR);  
```  
  
 行处理 \(*HROW*\) 和访问器处理 \(*HACCESSOR*\) 参数使您得以指定写入的区域。  通常是一次写入一个数据字段。  
  
 `FlushData` 方法按数据最初存储的格式写入数据。  如果不重写此函数，则提供程序将正确运行，但更改不刷新到数据存储区。  
  
### 何时刷新  
 每当数据需要写入数据存储区时，提供程序模板都调用 `FlushData`；这通常（但并非总是）在下列函数调用后发生：  
  
-   **IRowsetChange::DeleteRows**  
  
-   **IRowsetChange::SetData**  
  
-   **IRowsetChange::InsertRows**（如果有新数据需要插入到行中）  
  
-   **IRowsetUpdate::Update**  
  
### 工作机制  
 使用者发出要求刷新的调用（如 **Update**），而此调用被传递到提供程序，后者总是执行以下操作：  
  
-   每当绑定状态值时都调用 `SetDBStatus`（请参见《OLE DB 程序员参考》的第 6 章“数据部分：状态”）。  
  
-   检查列标志。  
  
-   调用 `IsUpdateAllowed`。  
  
 这三个步骤帮助提供安全性。  然后提供程序调用 `FlushData`。  
  
### 如何实现 FlushData  
 若要实现 `FlushData`，需要考虑若干问题：  
  
-   确保数据存储区可以处理更改。  
  
-   处理 **NULL** 值。  
  
-   处理默认值。  
  
 若要实现自己的 `FlushData` 方法，需要：  
  
-   转到行集合类。  
  
-   在行集合类中，放置如下声明：  
  
```  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    // Insert your implementation here and return an HRESULT.  
}  
```  
  
-   提供 `FlushData` 的实现。  
  
 好的 `FlushData` 实现只存储实际更新的行和列。  可以使用 *HROW* 和 *HACCESSOR* 参数确定为优化而存储的当前行和列。  
  
 通常，最大的难题是如何使用您自己的本机数据存储区。  如果可能，尝试：  
  
-   使写入数据存储区的方法尽可能保持简单。  
  
-   处理 **NULL** 值（可选但建议）。  
  
-   处理默认值（可选但建议）。  
  
 所要做的最好的事情是在数据存储区中具有 **NULL** 和默认值的实际指定值。  最好是能够外推此数据。  如果不能，建议不要允许 **NULL** 和默认值。  
  
 下面的示例显示如何 `FlushData` 在 [UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f) 示例的 `RUpdateRowset` 类中的实现（请参见代码示例中的 Rowset.h）：  
  
```  
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
  
### 处理更改  
 为使提供程序可以处理更改，首先需要确保数据存储区（例如，文本文件或视频文件）具有使您能够对它进行更改的功能。  如果不具有，则应同提供程序项目分开创建此代码。  
  
### 处理 NULL 数据  
 最终用户可能会发送 **NULL** 数据。  当将 **NULL** 值写入数据源中的字段时，可能会有潜在的问题。  假设有一个接受城市代码值和邮政编码值的订单接收程序；它可以接受这两个值中的任何一个或者两个值都接受，但不可能两个都不接受，因为这种情况下交货将是不可能的。  因此必须在对应用程序有意义的字段中限制某些 **NULL** 值组合。  
  
 作为提供程序开发人员，必须考虑如何存储那些数据，如何从数据存储区中读取那些数据，以及如何给用户指定那些数据。  特别是，必须考虑如何更改数据源中行集合数据的数据状态（例如，DataStatus \= **NULL**）。  决定当使用者访问包含 **NULL** 值的字段时返回什么值。  
  
 查看 [UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f) 示例中的代码；它阐释提供程序可以如何处理 **NULL** 数据。  在 UpdatePV 中，提供程序通过在数据存储区中写入字符串“NULL”存储 **NULL** 数据。  当它从数据存储区中读取 **NULL** 数据时，它会看到该字符串然后清空缓冲区以创建 **NULL** 字符串。  它还具有 `IRowsetImpl::GetDBStatus` 的重写，如果该数据值是空的它将返回 **DBSTATUS\_S\_ISNULL**。  
  
### 标记可为 null 的列  
 如果还实现了架构行集合（请参见 `IDBSchemaRowsetImpl`），该实现应在 **DBSCHEMA\_COLUMNS** 行集合（在提供程序中通常由 **C***xxx***SchemaColSchemaRowset** 标记）中指定列可为 null。  
  
 还需要指定所有可为 null 的列在 `GetColumnInfo` 版本中都包含 **DBCOLUMNFLAGS\_ISNULLABLE** 值。  
  
 在 OLE DB 模板实现中，如果未能将列标记为可为 null，提供程序将假定它们必须包含值，并且不允许使用者向它发送 null 值。  
  
 下面的示例显示 **CommonGetColInfo** 函数在 UpdatePV 的 **CUpdateCommand**（请参见 UpProvRS.cpp）中的实现。  注意对于可为 null 的列，列如何具有此 **DBCOLUMNFLAGS\_ISNULLABLE**。  
  
```  
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
  
### 默认值  
 与 **NULL** 数据一样，您有责任处理如何更改默认值。  
  
 `FlushData` 和 **Execute** 的默认值返回 `S_OK`。  因此，如果不重写此函数，更改看起来是成功的（返回 `S_OK`），但它们不能传输到数据存储区。  
  
 在 [UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f) 示例（在 Rowset.h 中）中，`SetDBStatus` 方法以如下方式处理默认值：  
  
```  
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
  
### 列标志  
 如果支持该列的默认值，请使用在 **\<***提供程序类*的元数据，**\>SchemaRowset** 类需要设置。  将 *m\_bColumnHasDefault* 设置为 \= `VARIANT_TRUE`。  
  
 您也有责任设置列标志，它们是用 **DBCOLUMNFLAGS** 枚举类型指定的。  列标志描述列特性。  
  
 例如，在 [UpdatePV](http://msdn.microsoft.com/zh-cn/c8bed873-223c-4a7d-af55-f90138c6f38f)（在 Session.h 中）中的 `CUpdateSessionColSchemaRowset` 类中，第一列这种设置：  
  
```  
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
  
 除了其他的事项，此代码还指定列支持默认值 0，指定它是可写的，并且指定列中的所有数据具有相同长度。  如果希望列中的数据具有可变长度，则不要设置此标志。  
  
## 请参阅  
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)