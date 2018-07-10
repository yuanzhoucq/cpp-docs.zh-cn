---
title: 创建可更新提供程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 317ccd043b3a69489f9cbd2737ad7741389863c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098636"
---
# <a name="creating-an-updatable-provider"></a>创建可更新的提供程序
Visual c + + 支持可更新提供程序或可更新的提供程序 （写入） 数据存储区。 本主题讨论如何创建可更新提供程序使用 OLE DB 模板。  
  
 本主题假定你着手可行的提供程序。 有两个步骤创建可更新提供程序。 你必须首先决定如何提供程序将对数据存储区; 进行更改具体而言，是否要立即完成或更改推迟，直到发出更新命令。 部分"[使提供程序可更新](#vchowmakingprovidersupdatable)"描述的更改和设置，需要在提供程序代码中执行操作。  
  
 接下来，你必须确保你的提供商包含用于支持使用者可能会请求它的任何内容的所有功能。 如果使用者想要更新的数据存储区，则提供程序必须包含保持与数据存储的数据的代码。 例如，你可能使用 MFC 的 C 运行时库来执行此类操作对数据源。 部分"[写入到数据源](#vchowwritingtothedatasource)"介绍如何将写入到数据源，处理**NULL**和默认值，以及如何设置列标志。  
  
> [!NOTE]
>  UpdatePV 是可更新的提供程序的示例。 UpdatePV 相同作为 MyProv 只是包含可更新的支持。  
  
##  <a name="vchowmakingprovidersupdatable"></a> 使提供程序可更新  
 使提供程序可更新的关键了解你希望你提供程序对数据存储和你想要执行这些操作的提供程序如何执行哪些的操作。 具体而言，主要问题是对数据存储区更新是否要立即完成或延迟 （批处理） 发出更新命令之前。  
  
 你必须首先决定是否要从其继承`IRowsetChangeImpl`或`IRowsetUpdateImpl`行集类中。 根据以下哪种你选择实现，三个方法的功能将受到影响： `SetData`， **InsertRows**，和`DeleteRows`。  
  
-   如果从继承[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)，立即调用这三种方法更改数据存储区。  
  
-   如果从继承[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)，方法将推迟到数据存储区的更改，直到你调用**更新**， `GetOriginalData`，或**撤消**。 如果更新涉及多项更改，它们将以批处理模式 （请注意，批处理更改可以添加相当大的内存开销） 执行。  
  
 请注意，`IRowsetUpdateImpl`派生自`IRowsetChangeImpl`。 因此，`IRowsetUpdateImpl`提供更改功能以及批处理功能。  
  
#### <a name="to-support-updatability-in-your-provider"></a>若要在提供程序中支持可更新性  
  
