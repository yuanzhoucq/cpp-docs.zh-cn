---
title: "CDataRecoveryHandler Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDataRecoveryHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataRecoveryHandler class"
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CDataRecoveryHandler Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果应用程序意外退出，`CDataRecoveryHandler` 自动存储文档和还原它们。  
  
## 语法  
  
```  
class CDataRecoveryHandler : public CObject  
```  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[CDataRecoveryHandler::CDataRecoveryHandler](../Topic/CDataRecoveryHandler::CDataRecoveryHandler.md)|构造 `CDataRecoveryHandler` 对象。|  
  
### 方法  
  
|||  
|-|-|  
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](../Topic/CDataRecoveryHandler::AutosaveAllDocumentInfo.md)|自动存储每个文件移动到 `CDataRecoveryHandler` 选件类中。|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](../Topic/CDataRecoveryHandler::AutosaveDocumentInfo.md)|自动存储指定文档。|  
|[CDataRecoveryHandler::CreateDocumentInfo](../Topic/CDataRecoveryHandler::CreateDocumentInfo.md)|添加文档到列表打开文档。|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](../Topic/CDataRecoveryHandler::DeleteAllAutosavedFiles.md)|删除所有当前已自动存储的文件。|  
|[CDataRecoveryHandler::DeleteAutosavedFile](../Topic/CDataRecoveryHandler::DeleteAutosavedFile.md)|删除指定的将自动存储的文件。|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](../Topic/CDataRecoveryHandler::GenerateAutosaveFileName.md)|生成名称自动存储文件与所提供的文档文件的名称。|  
|[CDataRecoveryHandler::GetAutosaveInterval](../Topic/CDataRecoveryHandler::GetAutosaveInterval.md)|返回之间此间隔自动存储试。|  
|[CDataRecoveryHandler::GetAutosavePath](../Topic/CDataRecoveryHandler::GetAutosavePath.md)|返回已自动存储的文件的路径。|  
|[CDataRecoveryHandler::GetDocumentListName](../Topic/CDataRecoveryHandler::GetDocumentListName.md)|从 `CDocument` 对象检索文档名称。|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](../Topic/CDataRecoveryHandler::GetNormalDocumentTitle.md)|检索的常规前缀指定文档。|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](../Topic/CDataRecoveryHandler::GetRecoveredDocumentTitle.md)|创建并返回恢复的标题文档。|  
|[CDataRecoveryHandler::GetRestartIdentifier](../Topic/CDataRecoveryHandler::GetRestartIdentifier.md)|检索应用程序的唯一重新启动标识符。|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](../Topic/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle.md)|指示 `CDataRecoveryHandler` 是否对当前空闲循环的一自动存储。|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](../Topic/CDataRecoveryHandler::GetShutdownByRestartManager.md)|指示重新启动管理器是导致应用程序退出。|  
|[CDataRecoveryHandler::Initialize](../Topic/CDataRecoveryHandler::Initialize.md)|初始化 `CDataRecoveryHandler`。|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](../Topic/CDataRecoveryHandler::QueryRestoreAutosavedDocuments.md)|显示对话框为每个用户的文档 `CDataRecoveryHandler` 自动用于存储。  对话框确定用户是否希望还原已自动存储的文档。|  
|[CDataRecoveryHandler::ReadOpenDocumentList](../Topic/CDataRecoveryHandler::ReadOpenDocumentList.md)|加载打开文档从注册表列表。|  
|[CDataRecoveryHandler::RemoveDocumentInfo](../Topic/CDataRecoveryHandler::RemoveDocumentInfo.md)|移除所提供的从文档打开文档列表。|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](../Topic/CDataRecoveryHandler::ReopenPreviousDocuments.md)|打开以前打开文档。|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](../Topic/CDataRecoveryHandler::RestoreAutosavedDocuments.md)|还原已自动存储的文档基于用户输入。|  
|[CDataRecoveryHandler::SaveOpenDocumentList](../Topic/CDataRecoveryHandler::SaveOpenDocumentList.md)|保存当前列表打开文档到Windows注册表。|  
|[CDataRecoveryHandler::SetAutosaveInterval](../Topic/CDataRecoveryHandler::SetAutosaveInterval.md)|在毫秒设置之间时自动存储循环。|  
|[CDataRecoveryHandler::SetAutosavePath](../Topic/CDataRecoveryHandler::SetAutosavePath.md)|设置存储区中自动存储文件的目录。|  
|[CDataRecoveryHandler::SetRestartIdentifier](../Topic/CDataRecoveryHandler::SetRestartIdentifier.md)|设置 `CDataRecoveryHandler`的此实例的唯一重新启动标识符。|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](../Topic/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle.md)|设置 `CDataRecoveryHandler` 在当前空闲循环中，是否保存打开的文档信息对于Windows注册表。|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](../Topic/CDataRecoveryHandler::SetShutdownByRestartManager.md)|将上是否退出应用程序被重新启动管理器会导致的。|  
|[CDataRecoveryHandler::UpdateDocumentInfo](../Topic/CDataRecoveryHandler::UpdateDocumentInfo.md)|因为用户保存的代码，更新文档的信息。|  
  
