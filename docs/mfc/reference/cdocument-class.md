---
title: "CDocument 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocument
- AFXWIN/CDocument
- AFXWIN/CDocument::CDocument
- AFXWIN/CDocument::AddView
- AFXWIN/CDocument::BeginReadChunks
- AFXWIN/CDocument::CanCloseFrame
- AFXWIN/CDocument::ClearChunkList
- AFXWIN/CDocument::ClearPathName
- AFXWIN/CDocument::DeleteContents
- AFXWIN/CDocument::FindChunk
- AFXWIN/CDocument::GetAdapter
- AFXWIN/CDocument::GetDocTemplate
- AFXWIN/CDocument::GetFile
- AFXWIN/CDocument::GetFirstViewPosition
- AFXWIN/CDocument::GetNextView
- AFXWIN/CDocument::GetPathName
- AFXWIN/CDocument::GetThumbnail
- AFXWIN/CDocument::GetTitle
- AFXWIN/CDocument::InitializeSearchContent
- AFXWIN/CDocument::IsModified
- AFXWIN/CDocument::IsSearchAndOrganizeHandler
- AFXWIN/CDocument::LoadDocumentFromStream
- AFXWIN/CDocument::OnBeforeRichPreviewFontChanged
- AFXWIN/CDocument::OnChangedViewList
- AFXWIN/CDocument::OnCloseDocument
- AFXWIN/CDocument::OnCreatePreviewFrame
- AFXWIN/CDocument::OnDocumentEvent
- AFXWIN/CDocument::OnDrawThumbnail
- AFXWIN/CDocument::OnLoadDocumentFromStream
- AFXWIN/CDocument::OnNewDocument
- AFXWIN/CDocument::OnOpenDocument
- AFXWIN/CDocument::OnPreviewHandlerQueryFocus
- AFXWIN/CDocument::OnPreviewHandlerTranslateAccelerator
- AFXWIN/CDocument::OnRichPreviewBackColorChanged
- AFXWIN/CDocument::OnRichPreviewFontChanged
- AFXWIN/CDocument::OnRichPreviewSiteChanged
- AFXWIN/CDocument::OnRichPreviewTextColorChanged
- AFXWIN/CDocument::OnSaveDocument
- AFXWIN/CDocument::OnUnloadHandler
- AFXWIN/CDocument::PreCloseFrame
- AFXWIN/CDocument::ReadNextChunkValue
- AFXWIN/CDocument::ReleaseFile
- AFXWIN/CDocument::RemoveChunk
- AFXWIN/CDocument::RemoveView
- AFXWIN/CDocument::ReportSaveLoadException
- AFXWIN/CDocument::SaveModified
- AFXWIN/CDocument::SetChunkValue
- AFXWIN/CDocument::SetModifiedFlag
- AFXWIN/CDocument::SetPathName
- AFXWIN/CDocument::SetTitle
- AFXWIN/CDocument::UpdateAllViews
- AFXWIN/CDocument::OnFileSendMail
- AFXWIN/CDocument::OnUpdateFileSendMail
- AFXWIN/CDocument::m_bGetThumbnailMode
- AFXWIN/CDocument::m_bPreviewHandlerMode
- AFXWIN/CDocument::m_bSearchMode
- AFXWIN/CDocument::m_clrRichPreviewBackColor
- AFXWIN/CDocument::m_clrRichPreviewTextColor
- AFXWIN/CDocument::m_lfRichPreviewFont
dev_langs: C++
helpviewer_keywords:
- CDocument [MFC], CDocument
- CDocument [MFC], AddView
- CDocument [MFC], BeginReadChunks
- CDocument [MFC], CanCloseFrame
- CDocument [MFC], ClearChunkList
- CDocument [MFC], ClearPathName
- CDocument [MFC], DeleteContents
- CDocument [MFC], FindChunk
- CDocument [MFC], GetAdapter
- CDocument [MFC], GetDocTemplate
- CDocument [MFC], GetFile
- CDocument [MFC], GetFirstViewPosition
- CDocument [MFC], GetNextView
- CDocument [MFC], GetPathName
- CDocument [MFC], GetThumbnail
- CDocument [MFC], GetTitle
- CDocument [MFC], InitializeSearchContent
- CDocument [MFC], IsModified
- CDocument [MFC], IsSearchAndOrganizeHandler
- CDocument [MFC], LoadDocumentFromStream
- CDocument [MFC], OnBeforeRichPreviewFontChanged
- CDocument [MFC], OnChangedViewList
- CDocument [MFC], OnCloseDocument
- CDocument [MFC], OnCreatePreviewFrame
- CDocument [MFC], OnDocumentEvent
- CDocument [MFC], OnDrawThumbnail
- CDocument [MFC], OnLoadDocumentFromStream
- CDocument [MFC], OnNewDocument
- CDocument [MFC], OnOpenDocument
- CDocument [MFC], OnPreviewHandlerQueryFocus
- CDocument [MFC], OnPreviewHandlerTranslateAccelerator
- CDocument [MFC], OnRichPreviewBackColorChanged
- CDocument [MFC], OnRichPreviewFontChanged
- CDocument [MFC], OnRichPreviewSiteChanged
- CDocument [MFC], OnRichPreviewTextColorChanged
- CDocument [MFC], OnSaveDocument
- CDocument [MFC], OnUnloadHandler
- CDocument [MFC], PreCloseFrame
- CDocument [MFC], ReadNextChunkValue
- CDocument [MFC], ReleaseFile
- CDocument [MFC], RemoveChunk
- CDocument [MFC], RemoveView
- CDocument [MFC], ReportSaveLoadException
- CDocument [MFC], SaveModified
- CDocument [MFC], SetChunkValue
- CDocument [MFC], SetModifiedFlag
- CDocument [MFC], SetPathName
- CDocument [MFC], SetTitle
- CDocument [MFC], UpdateAllViews
- CDocument [MFC], OnFileSendMail
- CDocument [MFC], OnUpdateFileSendMail
- CDocument [MFC], m_bGetThumbnailMode
- CDocument [MFC], m_bPreviewHandlerMode
- CDocument [MFC], m_bSearchMode
- CDocument [MFC], m_clrRichPreviewBackColor
- CDocument [MFC], m_clrRichPreviewTextColor
- CDocument [MFC], m_lfRichPreviewFont
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dad4a2bb3da49b0163367761aeefe85384ecdfb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdocument-class"></a>CDocument 类
提供用户定义文档类的基本功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CDocument : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDocument::CDocument](#cdocument)|构造 `CDocument` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocument::AddView](#addview)|将视图附加到文档。|  
|[CDocument::BeginReadChunks](#beginreadchunks)|初始化消息的分块读取。|  
|[CDocument::CanCloseFrame](#cancloseframe)|高级可重写;在关闭帧窗口查看本文档之前调用。|  
|[CDocument::ClearChunkList](#clearchunklist)|清除块列表。|  
|[CDocument::ClearPathName](#clearpathname)|清除文档对象的路径。|  
|[CDocument::DeleteContents](#deletecontents)|调用以执行清理的文档。|  
|[CDocument::FindChunk](#findchunk)|查找指定 GUID 的块区。|  
|[CDocument::GetAdapter](#getadapter)|将指针返回到对象实现`IDocument`接口。|  
|[CDocument::GetDocTemplate](#getdoctemplate)|返回一个指向描述文档的类型的文档模板。|  
|[CDocument::GetFile](#getfile)|将指针返回到所需`CFile`对象。|  
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|返回的第一个位置中的视图; 列表用于开始迭代。|  
|[CDocument::GetNextView](#getnextview)|循环访问与文档关联的视图的列表。|  
|[CDocument::GetPathName](#getpathname)|返回文档的数据文件的路径。|  
|[CDocument::GetThumbnail](#getthumbnail)|调用创建的位图的缩略图的提供程序用于显示缩略图。|  
|[CDocument::GetTitle](#gettitle)|返回文档的标题。|  
|[CDocument::InitializeSearchContent](#initializesearchcontent)|调用以初始化搜索内容搜索处理程序。|  
|[CDocument::IsModified](#ismodified)|指示是否在自上次保存后，已被修改文档。|  
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|指示是否的此实例`CDocument`对搜索和组织的处理程序创建对象。|  
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|调用以从流加载文档数据。|  
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|在更改丰富预览字体之前调用。|  
|[CDocument::OnChangedViewList](#onchangedviewlist)|调用后添加到视图或将其从文档中移除。|  
|[CDocument::OnCloseDocument](#onclosedocument)|调用以关闭文档。|  
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|需要创建丰富预览的预览帧时，由框架调用。|  
|[CDocument::OnDocumentEvent](#ondocumentevent)|由框架调用以响应文档事件。|  
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|重写此方法在派生类中，若要绘制的缩略图的内容。|  
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|当它需要从流中加载的文档数据时，由框架调用。|  
|[CDocument::OnNewDocument](#onnewdocument)|调用以创建新文档。|  
|[CDocument::OnOpenDocument](#onopendocument)|调用以打开现有文档。|  
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|指示要从调用 GetFocus 函数返回 HWND 的预览处理程序。|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|指示要处理中向上传递，从在其中预览处理程序正在运行的进程的消息泵击键的预览处理程序。|  
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|丰富预览背景色已更改时调用。|  
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|丰富预览字体已更改时调用。|  
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|丰富预览站点已更改时调用。|  
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|丰富预览文本颜色已更改时调用。|  
|[CDocument::OnSaveDocument](#onsavedocument)|调用以将文档保存到磁盘。|  
|[CDocument::OnUnloadHandler](#onunloadhandler)|当正在卸载预览处理程序时，由框架调用。|  
|[CDocument::PreCloseFrame](#precloseframe)|在关闭帧窗口之前调用。|  
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|读取下一个块区值。|  
|[CDocument::ReleaseFile](#releasefile)|释放文件使其可供其他应用程序。|  
|[CDocument::RemoveChunk](#removechunk)|删除指定 GUID 的块区。|  
|[CDocument::RemoveView](#removeview)|分离从文档的视图。|  
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|高级可重写;调用时打开或保存操作无法完成由于出现异常。|  
|[CDocument::SaveModified](#savemodified)|高级可重写;调用以要求用户是否应保存文档。|  
|[CDocument::SetChunkValue](#setchunkvalue)|设置一个块区值。|  
|[CDocument::SetModifiedFlag](#setmodifiedflag)|设置一个标志，指示自上次保存后已修改文档。|  
|[CDocument::SetPathName](#setpathname)|设置文档使用的数据文件的路径。|  
|[CDocument::SetTitle](#settitle)|设置文档的标题。|  
|[CDocument::UpdateAllViews](#updateallviews)|通知所有文档的视图已修改。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocument::OnFileSendMail](#onfilesendmail)|将一封电子邮件发送与附加的文档。|  
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|如果邮件支持存在，请启用发送邮件命令。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|指定`CDocument`对象由 dllhost 缩略图。 应签入`CView::OnDraw`。|  
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|指定`CDocument`对象由 prevhost 为`Rich Preview`。 应签入`CView::OnDraw`。|  
|[CDocument::m_bSearchMode](#m_bsearchmode)|指定`CDocument`对象由索引器或其他搜索应用程序。|  
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|指定丰富预览窗口的背景的色。 由主机设置此颜色。|  
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|指定丰富预览窗口前的景色。 由主机设置此颜色。|  
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|指定丰富预览窗口的文本字体。 此字体信息是由主机设置。|  
  
## <a name="remarks"></a>备注  
 文档表示用户通常使用文件打开的命令将打开，并将文件保存命令和保存的数据的单位。  
  
 **CDocument**支持标准的操作，如创建文档、 加载它，并将其保存。 框架操作使用由定义的接口的文档**CDocument**。  
  
 应用程序可以支持多个类型的文档;例如，应用程序可能支持电子表格和文本文档。 每种类型的文档具有关联的文档模板;文档模板指定为该类型的文档使用哪些资源 （例如，菜单、 图标或快捷键对应表）。 每个文档包含及其关联的指针`CDocTemplate`对象。  
  
 用户通过文档与之交互[CView](../../mfc/reference/cview-class.md)与之关联的对象。 视图呈现文档框架窗口中的映像，并将用户输入解释为对文档的操作。 文档可具有与之关联的多个视图。 当用户打开文档上的窗口时，框架将创建一个视图，并将其附加到文档。 文档模板指定哪种类型的视图和框架窗口用于显示每种类型的文档。  
  
 文档属于框架的标准命令路由，并因此从标准用户界面组件 （如保存文件菜单项） 中接收命令。 文档接收转发的活动视图的命令。 如果该文档不处理给定的命令，它会将转发到管理它的文档模板的命令。  
  
 文档的数据修改时，每个其视图必须反映这些修改。 **CDocument**提供[UpdateAllViews](#updateallviews)要通知的此类更改视图，以便视图可以根据需要重新绘制自己的成员函数。 框架还会提示用户将其关闭之前保存已修改的文件。  
  
 若要实现典型的应用程序中的文档，必须执行以下操作：  
  
-   从派生类**CDocument**每种类型的文档。  
  
-   添加成员变量以存储每个文档的数据。  
  
-   实现用于读取和修改文档的数据的成员函数。 文档的视图是这些成员函数的最重要用户。  
  
-   重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)文档类写入和读取文档的数据传入和传出磁盘中的成员函数。  
  
 **CDocument**支持将您的文档通过邮件发送邮件支持 (MAPI) 是否存在。 请参阅文章[MAPI](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)。  
  
 有关详细信息**CDocument**，请参阅[序列化](../../mfc/serialization-in-mfc.md)，[文档/视图体系结构主题](../../mfc/document-view-architecture.md)，和[文档/视图创建](../../mfc/document-view-creation.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## <a name="requirements"></a>惠?  
 **标头:** afxwin.h  
  
##  <a name="addview"></a>CDocument::AddView  
 调用此函数可将视图附加到文档。  
  
```  
void AddView(CView* pView);
```  
  
### <a name="parameters"></a>参数  
 `pView`  
 指向要添加的视图。  
  
### <a name="remarks"></a>备注  
 此函数将指定的视图添加到与文档; 关联的视图的列表函数还将设置到此文档的视图的文档指针。 将新创建的视图对象附加到文档; 时，框架会调用此函数响应文件新的、 文件打开的或新的窗口的命令或拆分的拆分器窗口时出现这种情况。  
  
 仅当要手动创建和附加视图，请调用此函数。 通常，你将让连接通过定义的文档和视图的框架[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象关联的文档类，视图类和框架窗口类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]  
  
##  <a name="beginreadchunks"></a>CDocument::BeginReadChunks  
 初始化消息的分块读取。  
  
```  
virtual void BeginReadChunks ();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="cancloseframe"></a>CDocument::CanCloseFrame  
 显示文档的框架窗口关闭之前，由框架调用。  
  
```  
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>参数  
 `pFrame`  
 指向附加到文档的视图的框架窗口。  
  
### <a name="return-value"></a>返回值  
 非零，则可以安全地关闭帧窗口中; 如果否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现将检查是否有其他显示文档的框架窗口。 如果指定的框架窗口，显示文档的最后一个函数将提示用户保存文档，如果修改它。 如果你想要执行特殊处理，关闭帧窗口时，重写此函数。 这是一个高级可重写。  
  
##  <a name="cdocument"></a>CDocument::CDocument  
 构造**CDocument**对象。  
  
```  
CDocument();
```  
  
### <a name="remarks"></a>备注  
 该框架将处理为你的文档创建。 重写[OnNewDocument](#onnewdocument)成员函数以执行初始化基于每个文档; 这是单文档界面 (SDI) 应用程序中特别重要。  
  
##  <a name="clearchunklist"></a>CDocument::ClearChunkList  
 清除块列表。  
  
```  
virtual void ClearChunkList ();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="clearpathname"></a>CDocument::ClearPathName  
 清除文档对象的路径。  
  
```  
virtual void ClearPathName();
```  
  
### <a name="remarks"></a>备注  
 清除从路径`CDocument`对象导致应用程序下一步保存文档时提示用户。 这使得**保存**命令的行为类似于**另存为**命令。  
  
##  <a name="deletecontents"></a>CDocument::DeleteContents  
 由框架，以删除文档的数据而不销毁**CDocument**对象本身。  
  
```  
virtual void DeleteContents();
```  
  
### <a name="remarks"></a>备注  
 文档是将其销毁之前调用它。 它也称为以确保之前它将重复使用了空的文档。 这一点尤为重要了 SDI 应用程序，它使用只有一个文档;每当用户创建或打开另一个文档，文档将重复使用。 调用此函数可实现的"编辑全部清除"或删除所有文档的数据的类似命令。 此函数的默认实现不执行任何操作。 重写此函数可删除你的文档中的数据。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]  
  
##  <a name="findchunk"></a>CDocument::FindChunk  
 查找指定 GUID 的块区。  
  
```  
virtual POSITION FindChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>参数  
 `guid`  
 指定要查找一个块的 GUID。  
  
 `pid`  
 指定的块区的 PID，若要查找。  
  
### <a name="return-value"></a>返回值  
 如果成功的内部块列表中的位置。 否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getadapter"></a>CDocument::GetAdapter  
 将指针返回到一个对象，实现`IDocument`接口。  
  
```  
virtual ATL::IDocument* GetAdapter();
```  
  
### <a name="return-value"></a>返回值  
 指向一个对象，实现`IDocument`接口。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getdoctemplate"></a>CDocument::GetDocTemplate  
 调用此函数可获取指向文档模板的指针，此文档类型。  
  
```  
CDocTemplate* GetDocTemplate() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向此文档类型的文档模板的指针或**NULL**如果文档未被管理的文档模板。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]  
  
##  <a name="getfile"></a>CDocument::GetFile  
 调用此成员函数以获取指向`CFile`对象。  
  
```  
virtual CFile* GetFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError);
```  
  
### <a name="parameters"></a>参数  
 `lpszFileName`  
 一个字符串，是所需的文件的路径。 路径可能是相对或绝对。  
  
 `pError`  
 指向现有文件异常对象，该值指示该操作的完成状态的指针。  
  
 `nOpenFlags`  
 共享和访问模式。 指定当打开文件时要执行的操作。 你可以组合 CFile 构造函数中所列选项[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)使用按位 OR (&#124;) 运算符。 一个访问权限和一个共享选项是必需的;**modeCreate**和**modeNoInherit**模式是可选的。  
  
### <a name="return-value"></a>返回值  
 指向的指针`CFile`对象。  
  
##  <a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition  
 调用此函数可获取与文档关联的视图的列表中的第一个视图的位置。  
  
```  
virtual POSITION GetFirstViewPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 A**位置**可以用于迭代使用值[GetNextView](#getnextview)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getnextview"></a>CDocument::GetNextView  
 调用此函数用于循环访问所有文档的视图。  
  
```  
virtual CView* GetNextView(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 `rPosition`  
 对引用**位置**返回上次调用值`GetNextView`或[GetFirstViewPosition](#getfirstviewposition)成员函数。 此值不能**NULL**。  
  
### <a name="return-value"></a>返回值  
 指向由标识的视图的指针`rPosition`。  
  
### <a name="remarks"></a>备注  
 该函数将返回由标识的视图`rPosition`，然后将设置`rPosition`到**位置**值的列表中的下一步视图。 如果检索到的视图是在列表中，最后然后`rPosition`设置为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getpathname"></a>CDocument::GetPathName  
 调用此函数可获取文档的磁盘文件的完全限定的路径。  
  
```  
const CString& GetPathName() const;  
```  
  
### <a name="return-value"></a>返回值  
 文档的完全限定的路径。 如果文档尚未保存，或者没有与它关联的磁盘文件，此字符串为空。  
  
##  <a name="getthumbnail"></a>CDocument::GetThumbnail  
 创建缩略图的提供程序用于显示缩略图的位图。  
  
```  
virtual BOOL GetThumbnail(
    UINT cx,  
    HBITMAP* phbmp,  
    DWORD* pdwAlpha);
```  
  
### <a name="parameters"></a>参数  
 `cx`  
 指定的宽度和位图的高度。  
  
 `phbmp`  
 当该函数成功返回时包含位图的句柄。  
  
 `pdwAlpha`  
 包含在该函数将返回成功时指定的 alpha 通道值，一个 dword 值。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`成功; 否则为如果创建缩略图的位图`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettitle"></a>CDocument::GetTitle  
 调用此函数可获取该文档的标题，通常派生自文档的文件名。  
  
```  
const CString& GetTitle() const;  
```  
  
### <a name="return-value"></a>返回值  
 文档的标题。  
  
##  <a name="initializesearchcontent"></a>CDocument::InitializeSearchContent  
 调用以初始化搜索内容搜索处理程序。  
  
```  
virtual void InitializeSearchContent ();
```  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类来初始化搜索内容。 内容应该是由分隔的部分的字符串";"。 例如，"点;矩形;ole 项"。  
  
##  <a name="ismodified"></a>CDocument::IsModified  
 调用此函数可确定自上次保存后是否已修改文档。  
  
```  
virtual BOOL IsModified();
```  
  
### <a name="return-value"></a>返回值  
 如果文档已被修改，因为自上次保存; 则为非 0否则为 0。  
  
##  <a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler  
 指示是否的此实例`CDocument`针对搜索和组织的处理程序创建的。  
  
```  
BOOL IsSearchAndOrganizeHandler() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果此实例的`CDocument`针对搜索和组织的处理程序创建的。  
  
### <a name="remarks"></a>备注  
 此函数将返回当前`TRUE`仅对中的进程服务器实现的丰富预览处理程序。 您可以在你的应用程序级别，以使此函数返回设置相应的标志 （m_bPreviewHandlerMode、 m_bSearchMode、 m_bGetThumbnailMode） `TRUE`。  
  
##  <a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream  
 调用以从流加载文档数据。  
  
```  
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,  
    DWORD dwGrfMode);
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 指向流的指针。 Shell 提供此流。  
  
 `dwGrfMode`  
 写入流的访问模式。  
  
### <a name="return-value"></a>返回值  
 如果在加载操作成功，否则为 HRESULT 错误代码，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 你可以重写此方法在派生类以自定义如何从流中加载数据。  
  
##  <a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode  
 指定`CDocument`对象由 dllhost 缩略图。 应签入`CView::OnDraw`。  
  
```  
BOOL m_bGetThumbnailMode;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE`指示文档由 dllhost 缩略图。  
  
##  <a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode  
 指定`CDocument`对象由 prevhost 创建用于丰富预览。 应签入`CView::OnDraw`。  
  
```  
BOOL m_bPreviewHandlerMode;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE`指示，文档已被创建 prevhost 的丰富预览。  
  
##  <a name="m_bsearchmode"></a>CDocument::m_bSearchMode  
 指定`CDocument`通过索引器或其他搜索应用程序创建对象。  
  
```  
BOOL m_bSearchMode;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE`指示创建文档时通过索引器或其他搜索应用程序。  
  
##  <a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor  
 指定丰富预览窗口的背景的色。 由主机设置此颜色。  
  
```  
COLORREF m_clrRichPreviewBackColor;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor  
 指定的丰富预览窗口的前景色。 由主机设置此颜色。  
  
```  
COLORREF m_clrRichPreviewTextColor;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont  
 指定的丰富预览窗口的文本字体。 此字体信息是由主机设置。  
  
```  
CFont m_lfRichPreviewFont;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged  
 在调用之前更改的丰富预览字体。  
  
```  
virtual void OnBeforeRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onchangedviewlist"></a>CDocument::OnChangedViewList  
 视图被添加到或从文档中删除后，由框架调用。  
  
```  
virtual void OnChangedViewList();
```  
  
### <a name="remarks"></a>备注  
 此函数的默认实现检查最后一个视图正被删除，是否是这样，删除文档。 如果你想要执行特殊处理，框架将添加或删除视图时，重写此函数。 例如，如果你想要保持打开状态，即使没有附加到它的视图的文档，重写此函数。  
  
##  <a name="onclosedocument"></a>CDocument::OnCloseDocument  
 文档关闭时，通常为文件关闭命令的一部分，由框架调用。  
  
```  
virtual void OnCloseDocument();
```  
  
### <a name="remarks"></a>备注  
 此函数的默认实现销毁的所有帧用于查看文档，关闭该视图、 清理文档的内容，然后调用[DeleteContents](#deletecontents)可用于删除文档的成员函数数据。  
  
 如果你想要执行的特殊清理处理 framework 关闭文档时，重写此函数。 例如，如果文档表示数据库中的记录，你可能想要重写此函数可在关闭该数据库。 通过重写，应调用此函数的基类版本。  
  
##  <a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame  
 需要创建丰富预览的预览帧时，由框架调用。  
  
```  
virtual BOOL OnCreatePreviewFrame();
```  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果成功; 否则为创建框架`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondocumentevent"></a>CDocument::OnDocumentEvent  
 由框架调用以响应文档事件。  
  
```  
virtual void OnDocumentEvent(DocumentEvent deEvent);
```  
  
### <a name="parameters"></a>参数  
 [in] `deEvent`  
 枚举的数据类型，用于描述事件的类型。  
  
### <a name="remarks"></a>备注  
 文档事件可能会影响多个类。 此方法负责处理而不影响类的文档事件[CDocument 类](../../mfc/reference/cdocument-class.md)。 目前，唯一必须响应文档事件的类是[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。 `CDocument`类具有负责处理效果上其他可重写方法`CDocument`。  
  
 下表列出的可能值`deEvent`以及它们对应的事件。  
  
|“值”|相应的事件|  
|-----------|-------------------------|  
|`onAfterNewDocument`|创建新文档。|  
|`onAfterOpenDocument`|打开新文档。|  
|`onAfterSaveDocument`|已保存文档。|  
|`onAfterCloseDocument`|文档已关闭。|  
  
##  <a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail  
 重写此方法在派生类绘制缩略图。  
  
```  
virtual void OnDrawThumbnail(
    CDC& dc,  
    LPRECT lprcBounds);
```  
  
### <a name="parameters"></a>参数  
 `dc`  
 对设备上下文的引用。  
  
 `lprcBounds`  
 指定应在其中绘制缩略图的区域的边框。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onfilesendmail"></a>CDocument::OnFileSendMail  
 发送消息通过常驻邮件主机 （如果有） 与文档作为附件。  
  
```  
void OnFileSendMail();
```  
  
### <a name="remarks"></a>备注  
 `OnFileSendMail`调用[OnSaveDocument](#onsavedocument) （保存） 到一个临时文件，然后通过电子邮件发送的未命名和修改文档序列化。 如果文档未进行修改，则不需要的临时文件;发送原始。 `OnFileSendMail`加载 MAPI32。如果尚未加载的 DLL。  
  
 一种特殊的实现`OnFileSendMail`为[COleDocument](../../mfc/reference/coledocument-class.md)句柄复合文件正确。  
  
 **CDocument**支持将您的文档通过邮件发送邮件支持 (MAPI) 是否存在。 请参阅文章[MAPI 主题](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)。  
  
##  <a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream  
 当它需要从流中加载的文档数据时，由框架调用。  
  
```  
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,  
    DWORD grfMode);
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 指向传入流的指针。  
  
 `grfMode`  
 写入流的访问模式。  
  
### <a name="return-value"></a>返回值  
 如果负载是成功; 则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onnewdocument"></a>CDocument::OnNewDocument  
 由框架作为文件新的命令的一部分调用。  
  
```  
virtual BOOL OnNewDocument();
```  
  
### <a name="return-value"></a>返回值  
 如果文档已成功初始化; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[DeleteContents](#deletecontents)成员函数，以确保该文档为空，并且随后会标记干净的新文档。 重写此函数可初始化新的文档的数据结构。 通过重写，应调用此函数的基类版本。  
  
 如果用户在 SDI 应用程序中选择新建文件命令，框架将使用此函数来重新初始化现有文档，而不是创建一个新。 如果用户选择新文件在多文档界面 (MDI) 应用程序中，框架每次创建一个新文档，，然后调用此函数可对其进行初始化。 你必须将初始化代码放在此函数，而不是文件新的命令是在 SDI 应用程序中有效的构造函数中。  
  
 请注意，存在情况`OnNewDocument`调用两次。 当为 ActiveX 文档服务器嵌入文档时，将发生这种情况。 第一次调用该函数`CreateInstance`方法 (由公开`COleObjectFactory`-派生类) 和由第二个时间`InitNew`方法 (由公开`COleServerDoc`-派生类)。  
  
### <a name="example"></a>示例  
 下面的示例说明了初始化文档对象的替代方法。  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
##  <a name="onopendocument"></a>CDocument::OnOpenDocument  
 由框架作为文件打开命令的一部分调用。  
  
```  
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 指向要打开的文档的路径。  
  
### <a name="return-value"></a>返回值  
 如果成功加载该文档; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现将打开指定的文件中，调用[DeleteContents](#deletecontents)成员函数，以确保该文档为空，调用[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)读取的文件内容，并随后会标记干净的文档。 如果你想要使用的存档机制或文件机制以外，重写此函数。 例如，你可以编写应用程序文档其中表示数据库而不是单独的文件中的记录。  
  
 如果用户在 SDI 应用程序中选择文件打开命令，框架将使用此函数重新初始化现有**CDocument**对象，而不是创建一个新。 如果用户选择文件打开 MDI 应用程序中，该框架构造一个新**CDocument**对象每个时间，然后调用此函数对其进行初始化。 你必须将初始化代码放在此函数而不是在文件打开命令是在 SDI 应用程序中有效的构造函数中。  
  
### <a name="example"></a>示例  
 下面的示例说明了初始化文档对象的替代方法。  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]  
  
##  <a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus  
 指示要返回 HWND 从调用中检索到的预览处理程序`GetFocus`函数。  
  
```  
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```  
  
### <a name="parameters"></a>参数  
 `phwnd`  
 [out]此方法返回时，包含指向从调用返回的 HWND 的`GetFocus`从预览处理程序的前台线程的函数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK 返回或以其他方式的错误值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator  
 指示要处理中向上传递，从在其中预览处理程序正在运行的进程的消息泵击键的预览处理程序。  
  
```  
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```  
  
### <a name="parameters"></a>参数  
 `pmsg`  
 [in]指向窗口消息的指针。  
  
### <a name="return-value"></a>返回值  
 如果可以通过预览处理程序处理该击键消息，该处理程序处理它，并返回，则为 S_OK。 如果预览处理程序无法处理该击键消息，它提供该主机可通过`IPreviewHandlerFrame::TranslateAccelerator`。 如果主机处理此消息，此方法返回，则为 S_OK。 如果主机不处理消息，此方法将返回 S_FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged  
 已更改的丰富预览背景色时调用。  
  
```  
virtual void OnRichPreviewBackColorChanged();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged  
 丰富预览字体已更改时调用。  
  
```  
virtual void OnRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged  
 丰富预览站点已更改时调用。  
  
```  
virtual void OnRichPreviewSiteChanged();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged  
 丰富预览文本颜色已更改时调用。  
  
```  
virtual void OnRichPreviewTextColorChanged();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onsavedocument"></a>CDocument::OnSaveDocument  
 由框架作为文件保存或文件另存为命令的一部分调用。  
  
```  
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 指向该文件应保存到的完全限定路径。  
  
### <a name="return-value"></a>返回值  
 如果已成功保存文档; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现将打开指定的文件中，调用[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)文档的数据写入文件，然后标记作为文档清理。 如果你想要执行特殊处理，当框架保存文档时，重写此函数。 例如，你可以编写应用程序文档其中表示数据库而不是单独的文件中的记录。  
  
##  <a name="onunloadhandler"></a>CDocument::OnUnloadHandler  
 卸载预览处理程序时，由框架调用。  
  
```  
virtual void OnUnloadHandler();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onupdatefilesendmail"></a>CDocument::OnUpdateFileSendMail  
 使**ID_FILE_SEND_MAIL**命令邮件支持 (MAPI) 是否存在。  
  
```  
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向的指针[CCmdUI](../../mfc/reference/ccmdui-class.md)与关联的对象**ID_FILE_SEND_MAIL**命令。  
  
### <a name="remarks"></a>备注  
 否则函数删除**ID_FILE_SEND_MAIL**从菜单中，包括分隔符上面或下面根据项的菜单命令。 如果启用 MAPI MAPI32。DLL 文件的路径中，和 WIN [邮件] 部分中出现。INI 文件，MAPI = 1。 大多数应用程序放在文件菜单上的此命令。  
  
 **CDocument**支持将您的文档通过邮件发送邮件支持 (MAPI) 是否存在。 请参阅文章[MAPI 主题](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)。  
  
##  <a name="precloseframe"></a>CDocument::PreCloseFrame  
 销毁框架窗口之前，将由框架调用此成员函数。  
  
```  
virtual void PreCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>参数  
 `pFrame`  
 指向[CFrameWnd](../../mfc/reference/cframewnd-class.md)保存关联**CDocument**对象。  
  
### <a name="remarks"></a>备注  
 它可以重写以提供自定义清理，但一定要调用的基类的类。  
  
 默认`PreCloseFrame`不执行任何操作**CDocument**。 **CDocument**-派生类[COleDocument](../../mfc/reference/coledocument-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)使用此成员函数。  
  
##  <a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue  
 读取下一个块区值。  
  
```  
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```  
  
### <a name="parameters"></a>参数  
 `ppValue`  
 [out]当函数返回时，`ppValue`包含已读取的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="releasefile"></a>CDocument::ReleaseFile  
 由框架版本的文件，使其可供其他应用程序调用此成员函数。  
  
```  
virtual void ReleaseFile(
    CFile* pFile,  
    BOOL bAbort);
```  
  
### <a name="parameters"></a>参数  
 `pFile`  
 指向要释放的 CFile 对象的指针。  
  
 `bAbort`  
 指定该文件是否通过使用释放`CFile::Close`或`CFile::Abort`。 **FALSE**如果该文件是要释放使用[CFile::Close](../../mfc/reference/cfile-class.md#close);**TRUE**如果该文件是要释放使用[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="remarks"></a>备注  
 如果`bAbort`是**TRUE**，`ReleaseFile`调用`CFile::Abort`，并释放该文件。 `CFile::Abort`不会引发异常。  
  
 如果`bAbort`是**FALSE**，`ReleaseFile`调用`CFile::Close`上并释放该文件。  
  
 重写该成员函数以释放该文件之前需要用户执行操作。  
  
##  <a name="removechunk"></a>CDocument::RemoveChunk  
 删除指定的 GUID 的块区。  
  
```  
virtual void RemoveChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>参数  
 `Guid`  
 指定要删除一个块的 GUID。  
  
 `Pid`  
 指定要删除一个块的 PID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="removeview"></a>CDocument::RemoveView  
 调用此函数可分离从文档的视图。  
  
```  
void RemoveView(CView* pView);
```  
  
### <a name="parameters"></a>参数  
 `pView`  
 指向要删除的视图。  
  
### <a name="remarks"></a>备注  
 此函数从与文档; 关联的视图的列表中移除指定的视图它还将视图的文档指针设置**NULL**。 框架窗口已关闭或拆分窗口的窗格关闭时，将由框架调用此函数。  
  
 仅当手动分离视图，请调用此函数。 通常，你将让分离通过定义的文档和视图的框架[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象关联的文档类，视图类和框架窗口类。  
  
 参阅位于以下示例[AddView](#addview)有关示例实现。  
  
##  <a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException  
 如果引发异常，则调用 (通常[CFileException](../../mfc/reference/cfileexception-class.md)或[CArchiveException](../../mfc/reference/carchiveexception-class.md)) 保存或加载文档时。  
  
```  
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,  
    CException* e,  
    BOOL bSaving,  
    UINT nIDPDefault);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 指向在文档的名称保存或加载。  
  
 *e*  
 指向已引发的异常。 可能是**NULL**。  
  
 *bSaving*  
 标志，指示哪些操作正在进行;如果文档保存时，0 如果已加载该文档，则为非 0。  
  
 `nIDPDefault`  
 如果函数未指定一个更具体显示的错误消息的标识符。  
  
### <a name="remarks"></a>备注  
 默认实现将检查的异常对象，并查找专门说明的原因的错误消息。 如果找不到特定的消息，或如果*e*是**NULL**，由指定的常规消息`nIDPDefault`使用参数。 然后，该函数将显示包含错误消息的消息框。 如果你想要提供其他自定义错误消息，重写此函数。 这是一个高级可重写。  
  
##  <a name="savemodified"></a>CDocument::SaveModified  
 要关闭修改后的文档之前，由框架调用。  
  
```  
virtual BOOL SaveModified();
```  
  
### <a name="return-value"></a>返回值  
 非零，则可以安全地继续并关闭文档; 如果如果不应关闭文档，则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现将显示一个消息框，询问用户是否将所做的更改保存到文档中，如果已进行了任何。 如果您的程序要求不同的提示过程，重写此函数。 这是一个高级可重写。  
  
##  <a name="setchunkvalue"></a>CDocument::SetChunkValue  
 设置一个块区值。  
  
```  
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>参数  
 `pValue`  
 指定一个要设置的区块值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setmodifiedflag"></a>CDocument::SetModifiedFlag  
 调用此函数后所做的对文档进行任何修改。  
  
```  
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bModified`  
 指示文档是否已修改的标志。  
  
### <a name="remarks"></a>备注  
 通过一致地调用此函数时，可以确保框架提示用户在关闭文档前保存更改。 通常应使用的默认值**TRUE**为`bModified`参数。 若要将尽可能全新的文档标记 （未修改），调用此函数中使用的值**FALSE**。  
  
##  <a name="setpathname"></a>CDocument::SetPathName  
 调用此函数可指定文档的磁盘文件的完全限定的路径。  
  
```  
virtual void SetPathName(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 指向要用作文档路径的字符串。  
  
 `bAddToMRU`  
 确定是否文件名添加到最近使用的 (MRU) 文件列表。 如果**为 TRUE，**添加文件名; 如果**FALSE**，未添加。  
  
### <a name="remarks"></a>备注  
 根据值`bAddToMRU`的路径不添加，或者未添加到由应用程序维护的 MRU 列表。 请注意，一些文档不与磁盘文件关联。 仅当您要重写用于打开和保存框架使用的文件的默认实现调用此函数。  
  
##  <a name="settitle"></a>CDocument::SetTitle  
 调用此函数可指定文档的标题 （在框架窗口的标题栏中显示的字符串）。  
  
```  
virtual void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>参数  
 `lpszTitle`  
 指向要用作文档的标题的字符串。  
  
### <a name="remarks"></a>备注  
 调用此函数将更新的所有显示的文档的框架窗口的标题。  
  
##  <a name="updateallviews"></a>CDocument::UpdateAllViews  
 修改文档后，请调用此函数。  
  
```  
void UpdateAllViews(
    CView* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pSender`  
 指向修改文档，该视图或**NULL**如果所有视图进行更新。  
  
 `lHint`  
 包含有关修改信息。  
  
 `pHint`  
 指向以存储有关修改信息的对象。  
  
### <a name="remarks"></a>备注  
 您应调用此函数后调用[SetModifiedFlag](#setmodifiedflag)成员函数。 此函数会通知附加到文档中，除由指定的视图的每个视图`pSender`，已修改文档。 同时你通常调用出了用户更改通过视图文档后，从视图类的此函数。  
  
 此函数将调用[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)除发送的文档的视图的每个成员函数查看，请传递`pHint`和`lHint`。 使用这些参数将信息传递给视图获取有关对文档进行修改。 你可以编码信息使用`lHint`和/或你可以定义[CObject](../../mfc/reference/cobject-class.md)-派生类来存储有关修改信息和传递，类使用的对象`pHint`。 重写`CView::OnUpdate`成员函数在你[CView](../../mfc/reference/cview-class.md)-派生类以优化基于传递的信息的视图的显示的更新。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDIDOCVW](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [MFC 示例 NPP](../../visual-cpp-samples.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)