1.  在行集类中，继承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`。 这些类用于更改数据存储区提供相应的接口：  
  
     **添加 IRowsetChange**  
  
     添加`IRowsetChangeImpl`到您使用此窗体的继承链：  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     此外添加`COM_INTERFACE_ENTRY(IRowsetChange)`到`BEGIN_COM_MAP`行集类中的部分。  
  
     **添加 IRowsetUpdate**  
  
     添加`IRowsetUpdate`到您使用此窗体的继承链：  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  应删除`IRowsetChangeImpl`从继承链的行。 此向该指令前面提到的一个异常必须包含的代码`IRowsetChangeImpl`。  
  
2.  将以下代码添加到 COM 映射 (**BEGIN_COM_MAP...END_COM_MAP**):  
  
    |如果你实现|将添加到 COM 映射|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  在命令中，将以下代码添加到属性集映射中 (**BEGIN_PROPSET_MAP...END_PROPSET_MAP**):  
  
    |如果你实现|将添加到属性集映射|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  在属性集映射中，你还应包括以下设置的所有按照如下所示：  
  
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
  
     你可以找到这些宏调用中使用通过在 Atldb.h 中查看的属性 Id 和值的值 （如果 Atldb.h 不同于联机文档，Atldb.h 取代文档）。  
  
    > [!NOTE]
    >  许多**VARIANT_FALSE**和`VARIANT_TRUE`设置所需的 OLE DB 模板; 该 OLE DB 规范内容它们可以是读/写，但 OLE DB 模板只能支持一个值。  
  
     **如果实现 IRowsetChangeImpl**  
  
     如果你实现`IRowsetChangeImpl`，必须在你的提供商上设置以下属性。 这些属性主要用于请求通过接口**ICommandProperties::SetProperties**。  
  
    -   `DBPROP_IRowsetChange`： 此自动设置集**DBPROP_IRowsetChange**。  
  
    -   `DBPROP_UPDATABILITY`： 指定支持的方法上一个位屏蔽`IRowsetChange`: `SetData`， `DeleteRows`，或`InsertRow`。  
  
    -   `DBPROP_CHANGEINSERTEDROWS`： 使用者可以调用**IRowsetChange::DeleteRows**或`SetData`新插入行。  
  
    -   `DBPROP_IMMOBILEROWS`： 行集不会对插入或更新的行重新排序。  
  
     **如果实现 IRowsetUpdateImpl**  
  
     如果你实现`IRowsetUpdateImpl`，你必须设置以下属性提供程序，此外到设置的所有属性`IRowsetChangeImpl`前面所列：  
  
    -   `DBPROP_IRowsetUpdate`。  
  
    -   `DBPROP_OWNINSERT`： 必须为 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_OWNUPDATEDELETE`： 必须为 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_OTHERINSERT`： 必须为 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_OTHERUPDATEDELETE`： 必须为 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_REMOVEDELETED`： 必须为 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_MAXPENDINGROWS`。  
  
        > [!NOTE]
        >  如果支持通知，您可能还有其他一些属性以及;请参阅的部分`IRowsetNotifyCP`有关此列表。  
  
     有关示例的属性的设置方式，请参阅在该属性设置的地图**CUpdateCommand** （在 Rowset.h) 中[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)。  
  
##  <a name="vchowwritingtothedatasource"></a> 写入到数据源  
 若要从数据源中读取，调用**执行**函数。 若要写入的数据源，请调用`FlushData`函数。 （在常规的意义上，刷新表示以保存对表或索引到磁盘进行的修改。）  
  
```  
FlushData(HROW, HACCESSOR);  
```  
  
 行句柄 (*HROW*) 和访问器句柄 (*HACCESSOR*) 自变量允许你指定要写入的区域。 通常，如果你编写一次的单个数据字段。  
  
 `FlushData`方法中最初存储的格式写入数据。 如果你不重写此函数，你的提供商将正常工作，但更改不会刷新到数据存储。  
  
### <a name="when-to-flush"></a>何时刷新  
 提供程序模板调用`FlushData`每当需要写入到数据存储区数据; 这通常 （但不是总是），将发生对以下函数的调用：  
  
-   **IRowsetChange::DeleteRows**  
  
-   **IRowsetChange::SetData**  
  
-   **IRowsetChange::InsertRows** （如果没有要插入的行中的新数据）  
  
-   **IRowsetUpdate::Update**  
  
### <a name="how-it-works"></a>它是如何工作  
 使用者发出的调用需要刷新 (如**更新**) 和此调用传递给提供程序，后者始终执行下列任务：  
  
-   调用`SetDBStatus`每当有绑定的状态值 (请参阅*OLE DB 程序员参考*，第 6 章*数据部分： 状态*)。  
  
-   检查列的标志。  
  
-   调用 `IsUpdateAllowed`。  
  
 这三个步骤帮助提供安全性。 然后，该提供程序调用`FlushData`。  
  
### <a name="how-to-implement-flushdata"></a>如何实现 FlushData  
 若要实现`FlushData`，你需要考虑几个问题：  
  
-   必须确保在数据存储区可以处理更改。  
  
-   处理**NULL**值。  
  
-   处理默认值。  
  
 若要实现自己`FlushData`方法，你需要：  
  
-   请转到行集类。  
  
-   在行集中类中，放置的声明：  
  
```  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    // Insert your implementation here and return an HRESULT.  
}  
```  
  
-   提供的一个实现`FlushData`。  
  
 好实现的`FlushData`存储行和实际更新的列。 你可以使用*HROW*和*HACCESSOR*参数，以确定当前行和列存储的优化。  
  
 通常情况下，最大的难题如何使用本机数据存储区中。 如果可能，请尝试：  
  
