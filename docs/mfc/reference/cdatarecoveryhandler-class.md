---
title: CDataRecoveryHandler 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73596ec5ec9f17b2007a6816bbe0ab90b1463430
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957099"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler 类
`CDataRecoveryHandler`自动保存文档并将其还原，如果应用程序意外退出。  
  
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
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|每个文件中注册的自动保存`CDataRecoveryHandler`类。|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|将指定的文档。|  
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|将文档添加到打开的文档的列表。|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|删除当前的所有自动保存文件。|  
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|删除指定的自动保存的文件。|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|生成与提供的文档文件名称关联的自动保存文件的名称。|  
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|返回自动保存尝试之间的间隔。|  
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|返回自动保存文件的路径。|  
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|检索的文档名称`CDocument`对象。|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|检索指定的文档的正常标题。|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|创建并返回已恢复的文档的标题。|  
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|检索应用程序的唯一的重新启动标识符。|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|指示是否`CDataRecoveryHandler`当前空闲循环中执行了自动保存。|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|指示是否重新启动管理器将导致退出该应用程序。|  
|[CDataRecoveryHandler::Initialize](#initialize)|初始化 `CDataRecoveryHandler`。|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|向用户显示一个对话框，为每个文档`CDataRecoveryHandler`自动保存。 对话框中确定用户是否想要还原自动保存文档。|  
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|从注册表加载打开的文档列表。|  
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|从打开的文档列表中移除所提供的文档。|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|将打开以前打开的文档。|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|还原根据用户输入的自动保存文档。|  
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|将打开的文档的当前列表保存到 Windows 注册表。|  
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|设置以毫秒为单位的自动保存周期之间的时间。|  
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|设置存储自动保存文件的目录。|  
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|设置的此实例的唯一的重新启动标识符`CDataRecoveryHandler`。|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|集是否`CDataRecoveryHandler`在当前的空闲周期内将打开的文档信息保存到 Windows 注册表。|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|设置是否以前退出应用程序而引起的重新启动管理器。|  
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|因为用户将其保存，请更新文档的信息。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|m_bRestoringPreviousOpenDocs|指示是否数据恢复处理程序重新打开以前打开的文档。|  
|m_bSaveDocumentInfoOnIdle|指示是否将数据恢复处理程序自动保存文档在下一步的空闲循环。|  
|m_bShutdownByRestartManager|指示是否重新启动管理器将导致退出该应用程序。|  
|m_dwRestartManagerSupportFlags|标志，指示什么支持重新启动管理器提供应用程序。|  
|m_lstAutosavesToDelete|未删除原始文档已关闭时自动保存文件的列表。 应用程序退出时，重新启动管理器重新尝试删除文件。|  
|m_mapDocNameToAutosaveName|自动保存文件名称的文档名称的映射。|  
|m_mapDocNameToDocumentPtr|映射到的文档名称[CDocument](../../mfc/reference/cdocument-class.md)指针。|  
|m_mapDocNameToRestoreBool|一个布尔型参数，该值指示是否将自动保存文档还原到的文档名称的映射。|  
|m_mapDocumentPtrToDocName|映射`CDocument`指向文档名称。|  
|m_mapDocumentPtrToDocTitle|映射`CDocument`指向文档标题。 这些标题用于保存文件。|  
|m_nAutosaveInterval|以毫秒为单位之间自动保存的时间。|  
|m_nTimerID|自动保存计时器标识符。|  
|m_strAutosavePath|存储自动保存文档的位置。|  
|m_strRestartIdentifier|重新启动管理器 GUID 的字符串表示形式。|  
  
## <a name="remarks"></a>备注  
 重新启动管理器使用`CDataRecoveryHandler`类需要跟踪的所有打开的文档和自动保存到它们根据需要。 若要启用自动保存，请使用[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)方法。 此方法将定向`CDataRecoveryHandler`在下一步的空闲循环上执行了自动保存。 重新启动管理器调用`SetSaveDocumentInfoOnIdle`时`CDataRecoveryHandler`应执行了自动保存。  
  
 所有的方法`CDataRecoveryHandler`类都是虚拟的。 重写此类，以创建你自己的自定义数据恢复处理程序中的方法。 除非创建你自己的数据恢复处理程序或重新启动管理器，否则不要实例化 CDataRecoveryHandler。 [CWinApp 类](../../mfc/reference/cwinapp-class.md)创建`CDataRecoveryHandler`对象在需要时。  
  
 你可以使用之前`CDataRecoveryHandler`对象，必须调用[CDataRecoveryHandler::Initialize](#initialize)。  
  
 因为`CDataRecoveryHandler`类紧密关联到重新启动管理器，`CDataRecoveryHandler`取决于全局参数`m_dwRestartManagerSupportFlags`。 此参数确定的重新启动管理器具有哪些权限以及它如何与你的应用程序交互。 若要将重新启动管理器合并到现有应用程序，你必须分配`m_dwRestartManagerSupportFlags`主应用程序的构造函数中的相应值。 有关如何使用重新启动管理器的详细信息，请参阅[如何： 添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** afxdatarecovery.h  
  
##  <a name="autosavealldocumentinfo"></a>  CDataRecoveryHandler::AutosaveAllDocumentInfo  
 每个文件中注册的自动保存`CDataRecoveryHandler`类。  
  
```  
virtual BOOL AutosaveAllDocumentInfo();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果`CDataRecoveryHandler`已保存的所有文档;`FALSE`如果不保存任何文档。  
  
### <a name="remarks"></a>备注  
 此方法返回`TRUE`如果不有任何必须保存的文档。 它还返回`TRUE`而不保存任何文档，如果检索`CWinApp`或`CDocManager`为应用程序生成错误。  
  
 若要使用此方法，这两个`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`或`AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL`必须设置`m_dwRestartManagerSupportFlags`。 请参阅[m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)有关详细信息。  
  
##  <a name="autosavedocumentinfo"></a>  CDataRecoveryHandler::AutosaveDocumentInfo  
 将指定的文档。  
  
```  
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,  
    BOOL bResetModifiedFlag = TRUE);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*pDocument*|指向的指针`CDocument`保存。|  
|[in]*bResetModifiedFlag*|`TRUE` 指示`CDataRecoveryHandler`认为*pDocument*要修改;`FALSE`指示框架会考虑*pDocument*以保持不变。 请参阅影响此标志的详细信息备注部分。|  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果设置了适当的标志和*pDocument*是一个有效`CDocument`对象。  
  
### <a name="remarks"></a>备注  
 每个`CDocument`对象具有一个标志，指示是否已更改自上次保存后。 使用[CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified)以确定此标志的状态。 如果`CDocument`自上次保存后, 未更改`AutosaveDocumentInfo`删除该文档的任何自动保存文件。 如果自上次保存以来已更改文档，关闭它提示用户将文档保存到在关闭之前。  
  
> [!NOTE]
>  使用*bResetModifiedFlag*文档的状态更改为未修改可能导致用户丢失未保存的数据。 如果框架认为文档不做任何修改，则关闭它不提示用户将保存。  
  
 此方法将引发的异常[断言](diagnostic-services.md#assert)宏如果*pDocument*不是有效`CDocument`对象。  
  
 若要使用此方法，这两个`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`或`AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL`必须设置*m_dwRestartManagerSupportFlags*。   
  
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
|[in]*dwRestartManagerSupportFlags*|指示支持哪些选项重新启动管理器。|  
|[in]*nAutosaveInterval*|自动保存之间的时间。 此参数是以毫秒为单位。|  
  
### <a name="remarks"></a>备注  
 MFC 框架会自动创建`CDataRecoveryHandler`当你使用的应用程序的对象**新项目**向导。 除非自定义数据恢复行为或重新启动管理器时，不应创建`CDataRecoveryHandler`对象。  
  
  
##  <a name="createdocumentinfo"></a>  CDataRecoveryHandler::CreateDocumentInfo  
 将文档添加到打开的文档的列表。  
  
```  
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*pDocument*|指向的指针`CDocument`。 此方法创建此文档信息`CDocument`。|  
  
### <a name="return-value"></a>返回值  
 默认实现返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 此方法检查如果*pDocument*文档之前已在文档的列表。 如果*pDocument*已在列表中，此方法与关联的自动保存文件的删除*pDocument*。  
  
 若要使用此方法，这两个`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`或`AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL`必须设置*m_dwRestartManagerSupportFlags*。 
  
##  <a name="deleteallautosavedfiles"></a>  CDataRecoveryHandler::DeleteAllAutosavedFiles  
 删除当前的所有自动保存文件。  
  
```  
virtual BOOL DeleteAllAutosavedFiles();
```  
  
### <a name="return-value"></a>返回值  
 默认实现始终返回 `TRUE`。  
  
##  <a name="deleteautosavedfile"></a>  CDataRecoveryHandler::DeleteAutosavedFile  
 删除指定的自动保存的文件。  
  
```  
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*strAutosavedFile*|包含自动保存文件名称的字符串。|  
  
### <a name="return-value"></a>返回值  
 默认实现始终返回`TRUE`。  
  
### <a name="remarks"></a>备注  
 如果此方法不能删除自动保存文件，它将在列表中保存文件的名称。 析构函数`CDataRecoveryHandler`尝试删除该列表中指定每个自动保存文件。  
  
##  <a name="generateautosavefilename"></a>  CDataRecoveryHandler::GenerateAutosaveFileName  
 生成与提供的文档文件名称关联的自动保存文件的名称。  
  
```  
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;  
```  
  
### <a name="parameters"></a>参数  
 [in]*strDocumentName*  
 包含文档名称的字符串。 `GenerateAutosaveFileName` 使用此文档名称来生成相应的自动保存文件名称。  
  
### <a name="return-value"></a>返回值  
 从生成的自动保存文件名称*strDocumentName*。  
  
### <a name="remarks"></a>备注  
 每个文档名称具有自动保存文件同名的一对一映射。  
  
##  <a name="getautosaveinterval"></a>  CDataRecoveryHandler::GetAutosaveInterval  
 返回自动保存尝试之间的间隔。  
  
```  
virtual int GetAutosaveInterval() const;  
```  
  
### <a name="return-value"></a>返回值  
 尝试之间自动保存的毫秒数。  
  
##  <a name="getautosavepath"></a>  CDataRecoveryHandler::GetAutosavePath  
 返回自动保存文件的路径。  
  
```  
virtual CString GetAutosavePath() const;  
```  
  
### <a name="return-value"></a>返回值  
 存储自动保存文档的位置。  
  
##  <a name="getdocumentlistname"></a>  CDataRecoveryHandler::GetDocumentListName  
 检索的文档名称`CDocument`对象。  
  
```  
virtual CString GetDocumentListName(CDocument* pDocument) const;  
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*pDocument*|指向的指针`CDocument`。 `GetDocumentListName` 从此检索的文档名称`CDocument`。|  
  
### <a name="return-value"></a>返回值  
 中的文档名称*pDocument*。  
  
### <a name="remarks"></a>备注  
 `CDataRecoveryHandler`作为键中使用的文档名称*m_mapDocNameToAutosaveName*， *m_mapDocNameToDocumentPtr*，和*m_mapDocNameToRestoreBool*。 这些参数启用`CDataRecoveryHandler`监视`CDocument`对象、 自动保存文件名称和自动保存设置。  
  
##  <a name="getnormaldocumenttitle"></a>  CDataRecoveryHandler::GetNormalDocumentTitle  
 检索指定的文档的正常标题。  
  
```  
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*pDocument*|指向的指针`CDocument`。|  
  
### <a name="return-value"></a>返回值  
 指定的文档普通标题。  
  
### <a name="remarks"></a>备注  
 正常的标题通常是文档的文档的不含路径的文件名称。 这是中的标题**文件名**字段**另存为**对话框。  
  
##  <a name="getrecovereddocumenttitle"></a>  CDataRecoveryHandler::GetRecoveredDocumentTitle  
 创建并返回已恢复的文档的标题。  
  
```  
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;  
```  
  
### <a name="parameters"></a>参数  
 [in]*strDocumentTitle*  
 正常的文档的标题。  
  
### <a name="return-value"></a>返回值  
 恢复后的文档标题中。  
  
### <a name="remarks"></a>备注  
 默认情况下，已恢复的文档的标题是正常的标题与 **[恢复]** 追加到它。 向用户显示的已恢复的标题时`CDataRecoveryHandler`查询要还原自动保存文档的用户。  
  
##  <a name="getrestartidentifier"></a>  CDataRecoveryHandler::GetRestartIdentifier  
 检索应用程序的唯一的重新启动标识符。  
  
```  
virtual CString GetRestartIdentifier() const;  
```  
  
### <a name="return-value"></a>返回值  
 唯一，则将重新启动标识符。  
  
### <a name="remarks"></a>备注  
 重新启动标识符是唯一的每次执行的应用程序。  
  
 `CDataRecoveryHandler`将信息存储在注册表中有关当前打开的文档。 当重新启动管理器退出应用程序，并重新启动它时，它会提供到的重启标识符`CDataRecoveryHandler`。 `CDataRecoveryHandler`使用重新启动标识符来检索以前打开的文档的列表。 这使`CDataRecoveryHandler`尝试查找并还原自动保存文件。  
  
##  <a name="getsavedocumentinfoonidle"></a>  CDataRecoveryHandler::GetSaveDocumentInfoOnIdle  
 指示是否`CDataRecoveryHandler`当前空闲循环中执行了自动保存。  
  
```  
virtual BOOL GetSaveDocumentInfoOnIdle() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 指示`CDataRecoveryHandler`自动保存当前的空闲循环;`FALSE`表明它没有。  
  
##  <a name="getshutdownbyrestartmanager"></a>  CDataRecoveryHandler::GetShutdownByRestartManager  
 指示是否重新启动管理器将导致退出该应用程序。  
  
```  
virtual BOOL GetShutdownByRestartManager() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 指示重新启动管理器导致应用程序退出;`FALSE`指示未能。  
  
##  <a name="initialize"></a>  CDataRecoveryHandler::Initialize  
 初始化 `CDataRecoveryHandler`。  
  
```  
virtual BOOL Initialize();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果初始化成功;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 初始化过程加载用于存储从注册表的自动保存文件的路径。 如果`Initialize`方法找不到此目录或如果路径是`NULL`，`Initialize`将失败并返回`FALSE`。  
  
 使用[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)若要更改自动保存路径后你的应用程序初始化, `CDataRecoveryHandler`。  
  
 `Initialize`方法也会启动一个计时器，以监视发生下一步自动保存。 使用[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)要更改自动保存间隔，在应用程序初始化后`CDataRecoveryHandler`。  
  
##  <a name="queryrestoreautosaveddocuments"></a>  CDataRecoveryHandler::QueryRestoreAutosavedDocuments  
 向用户显示一个对话框，为每个文档`CDataRecoveryHandler`自动保存。 对话框中确定用户是否想要还原自动保存文档。  
  
```  
virtual void QueryRestoreAutosavedDocuments();
```  
  
### <a name="remarks"></a>备注  
 如果你的应用程序采用 unicode 编码，此方法会显示[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)给用户。 否则，框架将使用[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)来查询用户。  
  
 后`QueryRestoreAutosavedDocuments`收集所有响应来自用户，它将信息存储在成员变量*m_mapDocNameToRestoreBool*。 此方法不会还原自动保存文档。  
  
##  <a name="readopendocumentlist"></a>  CDataRecoveryHandler::ReadOpenDocumentList  
 从注册表加载打开的文档列表。  
  
```  
virtual BOOL ReadOpenDocumentList();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 指示`ReadOpenDocumentList`从注册表; 加载至少一个文档的信息`FALSE`指示不加载任何文档信息。  
  
### <a name="remarks"></a>备注  
 此函数从注册表加载打开的文档信息，并将其存储在成员变量*m_mapDocNameToAutosaveName*。  
  
 后`ReadOpenDocumentList`加载所有数据，它从注册表中删除文档信息。  
  
##  <a name="removedocumentinfo"></a>  CDataRecoveryHandler::RemoveDocumentInfo  
 从打开的文档列表中移除所提供的文档。  
  
```  
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*pDocument*|指向要删除的文档的指针。|  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果*pDocument*已从列表中; 中删除`FALSE`如果发生错误。  
  
### <a name="remarks"></a>备注  
 当用户关闭文档时，框架将使用此方法来从打开的文档的列表中删除它。  
  
 如果`RemoveDocumentInfo`找不到*pDocument*在打开的文档列表中，它不执行任何操作并返回`TRUE`。  
  
 若要使用此方法，`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`必须设置*m_dwRestartManagerSupportFlags*。   
  
##  <a name="reopenpreviousdocuments"></a>  CDataRecoveryHandler::ReopenPreviousDocuments  
 将打开以前打开的文档。  
  
```  
virtual BOOL ReopenPreviousDocuments();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果打开至少一个文档;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法打开以前打开的文档的最新存储。 如果未保存文档或自动保存，`ReopenPreviousDocuments`打开基于该文件类型的模板的空白文档。  
  
 若要使用此方法，`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`必须设置*m_dwRestartManagerSupportFlags*。 如果未设置此参数，`ReopenPreviousDocuments`不执行任何操作并返回`FALSE`。  
  
 如果没有以前打开的文档列表中存储文档`ReopenPreviousDocuments`不执行任何操作并返回`FALSE`。  
  
##  <a name="restoreautosaveddocuments"></a>  CDataRecoveryHandler::RestoreAutosavedDocuments  
 还原根据用户输入的自动保存文档。  
  
```  
virtual BOOL RestoreAutosavedDocuments();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法已成功还原文档。  
  
### <a name="remarks"></a>备注  
 此方法调用[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)以确定该文档用户想要还原。 如果用户决定不恢复自动保存的文档，`RestoreAutosavedDocuments`删除自动保存文件。 否则为`RestoreAutosavedDocuments`打开的文档替换自动保存的版本。  
  
 若要使用此方法，这两个`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`或`AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`必须设置`m_dwRestartManagerSupportFlags`。   
  
##  <a name="saveopendocumentlist"></a>  CDataRecoveryHandler::SaveOpenDocumentList  
 将打开的文档的当前列表保存到 Windows 注册表。  
  
```  
virtual BOOL SaveOpenDocumentList();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果没有任何打开的文档，以保存，或它们已成功保存。 `FALSE` 如果要将保存到注册表中，文档，但它们未保存，因为出现错误。  
  
### <a name="remarks"></a>备注  
 重新启动管理器调用`SaveOpenDocumentList`应用程序意外退出的时或当退出升级。 当应用程序重新启动时，它会使用[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)检索打开的文档的列表。  
  
 此方法将保存仅在打开的文档的列表。 该方法[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)负责保存文档本身。  
  
##  <a name="setautosaveinterval"></a>  CDataRecoveryHandler::SetAutosaveInterval  
 设置以毫秒为单位的自动保存周期之间的时间。  
  
```  
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```  
  
### <a name="parameters"></a>参数  
 [in]*nAutosaveInterval*  
 新自动保存间隔 （毫秒）。  
  
##  <a name="setautosavepath"></a>  CDataRecoveryHandler::SetAutosavePath  
 设置存储自动保存文件的目录。  
  
```  
virtual void SetAutosavePath(const CString& strAutosavePath);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*strAutosavePath*|存储自动保存文件的路径。|  
  
### <a name="remarks"></a>备注  
 更改自动保存目录不会移动当前自动保存文件。  
  
##  <a name="setrestartidentifier"></a>  CDataRecoveryHandler::SetRestartIdentifier  
 设置的此实例的唯一的重新启动标识符`CDataRecoveryHandler`。  
  
```  
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*strRestartIdentifier*|重新启动管理器唯一标识符。|  
  
### <a name="remarks"></a>备注  
 有关在注册表中打开的文档的重新启动管理器记录信息。 此信息作为键存储具有唯一的重新启动标识符。 由于重新启动标识符是唯一的应用程序的每个实例，应用程序的多个实例可能会意外退出，并且重新启动管理器可以恢复每个。  
  
##  <a name="setsavedocumentinfoonidle"></a>  CDataRecoveryHandler::SetSaveDocumentInfoOnIdle  
 集是否`CDataRecoveryHandler`在当前的空闲周期内将打开的文档信息保存到 Windows 注册表。  
  
```  
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*bSaveOnIdle*|`TRUE` 若要保存当前的空闲周期; 文档信息`FALSE to not perform a save`.|  
  
##  <a name="setshutdownbyrestartmanager"></a>  CDataRecoveryHandler::SetShutdownByRestartManager  
 设置是否以前退出应用程序而引起的重新启动管理器。  
  
```  
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*bShutdownByRestartManager*|`TRUE` 若要指示重新启动管理器导致应用程序退出;`FALSE`以指示由于其他原因退出应用程序。|  
  
### <a name="remarks"></a>备注  
 框架的行为以不同的方式基于以前退出是否意外或它已启动重新启动管理器。  
  
##  <a name="updatedocumentinfo"></a>  CDataRecoveryHandler::UpdateDocumentInfo  
 因为用户将其保存，请更新文档的信息。  
  
```  
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*pDocument*|指向已保存的文档的指针。|  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法删除自动保存文档，并且更新了文档信息;`FALSE`如果发生错误。  
  
### <a name="remarks"></a>备注  
 当用户保存文档时，应用程序中删除自动保存文件，因为不再需要它。 `UpdateDocumentInfo` 通过调用中删除自动保存的文件[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)。 `UpdateDocumentInfo` 然后将从信息添加*pDocument*到列表中当前打开文档因为`RemoveDocumentInfo`删除该信息，但已保存文档仍处于打开状态。  
  
 若要使用此方法，`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`必须设置*m_dwRestartManagerSupportFlags*。   
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [如何：添加重启管理器支持](../../mfc/how-to-add-restart-manager-support.md)

