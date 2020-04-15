---
title: CData恢复处理程序类
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
ms.openlocfilehash: bdfcbea6c345235358384691388afcdbbd2d0a42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321930"
---
# <a name="cdatarecoveryhandler-class"></a>CData恢复处理程序类

如果`CDataRecoveryHandler`应用程序意外退出，自动保存文档并还原它们。

## <a name="syntax"></a>语法

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[C数据恢复处理程序：：C数据恢复处理程序](#cdatarecoveryhandler)|构造 `CDataRecoveryHandler` 对象。|

### <a name="methods"></a>方法

|||
|-|-|
|[CData恢复处理程序：：自动保存所有文档信息](#autosavealldocumentinfo)|自动保存向`CDataRecoveryHandler`类注册的每个文件。|
|[CData恢复处理程序：：自动保存文档信息](#autosavedocumentinfo)|自动保存指定的文档。|
|[CData恢复处理程序：：创建文档信息](#createdocumentinfo)|将文档添加到打开的文档列表中。|
|[CData恢复处理程序：:DeleteAll自动保存文件](#deleteallautosavedfiles)|删除所有当前自动保存的文件。|
|[CData恢复处理程序：:Delete自动保存文件](#deleteautosavedfile)|删除指定的自动保存文件。|
|[CData恢复处理程序：：生成自动保存文件名](#generateautosavefilename)|生成与提供的文档文件名关联的自动保存文件的名称。|
|[CData恢复处理程序：：获取自动保存间隔](#getautosaveinterval)|返回自动保存尝试之间的间隔。|
|[CData恢复处理程序：获取自动保存路径](#getautosavepath)|返回自动保存文件的路径。|
|[CData恢复处理程序：获取文档列表名称](#getdocumentlistname)|从`CDocument`对象检索文档名称。|
|[CData恢复处理程序：：获取正常文档标题](#getnormaldocumenttitle)|检索指定文档的正常标题。|
|[CData恢复处理程序：：获取恢复文档标题](#getrecovereddocumenttitle)|创建并返回恢复的文档的标题。|
|[CData恢复处理程序：：获取重新启动标识符](#getrestartidentifier)|检索应用程序的唯一重新启动标识符。|
|[CData恢复处理程序：：获取保存文档信息在空闲](#getsavedocumentinfoonidle)|指示 是否`CDataRecoveryHandler`对当前空闲环路执行自动保存。|
|[CData恢复处理程序：：获取关闭通过重新启动管理器](#getshutdownbyrestartmanager)|指示重新启动管理器是否导致应用程序退出。|
|[CData恢复处理程序：：初始化](#initialize)|初始化 `CDataRecoveryHandler`。|
|[CData恢复处理程序：：查询还原自动保存的文档](#queryrestoreautosaveddocuments)|为用户显示自动保存的每个文档的`CDataRecoveryHandler`对话框。 该对话框确定用户是否要还原自动保存的文档。|
|[CData恢复处理程序：：阅读打开文档列表](#readopendocumentlist)|从注册表加载打开的文档列表。|
|[CData恢复处理程序：：删除文档信息](#removedocumentinfo)|从打开的文档列表中删除提供的文档。|
|[CData恢复处理程序：：重新打开以前的文档](#reopenpreviousdocuments)|打开以前打开的文档。|
|[CData恢复处理程序：：还原自动保存的文档](#restoreautosaveddocuments)|根据用户输入还原自动保存的文档。|
|[CData恢复处理程序：：保存打开文档列表](#saveopendocumentlist)|将当前打开的文档列表保存到 Windows 注册表。|
|[CData恢复处理程序：：设置自动保存间隔](#setautosaveinterval)|设置自动保存周期之间的时间（以毫秒为单位）。|
|[CData恢复处理程序：：设置自动保存路径](#setautosavepath)|设置存储自动保存文件的目录。|
|[CData恢复处理程序：：设置重新启动标识符](#setrestartidentifier)|设置 此实例的唯一重新启动标识符`CDataRecoveryHandler`。|
|[CData恢复处理程序：：设置保存文档信息](#setsavedocumentinfoonidle)|设置 是否`CDataRecoveryHandler`在当前空闲周期内将打开的文档信息保存到 Windows 注册表。|
|[CData恢复处理程序：：设置关闭通过重新启动管理器](#setshutdownbyrestartmanager)|设置应用程序的上一个退出是否由重新启动管理器引起。|
|[CData恢复处理程序：：更新文档信息](#updatedocumentinfo)|更新文档的信息，因为用户保存了它。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|m_bRestoringPreviousOpenDocs|指示数据恢复处理程序是否重新打开以前打开的文档。|
|m_bSaveDocumentInfoOnIdle|指示数据恢复处理程序是否自动保存下一个空闲循环上的文档。|
|m_bShutdownByRestartManager|指示重新启动管理器是否导致应用程序退出。|
|m_dwRestartManagerSupportFlags|指示重新启动管理器为应用程序提供的支持的标志。|
|m_lstAutosavesToDelete|关闭原始文档时未删除的自动保存文件的列表。 当应用程序退出时，重新启动管理器将重试删除文件。|
|m_mapDocNameToAutosaveName|文档名称的映射到自动保存的文件名。|
|m_mapDocNameToDocumentPtr|文档名称的映射到[CDocument](../../mfc/reference/cdocument-class.md)指针。|
|m_mapDocNameToRestoreBool|文档名称的映射到布尔参数，指示是否还原自动保存的文档。|
|m_mapDocumentPtrToDocName|指向文档名称的`CDocument`指针的映射。|
|m_mapDocumentPtrToDocTitle|指向文档标题的`CDocument`指针的映射。 这些标题用于保存文件。|
|m_nAutosaveInterval|自动保存之间的时间（以毫秒为单位）。|
|m_nTimerID|自动保存计时器的标识符。|
|m_strAutosavePath|自动保存的文档存储的位置。|
|m_strRestartIdentifier|重新启动管理器的 GUID 的字符串表示形式。|

## <a name="remarks"></a>备注

重新启动管理器使用 类`CDataRecoveryHandler`跟踪所有打开的文档，并在必要时自动保存它们。 要启用自动保存，请使用[CData 恢复处理程序：：设置文档信息系统](#setsavedocumentinfoonidle)方法。 此方法指示 在`CDataRecoveryHandler`下一个空闲循环上执行自动保存。 重新启动管理器在`SetSaveDocumentInfoOnIdle``CDataRecoveryHandler`应执行自动保存时调用。

类的所有方法都是虚拟的`CDataRecoveryHandler`。 重写此类中的方法以创建自己的自定义数据恢复处理程序。 除非创建自己的数据恢复处理程序或重新启动管理器，否则不要实例化 CDataRecoveryHandler。 [CWinApp 类](../../mfc/reference/cwinapp-class.md)根据需要创建`CDataRecoveryHandler`对象。

在使用`CDataRecoveryHandler`对象之前，必须调用[CDataRecoveryHandler：：：初始化](#initialize)。

由于`CDataRecoveryHandler`类与重新启动管理器紧密连接，`CDataRecoveryHandler`因此取决于全局参数`m_dwRestartManagerSupportFlags`。 此参数确定重新启动管理器具有哪些权限，以及它如何与应用程序交互。 要将重新启动管理器合并到现有应用程序中，您必须在主应用程序的构造`m_dwRestartManagerSupportFlags`函数中分配适当的值。 有关如何使用重新启动管理器的详细信息，请参阅[如何：添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)。

## <a name="requirements"></a>要求

**标题：** afxdata 恢复.h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a>CData恢复处理程序：：自动保存所有文档信息

自动保存向`CDataRecoveryHandler`类注册的每个文件。

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>返回值

如果`CDataRecoveryHandler`保存了所有文档，则为 TRUE;如果未保存任何文档，则 FALSE。

### <a name="remarks"></a>备注

如果没有必须保存的文档，此方法将返回 TRUE。 如果检索 或`CWinApp``CDocManager`应用程序生成错误，它还返回 TRUE 而不保存任何文档。

要使用此方法，必须在 中`m_dwRestartManagerSupportFlags`设置AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART或AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL。 有关详细信息，请参阅[如何：添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)。

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a>CData恢复处理程序：：自动保存文档信息

自动保存指定的文档。

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pDocument*|[在]要保存的`CDocument`指针。|
|*bReset 修改的标记*|[在]TRUE 表示要`CDataRecoveryHandler`修改的考虑*pDocument;* FALSE 表示框架认为*pDocument*未修改。 有关此标志的效果的详细信息，请参阅备注部分。|

### <a name="return-value"></a>返回值

如果设置了适当的标志，并且*pDocument*是有效的`CDocument`对象，则为 TRUE。

### <a name="remarks"></a>备注

每个`CDocument`对象都有一个标志，指示自上次保存以来是否已更改。 使用[CDocument：：修改](../../mfc/reference/cdocument-class.md#ismodified)以确定此标志的状态。 如果`CDocument`自上次保存以来未更改 ，请`AutosaveDocumentInfo`删除该文档的任何自动保存文件。 如果文档自上次保存以来已更改，则关闭文档会提示用户在关闭之前保存该文档。

> [!NOTE]
> 使用*bReset 修改标志*将文档的状态更改为未修改可能会导致用户丢失未保存的数据。 如果框架认为文档未修改，则关闭它不会提示用户保存。

如果*pDocument*不是有效`CDocument`对象，则此方法会向[ASSERT](diagnostic-services.md#assert)宏引发异常。

要使用此方法，必须在*m_dwRestartManagerSupportFlags*中设置AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART或AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL。

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a>C数据恢复处理程序：：C数据恢复处理程序

构造 `CDataRecoveryHandler` 对象。

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*dwRestartManagerSupportFlags*|[在]指示支持重新启动管理器的哪些选项。|
|*n 自动保存间隔*|[在]自动保存之间的时间。 此参数以毫秒为单位。|

### <a name="remarks"></a>备注

当您使用 **"新项目"** 向导时`CDataRecoveryHandler`，MFC 框架会自动为应用程序创建一个对象。 除非要自定义数据恢复行为或重新启动管理器，否则不应创建`CDataRecoveryHandler`对象。

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a>CData恢复处理程序：：创建文档信息

将文档添加到打开的文档列表中。

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pDocument*|[在]指向 的`CDocument`指针。 此方法为此`CDocument`创建文档信息。|

### <a name="return-value"></a>返回值

默认实现返回 TRUE。

### <a name="remarks"></a>备注

此方法在添加文档之前检查*pDocument*是否已在文档列表中。 如果*pDocument*已在列表中，则此方法将删除与*pDocument*关联的自动保存文件。

要使用此方法，必须在*m_dwRestartManagerSupportFlags*中设置AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART或AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL。

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a>CData恢复处理程序：:DeleteAll自动保存文件

删除所有当前自动保存的文件。

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>返回值

默认实现始终返回 TRUE。

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a>CData恢复处理程序：:Delete自动保存文件

删除指定的自动保存文件。

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*strAuto保存文件*|[在]包含自动保存的文件名的字符串。|

### <a name="return-value"></a>返回值

默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

如果此方法无法删除自动保存的文件，它将文件的名称保存在列表中。 的析构函数`CDataRecoveryHandler`尝试删除该列表中指定的每个自动保存的文件。

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a>CData恢复处理程序：：生成自动保存文件名

生成与提供的文档文件名关联的自动保存文件的名称。

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>参数

*strDocument名称*<br/>
[在]包含文档名称的字符串。 `GenerateAutosaveFileName`使用此文档名称生成相应的自动保存文件名。

### <a name="return-value"></a>返回值

从*strDocumentName*生成的自动保存文件名。

### <a name="remarks"></a>备注

每个文档名称都有一个带有自动保存文件名的一对一映射。

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a>CData恢复处理程序：：获取自动保存间隔

返回自动保存尝试之间的间隔。

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>返回值

自动保存尝试之间的毫秒数。

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a>CData恢复处理程序：获取自动保存路径

返回自动保存文件的路径。

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>返回值

自动保存的文档存储的位置。

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a>CData恢复处理程序：获取文档列表名称

从`CDocument`对象检索文档名称。

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pDocument*|[在]指向 的`CDocument`指针。 `GetDocumentListName`从 中`CDocument`检索文档名称。|

### <a name="return-value"></a>返回值

*pDocument*中的文档名称。

### <a name="remarks"></a>备注

使用`CDataRecoveryHandler`文档名称作为*m_mapDocNameToAutosaveName、m_mapDocNameToDocumentPtr*和*m_mapDocNameToDocumentPtr**m_mapDocNameToRestoreBool*中的键。 这些参数允许`CDataRecoveryHandler`监视`CDocument`对象、自动保存文件名和自动保存设置。

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a>CData恢复处理程序：：获取正常文档标题

检索指定文档的正常标题。

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pDocument*|[在]指向 的`CDocument`指针。|

### <a name="return-value"></a>返回值

指定文档的正常标题。

### <a name="remarks"></a>备注

文档的正常标题通常是没有路径的文档的文件名。 这是"**保存为"** 对话框**的文件名**字段中的标题。

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a>CData恢复处理程序：：获取恢复文档标题

创建并返回恢复的文档的标题。

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>参数

*strDocumentTitle*<br/>
[在]文档的正常标题。

### <a name="return-value"></a>返回值

恢复的文档标题。

### <a name="remarks"></a>备注

默认情况下，文档的恢复标题是附加 **[恢复]** 的正常标题。 当用户查询还原自动保存的文档时，`CDataRecoveryHandler`将向用户显示恢复的标题。

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a>CData恢复处理程序：：获取重新启动标识符

检索应用程序的唯一重新启动标识符。

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>返回值

唯一的重新启动标识符。

### <a name="remarks"></a>备注

重新启动标识符对于应用程序的每次执行都是唯一的。

在`CDataRecoveryHandler`注册表中存储有关当前打开的文档的信息。 当重新启动管理器退出应用程序并重新启动应用程序时，它将重新启动标识符提供到`CDataRecoveryHandler`。 `CDataRecoveryHandler`使用重新启动标识符检索以前打开的文档的列表。 这使 可以`CDataRecoveryHandler`尝试查找和还原自动保存的文件。

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a>CData恢复处理程序：：获取保存文档信息在空闲

指示 是否`CDataRecoveryHandler`对当前空闲环路执行自动保存。

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>返回值

TRUE 表示`CDataRecoveryHandler`当前空闲环路上的自动保存;FALSE 表示它不。

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a>CData恢复处理程序：：获取关闭通过重新启动管理器

指示重新启动管理器是否导致应用程序退出。

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>返回值

TRUE 表示重新启动管理器导致应用程序退出;FALSE 表示它没有。

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a>CData恢复处理程序：：初始化

初始化 `CDataRecoveryHandler`。

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>返回值

如果初始化成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

初始化过程加载用于从注册表存储自动保存文件的路径。 如果`Initialize`方法找不到此目录或路径为 NULL，则`Initialize`失败并返回`FALSE`。

使用[CData 恢复处理程序：：设置自动保存路径](#setautosavepath)，在应用程序初始化 后更改自动保存路径`CDataRecoveryHandler`。

该方法`Initialize`还会启动计时器来监视下一次自动保存时的情况。 使用[CData 恢复处理程序：：设置自动保存间隔](#setautosaveinterval)，在应用程序初始化 后更改自动保存间隔`CDataRecoveryHandler`。

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a>CData恢复处理程序：：查询还原自动保存的文档

为用户显示自动保存的每个文档的`CDataRecoveryHandler`对话框。 该对话框确定用户是否要还原自动保存的文档。

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>备注

如果应用程序为 Unicode，则此方法向用户显示[CTaskDialog。](../../mfc/reference/ctaskdialog-class.md) 否则，框架将使用[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)查询用户。

从`QueryRestoreAutosavedDocuments`用户收集所有响应后，它将信息存储在成员变量*m_mapDocNameToRestoreBool*。 此方法不还原自动保存的文档。

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a>CData恢复处理程序：：阅读打开文档列表

从注册表加载打开的文档列表。

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>返回值

TRUE 表示`ReadOpenDocumentList`从注册表中加载了至少一个文档的信息;FALSE 表示未加载任何文档信息。

### <a name="remarks"></a>备注

此函数从注册表加载打开的文档信息，并将其存储在成员变量*m_mapDocNameToAutosaveName*。

加载`ReadOpenDocumentList`所有数据后，它会从注册表中删除文档信息。

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a>CData恢复处理程序：：删除文档信息

从打开的文档列表中删除提供的文档。

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pDocument*|[在]指向要删除的文档的指针。|

### <a name="return-value"></a>返回值

如果*pDocument*从列表中删除，则为 TRUE;如果发生错误，则 FALSE。

### <a name="remarks"></a>备注

当用户关闭文档时，框架使用此方法将其从打开的文档列表中删除。

如果在`RemoveDocumentInfo`打开的文档列表中找不到*pDocument，* 则它不执行任何操作并返回 TRUE。

要使用此方法，必须在*m_dwRestartManagerSupportFlags*中设置AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES。

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a>CData恢复处理程序：：重新打开以前的文档

打开以前打开的文档。

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>返回值

如果至少打开一个文档，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

此方法将打开以前打开的文档的最新保存。 如果未保存或自动保存文档，`ReopenPreviousDocuments`则基于该文件类型的模板打开空白文档。

要使用此方法，必须在*m_dwRestartManagerSupportFlags*中设置AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES。 如果未设置此参数，`ReopenPreviousDocuments`则不执行任何操作并返回 FALSE。

如果以前打开的文档列表中没有存储任何文档，`ReopenPreviousDocuments`则不执行任何操作并返回 FALSE。

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a>CData恢复处理程序：：还原自动保存的文档

根据用户输入还原自动保存的文档。

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>返回值

如果此方法成功还原文档，则为 TRUE。

### <a name="remarks"></a>备注

此方法调用[CDataRecoveryHandler：：查询还原自动保存的文档](#queryrestoreautosaveddocuments)，以确定用户要还原的文档。 如果用户决定不还原自动保存的文档，`RestoreAutosavedDocuments`请删除自动保存文件。 否则，`RestoreAutosavedDocuments`将打开的文档替换为自动保存的版本。

要使用此方法，必须在 中`m_dwRestartManagerSupportFlags`设置AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES或AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES。

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a>CData恢复处理程序：：保存打开文档列表

将当前打开的文档列表保存到 Windows 注册表。

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>返回值

如果没有要保存的打开的文档，或者它们已成功保存，则为 TRUE。 如果有要保存到注册表的文档，但由于发生错误而未保存文档，则 FALSE。

### <a name="remarks"></a>备注

重新启动管理器在应用程序`SaveOpenDocumentList`意外退出或退出升级时调用。 当应用程序重新启动时，它使用[CDataRecoveryHandler：：读取 OpenDocumentList](#readopendocumentlist)检索打开的文档列表。

此方法仅保存打开的文档列表。 方法[CDataRecoveryHandler：：自动保存文档信息](#autosavedocumentinfo)负责保存文档本身。

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a>CData恢复处理程序：：设置自动保存间隔

设置自动保存周期之间的时间（以毫秒为单位）。

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>参数

*n 自动保存间隔*<br/>
[在]新的自动保存间隔（以毫秒为单位）。

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a>CData恢复处理程序：：设置自动保存路径

设置存储自动保存文件的目录。

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*strAutosavePath*|[在]存储自动保存文件的路径。|

### <a name="remarks"></a>备注

更改自动保存目录不会移动当前自动保存的文件。

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a>CData恢复处理程序：：设置重新启动标识符

设置 此实例的唯一重新启动标识符`CDataRecoveryHandler`。

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*strRestart标识符*|[在]重新启动管理器的唯一标识符。|

### <a name="remarks"></a>备注

重新启动管理器记录有关注册表中打开的文档的信息。 此信息以唯一的重新启动标识符作为密钥存储。 由于重新启动标识符对于应用程序的每个实例都是唯一的，因此应用程序的多个实例可能会意外退出，重新启动管理器可以恢复每个实例。

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a>CData恢复处理程序：：设置保存文档信息

设置 是否`CDataRecoveryHandler`在当前空闲周期内将打开的文档信息保存到 Windows 注册表。

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*bSaveonidle*|[在]TRUE 以保存当前空闲周期中的文档信息;FALSE 不执行保存。|

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a>CData恢复处理程序：：设置关闭通过重新启动管理器

设置应用程序的上一个退出是否由重新启动管理器引起。

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*b 关闭由重新启动管理器*|[在]TRUE 指示重新启动管理器导致应用程序退出;FALSE 以指示应用程序出于其他原因退出。|

### <a name="remarks"></a>备注

框架的行为方式因上一个退出是否意外或是否由重新启动管理器启动而不同。

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a>CData恢复处理程序：：更新文档信息

更新文档的信息，因为用户保存了它。

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pDocument*|[在]指向已保存文档的指针。|

### <a name="return-value"></a>返回值

如果此方法删除了自动保存的文档并更新了文档信息，则为 TRUE;如果发生错误，则 FALSE。

### <a name="remarks"></a>备注

当用户保存文档时，应用程序将删除自动保存的文件，因为它不再需要它。 `UpdateDocumentInfo`通过调用[CDataRecoveryHandler 删除自动保存的文件：：删除文档信息](#removedocumentinfo)。 `UpdateDocumentInfo`然后将*pDocument*中的信息添加到当前打开的文档列表中，因为`RemoveDocumentInfo`删除该信息，但保存的文档仍处于打开状态。

要使用此方法，必须在*m_dwRestartManagerSupportFlags*中设置AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[如何：添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)