-   保留写入数据存储区尽可能简单的方法。  
  
-   处理**NULL**值 （可选但建议）。  
  
-   处理默认值 （可选但建议）。  
  
 最佳做法是在你数据存储区中具有实际指定的值**NULL**和默认值。 最好可以推测此数据。 如果没有，建议您将不允许**NULL**和默认值。  
  
 下面的示例演示如何`FlushData`中实现`RUpdateRowset`类[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)示例 （在示例代码中看到 Rowset.h）：  
  
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
 您可以处理更改的提供程序，首先需要确保数据存储区 （如文本文件或视频文件） 具有使您能够对它进行更改的功能。 如果不存在，则应从提供程序项目单独创建该代码。  
  
### <a name="handling-null-data"></a>处理 NULL 数据  
 很可能最终用户将发送**NULL**数据。 当你编写**NULL**值到数据源中的字段，可能会有潜在问题。 假设的顺序拍摄应用程序接受的城市和邮政编码; 值因为在这种情况下传递将无法完成，它可以接受一个或两个值，但不是都不。 因此，你需要限制某些组合**NULL**对你的应用程序而言非常重要的字段中的值。  
  
 作为提供程序开发人员，你必须考虑如何将存储该数据、 如何在从数据存储中，将读取该数据和如何向用户指定的。 具体而言，必须考虑如何更改数据源中的行集数据的数据状态 (例如，DataStatus = **NULL**)。 决定什么值时使用者访问一个字段，其中包含要返回**NULL**值。  
  
 中的代码查看[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)示例; 它阐释了如何处理提供程序**NULL**数据。 提供程序将存储在 UpdatePV， **NULL**通过编写字符串"NULL"数据存储区中的数据。 当它读取**NULL**数据从数据存储，它会看到该字符串，然后清空缓冲区，创建**NULL**字符串。 它还具有的重写`IRowsetImpl::GetDBStatus`在它返回**是 DBSTATUS_S_ISNULL**该数据值是否为空。  
  
### <a name="marking-nullable-columns"></a>将标记为 Null 的列  
 如果您还实现架构行集 (请参阅`IDBSchemaRowsetImpl`)，您的实现应在指定**DBSCHEMA_COLUMNS**行集 (通常在你提供程序中标记为**C***xxx***SchemaColSchemaRowset**)，列可以为 null。  
  
 你还必须指定所有可以为 null 的列包含**DBCOLUMNFLAGS_ISNULLABLE**你的版本中的值`GetColumnInfo`。  
  
 在 OLE DB 模板实现中，如果您不能将标记为可为 null，列提供程序将假定它们必须包含一个值，并且将不允许使用者向它发送 null 值。  
  
 下面的示例演示如何**CommonGetColInfo**中实现函数**CUpdateCommand** （请参阅 UpProvRS.cpp） UpdatePV 中。 请注意如何列具有这**DBCOLUMNFLAGS_ISNULLABLE**为 null 的列。  
  
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
 与**NULL**数据，您有责任处理如何更改默认值。  
  
 默认`FlushData`和**执行**是返回`S_OK`。 因此，如果你不重写此函数，所做的更改看起来是成功 (`S_OK`将返回)，但它们不能传输到数据存储。  
  
 在[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)示例 （Rowset.h)，`SetDBStatus`方法可处理默认值，如下所示：  
  
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
  
### <a name="column-flags"></a>列的标志  
 如果你的列上支持默认值，你需要将其使用中的元数据设置 **\<***提供程序类***> SchemaRowset**类。 设置*m_bColumnHasDefault* = `VARIANT_TRUE`。  
  
 你还可以设置使用指定的列标志的责任**DBCOLUMNFLAGS**枚举类型。 列标志描述列特征。  
  
 例如，在`CUpdateSessionColSchemaRowset`类[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) （在 Session.h)，第一列设置这种方式：  
  
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
  
 此代码指定，除了别的之外列支持默认值为 0，它是可写，并且列中的所有数据都具有相同的长度。 如果你想要具有可变长度的列中的数据，则不要设置此标志。  
  
## <a name="see-also"></a>请参阅  
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)