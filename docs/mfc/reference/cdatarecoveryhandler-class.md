---
title: CDataRecoveryHandler 类
ms.date: 03/27/2019
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
helpviewer_keywords:
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
ms.openlocfilehash: 5c5836a11dbf9e05db5b56e0bc5c062dd1617b2f
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565852"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler 类

`CDataRecoveryHandler`则自动保存文档并将其还原，如果应用程序意外退出。

## <a name="syntax"></a>语法

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|构造 `CDataRecoveryHandler` 对象。|

### <a name="methods"></a>方法

|||
|-|-|
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|则自动保存每个文件注册`CDataRecoveryHandler`类。|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|则自动保存指定的文档。|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|将文档添加到打开的文档的列表。|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|删除所有当前的自动保存文件。|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|删除指定的自动保存文件。|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|生成与提供的文档文件名称相关联的自动保存文件的名称。|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|返回自动保存次尝试之间的间隔。|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|返回自动保存文件的路径。|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|检索文档名从`CDocument`对象。|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|检索指定的文档的普通标题。|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|创建并返回已恢复文档的标题。|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|检索应用程序的唯一重启标识符。|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|指示是否`CDataRecoveryHandler`自动保存对当前空闲循环。|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|表示重新启动管理器是否导致退出该应用程序。|
|[CDataRecoveryHandler::Initialize](#initialize)|初始化 `CDataRecoveryHandler`。|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|向用户显示一个对话框，为每个文档的`CDataRecoveryHandler`自动保存。 对话框中确定用户是否想要还原自动保存文档。|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|从注册表加载打开的文档列表。|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|从打开的文档列表中删除所提供的文档。|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|打开以前打开的文档。|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|还原自动保存文档根据用户输入。|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|将当前打开的文档的列表保存到 Windows 注册表。|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|设置自动保存周期以毫秒为单位之间的时间。|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|设置自动保存文件的存储位置的目录。|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|设置的此实例的唯一重启标识符`CDataRecoveryHandler`。|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|集是否`CDataRecoveryHandler`当前空闲周期内将打开的文档信息保存到 Windows 注册表。|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|设置是否以前退出该应用程序而引起的重新启动管理器。|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|由于用户保存它，请更新文档的信息。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|m_bRestoringPreviousOpenDocs|指示数据恢复处理程序是否重新打开以前打开的文档。|
|m_bSaveDocumentInfoOnIdle|指示是否数据恢复处理程序则自动保存文档上的下一步的空闲循环。|
|m_bShutdownByRestartManager|指示是否重新启动管理器会导致应用程序退出。|
|m_dwRestartManagerSupportFlags|这些标志指示什么支持重新启动管理器提供的应用程序。|
|m_lstAutosavesToDelete|未删除原始文档已关闭时自动保存文件的列表。 应用程序退出时，重新启动管理器重试删除文件。|
|m_mapDocNameToAutosaveName|自动保存文件名称的文档名称的映射。|
|m_mapDocNameToDocumentPtr|映射到的文档名称[CDocument](../../mfc/reference/cdocument-class.md)指针。|
|m_mapDocNameToRestoreBool|一个布尔型参数，该值指示是否将自动保存文档还原到的文档名称的映射。|
|m_mapDocumentPtrToDocName|映射的`CDocument`文档名称的指针。|
|m_mapDocumentPtrToDocTitle|映射的`CDocument`指向文档标题。 这些标题用于保存文件。|
|m_nAutosaveInterval|以毫秒为单位，则自动保存之间的时间。|
|m_nTimerID|自动保存计时器标识符。|
|m_strAutosavePath|存储自动保存文档的位置。|
|m_strRestartIdentifier|重新启动管理器 GUID 的字符串表示形式。|

## <a name="remarks"></a>备注

重新启动管理器使用`CDataRecoveryHandler`类，以使跟踪的所有打开的文档和自动保存到它们在必要时。 若要启用自动保存，请使用[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)方法。 此方法将定向`CDataRecoveryHandler`对下一个空闲循环中执行了自动保存。 重新启动管理器调用`SetSaveDocumentInfoOnIdle`时`CDataRecoveryHandler`应执行自动保存。

所有的方法`CDataRecoveryHandler`类是虚的。 重写此类，以创建自己的自定义数据恢复处理程序中的方法。 除非创建你自己的数据恢复处理程序或重新启动管理器，否则不要实例化 CDataRecoveryHandler。 [CWinApp 类](../../mfc/reference/cwinapp-class.md)创建`CDataRecoveryHandler`对象，因为它是必填。

可以使用之前`CDataRecoveryHandler`对象，必须调用[CDataRecoveryHandler::Initialize](#initialize)。

因为`CDataRecoveryHandler`类紧密地连接到重新启动管理器中，`CDataRecoveryHandler`取决于全局参数`m_dwRestartManagerSupportFlags`。 此参数确定的重新启动管理器具有什么权限以及它如何与你的应用程序交互。 若要将重新启动管理器合并到现有应用程序，必须将分配`m_dwRestartManagerSupportFlags`主应用程序的构造函数中的相应值。 有关如何使用重新启动管理器的详细信息，请参阅[如何：添加重启管理器支持](../../mfc/how-to-add-restart-manager-support.md)。

## <a name="requirements"></a>要求

**标头：** afxdatarecovery.h

##  <a name="autosavealldocumentinfo"></a>  CDataRecoveryHandler::AutosaveAllDocumentInfo

则自动保存每个文件注册`CDataRecoveryHandler`类。

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>返回值

如果`CDataRecoveryHandler`保存所有文档;如果不保存任何文档，则为 FALSE。

### <a name="remarks"></a>备注

如果没有必须保存的文档，则此方法返回 TRUE。 它还会而不保存任何文档，如果检索，则返回 TRUE`CWinApp`或`CDocManager`的应用程序将生成错误。

若要使用此方法，AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 或 AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL 必须设置`m_dwRestartManagerSupportFlags`。 有关详细信息，请参阅[如何：添加重启管理器支持](../../mfc/how-to-add-restart-manager-support.md)。

##  <a name="autosavedocumentinfo"></a>  CDataRecoveryHandler::AutosaveDocumentInfo

则自动保存指定的文档。

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pDocument*|[in]一个指向`CDocument`保存。|
|*bResetModifiedFlag*|[in]TRUE 表示`CDataRecoveryHandler`认为*pDocument*要修改;FALSE 表示该框架会考虑*pDocument*是未修改。 请参阅备注部分有关效果的此标志的详细信息。|

### <a name="return-value"></a>返回值

如果未设置相应标志为 TRUE 并*pDocument*是一个有效`CDocument`对象。

### <a name="remarks"></a>备注

每个`CDocument`对象具有一个标志，指示是否已更改自上次保存后。 使用[CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified)来确定此标志的状态。 如果`CDocument`自上次保存以来未更改`AutosaveDocumentInfo`删除该文档的任何自动保存文件。 如果文档自上次保存以来已更改，关闭它会提示用户保存文档，再关闭。

> [!NOTE]
>  使用*bResetModifiedFlag*文档的状态更改为未修改可能导致用户丢失未保存的数据。 如果框架认为未修改的文档，则关闭它不提示用户保存。

此方法将引发的异常[ASSERT](diagnostic-services.md#assert)宏如果*pDocument*不是有效`CDocument`对象。

若要使用此方法，AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 或 AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL 必须设置*m_dwRestartManagerSupportFlags*。

##  <a name="cdatarecoveryhandler"></a>  CDataRecoveryHandler::CDataRecoveryHandler

构造 `CDataRecoveryHandler` 对象。

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*dwRestartManagerSupportFlags*|[in]指示支持重新启动管理器的选项。|
|*nAutosaveInterval*|[in]则自动保存间隔时间。 此参数是以毫秒为单位。|

### <a name="remarks"></a>备注

MFC 框架会自动创建`CDataRecoveryHandler`为应用程序时使用的对象**新建项目**向导。 除非自定义数据恢复行为或重新启动管理器时，不应创建`CDataRecoveryHandler`对象。

##  <a name="createdocumentinfo"></a>  CDataRecoveryHandler::CreateDocumentInfo

将文档添加到打开的文档的列表。

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pDocument*|[in]一个指向`CDocument`。 此方法创建的文档信息`CDocument`。|

### <a name="return-value"></a>返回值

默认实现，则返回 TRUE。

### <a name="remarks"></a>备注

此方法检查是否*pDocument*添加文档之前已在文档的列表。 如果*pDocument*是已在列表中，此方法删除自动保存文件与相关联*pDocument*。

若要使用此方法，AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART 或 AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL 必须设置*m_dwRestartManagerSupportFlags*。

##  <a name="deleteallautosavedfiles"></a>  CDataRecoveryHandler::DeleteAllAutosavedFiles

删除所有当前的自动保存文件。

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>返回值

默认实现始终返回 TRUE。

##  <a name="deleteautosavedfile"></a>  CDataRecoveryHandler::DeleteAutosavedFile

删除指定的自动保存文件。

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*strAutosavedFile*|[in]包含自动保存文件名称的字符串。|

### <a name="return-value"></a>返回值

默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

如果此方法不能删除自动保存文件，它将在列表中保存的文件的名称。 析构函数`CDataRecoveryHandler`尝试删除该列表中指定的每个自动保存文件。

##  <a name="generateautosavefilename"></a>  CDataRecoveryHandler::GenerateAutosaveFileName

生成与提供的文档文件名称相关联的自动保存文件的名称。

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>参数

*strDocumentName*<br/>
[in]包含文档名称的字符串。 `GenerateAutosaveFileName` 使用此文档名称来生成相应的自动保存文件名称。

### <a name="return-value"></a>返回值

从生成的自动保存文件名称*strDocumentName*。

### <a name="remarks"></a>备注

每个文档名称具有一对一的映射与自动保存文件的名称。

##  <a name="getautosaveinterval"></a>  CDataRecoveryHandler::GetAutosaveInterval

返回自动保存次尝试之间的间隔。

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>返回值

将尝试自动保存功能之间的毫秒数。

##  <a name="getautosavepath"></a>  CDataRecoveryHandler::GetAutosavePath

返回自动保存文件的路径。

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>返回值

存储自动保存文档的位置。

##  <a name="getdocumentlistname"></a>  CDataRecoveryHandler::GetDocumentListName

检索文档名从`CDocument`对象。

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pDocument*|[in]一个指向`CDocument`。 `GetDocumentListName` 检索文档名从此`CDocument`。|

### <a name="return-value"></a>返回值

中的文档名称*pDocument*。

### <a name="remarks"></a>备注

`CDataRecoveryHandler`将使用文档名称的密钥作为*m_mapDocNameToAutosaveName*， *m_mapDocNameToDocumentPtr*，并且*m_mapDocNameToRestoreBool*。 这些参数启用`CDataRecoveryHandler`监视`CDocument`对象、 自动保存文件名称和自动保存设置。

##  <a name="getnormaldocumenttitle"></a>  CDataRecoveryHandler::GetNormalDocumentTitle

检索指定的文档的普通标题。

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pDocument*|[in]一个指向`CDocument`。|

### <a name="return-value"></a>返回值

正常的标题，为指定的文档的。

### <a name="remarks"></a>备注

正常的标题通常是文档的文档的不带路径的文件名。 这是中的标题**文件名**字段**另存为**对话框。

##  <a name="getrecovereddocumenttitle"></a>  CDataRecoveryHandler::GetRecoveredDocumentTitle

创建并返回已恢复文档的标题。

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>参数

*strDocumentTitle*<br/>
[in]正常的文档的标题。

### <a name="return-value"></a>返回值

恢复后的文档标题。

### <a name="remarks"></a>备注

默认情况下恢复文档的标题是使用正常的标题 **[已恢复]** 追加到它。 已恢复的标题显示给用户时`CDataRecoveryHandler`查询要还原自动保存文档的用户。

##  <a name="getrestartidentifier"></a>  CDataRecoveryHandler::GetRestartIdentifier

检索应用程序的唯一重启标识符。

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>返回值

唯一重启标识符。

### <a name="remarks"></a>备注

重启标识符是唯一的应用程序每次执行。

`CDataRecoveryHandler`将信息存储在注册表中有关当前打开的文档。 当重新启动管理器退出应用程序并重新启动它时，它提供的重启标识符`CDataRecoveryHandler`。 `CDataRecoveryHandler`使用重新启动标识符来检索以前打开的文档的列表。 这使`CDataRecoveryHandler`来尝试找到和还原自动保存文件。

##  <a name="getsavedocumentinfoonidle"></a>  CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

指示是否`CDataRecoveryHandler`自动保存对当前空闲循环。

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>返回值

TRUE 表示`CDataRecoveryHandler`则自动保存在当前的空闲循环;FALSE 表示不是。

##  <a name="getshutdownbyrestartmanager"></a>  CDataRecoveryHandler::GetShutdownByRestartManager

表示重新启动管理器是否导致退出该应用程序。

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>返回值

TRUE 指示重新启动管理器导致应用程序退出;FALSE 表示并未如此。

##  <a name="initialize"></a>  CDataRecoveryHandler::Initialize

初始化 `CDataRecoveryHandler`。

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>返回值

如果初始化成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

初始化过程将加载用于存储在注册表中的自动保存文件的路径。 如果`Initialize`方法找不到此目录或如果路径为 NULL，`Initialize`失败并返回`FALSE`。

使用[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)若要在应用程序初始化后更改自动保存路径`CDataRecoveryHandler`。

`Initialize`方法还可启动一个计时器，以监视发生下一步自动保存。 使用[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)若要在应用程序初始化后更改自动保存间隔`CDataRecoveryHandler`。

##  <a name="queryrestoreautosaveddocuments"></a>  CDataRecoveryHandler::QueryRestoreAutosavedDocuments

向用户显示一个对话框，为每个文档的`CDataRecoveryHandler`自动保存。 对话框中确定用户是否想要还原自动保存文档。

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>备注

如果应用程序是 Unicode，此方法显示[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)给用户。 否则，该框架将使用[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)来查询用户。

之后`QueryRestoreAutosavedDocuments`收集所有响应来自用户，它将信息存储在成员变量*m_mapDocNameToRestoreBool*。 此方法不会还原自动保存文档。

##  <a name="readopendocumentlist"></a>  CDataRecoveryHandler::ReadOpenDocumentList

从注册表加载打开的文档列表。

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>返回值

TRUE 表示`ReadOpenDocumentList`从注册表; 加载至少一个文档的信息FALSE 表示已加载任何文档信息。

### <a name="remarks"></a>备注

此函数从注册表加载打开的文档信息，并将其存储在成员变量*m_mapDocNameToAutosaveName*。

之后`ReadOpenDocumentList`加载的所有数据，它从注册表中删除的文档信息。

##  <a name="removedocumentinfo"></a>  CDataRecoveryHandler::RemoveDocumentInfo

从打开的文档列表中删除所提供的文档。

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pDocument*|[in]指向要删除的文档的指针。|

### <a name="return-value"></a>返回值

则为 TRUE *pDocument*已从列表中; 删除如果出现错误，则为 FALSE。

### <a name="remarks"></a>备注

当用户关闭文档时，框架将使用此方法以从打开的文档的列表中删除它。

如果`RemoveDocumentInfo`找不到*pDocument*在打开的文档列表中，它不执行任何操作，则返回 TRUE。

要使用此方法，必须将设置 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*。

##  <a name="reopenpreviousdocuments"></a>  CDataRecoveryHandler::ReopenPreviousDocuments

打开以前打开的文档。

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>返回值

如果至少一个文档已打开; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法可以打开以前打开的文档的最新存储。 如果不保存文档或自动保存，`ReopenPreviousDocuments`打开该文件类型的模板所基于的空白文档。

要使用此方法，必须将设置 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*。 如果未设置此参数，`ReopenPreviousDocuments`不执行任何操作，返回 FALSE。

如果没有以前打开的文档列表中所存储文档`ReopenPreviousDocuments`不执行任何操作，返回 FALSE。

##  <a name="restoreautosaveddocuments"></a>  CDataRecoveryHandler::RestoreAutosavedDocuments

还原自动保存文档根据用户输入。

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>返回值

如果此方法已成功还原文档，则为 TRUE。

### <a name="remarks"></a>备注

此方法调用[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)来确定记录用户想要还原。 如果用户决定不还原自动保存文档`RestoreAutosavedDocuments`删除自动保存文件。 否则为`RestoreAutosavedDocuments`打开的文档替换自动保存的版本。

若要使用此方法，AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 或 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES 必须设置`m_dwRestartManagerSupportFlags`。

##  <a name="saveopendocumentlist"></a>  CDataRecoveryHandler::SaveOpenDocumentList

将当前打开的文档的列表保存到 Windows 注册表。

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>返回值

如果没有打开的文档保存或已成功保存，则为 TRUE。 如果文档将保存到注册表中，但它们未保存，因为出现错误，则为 FALSE。

### <a name="remarks"></a>备注

重新启动管理器调用`SaveOpenDocumentList`应用程序意外退出或退出以进行升级时。 应用程序重新启动时，它使用[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)来检索打开的文档的列表。

此方法将保存打开的文档列表。 该方法[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)负责将保存在文档中自行。

##  <a name="setautosaveinterval"></a>  CDataRecoveryHandler::SetAutosaveInterval

设置自动保存周期以毫秒为单位之间的时间。

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>参数

*nAutosaveInterval*<br/>
[in]新的自动保存间隔以毫秒为单位。

##  <a name="setautosavepath"></a>  CDataRecoveryHandler::SetAutosavePath

设置自动保存文件的存储位置的目录。

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*strAutosavePath*|[in]存储自动保存文件的路径。|

### <a name="remarks"></a>备注

自动保存目录的更改不会移动当前自动保存文件。

##  <a name="setrestartidentifier"></a>  CDataRecoveryHandler::SetRestartIdentifier

设置的此实例的唯一重启标识符`CDataRecoveryHandler`。

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*strRestartIdentifier*|[in]重新启动管理器唯一标识符。|

### <a name="remarks"></a>备注

有关在注册表中打开的文档的重新启动管理器记录信息。 此信息作为键存储具有唯一的重启标识符。 重启标识符是唯一的应用程序的每个实例，因为应用程序的多个实例可能会意外退出并重新启动管理器可以恢复每个。

##  <a name="setsavedocumentinfoonidle"></a>  CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

集是否`CDataRecoveryHandler`当前空闲周期内将打开的文档信息保存到 Windows 注册表。

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*bSaveOnIdle*|[in]为 TRUE，则将保存在当前的空闲周期内; 文档信息为 FALSE，则不执行存储。|

##  <a name="setshutdownbyrestartmanager"></a>  CDataRecoveryHandler::SetShutdownByRestartManager

设置是否以前退出该应用程序而引起的重新启动管理器。

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*bShutdownByRestartManager*|[in]若要指示重新启动管理器，导致应用程序退出;如果为 FALSE，以指示该应用程序退出的另一个原因。|

### <a name="remarks"></a>备注

该框架的行为与基于上一个退出是否意外或它已启动重新启动管理器以不同方式。

##  <a name="updatedocumentinfo"></a>  CDataRecoveryHandler::UpdateDocumentInfo

由于用户保存它，请更新文档的信息。

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pDocument*|[in]指向已保存的文档的指针。|

### <a name="return-value"></a>返回值

如果此方法删除自动保存文档并更新该文档信息，则为 TRUE如果出现错误，则为 FALSE。

### <a name="remarks"></a>备注

当用户保存文档时，因为不再需要应用程序中删除自动保存文件。 `UpdateDocumentInfo` 通过调用中删除自动保存文件[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)。 `UpdateDocumentInfo` 然后将信息从添加*pDocument*到列表中当前打开文档因为`RemoveDocumentInfo`删除该信息，但已保存文档仍处于打开状态。

要使用此方法，必须将设置 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[如何：添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)