### 数据成员  
  
|||  
|-|-|  
|m\_bRestoringPreviousOpenDocs|指示数据还原处理程序是否重新打开以前打开文档。|  
|m\_bSaveDocumentInfoOnIdle|指示数据还原处理程序在下空闲循环自动存储文档。|  
|m\_bShutdownByRestartManager|指示重新启动管理器是导致应用程序退出。|  
|m\_dwRestartManagerSupportFlags|指定的标志哪些支持重新启动管理器的应用程序。|  
|m\_lstAutosavesToDelete|未删除自动存储的文件的列表，在原文件时已关闭。  当应用程序退出时，重新启动管理器再次尝试删除文件。|  
|m\_mapDocNameToAutosaveName|文档名称的映射到时自动存储的文件的名称。|  
|m\_mapDocNameToDocumentPtr|文档名称的映射到 [CDocument](../../mfc/reference/cdocument-class.md) 指针的。|  
|m\_mapDocNameToRestoreBool|文档名称的映射到指示是否还原已自动存储的文档的boolean参数的。|  
|m\_mapDocumentPtrToDocName|`CDocument` 指针的映射到文档的名称。|  
|m\_mapDocumentPtrToDocTitle|`CDocument` 指针的映射到文档的标题。  这些前缀用于保存文件。|  
|m\_nAutosaveInterval|时间之间毫秒自动存储。|  
|m\_nTimerID|自动存储timer的标识符。|  
|m\_strAutosavePath|将自动存储的文档存储的位置。|  
|m\_strRestartIdentifier|GUID的字符串表示形式重新启动管理器的。|  
  
## 备注  
 重新启动管理器使用 `CDataRecoveryHandler` 选件类记录所有打开文档并在必要时自动存储它们。  若要关闭"自动存储，使用 [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](../Topic/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle.md) 方法。  此方法处理 `CDataRecoveryHandler` 对下空闲循环的一自动存储。  当 `CDataRecoveryHandler` 应执行自动存储时，重新启动管理器调用 `SetSaveDocumentInfoOnIdle`。  
  
 所有 `CDataRecoveryHandler` 选件类的方法是虚拟的。  重写在选件类的方法创建自己的自定义数据还原处理程序。  除非您创建自己的数据还原处理程序或重新启动管理器，不要实例化CDataRecoveryHandler。  并根据需要，[CWinApp Class](../../mfc/reference/cwinapp-class.md) 创建一 `CDataRecoveryHandler` 对象。  
  
 在使用 `CDataRecoveryHandler` 对象之前，必须调用 [CDataRecoveryHandler::Initialize](../Topic/CDataRecoveryHandler::Initialize.md)。  
  
 由于 `CDataRecoveryHandler` 选件类非常地连接到重新启动管理器，`CDataRecoveryHandler` 取决于全局参数 `m_dwRestartManagerSupportFlags`。  此参数确定权限重新启动管理器具有，它与应用程序交互的方式。  若要将重新启动管理器向现有的应用程序中，则必须进行 `m_dwRestartManagerSupportFlags` 在主应用构造函数的适当值。  有关如何使用重新启动管理器的更多信息，请参见 [如何：添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)。  
  
## 要求  
 **标头:** afxdatarecovery.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [如何：添加重新启动管理器支持](../../mfc/how-to-add-restart-manager-support.md)