---
title: "CDataRecoveryHandler 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CDataRecoveryHandler class
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c2a99e32a88b8cb3f12d0961451025596886abb0
ms.lasthandoff: 02/24/2017

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
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|每个文件注册的自动保存`CDataRecoveryHandler`类。|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|将指定的文档。|  
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|将文档添加到打开的文档的列表。|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|删除所有当前的自动保存文件。|  
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|删除指定的自动保存文件。|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|生成与提供的文档文件名称关联的自动保存文件的名称。|  
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|返回自动保存尝试间隔的间隔。|  
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|返回的自动保存文件的路径。|  
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|检索的文档名称`CDocument`对象。|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|检索指定文档的普通标题。|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|创建并返回已恢复文档的标题。|  
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|检索应用程序的唯一重启标识符。|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|指示是否`CDataRecoveryHandler`对当前的空闲循环中执行了自动保存。|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|指示是否重新启动管理器引起退出该应用程序。|  
|[CDataRecoveryHandler::Initialize](#initialize)|初始化 `CDataRecoveryHandler`。|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|向用户显示一个对话框，为每个文档，`CDataRecoveryHandler`自动保存。 对话框中确定用户想要恢复自动保存文档。|  
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|从注册表中加载的打开的文档列表。|  
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|打开的文档列表中移除所提供的文档。|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|将打开以前打开的文档。|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|还原基于用户输入的自动保存文档。|  
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|将当前打开的文档的列表保存到 Windows 注册表。|  
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|设置以毫秒为单位的自动保存周期之间的时间。|  
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|设置自动保存文件的存储位置的目录。|  
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|设置的此实例的唯一重启标识符`CDataRecoveryHandler`。|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|集是否`CDataRecoveryHandler`当前空闲周期将打开的文档信息保存到 Windows 注册表。|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|设置是否由以前的应用程序退出引起的重新启动管理器。|  
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|因为用户将其保存，请更新文档的信息。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|m_bRestoringPreviousOpenDocs|指示数据恢复处理程序是否重新打开以前打开的文档。|  
|m_bSaveDocumentInfoOnIdle|指示是否将数据恢复处理程序自动保存文档在下一个空闲循环。|  
|m_bShutdownByRestartManager|指示是否重新启动管理器会导致退出该应用程序。|  
|m_dwRestartManagerSupportFlags|这些标志指示重新启动管理器支持哪些提供应用程序。|  
|m_lstAutosavesToDelete|未被删除时已关闭的原始文档的自动保存文件的列表。 当应用程序退出时，重新启动管理器重新尝试删除文件。|  
|m_mapDocNameToAutosaveName|自动保存文件名称的文档名称映射。|  
|m_mapDocNameToDocumentPtr|映射到的文档名称[CDocument](../../mfc/reference/cdocument-class.md)指针。|  
|m_mapDocNameToRestoreBool|一个布尔型参数，该值指示是否将自动保存文档还原到的文档名称映射。|  
|m_mapDocumentPtrToDocName|地图`CDocument`文档名称的指针。|  
|m_mapDocumentPtrToDocTitle|地图`CDocument`文档标题的指针。 这些标题用于保存文件。|  
|m_nAutosaveInterval|以毫秒为单位之间自动保存的时间。|  
|m_nTimerID|自动保存计时器的标识符。|  
|m_strAutosavePath|存储自动保存文档的位置。|  
|m_strRestartIdentifier|重新启动管理器 GUID 的字符串表示形式。|  
  
## <a name="remarks"></a>备注  
 重新启动管理器使用`CDataRecoveryHandler`类需要跟踪的所有打开的文档，并自动保存它们根据需要。 若要启用自动保存，请使用[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)方法。 此方法将定向`CDataRecoveryHandler`对下一个空闲循环中执行了自动保存。 重新启动管理器调用`SetSaveDocumentInfoOnIdle`时`CDataRecoveryHandler`应执行自动保存。  
  
 所有的方法`CDataRecoveryHandler`类都是虚函数。 重写此类，以创建您自己的自定义数据恢复处理程序中的方法。 除非创建您自己的数据恢复处理程序或重新启动管理器，否则不要实例化 CDataRecoveryHandler。 [CWinApp 类](../../mfc/reference/cwinapp-class.md)创建`CDataRecoveryHandler`对象在需要时。  
  
 然后才能使用`CDataRecoveryHandler`对象时，必须调用[CDataRecoveryHandler::Initialize](#initialize)。  
  
 因为`CDataRecoveryHandler`类紧密连接到重新启动管理器中，`CDataRecoveryHandler`取决于全局参数`m_dwRestartManagerSupportFlags`。 此参数确定重新启动管理器拥有的权限以及它如何与您的应用程序交互。 若要将重新启动管理器合并到现有应用程序，您必须分配`m_dwRestartManagerSupportFlags`主应用程序的构造函数中适当的值。 有关如何使用重新启动管理器的详细信息，请参阅[如何︰ 添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdatarecovery.h  
  
##  <a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo  
 每个文件注册的自动保存`CDataRecoveryHandler`类。  
  
```  
virtual BOOL AutosaveAllDocumentInfo();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`CDataRecoveryHandler`保存所有文档;`FALSE`如果不保存任何文档。  
  
### <a name="remarks"></a>备注  
 此方法返回`TRUE`如果必须保存没有文档。 它还会返回`TRUE`而不保存任何文档，如果检索`CWinApp`或`CDocManager`应用程序将生成错误。  
  
 若要使用此方法中，这两个`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`或`AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL`选项必须设置`m_dwRestartManagerSupportFlags`。 请参阅[m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)有关详细信息。  
  
##  <a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo  
 将指定的文档。  
  
```  
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,  
    BOOL bResetModifiedFlag = TRUE);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pDocument`|一个指向`CDocument`保存。|  
|[in] `bResetModifiedFlag`|`TRUE`指示`CDataRecoveryHandler`认为`pDocument`要修改;`FALSE`指示框架将视为`pDocument`以保持不变。 请参阅备注部分中有关对此标志的详细信息。|  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果设置了适当的标志和`pDocument`是有效`CDocument`对象。  
  
### <a name="remarks"></a>备注  
 每个`CDocument`对象都有一个标志，指示是否已更改自上次保存后。 使用[CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified)以确定此标志的状态。 如果`CDocument`自上次保存以来未更改`AutosaveDocumentInfo`，删除该文档的所有自动保存文件。 如果自上次保存以来已更改文档，关闭它提示用户将文档保存到在关闭之前。  
  
> [!NOTE]
>  使用`bResetModifiedFlag`文档的状态更改为未修改可能导致用户丢失未保存的数据。 如果框架认为不被修改的文档，则关闭它不提示用户保存。  
  
 此方法将引发的异常，而且[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)宏如果`pDocument`不是有效`CDocument`对象。  
  
 若要使用此方法中，这两个`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`或`AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL`选项必须设置`m_dwRestartManagerSupportFlags`。   
  
##  <a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler  
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
|[in] `dwRestartManagerSupportFlags`|指示支持重新启动管理器的选项。|  
|[in] `nAutosaveInterval`|自动保存间隔时间。 此参数是以毫秒为单位。|  
  
### <a name="remarks"></a>备注  
 MFC 框架会自动创建`CDataRecoveryHandler`您的应用程序，当您使用的对象**新项目**向导。 除非自定义的数据恢复行为或重新启动管理器时，不应创建`CDataRecoveryHandler`对象。  
  
  
##  <a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo  
 将文档添加到打开的文档的列表。  
  
```  
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pDocument`|一个指向`CDocument`。 此方法创建的文档信息`CDocument`。|  
  
### <a name="return-value"></a>返回值  
 默认实现返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 此方法检查是否`pDocument`之前它将文档添加已在文档的列表。 如果`pDocument`已在列表中，此方法与关联的自动保存文件的删除`pDocument`。  
  
 若要使用此方法中，这两个`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`或`AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL`选项必须设置`m_dwRestartManagerSupportFlags`。 
  
##  <a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles  
 删除所有当前的自动保存文件。  
  
```  
virtual BOOL DeleteAllAutosavedFiles();
```  
  
### <a name="return-value"></a>返回值  
 默认实现始终返回`TRUE`。  
  
##  <a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile  
 删除指定的自动保存文件。  
  
```  
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `strAutosavedFile`|一个字符串，包含自动保存文件的名称。|  
  
### <a name="return-value"></a>返回值  
 默认实现始终返回`TRUE`。  
  
### <a name="remarks"></a>备注  
 如果此方法不能删除自动保存文件，它将在列表中保存文件的名称。 析构函数`CDataRecoveryHandler`尝试删除该列表中指定的每个自动保存文件。  
  
##  <a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName  
 生成与提供的文档文件名称关联的自动保存文件的名称。  
  
```  
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `strDocumentName`  
 一个字符串，包含该文档的名称。 `GenerateAutosaveFileName`使用此文档的名称来生成相应的自动保存文件名称。  
  
### <a name="return-value"></a>返回值  
 从生成的自动保存文件名称`strDocumentName`。  
  
### <a name="remarks"></a>备注  
 每个文档名称具有自动保存文件同名的一对一映射。  
  
##  <a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval  
 返回自动保存尝试间隔的间隔。  
  
```  
virtual int GetAutosaveInterval() const;  
```  
  
### <a name="return-value"></a>返回值  
 将尝试自动保存功能之间的毫秒数。  
  
##  <a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath  
 返回的自动保存文件的路径。  
  
```  
virtual CString GetAutosavePath() const;  
```  
  
### <a name="return-value"></a>返回值  
 存储自动保存文档的位置。  
  
##  <a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName  
 检索的文档名称`CDocument`对象。  
  
```  
virtual CString GetDocumentListName(CDocument* pDocument) const;  
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pDocument`|一个指向`CDocument`。 `GetDocumentListName`从此检索的文档名称`CDocument`。|  
  
### <a name="return-value"></a>返回值  
 中的文档名称`pDocument`。  
  
### <a name="remarks"></a>备注  
 `CDataRecoveryHandler`作为键中使用的文档名称`m_mapDocNameToAutosaveName`， `m_mapDocNameToDocumentPtr`，和`m_mapDocNameToRestoreBool`。 这些参数启用`CDataRecoveryHandler`监视`CDocument`对象、 自动保存文件名称和自动保存设置。  
  
##  <a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle  
 检索指定文档的普通标题。  
  
```  
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pDocument`|一个指向`CDocument`。|  
  
### <a name="return-value"></a>返回值  
 正常的标题，为指定的文档的。  
  
### <a name="remarks"></a>备注  
 文档的正常的标题通常是文档的不带路径的文件名。 这就是在标题**文件名**字段**另存为**对话框。  
  
##  <a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle  
 创建并返回已恢复文档的标题。  
  
```  
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `strDocumentTitle`  
 正常的文档的标题。  
  
### <a name="return-value"></a>返回值  
 已恢复的文档的标题。  
  
### <a name="remarks"></a>备注  
 默认情况下，恢复文档的标题是普通标题与**[恢复]**追加到该日志。 已恢复的标题显示给用户时`CDataRecoveryHandler`查询要还原自动保存文档的用户。  
  
##  <a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier  
 检索应用程序的唯一重启标识符。  
  
```  
virtual CString GetRestartIdentifier() const;  
```  
  
### <a name="return-value"></a>返回值  
 唯一的重启标识符中。  
  
### <a name="remarks"></a>备注  
 重新启动标识符是唯一的每次执行的应用程序。  
  
 `CDataRecoveryHandler`将信息存储在注册表中有关当前打开的文档。 当重新启动管理器退出应用程序并重新启动它时，它提供将重启标识符与`CDataRecoveryHandler`。 `CDataRecoveryHandler`重启标识符用于检索以前打开的文档的列表。 这使`CDataRecoveryHandler`尝试查找并还原自动保存文件。  
  
##  <a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle  
 指示是否`CDataRecoveryHandler`对当前的空闲循环中执行了自动保存。  
  
```  
virtual BOOL GetSaveDocumentInfoOnIdle() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`指示`CDataRecoveryHandler`自动保存在当前的空闲循环;`FALSE`表明它没有。  
  
##  <a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager  
 指示是否重新启动管理器引起退出该应用程序。  
  
```  
virtual BOOL GetShutdownByRestartManager() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`指示重新启动管理器导致退出; 该应用程序`FALSE`指示不是。  
  
##  <a name="initialize"></a>CDataRecoveryHandler::Initialize  
 初始化 `CDataRecoveryHandler`。  
  
```  
virtual BOOL Initialize();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果初始化成功。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 初始化过程中加载用于存储从注册表的自动保存文件的路径。 如果`Initialize`方法找不到此目录或如果路径是`NULL`，`Initialize`将失败并返回`FALSE`。  
  
 使用[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)后在应用程序初始化更改自动保存路径`CDataRecoveryHandler`。  
  
 `Initialize`方法还可启动一个计时器，用于监视在下一步自动保存时。 使用[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)后在应用程序初始化更改自动保存间隔`CDataRecoveryHandler`。  
  
##  <a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments  
 向用户显示一个对话框，为每个文档，`CDataRecoveryHandler`自动保存。 对话框中确定用户想要恢复自动保存文档。  
  
```  
virtual void QueryRestoreAutosavedDocuments();
```  
  
### <a name="remarks"></a>备注  
 如果您的应用程序是 unicode 编码，则此方法显示[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)给用户。 否则，该框架使用[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)来查询用户。  
  
 之后`QueryRestoreAutosavedDocuments`收集所有响应来自用户，它将信息存储在成员变量`m_mapDocNameToRestoreBool`。 此方法不会恢复自动保存文档。  
  
##  <a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList  
 从注册表中加载的打开的文档列表。  
  
```  
virtual BOOL ReadOpenDocumentList();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`指示`ReadOpenDocumentList`从注册表中; 加载至少一个文档的信息`FALSE`指示不加载任何文档信息。  
  
### <a name="remarks"></a>备注  
 此函数从注册表加载打开的文档信息，并将其存储在成员变量`m_mapDocNameToAutosaveName`。  
  
 之后`ReadOpenDocumentList`加载所有数据，从注册表中删除文档信息。  
  
##  <a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo  
 打开的文档列表中移除所提供的文档。  
  
```  
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pDocument`|指向要删除的文档的指针。|  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`pDocument`从列表中; 删除`FALSE`是否发生了错误。  
  
### <a name="remarks"></a>备注  
 当用户关闭文档时，框架将使用此方法以从打开的文档列表中删除。  
  
 如果`RemoveDocumentInfo`找不到`pDocument`在打开的文档列表中，它不执行任何操作并返回`TRUE`。  
  
 若要使用此方法，`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`选项必须设置`m_dwRestartManagerSupportFlags`。   
  
##  <a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments  
 将打开以前打开的文档。  
  
```  
virtual BOOL ReopenPreviousDocuments();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果至少一个文档已经打开;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法可以打开以前打开的文档的最新存储。 如果不保存文档或自动保存，`ReopenPreviousDocuments`打开基于该文件类型的模板的空白文档。  
  
 若要使用此方法，`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`选项必须设置`m_dwRestartManagerSupportFlags`。 如果未设置此参数，`ReopenPreviousDocuments`不执行任何操作，并返回`FALSE`。  
  
 如果没有存储在以前打开的文档，该列表的文档`ReopenPreviousDocuments`不执行任何操作，并返回`FALSE`。  
  
##  <a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments  
 还原基于用户输入的自动保存文档。  
  
```  
virtual BOOL RestoreAutosavedDocuments();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功还原这些文档。  
  
### <a name="remarks"></a>备注  
 此方法调用[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)来确定该文档用户想要还原。 如果用户决定不恢复自动保存的文档，`RestoreAutosavedDocuments`删除自动保存文件。 否则为`RestoreAutosavedDocuments`替换自动保存的版本为打开的文档。  
  
 若要使用此方法中，这两个`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`或`AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`选项必须设置`m_dwRestartManagerSupportFlags`。   
  
##  <a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList  
 将当前打开的文档的列表保存到 Windows 注册表。  
  
```  
virtual BOOL SaveOpenDocumentList();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果没有打开的文档保存，或已成功保存。 `FALSE`如果文档将保存到注册表中，但它们未保存由于出现错误。  
  
### <a name="remarks"></a>备注  
 重新启动管理器调用`SaveOpenDocumentList`应用程序意外退出，或当应用程序退出升级。 应用程序重新启动时，它使用[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)来检索打开的文档的列表。  
  
 此方法在保存打开的文档列表。 该方法[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)负责保存文档本身。  
  
##  <a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval  
 设置以毫秒为单位的自动保存周期之间的时间。  
  
```  
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```  
  
### <a name="parameters"></a>参数  
 [in] `nAutosaveInterval`  
 新的自动保存间隔以毫秒为单位。  
  
##  <a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath  
 设置自动保存文件的存储位置的目录。  
  
```  
virtual void SetAutosavePath(const CString& strAutosavePath);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `strAutosavePath`|存储自动保存文件的路径。|  
  
### <a name="remarks"></a>备注  
 自动保存目录的更改不会移动当前自动保存文件。  
  
##  <a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier  
 设置的此实例的唯一重启标识符`CDataRecoveryHandler`。  
  
```  
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `strRestartIdentifier`|重新启动管理器的唯一标识符。|  
  
### <a name="remarks"></a>备注  
 重新启动管理器记录在注册表中打开的文档有关的信息。 此信息存储具有唯一的重启标识符作为键。 重新启动标识符都是唯一的应用程序的每个实例，因为应用程序的多个实例可能会意外退出，并且重新启动管理器可以恢复每个。  
  
##  <a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoOnIdle  
 集是否`CDataRecoveryHandler`当前空闲周期将打开的文档信息保存到 Windows 注册表。  
  
```  
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `bSaveOnIdle`|`TRUE`若要保存当前的空闲周期; 在文档信息`FALSE to not perform a save`.|  
  
##  <a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager  
 设置是否由以前的应用程序退出引起的重新启动管理器。  
  
```  
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `bShutdownByRestartManager`|`TRUE`若要指明重新启动管理器导致退出; 该应用程序`FALSE`以指示该应用程序退出的另一个原因。|  
  
### <a name="remarks"></a>备注  
 该框架的行为有所不同，具体取决以前退出是否意外或是否由重新启动管理器。  
  
##  <a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo  
 因为用户将其保存，请更新文档的信息。  
  
```  
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pDocument`|指向已保存的文档的指针。|  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法删除自动保存文档，并且更新了文档的信息;`FALSE`是否发生了错误。  
  
### <a name="remarks"></a>备注  
 当用户保存文档时，该应用程序中删除自动保存文件，因为不再需要它。 `UpdateDocumentInfo`通过调用中删除自动保存文件[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)。 `UpdateDocumentInfo`然后将信息从添加`pDocument`到列表中当前打开的文档因为`RemoveDocumentInfo`删除该信息，而保存文档仍处于打开状态。  
  
 若要使用此方法，`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`选项必须设置`m_dwRestartManagerSupportFlags`。   
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [如何︰ 添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)


