---
title: CDocument 类
ms.date: 11/04/2016
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
ms.openlocfilehash: d356ba6b6134221c2fc9595fc6d78f91961c5b7f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753245"
---
# <a name="cdocument-class"></a>CDocument 类

提供用户定义文档类的基本功能。

## <a name="syntax"></a>语法

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDocument：CDocument](#cdocument)|构造 `CDocument` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDocument：：添加视图](#addview)|将视图附加到文档。|
|[CDocument：：开始阅读](#beginreadchunks)|初始化块读取。|
|[CDocument：：可以关闭框架](#cancloseframe)|高级可重写;在关闭查看此文档的框架窗口之前调用。|
|[CDocument：清除块列表](#clearchunklist)|清除块列表。|
|[CDocument：：清除路径名称](#clearpathname)|清除文档对象的路径。|
|[CDocument：:D内容](#deletecontents)|调用 以执行文档的清理。|
|[CDocument：：查找块](#findchunk)|查找具有指定 GUID 的块。|
|[CDocument：：获取适配器](#getadapter)|返回指向对象实现`IDocument`接口的指针。|
|[CDocument：：获取文档模板](#getdoctemplate)|返回指向描述文档类型的文档模板的指针。|
|[CDocument：：获取文件](#getfile)|返回指向所需`CFile`对象的指针。|
|[CDocument：获取第一视图位置](#getfirstviewposition)|返回视图列表中第一个位置;用于开始迭代。|
|[CDocument：：获取下一个视图](#getnextview)|通过与文档关联的视图列表进行一次遍视。|
|[CDocument：：获取路径名称](#getpathname)|返回文档数据文件的路径。|
|[CDocument：：获取缩略图](#getthumbnail)|调用 以创建要由缩略图提供程序用于显示缩略图的位图。|
|[CDocument：：获取标题](#gettitle)|返回文档的标题。|
|[CDocument：：初始化搜索内容](#initializesearchcontent)|已调用以初始化搜索处理程序的搜索内容。|
|[CDocument：：已修改](#ismodified)|指示自上次保存文档以来是否已修改文档。|
|[CDocument：：正在搜索和组织处理程序](#issearchandorganizehandler)|告知此`CDocument`对象实例是否为搜索&组织处理程序创建。|
|[CDocument：：从流加载文档](#loaddocumentfromstream)|调用以加载流中的文档数据。|
|[CDocument：：在里希预览字体更改之前打开](#onbeforerichpreviewfontchanged)|在更改"富预览"字体之前调用。|
|[CDocument：：打开查看列表](#onchangedviewlist)|在将视图添加到文档或从文档中删除后调用。|
|[CDocument：：打开文档](#onclosedocument)|已调用以关闭文档。|
|[CDocument：：在创建预览框架](#oncreatepreviewframe)|当需要为富预览创建预览框架时，由框架调用。|
|[CDocument：：在文档事件](#ondocumentevent)|框架为响应文档事件而调用。|
|[CDocument：：在缩略图上](#ondrawthumbnail)|重写派生类中的此方法以绘制缩略图的内容。|
|[CDocument：：从流加载文档](#onloaddocumentfromstream)|当需要从流加载文档数据时，由框架调用。|
|[CDocument：：关于新文档](#onnewdocument)|调用以创建新文档。|
|[CDocument：：打开文档](#onopendocument)|已调用以打开现有文档。|
|[CDocument：：在预览处理程序查询焦点](#onpreviewhandlerqueryfocus)|指示预览处理程序从调用 GetFocus 函数返回 HWND。|
|[CDocument：：在预览处理程序翻译加速器](#onpreviewhandlertranslateaccelerator)|指示预览处理程序处理从运行预览处理程序的进程的消息泵传入的击键。|
|[CDocument：：在里希预览背面颜色已更改](#onrichpreviewbackcolorchanged)|在"富预览"背景颜色已更改时调用。|
|[CDocument：：在里希预览字体上](#onrichpreviewfontchanged)|在"富预览"字体已更改时调用。|
|[CDocument：：在里希预览网站更改](#onrichpreviewsitechanged)|在"丰富预览"网站已更改时调用。|
|[CDocument：：在里希预览文本颜色修改](#onrichpreviewtextcolorchanged)|在"富预览"文本颜色已更改时调用。|
|[CDocument：：在保存文档上](#onsavedocument)|调用以将文档保存到磁盘。|
|[CDocument：：打开卸载处理程序](#onunloadhandler)|在卸载预览处理程序时由框架调用。|
|[CDocument：:P重新关闭框架](#precloseframe)|在框架窗口关闭之前调用。|
|[CDocument：：阅读下一个块值](#readnextchunkvalue)|读取下一个块值。|
|[CDocument：：发布文件](#releasefile)|释放文件，使其可供其他应用程序使用。|
|[CDocument：：删除块](#removechunk)|删除具有指定 GUID 的块。|
|[CDocument：：删除查看](#removeview)|从文档分离视图。|
|[CDocument：：报告保存加载异常](#reportsaveloadexception)|高级可重写;当由于异常而无法完成打开或保存操作时调用。|
|[CDocument：：保存修改](#savemodified)|高级可重写;调用 以询问用户是否应保存文档。|
|[CDocument：：设置块值](#setchunkvalue)|设置块值。|
|[CDocument：：设置修改后的 Flag](#setmodifiedflag)|设置一个标志，指示自上次保存文档以来已修改文档。|
|[CDocument：：设置路径名称](#setpathname)|设置文档使用的数据文件的路径。|
|[CDocument：：设置标题](#settitle)|设置文档的标题。|
|[CDocument：：更新所有视图](#updateallviews)|通知文档已修改的所有视图。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CDocument：：在文件发送邮件](#onfilesendmail)|发送附有文档的邮件。|
|[CDocument：：更新文件发送邮件](#onupdatefilesendmail)|如果存在邮件支持，请启用"发送邮件"命令。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDocument：：m_bGetThumbnailMode](#m_bgetthumbnailmode)|指定该`CDocument`对象由缩略图的 dllhost 创建。 应签入`CView::OnDraw`。|
|[CDocument：：m_bPreviewHandlerMode](#m_bpreviewhandlermode)|指定对象`CDocument`由 的预主为`Rich Preview`创建。 应签入`CView::OnDraw`。|
|[CDocument：m_bSearchMode](#m_bsearchmode)|指定`CDocument`对象由索引器或其他搜索应用程序创建。|
|[CDocument：：m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|指定"富预览"窗口的背景颜色。 此颜色由主机设置。|
|[CDocument：：m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|指定"富预览"窗口的前景颜色。 此颜色由主机设置。|
|[CDocument：：m_lfRichPreviewFont](#m_lfrichpreviewfont)|为"富预览"窗口指定文本字体。 此字体信息由主机设置。|

## <a name="remarks"></a>备注

文档表示用户通常使用文件打开命令打开的数据单元，并保存文件保存命令。

`CDocument`支持标准操作，如创建文档、加载文档和保存文档。 框架使用 定义的`CDocument`接口操作文档。

应用程序可以支持多种类型的文档;但是，应用程序可以支持多种类型的文档。例如，应用程序可能同时支持电子表格和文本文档。 每种类型的文档都有关联的文档模板;文档模板指定用于该类型文档的资源（例如，菜单、图标或快捷键表）。 每个文档都包含指向其关联`CDocTemplate`对象的指针。

用户通过与其关联的[CView](../../mfc/reference/cview-class.md)对象与文档进行交互。 视图在框架窗口中呈现文档的图像，并将用户输入解释为对文档的操作。 文档可以有多个与其关联的视图。 当用户打开文档上的窗口时，框架将创建一个视图并将其附加到文档。 文档模板指定用于显示每种文档类型的视图和框架窗口的类型。

文档是框架的标准命令路由的一部分，因此接收来自标准用户界面组件的命令（如文件保存菜单项）。 文档接收活动视图转发的命令。 如果文档不处理给定命令，它将该命令转发给管理该命令的文档模板。

修改文档数据时，其每个视图都必须反映这些修改。 `CDocument`提供[UpdateAllViews](#updateallviews)成员函数，以便通知您此类更改的视图，以便视图可以根据需要重新绘制它们。 框架还提示用户在关闭修改后的文件之前保存该文件。

要在典型应用程序中实现文档，必须执行以下操作：

- 从`CDocument`每种类型的文档派生类。

- 添加成员变量以存储每个文档的数据。

- 实现用于读取和修改文档数据的成员函数。 文档的视图是这些成员函数的最重要用户。

- 覆盖[CObject：：序列化](../../mfc/reference/cobject-class.md#serialize)文档类中的成员函数，以在磁盘和磁盘中写入和读取文档的数据。

`CDocument`支持通过邮件支持 （MAPI） 发送文档。 请参阅 MFC 中的[MAPI](../../mfc/mapi.md)和[MAPI 支持](../../mfc/mapi-support-in-mfc.md)文章。

有关`CDocument`的详细信息，请参阅[序列化](../../mfc/serialization-in-mfc.md)、[文档/视图体系结构主题](../../mfc/document-view-architecture.md)和[文档/视图创建](../../mfc/document-view-creation.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cdocumentaddview"></a><a name="addview"></a>CDocument：：添加视图

调用此函数以将视图附加到文档。

```cpp
void AddView(CView* pView);
```

### <a name="parameters"></a>参数

*pView*<br/>
指向要添加的视图。

### <a name="remarks"></a>备注

此函数将指定的视图添加到与文档关联的视图列表中;该函数还设置视图的文档指针到此文档。 将新创建的视图对象附加到文档时，框架将调用此功能;这将用于响应文件新建、文件打开或新建窗口命令或拆分窗口时发生的。

仅当手动创建和附加视图时，才调用此功能。 通常，通过定义[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象来关联文档类、视图类和框架窗口类，允许框架连接文档和视图。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

## <a name="cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>CDocument：：开始阅读

初始化块读取。

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>备注

## <a name="cdocumentcancloseframe"></a><a name="cancloseframe"></a>CDocument：：可以关闭框架

框架在关闭显示文档的框架窗口之前调用。

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>参数

*pFrame*<br/>
指向附加到文档的视图的帧窗口。

### <a name="return-value"></a>返回值

如果可以安全地关闭框架窗口，则非零;否则 0。

### <a name="remarks"></a>备注

默认实现检查是否有其他框架窗口显示文档。 如果指定的框架窗口是显示文档的最后一个框架窗口，则函数将提示用户保存文档（如果文档已被修改）。 如果要在框架窗口关闭时执行特殊处理，则重写此函数。 这是一个高级的可重写。

## <a name="cdocumentcdocument"></a><a name="cdocument"></a>CDocument：CDocument

构造 `CDocument` 对象。

```
CDocument();
```

### <a name="remarks"></a>备注

框架为您处理文档创建。 覆盖[OnNewDocument](#onnewdocument)成员函数，以按文档执行初始化;这在单文档接口 （SDI） 应用程序中尤其重要。

## <a name="cdocumentclearchunklist"></a><a name="clearchunklist"></a>CDocument：清除块列表

清除块列表。

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>备注

## <a name="cdocumentclearpathname"></a><a name="clearpathname"></a>CDocument：：清除路径名称

清除文档对象的路径。

```
virtual void ClearPathName();
```

### <a name="remarks"></a>备注

从`CDocument`对象清除路径会导致应用程序在下次保存文档时提示用户。 这使得 **"保存"** 命令类似于 **"保存为"** 命令。

## <a name="cdocumentdeletecontents"></a><a name="deletecontents"></a>CDocument：:D内容

由框架调用以删除文档的数据而不破坏`CDocument`对象本身。

```
virtual void DeleteContents();
```

### <a name="remarks"></a>备注

在销毁文档之前调用它。 还调用它以确保文档在重用之前为空。 这对仅使用一个文档的 SDI 应用程序尤其重要;每当用户创建或打开另一个文档时，文档都会被重用。 调用此函数以实现删除文档所有数据的"全部编辑清除"或类似命令。 此函数的默认实现不执行任何操作。 重写此函数以删除文档中的数据。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

## <a name="cdocumentfindchunk"></a><a name="findchunk"></a>CDocument：：查找块

查找具有指定 GUID 的块。

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>参数

*guid*<br/>
指定要查找的块的 GUID。

*Pid*<br/>
指定要查找的块的 PID。

### <a name="return-value"></a>返回值

如果成功，则位于内部区块列表中的位置。 否则 NULL。

### <a name="remarks"></a>备注

## <a name="cdocumentgetadapter"></a><a name="getadapter"></a>CDocument：：获取适配器

返回指向实现接口的对象的`IDocument`指针。

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>返回值

指向实现接口的对象的`IDocument`指针。

### <a name="remarks"></a>备注

## <a name="cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>CDocument：：获取文档模板

调用此函数以获取指向此文档类型的文档模板的指针。

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>返回值

指向此文档类型的文档模板的指针，如果文档不是由文档模板管理，则指向 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

## <a name="cdocumentgetfile"></a><a name="getfile"></a>CDocument：：获取文件

调用此成员函数以获取指向`CFile`对象的指针。

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>参数

*lpszFile名称*<br/>
是所需文件的路径的字符串。 路径可以是相对路径，也可以是绝对路径。

*pError*<br/>
指向指示操作完成状态的现有文件异常对象的指针。

*nOpenFlags*<br/>
共享和访问模式。 指定打开文件时要执行的操作。 您可以使用位或（&#124;）运算符组合 CFile 构造函数[CFile：：CFile](../../mfc/reference/cfile-class.md#cfile)中列出的选项。 需要一个访问权限和一个共享选项;`modeCreate`和`modeNoInherit`模式是可选的。

### <a name="return-value"></a>返回值

一个指向 `CFile` 对象的指针。

## <a name="cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>CDocument：获取第一视图位置

调用此函数以获取有关文档关联的视图列表中第一个视图的位置。

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>返回值

可用于使用[GetNextView](#getnextview)成员函数进行迭代的定位值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetnextview"></a><a name="getnextview"></a>CDocument：：获取下一个视图

调用此函数以遍接文档的所有视图。

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>参数

*r定位*<br/>
对前一个调用`GetNextView`或[GetFirstViewPosition](#getfirstviewposition)成员函数返回的定位值的引用。 此值不能为 NULL。

### <a name="return-value"></a>返回值

指向 r定位标识的视图*的指针*。

### <a name="remarks"></a>备注

函数返回*由 r定位*标识的视图，然后将*r定位*设置到列表中下一个视图的"位置"值。 如果检索到的视图是列表中的最后一个视图，则*r定位*设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetpathname"></a><a name="getpathname"></a>CDocument：：获取路径名称

调用此函数获取文档磁盘文件的完全限定路径。

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>返回值

文档的完全限定路径。 如果文档尚未保存或没有与其关联的磁盘文件，则此字符串为空。

## <a name="cdocumentgetthumbnail"></a><a name="getthumbnail"></a>CDocument：：获取缩略图

创建要由缩略图提供程序用于显示缩略图的位图。

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>参数

*残雪*<br/>
指定位图的宽度和高度。

*phbmp*<br/>
当函数成功返回时，包含位图的句柄。

*pdwAlpha*<br/>
包含指定 Alpha 通道值的 DWORD，当函数成功返回时。

### <a name="return-value"></a>返回值

如果成功创建了缩略图的位图，则返回 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cdocumentgettitle"></a><a name="gettitle"></a>CDocument：：获取标题

调用此函数获取文档的标题，该标题通常派生自文档的文件名。

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>返回值

文档的标题。

## <a name="cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>CDocument：：初始化搜索内容

已调用以初始化搜索处理程序的搜索内容。

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>备注

重写派生类中的此方法以初始化搜索内容。 内容应为字符串，其部分以";"分隔。 例如，"点;"矩形;ole 项目"。

## <a name="cdocumentismodified"></a><a name="ismodified"></a>CDocument：：已修改

调用此函数以确定文档自上次保存以来是否已修改。

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>返回值

自上次保存文档以来已修改的文档，则非零;否则 0。

## <a name="cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>CDocument：：正在搜索和组织处理程序

说明是否为搜索&`CDocument`组织处理程序创建了此实例。

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>返回值

如果为搜索&组织处理程序`CDocument`创建了此实例，则返回 TRUE。

### <a name="remarks"></a>备注

目前，此函数仅对在进程外服务器中实现的富预览处理程序返回 TRUE。 您可以在应用程序级别设置适当的标志（m_bPreviewHandlerMode、m_bSearchMode、m_bGetThumbnailMode），以使此函数返回 TRUE。

## <a name="cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>CDocument：：从流加载文档

调用以加载流中的文档数据。

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>参数

*pStream*<br/>
指向流的指针。 此流由 Shell 提供。

*德夫格夫莫德*<br/>
访问流模式。

### <a name="return-value"></a>返回值

如果加载操作成功，S_OK，否则使用错误代码的 HRESULT。

### <a name="remarks"></a>备注

可以在派生类中重写此方法，以自定义如何从流中加载数据。

## <a name="cdocumentm_bgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>CDocument：：m_bGetThumbnailMode

指定`CDocument`对象由缩略图的 dllhost 创建。 应签入`CView::OnDraw`。

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>备注

`TRUE`指示文档是由缩略图的 dllhost 创建的。

## <a name="cdocumentm_bpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>CDocument：：m_bPreviewHandlerMode

指定`CDocument`对象由富预览的前主创建。 应签入`CView::OnDraw`。

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>备注

TRUE 表示文档是由"富预览"的前主创建的。

## <a name="cdocumentm_bsearchmode"></a><a name="m_bsearchmode"></a>CDocument：m_bSearchMode

指定`CDocument`对象由索引器或其他搜索应用程序创建。

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>备注

`TRUE`指示文档是由索引器或其他搜索应用程序创建的。

## <a name="cdocumentm_clrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>CDocument：：m_clrRichPreviewBackColor

指定"富预览"窗口的背景颜色。 此颜色由主机设置。

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>备注

## <a name="cdocumentm_clrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>CDocument：：m_clrRichPreviewTextColor

指定"富预览"窗口的前景颜色。 此颜色由主机设置。

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>备注

## <a name="cdocumentm_lfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>CDocument：：m_lfRichPreviewFont

指定"富预览"窗口的文本字体。 此字体信息由主机设置。

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>备注

## <a name="cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>CDocument：：在里希预览字体更改之前打开

在更改"富预览"字体之前调用。

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>备注

## <a name="cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>CDocument：：打开查看列表

在将视图添加到文档或从文档中删除视图后由框架调用。

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>备注

此函数的默认实现检查是否删除了最后一个视图，如果是，则删除文档。 如果要在框架添加或删除视图时执行特殊处理，则重写此函数。 例如，如果希望文档保持打开状态，即使文档没有附加视图，则重写此函数。

## <a name="cdocumentonclosedocument"></a><a name="onclosedocument"></a>CDocument：：打开文档

在文档关闭时由框架调用，通常作为文件关闭命令的一部分调用。

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>备注

此函数的默认实现将销毁用于查看文档的所有帧、关闭视图、清理文档内容，然后调用[DeleteContents](#deletecontents)成员函数删除文档的数据。

如果要在框架关闭文档时执行特殊的清理处理，请覆盖此函数。 例如，如果文档表示数据库中的记录，则可能需要重写此函数以关闭数据库。 应从重写调用此函数的基类版本。

## <a name="cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>CDocument：：在创建预览框架

当需要为富预览创建预览框架时，由框架调用。

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>返回值

如果框架已成功创建，则返回 TRUE;如果框架已成功创建，则返回 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cdocumentondocumentevent"></a><a name="ondocumentevent"></a>CDocument：：在文档事件

框架为响应文档事件而调用。

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>参数

*deEvent*<br/>
[在]描述事件类型的枚举数据类型。

### <a name="remarks"></a>备注

文档事件可能会影响多个类。 此方法负责处理影响[CDocument 类](../../mfc/reference/cdocument-class.md)以外的类的文档事件。 目前，必须响应文档事件的唯一类是[CDataRecoveryHandler 类](../../mfc/reference/cdatarecoveryhandler-class.md)。 类`CDocument`还有其他可重写的方法，负责处理对 的影响`CDocument`。

下表列出了*deEvent*的可能值及其对应的事件。

|“值”|相应的事件|
|-----------|-------------------------|
|`onAfterNewDocument`|已创建新文档。|
|`onAfterOpenDocument`|打开了一个新文档。|
|`onAfterSaveDocument`|文档已保存。|
|`onAfterCloseDocument`|文档已关闭。|

## <a name="cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>CDocument：：在缩略图上

重写派生类中的此方法以绘制缩略图。

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>参数

*直流*<br/>
对设备上下文的引用。

*lprcBounds*<br/>
指定应绘制缩略图的区域的边界矩形。

### <a name="remarks"></a>备注

## <a name="cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>CDocument：：在文件发送邮件

通过驻留邮件主机（如果有）发送邮件，并将文档作为附件。

```cpp
void OnFileSendMail();
```

### <a name="remarks"></a>备注

`OnFileSendMail`调用[OnSaveDocument](#onsavedocument)将无标题和修改的文档序列化（保存）到临时文件，然后通过电子邮件发送。 如果文档尚未修改，则不需要临时文件;因此，不需要临时文件。原始文件已发送。 `OnFileSendMail`加载 MAPI32。尚未加载 DLL。

[COleDocument](../../mfc/reference/coledocument-class.md) `OnFileSendMail`的特殊实现可正确处理复合文件。

`CDocument`支持通过邮件支持 （MAPI） 发送文档。 请参阅 MFC 中的[MAPI 主题](../../mfc/mapi.md)和[MAPI 支持](../../mfc/mapi-support-in-mfc.md)文章。

## <a name="cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>CDocument：：从流加载文档

当需要从流加载文档数据时，由框架调用。

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>参数

*pStream*<br/>
指向传入流的指针。

*grfMode*<br/>
访问流模式。

### <a name="return-value"></a>返回值

如果负载成功，S_OK;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cdocumentonnewdocument"></a><a name="onnewdocument"></a>CDocument：：关于新文档

框架作为"文件新"命令的一部分调用。

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>返回值

如果文档已成功初始化，则非零;否则 0。

### <a name="remarks"></a>备注

此函数的默认实现调用[DeleteContents](#deletecontents)成员函数，以确保文档为空，然后将新文档标记为干净。 重写此函数以初始化新文档的数据结构。 应从重写调用此函数的基类版本。

如果用户在 SDI 应用程序中选择"文件新"命令，则框架使用此函数重新初始化现有文档，而不是创建新文档。 如果用户在多个文档接口 （MDI） 应用程序中选择"文件新建"，则框架每次都会创建新文档，然后调用此函数进行初始化。 您必须将初始化代码放在此函数中，而不是将初始化代码放在构造函数中，以便 File New 命令在 SDI 应用程序中有效。

请注意，在某些情况下`OnNewDocument`，调用两次。 当文档嵌入为 ActiveX 文档服务器时，将发生这种情况。 函数`CreateInstance`首先由方法调用（`COleObjectFactory`由派生类公开），第二次由`InitNew`方法调用（由`COleServerDoc`派生类公开）。

### <a name="example"></a>示例

以下示例说明了初始化文档对象的替代方法。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

## <a name="cdocumentonopendocument"></a><a name="onopendocument"></a>CDocument：：打开文档

框架作为文件打开命令的一部分调用。

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>参数

*lpszPath名称*<br/>
指向要打开的文档的路径。

### <a name="return-value"></a>返回值

如果文档已成功加载，则非零;否则 0。

### <a name="remarks"></a>备注

此函数的默认实现将打开指定的文件，调用[DeleteContents](#deletecontents)成员函数以确保文档为空，调用[CObject：：序列化](../../mfc/reference/cobject-class.md#serialize)以读取文件的内容，然后将文档标记为干净。 如果要使用存档机制或文件机制以外的内容，则重写此函数。 例如，可以编写一个应用程序，其中文档表示数据库中的记录，而不是单独的文件。

如果用户在 SDI 应用程序中选择"文件打开"命令，则框架使用此函数重新初始化现有`CDocument`对象，而不是创建新对象。 如果用户在 MDI 应用程序中选择"文件打开"，则框架每次都会构造一`CDocument`个新对象，然后调用此函数来初始化它。 您必须将初始化代码放在此函数中，而不是将文件打开命令放在构造函数中，才能在 SDI 应用程序中有效。

### <a name="example"></a>示例

以下示例说明了初始化文档对象的替代方法。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

## <a name="cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>CDocument：：在预览处理程序查询焦点

指示预览处理程序返回从调用`GetFocus`函数中检索到的 HWND。

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>参数

*phwnd*<br/>
[出]当此方法返回时，包含从预览处理程序的前景线程调用`GetFocus`函数返回的 HWND 的指针。

### <a name="return-value"></a>返回值

如果成功，返回S_OK;或错误值，否则。

### <a name="remarks"></a>备注

## <a name="cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>CDocument：：在预览处理程序翻译加速器

指示预览处理程序处理从运行预览处理程序的进程的消息泵传入的击键。

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>参数

*pmsg*<br/>
[在]指向窗口消息的指针。

### <a name="return-value"></a>返回值

如果预览处理程序可以处理击键消息，则处理程序将处理该消息并返回S_OK。 如果预览处理程序无法处理击键消息，则通过`IPreviewHandlerFrame::TranslateAccelerator`向主机提供该消息。 如果主机处理消息，此方法将返回S_OK。 如果主机不处理消息，此方法将返回S_FALSE。

### <a name="remarks"></a>备注

## <a name="cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>CDocument：：在里希预览背面颜色已更改

当"富预览"背景颜色已更改时调用。

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>备注

## <a name="cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>CDocument：：在里希预览字体上

当"富预览"字体已更改时调用。

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>备注

## <a name="cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>CDocument：：在里希预览网站更改

在"丰富预览"网站已更改时调用。

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>备注

## <a name="cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>CDocument：：在里希预览文本颜色修改

当"富预览"文本颜色已更改时调用。

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>备注

## <a name="cdocumentonsavedocument"></a><a name="onsavedocument"></a>CDocument：：在保存文档上

框架作为文件保存或文件保存为命令的一部分调用。

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>参数

*lpszPath名称*<br/>
指向应将文件保存到的完全限定路径。

### <a name="return-value"></a>返回值

如果文档已成功保存，则非零;否则 0。

### <a name="remarks"></a>备注

此函数的默认实现将打开指定的文件，调用[CObject：：序列化](../../mfc/reference/cobject-class.md#serialize)以将文档的数据写入文件，然后将文档标记为干净。 如果要在框架保存文档时执行特殊处理，则重写此函数。 例如，可以编写一个应用程序，其中文档表示数据库中的记录，而不是单独的文件。

## <a name="cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>CDocument：：打开卸载处理程序

卸载预览处理程序时由框架调用。

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>备注

## <a name="cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>CDocument：：更新文件发送邮件

如果存在邮件支持 （MAPI），则启用ID_FILE_SEND_MAIL命令。

```cpp
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向与ID_FILE_SEND_MAIL命令关联的[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的指针。

### <a name="remarks"></a>备注

否则，该函数将从菜单中删除ID_FILE_SEND_MAIL命令，包括菜单项上方或下方的分隔符（ 如果 MAPI32，则启用 MAPI。DLL 存在于路径中，并且存在于 WIN 的 [邮件] 部分中。INI 文件，MAPI=1。 大多数应用程序都在此命令放在"文件"菜单上。

`CDocument`支持通过邮件支持 （MAPI） 发送文档。 请参阅 MFC 中的[MAPI 主题](../../mfc/mapi.md)和[MAPI 支持](../../mfc/mapi-support-in-mfc.md)文章。

## <a name="cdocumentprecloseframe"></a><a name="precloseframe"></a>CDocument：:P重新关闭框架

在销毁框架窗口之前，框架将调用此成员函数。

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>参数

*pFrame*<br/>
指向保存关联`CDocument`对象的[CFrameWnd 的](../../mfc/reference/cframewnd-class.md)指针。

### <a name="remarks"></a>备注

可以重写它来提供自定义清理，但请务必调用基类。

中的默认值`PreCloseFrame`在 中`CDocument`不执行任何操作。 派生类[COleDocument](../../mfc/reference/coledocument-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)使用此成员函数。 `CDocument`

## <a name="cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>CDocument：：阅读下一个块值

读取下一个块值。

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>参数

*ppValue*<br/>
[出]当函数返回时 *，ppValue*包含读取的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

## <a name="cdocumentreleasefile"></a><a name="releasefile"></a>CDocument：：发布文件

框架调用此成员函数以发布文件，使其可供其他应用程序使用。

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>参数

*pFile*<br/>
指向要释放的 CFile 对象的指针。

*bAbort*<br/>
指定是否使用 或`CFile::Close`释放文件。 `CFile::Abort` 如果要使用 CFile 释放文件，则[FALSE：关闭](../../mfc/reference/cfile-class.md#close);如果要使用[CFile：：：中止](../../mfc/reference/cfile-class.md#abort)发布文件，则为 TRUE。

### <a name="remarks"></a>备注

如果*bAbort*为`ReleaseFile` `CFile::Abort`TRUE，则调用 ，然后释放该文件。 `CFile::Abort`不会引发异常。

如果*bAbort*是`ReleaseFile` `CFile::Close` FALSE，则调用和文件将被释放。

重写此成员函数，要求在释放文件之前由用户执行操作。

## <a name="cdocumentremovechunk"></a><a name="removechunk"></a>CDocument：：删除块

使用指定的 GUID 删除块。

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>参数

*Guid*<br/>
指定要删除的块的 GUID。

*Pid*<br/>
指定要删除的块的 PID。

### <a name="remarks"></a>备注

## <a name="cdocumentremoveview"></a><a name="removeview"></a>CDocument：：删除查看

调用此函数以从文档分离视图。

```cpp
void RemoveView(CView* pView);
```

### <a name="parameters"></a>参数

*pView*<br/>
指向要删除的视图。

### <a name="remarks"></a>备注

此函数从与文档关联的视图列表中删除指定的视图;它还将视图的文档指针设置为 NULL。 当框架窗口关闭或拆分器窗口的窗格关闭时，框架将调用此功能。

仅当手动分离视图时，才调用此功能。 通常，通过定义[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象来关联文档类、视图类和框架窗口类，可以让框架分离文档和视图。

有关示例实现，请参阅[AddView](#addview)上的示例。

## <a name="cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>CDocument：：报告保存加载异常

如果在保存或加载文档时引发异常（通常是[CFileException](../../mfc/reference/cfileexception-class.md)或[CArchiveexception），](../../mfc/reference/carchiveexception-class.md)则调用。

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>参数

*lpszPath名称*<br/>
指向要保存或加载的文档的名称。

*e*<br/>
指向引发的异常。 可以为 NULL。

*b 保存*<br/>
指示正在进行的操作的标志;如果保存文档，则非零;如果正在加载文档，则为 0。

*nIDPDefault*<br/>
如果函数未指定更具体的错误消息，则要显示的错误消息的标识符。

### <a name="remarks"></a>备注

默认实现检查异常对象并查找专门描述原因的错误消息。 如果未找到特定消息或*e*为 NULL，则使用*nIDPDefault*参数指定的常规消息。 然后，该函数将显示一个包含错误消息的消息框。 如果要提供其他自定义失败消息，请覆盖此函数。 这是一个高级的可重写。

## <a name="cdocumentsavemodified"></a><a name="savemodified"></a>CDocument：：保存修改

在要关闭修改的文档之前，框架调用。

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>返回值

如果可以安全地继续并关闭文档，则非零;如果不应关闭文档，则为 0。

### <a name="remarks"></a>备注

此函数的默认实现将显示一个消息框，询问用户是否保存对文档的更改（如果有）。 如果程序需要不同的提示过程，请覆盖此函数。 这是一个高级的可重写。

## <a name="cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>CDocument：：设置块值

设置块值。

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>参数

*pValue*<br/>
指定要设置的块值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

## <a name="cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>CDocument：：设置修改后的 Flag

对文档进行任何修改后，请调用此功能。

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>参数

*b 修改*<br/>
指示文档是否已修改的标志。

### <a name="remarks"></a>备注

通过一致地调用此函数，可确保框架在关闭文档之前提示用户保存更改。 通常，您应该对*b修改*参数使用默认值 TRUE。 要将文档标记为干净（未修改），请使用此函数的值为 FALSE。

## <a name="cdocumentsetpathname"></a><a name="setpathname"></a>CDocument：：设置路径名称

调用此函数以指定文档磁盘文件的完全限定路径。

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>参数

*lpszPath名称*<br/>
指向要用作文档路径的字符串。

*bAddtoMRU*<br/>
确定文件名是否添加到最近使用的 （MRU） 文件列表中。 如果为 TRUE，则添加文件名;如果为 TRUE，则添加文件名。如果 FALSE，则不添加它。

### <a name="remarks"></a>备注

根据*bAddToMRU*的值，路径将添加到应用程序维护的 MRU 列表中，或者未添加路径。 请注意，某些文档未与磁盘文件关联。 仅当重写用于打开和保存框架使用的文件的默认实现时，才调用此函数。

## <a name="cdocumentsettitle"></a><a name="settitle"></a>CDocument：：设置标题

调用此函数以指定文档的标题（框架窗口的标题栏中显示的字符串）。

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>参数

*lpszTitle*<br/>
指向要用作文档标题的字符串。

### <a name="remarks"></a>备注

调用此函数会更新显示文档的所有框架窗口的标题。

## <a name="cdocumentupdateallviews"></a><a name="updateallviews"></a>CDocument：：更新所有视图

修改文档后调用此函数。

```cpp
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>参数

*pSender*<br/>
指向修改文档的视图，如果要更新所有视图，则指向 NULL。

*lHint*<br/>
包含有关修改的信息。

*pHint*<br/>
指向存储有关修改信息的对象。

### <a name="remarks"></a>备注

调用[Set修改 Flag](#setmodifiedflag)成员函数后，应调用此函数。 此函数通知附加到文档的每个视图 *（pSender*指定的视图除外）文档已被修改。 通常在用户通过视图更改文档后，从视图类调用此函数。

此函数调用[CView：：OnUpdate](../../mfc/reference/cview-class.md#onupdate)成员函数，用于文档的每个视图，但发送视图、传递*pHint*和*lHint*除外。 使用这些参数将信息传递给有关文档修改的视图。 您可以使用*lHint*和/或者定义[CObject](../../mfc/reference/cobject-class.md)派生类来存储有关修改的信息，并使用*pHint*传递该类的对象。 覆盖`CView::OnUpdate`[CView](../../mfc/reference/cview-class.md)派生类中的成员函数，以便根据传递的信息优化视图显示的更新。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 NPP](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)
