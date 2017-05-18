---
title: "CDocument 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- documents [C++], serialization
- files [C++], documents
- command handling, documents and
- documents [C++], document classes
- documents [C++], multiple views
- serialization [C++], documents and
- CDocument class
- command routing, documents and
- views [C++], document
- documents [C++], command routing
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4d64b95f77139d984b855e710f3951434e489dd5
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
|[CDocument::AddView](#addview)|将视图附加到该文档。|  
|[CDocument::BeginReadChunks](#beginreadchunks)|初始化消息的分块读取。|  
|[CDocument::CanCloseFrame](#cancloseframe)|高级可重写;在关闭帧窗口查看该文档之前调用。|  
|[CDocument::ClearChunkList](#clearchunklist)|清除消息块列表。|  
|[CDocument::ClearPathName](#clearpathname)|清除文档对象的路径。|  
|[CDocument::DeleteContents](#deletecontents)|调用以执行清理操作文档。|  
|[CDocument::FindChunk](#findchunk)|查找指定 GUID 的块区。|  
|[CDocument::GetAdapter](#getadapter)|将指针返回到对象，实现`IDocument`接口。|  
|[CDocument::GetDocTemplate](#getdoctemplate)|返回描述文档的类型的文档模板的指针。|  
|[CDocument::GetFile](#getfile)|将指针返回到所需`CFile`对象。|  
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|返回的第一个位置中的列表视图。用于启动迭代。|  
|[CDocument::GetNextView](#getnextview)|循环访问与文档关联的视图的列表。|  
|[CDocument::GetPathName](#getpathname)|返回文档的数据文件的路径。|  
|[CDocument::GetThumbnail](#getthumbnail)|调用以创建缩略图提供程序将用其来显示缩略图的位图。|  
|[CDocument::GetTitle](#gettitle)|返回文档的标题。|  
|[CDocument::InitializeSearchContent](#initializesearchcontent)|调用以初始化搜索内容搜索处理程序。|  
|[CDocument::IsModified](#ismodified)|指示自上次保存以来是否已修改文档。|  
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|指示是否此实例的`CDocument`搜索 < 组织处理程序创建对象。|  
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|调用可从流加载文档数据。|  
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|在更改丰富预览字体之前调用。|  
|[CDocument::OnChangedViewList](#onchangedviewlist)|在视图已被添加到或从文档中移除之后调用。|  
|[CDocument::OnCloseDocument](#onclosedocument)|调用来关闭文档。|  
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|仅在需要创建丰富预览的预览帧时由框架调用。|  
|[CDocument::OnDocumentEvent](#ondocumentevent)|由对文档事件作出响应框架调用。|  
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|重写此方法在派生类来绘制内容的缩略图中。|  
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|当它需要从流加载文档数据时由框架调用。|  
|[CDocument::OnNewDocument](#onnewdocument)|调用以创建一个新的文档。|  
|[CDocument::OnOpenDocument](#onopendocument)|调用以打开现有文档。|  
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|指示要从调用 GetFocus 函数返回 HWND 的预览处理程序。|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|指示要从在其中预览处理程序正在运行的进程的消息泵中向上传递键击处理的预览处理程序。|  
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|丰富的预览背景色发生更改时调用。|  
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|丰富预览字体已更改时调用。|  
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|丰富的预览站点发生更改时调用。|  
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|丰富预览文本颜色发生更改时调用。|  
|[CDocument::OnSaveDocument](#onsavedocument)|调用以将文档保存到磁盘。|  
|[CDocument::OnUnloadHandler](#onunloadhandler)|当正在卸载模块预览处理程序时由框架调用。|  
|[CDocument::PreCloseFrame](#precloseframe)|框架窗口关闭前调用。|  
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|读取下一个块区值。|  
|[CDocument::ReleaseFile](#releasefile)|释放文件，使其可供使用的其他应用程序。|  
|[CDocument::RemoveChunk](#removechunk)|删除指定 GUID 的块区。|  
|[CDocument::RemoveView](#removeview)|分离该文档中的一个视图。|  
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|高级可重写;调用时打开或保存操作无法完成，因为存在异常。|  
|[CDocument::SaveModified](#savemodified)|高级可重写;调用以询问用户是否应保存该文档。|  
|[CDocument::SetChunkValue](#setchunkvalue)|设置消息块值。|  
|[CDocument::SetModifiedFlag](#setmodifiedflag)|设置一个标志，指示自上次保存后您已修改文档。|  
|[CDocument::SetPathName](#setpathname)|设置在文档中使用的数据文件的路径。|  
|[CDocument::SetTitle](#settitle)|设置文档的标题。|  
|[CDocument::UpdateAllViews](#updateallviews)|通知所有文档的视图已修改。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocument::OnFileSendMail](#onfilesendmail)|将包含附加的文档发送一封电子邮件。|  
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|如果邮件支持存在，请启用发送邮件的命令。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|指定`CDocument`对象由为缩略图的 dllhost 创建。 应签入`CView::OnDraw`。|  
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|指定`CDocument`对象由 prevhost 为创建`Rich Preview`。 应签入`CView::OnDraw`。|  
|[CDocument::m_bSearchMode](#m_bsearchmode)|指定`CDocument`对象由索引器或其他搜索应用程序创建。|  
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|指定丰富的预览窗口的背景的色。 此颜色是由主机设置。|  
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|指定背景色的丰富的预览窗口。 此颜色是由主机设置。|  
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|指定丰富的预览窗口中的文本字体。 此字体的信息是由主机设置。|  
  
## <a name="remarks"></a>备注  
 文档表示用户通常将打开文件打开命令，其中，并将文件另存命令与保存的数据的单位。  
  
 **CDocument**支持标准操作，如创建文档、 加载它，并将其保存。 框架处理文档中使用所定义接口**CDocument**。  
  
 应用程序可以支持多个类型的文档;例如，应用程序可能支持电子表格和文本文档。 每种类型的文档具有关联的文档模板;文档模板指定为该类型的文档使用哪些资源 （例如，菜单、 图标或快捷键对应表）。 每个文档包含一个指向其关联的`CDocTemplate`对象。  
  
 用户通过文档与之交互[CView](../../mfc/reference/cview-class.md)与之关联的对象。 视图呈现的文档框架窗口中的图像，并将用户输入解释为文档上的操作。 文档可具有与之关联的多个视图。 当用户打开的文档窗口时，框架将创建一个视图，并将其附加到该文档。 文档模板指定哪种类型的视图和框架窗口用于显示每种类型的文档。  
  
 文档属于框架的标准命令路由，并因此从标准用户界面组件 （如保存文件菜单项） 接收命令。 文档接收转发的活动视图的命令。 如果文档不处理给定的命令，它将转发到文档模板，用于管理它的命令。  
  
 文档的数据修改时，每个其视图必须反映这些修改。 **CDocument**提供[UpdateAllViews](#updateallviews)成员函数，您可以通知此类更改的视图，以便在视图可以根据需要重新绘制自己。 该框架还会提示用户在关闭前保存修改后的文件。  
  
 若要在典型的应用程序中实现的文档，必须执行以下操作︰  
  
-   从派生类**CDocument**每种类型的文档。  
  
-   添加成员变量来存储每个文档的数据。  
  
-   实现用于读取和修改文档的数据成员函数。 文档中的视图是这些成员函数的最重要的用户。  
  
-   重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)成员函数在您的文档类写入和读取该文档的数据传入和传出磁盘。  
  
 **CDocument**支持将您的文档通过邮件发送邮件支持 (MAPI) 是否存在。 请参阅文章[MAPI](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)。  
  
 有关详细信息**CDocument**，请参阅[序列化](../../mfc/serialization-in-mfc.md)，[文档/视图体系结构主题](../../mfc/document-view-architecture.md)，和[文档/视图创建](../../mfc/document-view-creation.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## <a name="requirements"></a>要求  
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
 此函数将指定的视图添加到与文档; 关联的视图的列表函数还将视图的文档指针设置到此文档。 框架将调用此函数将新创建的视图对象附加到文档中。此错误出现在响应文件新建、 打开文件、 还是新窗口中的命令或拆分的拆分器窗口时。  
  
 仅当要手动创建和附加视图，请调用此函数。 通常您就可以让连接通过定义的文档和视图的框架[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象相关联的文档类、 视图类和框架窗口类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocViewSDI #&12;](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]  
  
##  <a name="beginreadchunks"></a>CDocument::BeginReadChunks  
 初始化消息的分块读取。  
  
```  
virtual void BeginReadChunks ();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="cancloseframe"></a>CDocument::CanCloseFrame  
 显示文档的框架窗口关闭前由框架调用。  
  
```  
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>参数  
 `pFrame`  
 指向视图附加到文档的框架窗口。  
  
### <a name="return-value"></a>返回值  
 非零，则可以安全地关闭帧窗口; 如果否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现将检查是否有其他显示文档的框架窗口。 如果指定的框架窗口，显示的文档的最后一个函数将提示用户保存文档，如果它已被修改。 如果你想要执行特殊处理的框架窗口关闭时，重写此函数。 这是一个高级可重写。  
  
##  <a name="cdocument"></a>CDocument::CDocument  
 构造**CDocument**对象。  
  
```  
CDocument();
```  
  
### <a name="remarks"></a>备注  
 该框架将处理您的文档创建。 重写[OnNewDocument](#onnewdocument)成员函数以执行初始化基于每个文档; 这一点特别重要单文档界面 (SDI) 应用程序中。  
  
##  <a name="clearchunklist"></a>CDocument::ClearChunkList  
 清除消息块列表。  
  
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
 清除从路径`CDocument`对象会导致应用程序在接下来保存文档时提示用户。 这使得**保存**命令的行为类似**另存为**命令。  
  
##  <a name="deletecontents"></a>CDocument::DeleteContents  
 由框架调用以删除文档的数据，而不会破坏**CDocument**对象本身。  
  
```  
virtual void DeleteContents();
```  
  
### <a name="remarks"></a>备注  
 它只是在前调用该文档是将其销毁。 它也被称为以确保重用它之前一个文档为空。 这一点尤为重要了 SDI 应用程序，它使用只有一个文档;每当用户在创建或打开另一个文档时，将重复使用该文档。 调用此函数可实现"编辑全部清除"或类似的命令将删除所有文档的数据。 此函数的默认实现不执行任何操作。 重写此函数可删除您的文档中的数据。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&57;](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]  
  
##  <a name="findchunk"></a>CDocument::FindChunk  
 查找指定 GUID 的块区。  
  
```  
virtual POSITION FindChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>参数  
 `guid`  
 指定要查找一个块区的 GUID。  
  
 `pid`  
 指定的块区的 PID 来查找。  
  
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
 调用此函数可对此文档类型的文档模板中获取的指针。  
  
```  
CDocTemplate* GetDocTemplate() const;  
```  
  
### <a name="return-value"></a>返回值  
 此文档类型的文档模板的指针或**NULL**如果文档未被管理的文档模板。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&58; 页](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]  
  
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
 一个字符串，是所需的文件的路径。 路径可以是相对值还是绝对值。  
  
 `pError`  
 指向现有文件异常对象，该值指示该操作的完成状态的指针。  
  
 `nOpenFlags`  
 共享和访问模式。 指定当打开文件时要执行的操作。 您可以组合使用 CFile 构造函数中所列选项[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)通过使用按位 OR (| | |) 运算符。 一个访问权限和一个共享选项是必需的;**modeCreate**和**modeNoInherit**模式都是可选的。  
  
### <a name="return-value"></a>返回值  
 一个指向`CFile`对象。  
  
##  <a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition  
 调用此函数可获取与文档关联的视图的列表中的第一个视图的位置。  
  
```  
virtual POSITION GetFirstViewPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**值，可用于迭代[GetNextView](#getnextview)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&59;](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getnextview"></a>CDocument::GetNextView  
 调用此函数可循环访问的所有文档的视图。  
  
```  
virtual CView* GetNextView(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 `rPosition`  
 对引用**位置**的以前调用返回值`GetNextView`或[GetFirstViewPosition](#getfirstviewposition)成员函数。 此值不能**NULL**。  
  
### <a name="return-value"></a>返回值  
 指向由标识视图的指针`rPosition`。  
  
### <a name="remarks"></a>备注  
 该函数将返回由标识视图`rPosition`，然后设置`rPosition`到**位置**在列表中的下一视图的值。 如果检索到的视图是在列表中，最后再`rPosition`设置为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&59;](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getpathname"></a>CDocument::GetPathName  
 调用此函数可获取文档的磁盘文件的完全限定的路径。  
  
```  
const CString& GetPathName() const;  
```  
  
### <a name="return-value"></a>返回值  
 文档的完全限定的路径。 如果该文档尚未保存，或者没有与之关联的磁盘文件，该字符串为空。  
  
##  <a name="getthumbnail"></a>CDocument::GetThumbnail  
 创建要用于缩略图的提供程序显示缩略图的位图。  
  
```  
virtual BOOL GetThumbnail(
    UINT cx,  
    HBITMAP* phbmp,  
    DWORD* pdwAlpha);
```  
  
### <a name="parameters"></a>参数  
 `cx`  
 指定位图的高度和宽度。  
  
 `phbmp`  
 当该函数成功返回时包含位图的句柄。  
  
 `pdwAlpha`  
 包含在该函数将返回成功时指定的 alpha 通道值，一个 dword 值。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`成功; 否则为如果创建缩略图的位图`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettitle"></a>CDocument::GetTitle  
 调用此函数可获取文档的标题，通常派生自文档的文件名。  
  
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
 重写此方法在派生类来初始化搜索内容。 内容应与部分由分隔的字符串";"。 例如，"点;矩形;ole 项"。  
  
##  <a name="ismodified"></a>CDocument::IsModified  
 调用此函数可确定自上次保存以来是否已修改文档。  
  
```  
virtual BOOL IsModified();
```  
  
### <a name="return-value"></a>返回值  
 如果自上次保存; 该文档已被修改，则为非否则为 0。  
  
##  <a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler  
 指示是否此实例的`CDocument`搜索 < 组织处理程序创建。  
  
```  
BOOL IsSearchAndOrganizeHandler() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果此实例的`CDocument`搜索 < 组织处理程序创建。  
  
### <a name="remarks"></a>备注  
 此函数将返回当前`TRUE`仅对在进程内服务器扩展中实现的丰富预览处理程序。 您可以在您的应用程序级别，以使此函数返回设置适当的标记 （m_bPreviewHandlerMode、 m_bSearchMode、 m_bGetThumbnailMode） `TRUE`。  
  
##  <a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream  
 调用以从流加载文档数据。  
  
```  
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,  
    DWORD dwGrfMode);
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 指向流的指针。 此流提供的命令行界面。  
  
 `dwGrfMode`  
 写入流的访问模式。  
  
### <a name="return-value"></a>返回值  
 如果加载操作成功，否则为 HRESULT 错误代码为 S_OK。  
  
### <a name="remarks"></a>备注  
 您可以重写此方法在派生类以自定义如何将数据加载从流中。  
  
##  <a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode  
 指定`CDocument`对象由为缩略图的 dllhost 创建。 应签入`CView::OnDraw`。  
  
```  
BOOL m_bGetThumbnailMode;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE`指示文档由 dllhost 为缩略图。  
  
##  <a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode  
 指定`CDocument`对象由 prevhost 创建的丰富预览。 应签入`CView::OnDraw`。  
  
```  
BOOL m_bPreviewHandlerMode;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE`指示文档的丰富预览，由 prevhost 已创建。  
  
##  <a name="m_bsearchmode"></a>CDocument::m_bSearchMode  
 指定`CDocument`由索引器或其他搜索应用程序创建对象。  
  
```  
BOOL m_bSearchMode;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE`指示创建文档时通过索引器或另一个搜索应用程序。  
  
##  <a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor  
 指定的丰富的预览窗口的背景色。 此颜色是由主机设置。  
  
```  
COLORREF m_clrRichPreviewBackColor;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor  
 指定丰富预览窗口中的前景色。 此颜色是由主机设置。  
  
```  
COLORREF m_clrRichPreviewTextColor;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont  
 指定丰富预览窗口中的文本字体。 此字体的信息是由主机设置。  
  
```  
CFont m_lfRichPreviewFont;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged  
 在调用之前的丰富预览字体更改。  
  
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
 此函数的默认实现检查最后一个视图正被删除，是否是这样，将删除文档。 如果你想要在框架中添加或删除视图时执行特殊处理，重写此函数。 例如，如果您想要保持打开状态，即使没有附加到它的视图的文档，重写此函数。  
  
##  <a name="onclosedocument"></a>CDocument::OnCloseDocument  
 当文档关闭时，通常为 File Close 命令的一部分，由框架调用。  
  
```  
virtual void OnCloseDocument();
```  
  
### <a name="remarks"></a>备注  
 此函数的默认实现将破坏所有框架用于查看文档、 关闭视图、 清理文档的内容，然后调用[DeleteContents](#deletecontents)成员函数删除文档的数据。  
  
 如果您想要执行的特殊清理处理框架关闭文档时，重写此函数。 例如，如果文档表示数据库中的记录，您可能想要重写此函数以关闭该数据库。 通过重写应调用此函数的基类版本。  
  
##  <a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame  
 仅在需要创建丰富预览的预览帧时由框架调用。  
  
```  
virtual BOOL OnCreatePreviewFrame();
```  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果成功; 否则为创建框架`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondocumentevent"></a>CDocument::OnDocumentEvent  
 由对文档事件作出响应框架调用。  
  
```  
virtual void OnDocumentEvent(DocumentEvent deEvent);
```  
  
### <a name="parameters"></a>参数  
 [in] `deEvent`  
 枚举的数据类型，用于描述事件的类型。  
  
### <a name="remarks"></a>备注  
 文档事件可能会影响多个类。 此方法负责处理而不影响类的文档事件[CDocument 类](../../mfc/reference/cdocument-class.md)。 目前，唯一必须对文档事件做出响应的类是[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。 `CDocument`类具有负责处理产生的影响上其他可重写方法`CDocument`。  
  
 下表列出的可能值`deEvent`以及与其对应的事件。  
  
|值|相应的事件|  
|-----------|-------------------------|  
|`onAfterNewDocument`|已创建一个新的文档。|  
|`onAfterOpenDocument`|已打开一个新的文档。|  
|`onAfterSaveDocument`|保存文档。|  
|`onAfterCloseDocument`|该文档已关闭。|  
  
##  <a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail  
 重写此方法在派生类来绘制缩略图中。  
  
```  
virtual void OnDrawThumbnail(
    CDC& dc,  
    LPRECT lprcBounds);
```  
  
### <a name="parameters"></a>参数  
 `dc`  
 对设备上下文的引用。  
  
 `lprcBounds`  
 指定应在其中绘制该缩略图的区域的边框。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onfilesendmail"></a>CDocument::OnFileSendMail  
 从常驻邮件主机发送的消息 （如果有） 将包含发送文档以附件形式。  
  
```  
void OnFileSendMail();
```  
  
### <a name="remarks"></a>备注  
 `OnFileSendMail`调用[OnSaveDocument](#onsavedocument)要序列化 （保存） 到一个临时文件，然后通过电子邮件发送的未命名和修改文档。 如果文档未进行修改，则不需要的临时文件;发送原始。 `OnFileSendMail`加载 MAPI32。如果尚未加载的 DLL。  
  
 一种特殊的实现`OnFileSendMail`为[COleDocument](../../mfc/reference/coledocument-class.md)句柄正确复合文件。  
  
 **CDocument**支持将您的文档通过邮件发送邮件支持 (MAPI) 是否存在。 请参阅文章[MAPI 主题](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)。  
  
##  <a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream  
 当它需要从流加载文档数据时由框架调用。  
  
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
 如果负载是成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onnewdocument"></a>CDocument::OnNewDocument  
 由框架作为文件新建命令的一部分调用。  
  
```  
virtual BOOL OnNewDocument();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果已成功初始化文档;否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[DeleteContents](#deletecontents)成员函数，以确保文档是空的并且随后会标记为干净的新文档。 重写此函数可初始化新文档的数据结构。 通过重写应调用此函数的基类版本。  
  
 如果用户在 SDI 应用程序中选择新建文件命令，框架将使用此函数以重新初始化现有的文档，而不是创建一个新。 如果用户在多文档界面 (MDI) 应用程序中选择新文件时，框架将创建一个新文档每次，然后调用此函数可对其进行初始化。 必须将您的初始化代码放在此函数，而不是在新建文件命令是在 SDI 应用程序中有效的构造函数。  
  
 请注意，在事例`OnNewDocument`调用两次。 在作为 ActiveX 文档服务器嵌入文档，将发生这种情况。 第一次调用该函数`CreateInstance`方法 (由`COleObjectFactory`-派生类) 和第二次通过`InitNew`方法 (由`COleServerDoc`-派生类)。  
  
### <a name="example"></a>示例  
 下面的示例说明了初始化文档对象的替代方法。  
  
 [!code-cpp[NVC_MFCDocView #&60;](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&61;](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&62;](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
##  <a name="onopendocument"></a>CDocument::OnOpenDocument  
 由框架作为文件打开命令的一部分调用。  
  
```  
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 指向要打开的文档的路径。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功加载该文档;否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现将打开指定的文件中，调用[DeleteContents](#deletecontents)成员函数，以确保该文档为空，将调用[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)来读取该文件的内容，然后将标记为干净的文档。 如果你想要使用的内容存档机制或文件机制以外，重写此函数。 例如，您可能编写文档表示数据库，而不是单独的文件中的记录的其中一个应用程序。  
  
 如果用户在 SDI 应用程序中选择文件打开命令，框架将使用此函数重新初始化现有**CDocument**对象，而不是创建一个新。 如果用户选择在 MDI 应用程序中打开文件，该框架构造一个新**CDocument**对象每次，然后调用此函数可对其进行初始化。 必须将您的初始化代码放在此函数，而不是在文件打开命令是在 SDI 应用程序中有效的构造函数。  
  
### <a name="example"></a>示例  
 下面的示例说明了初始化文档对象的替代方法。  
  
 [!code-cpp[NVC_MFCDocView #&60;](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&61;](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&62;](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&63;](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]  
  
##  <a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus  
 指示要返回 HWND 检索调用的预览处理程序`GetFocus`函数。  
  
```  
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```  
  
### <a name="parameters"></a>参数  
 `phwnd`  
 [out]此方法返回时，包含指向从调用返回的 HWND`GetFocus`预览处理程序的前台线程中的函数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK 返回或以其他方式错误值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator  
 指示要从在其中预览处理程序正在运行的进程的消息泵中向上传递键击处理的预览处理程序。  
  
```  
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```  
  
### <a name="parameters"></a>参数  
 `pmsg`  
 [in]指向窗口消息的指针。  
  
### <a name="return-value"></a>返回值  
 如果键击消息可以由预览处理程序处理，该处理程序处理它，并返回，则为 S_OK。 如果预览处理程序无法处理键击消息，它提供给宿主通过`IPreviewHandlerFrame::TranslateAccelerator`。 如果主机处理消息时，此方法返回，则为 S_OK。 如果主机不会处理该消息，此方法将返回 S_FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged  
 丰富的预览背景色发生更改时调用。  
  
```  
virtual void OnRichPreviewBackColorChanged();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged  
 当已将丰富预览字体更改时调用。  
  
```  
virtual void OnRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged  
 丰富的预览站点发生更改时调用。  
  
```  
virtual void OnRichPreviewSiteChanged();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged  
 丰富预览文本颜色发生更改时调用。  
  
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
 非零，如果已成功保存文档。否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现将打开指定的文件中，调用[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)文档的数据写入文件，然后标记将文档作为清理。 如果你想要执行特殊处理，当框架保存文档时，重写此函数。 例如，您可能编写文档表示数据库，而不是单独的文件中的记录的其中一个应用程序。  
  
##  <a name="onunloadhandler"></a>CDocument::OnUnloadHandler  
 预览处理程序将在卸载时由框架调用。  
  
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
 一个指向[CCmdUI](../../mfc/reference/ccmdui-class.md)与关联对象**ID_FILE_SEND_MAIL**命令。  
  
### <a name="remarks"></a>备注  
 否则该函数将删除**ID_FILE_SEND_MAIL**命令从菜单中，包括分隔符上面或下面的菜单项视情况而定。 如果启用 MAPI MAPI32。DLL 文件的路径中，并赢得 [邮件] 部分中出现。INI 文件中，MAPI =&1;。 大多数应用程序放在文件菜单上的此命令。  
  
 **CDocument**支持将您的文档通过邮件发送邮件支持 (MAPI) 是否存在。 请参阅文章[MAPI 主题](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)。  
  
##  <a name="precloseframe"></a>CDocument::PreCloseFrame  
 销毁框架窗口之前，将由框架调用此成员函数。  
  
```  
virtual void PreCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>参数  
 `pFrame`  
 指向[CFrameWnd](../../mfc/reference/cframewnd-class.md) ，它持有关联**CDocument**对象。  
  
### <a name="remarks"></a>备注  
 它可以重写以提供自定义清理，但一定要调用基类的类。  
  
 默认值为`PreCloseFrame`不执行任何操作**CDocument**。 **CDocument**的派生类[COleDocument](../../mfc/reference/coledocument-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)使用此成员函数。  
  
##  <a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue  
 读取下一个块区值。  
  
```  
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```  
  
### <a name="parameters"></a>参数  
 `ppValue`  
 [out]当函数返回时，`ppValue`包含读取的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="releasefile"></a>CDocument::ReleaseFile  
 此成员函数是由框架调用以释放文件，使其可供使用的其他应用程序。  
  
```  
virtual void ReleaseFile(
    CFile* pFile,  
    BOOL bAbort);
```  
  
### <a name="parameters"></a>参数  
 `pFile`  
 指向要释放的 CFile 对象的指针。  
  
 `bAbort`  
 指定文件是否是通过使用释放`CFile::Close`或`CFile::Abort`。 **FALSE**如果文件是要释放使用[CFile::Close](../../mfc/reference/cfile-class.md#close);**TRUE**如果文件是要释放使用[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="remarks"></a>备注  
 如果`bAbort`是**TRUE**，`ReleaseFile`调用`CFile::Abort`，并释放该文件。 `CFile::Abort`不会引发异常。  
  
 如果`bAbort`是**FALSE**，`ReleaseFile`调用`CFile::Close`上并释放该文件。  
  
 重写该成员函数以释放该文件之前需要用户执行操作。  
  
##  <a name="removechunk"></a>CDocument::RemoveChunk  
 删除带有指定 GUID 的区块。  
  
```  
virtual void RemoveChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>参数  
 `Guid`  
 指定要删除区块的 GUID。  
  
 `Pid`  
 指定要删除区块的 PID。  
  
### <a name="remarks"></a>备注  
  
##  <a name="removeview"></a>CDocument::RemoveView  
 调用此函数可分离文档中的一个视图。  
  
```  
void RemoveView(CView* pView);
```  
  
### <a name="parameters"></a>参数  
 `pView`  
 指向要删除的视图。  
  
### <a name="remarks"></a>备注  
 此函数从与文档; 关联的视图的列表中移除指定的视图它还将视图的文档指针设置**NULL**。 框架窗口已关闭或关闭拆分器窗口中的某一窗格时，将由框架调用此函数。  
  
 仅当您将手动分离视图，请调用此函数。 通常您就可以让通过定义分离文档和视图的框架[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象相关联的文档类、 视图类和框架窗口类。  
  
 参阅位于示例[AddView](#addview)有关示例实现。  
  
##  <a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException  
 如果引发异常，则调用 (通常[CFileException](../../mfc/reference/cfileexception-class.md)或[CArchiveException](../../mfc/reference/carchiveexception-class.md)) 时保存或加载该文档。  
  
```  
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,  
    CException* e,  
    BOOL bSaving,  
    UINT nIDPDefault);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 指向正在的文档的名称保存或加载。  
  
 *e*  
 指向已引发的异常。 可能是**NULL**。  
  
 *bSaving*  
 该标志指明哪项操作正在进行中;如果要保存文档，0 已加载该文档如果非零。  
  
 `nIDPDefault`  
 该函数不指定一个更具体的情况下显示的错误消息的标识符。  
  
### <a name="remarks"></a>备注  
 默认实现将检查异常对象，并查找专门描述的原因的错误消息。 如果找不到特定的消息或*e*是**NULL**，由指定的常规消息`nIDPDefault`使用参数。 然后，该函数将显示包含错误消息的消息框。 如果您想要提供其他自定义错误消息，重写此函数。 这是一个高级可重写。  
  
##  <a name="savemodified"></a>CDocument::SaveModified  
 要关闭修改后的文档之前，由框架调用。  
  
```  
virtual BOOL SaveModified();
```  
  
### <a name="return-value"></a>返回值  
 非零，则可以安全地继续并关闭文档; 如果如果文档不应该关闭，则为 0。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现将显示消息框，询问用户是否将所做的更改保存到文档中，如果未进行任何。 如果您的程序要求一个不同的提示过程，重写此函数。 这是一个高级可重写。  
  
##  <a name="setchunkvalue"></a>CDocument::SetChunkValue  
 设置消息块值。  
  
```  
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>参数  
 `pValue`  
 指定一个块区值来设置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setmodifiedflag"></a>CDocument::SetModifiedFlag  
 对文档进行任何修改后，请调用此函数。  
  
```  
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bModified`  
 该标志指明是否已修改文档。  
  
### <a name="remarks"></a>备注  
 通过一致地调用此函数时，可以确保框架提示用户关闭文档之前保存的更改。 通常应使用的默认值**TRUE**为`bModified`参数。 要将文档作为清理标记 （未修改），用来调用此函数的值为**FALSE**。  
  
##  <a name="setpathname"></a>CDocument::SetPathName  
 调用此函数可指定文档的磁盘文件的完全限定的路径。  
  
```  
virtual void SetPathName(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 指向要用作文档的路径的字符串。  
  
 `bAddToMRU`  
 确定是否将文件名添加到最近使用的 (MRU) 文件列表。 如果**为 TRUE，**添加文件名; 如果**FALSE**，将不会添加。  
  
### <a name="remarks"></a>备注  
 具体取决于值`bAddToMRU`的路径不添加，或者未添加到应用程序维护的 MRU 列表。 请注意，某些文档不与磁盘文件相关联。 仅当您要重写用于打开和保存文件由框架使用的默认实现调用此函数。  
  
##  <a name="settitle"></a>CDocument::SetTitle  
 调用此函数可指定文档的标题 （框架窗口的标题栏中显示的字符串）。  
  
```  
virtual void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>参数  
 `lpszTitle`  
 指向要用作文档的标题的字符串。  
  
### <a name="remarks"></a>备注  
 调用此函数将更新所有显示的文档的框架窗口的标题。  
  
##  <a name="updateallviews"></a>CDocument::UpdateAllViews  
 调用此函数后修改该文档。  
  
```  
void UpdateAllViews(
    CView* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pSender`  
 指向修改了文档的视图或**NULL**如果要更新的所有视图都数。  
  
 `lHint`  
 包含有关修改信息。  
  
 `pHint`  
 指向以存储修改的相关信息的对象。  
  
### <a name="remarks"></a>备注  
 在您调用后，应调用此函数[SetModifiedFlag](#setmodifiedflag)成员函数。 此函数会通知每个视图的附加到文档时，由指定的视图除外`pSender`，该文档已被修改。 通常需要调用此函数通过视图类用户更改通过视图文档之后。  
  
 此函数将调用[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)除发送的文档中的视图的每个成员函数查看，请传递`pHint`和`lHint`。 使用这些参数将信息传递给视图获取有关对文档进行修改。 您可以使用信息进行编码`lHint`和/或您可以定义[CObject](../../mfc/reference/cobject-class.md)的派生类以存储信息所做的修改并传递一个对象的类使用`pHint`。 重写`CView::OnUpdate`成员函数在您[CView](../../mfc/reference/cview-class.md)的派生类来优化基于传递的信息的视图的显示的更新。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&64;](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 MDIDOCVW](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [MFC 示例 NPP](../../visual-cpp-samples.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)

