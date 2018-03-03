---
title: "CDocTemplate 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
dev_langs:
- C++
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71d44aac1ca7a018be7be1b375dd92920af96dba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdoctemplate-class"></a>CDocTemplate 类
定义文档模板基本功能的抽象基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CDocTemplate : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDocTemplate::CDocTemplate](#cdoctemplate)|构造 `CDocTemplate` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocTemplate::AddDocument](#adddocument)|将文档添加到模板。|  
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|关闭与此模板关联的所有文档。|  
|[CDocTemplate::CreateNewDocument](#createnewdocument)|创建一个新文档。|  
|[CDocTemplate::CreateNewFrame](#createnewframe)|创建新的框架窗口包含的文档和视图。|  
|[CDocTemplate::CreateOleFrame](#createoleframe)|创建支持 OLE 的框架窗口。|  
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|创建一个子框架用于丰富预览。|  
|[CDocTemplate::GetDocString](#getdocstring)|检索与文档类型相关联的字符串。|  
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|检索与此模板关联的第一个文档的位置。|  
|[CDocTemplate::GetNextDoc](#getnextdoc)|检索文档和下一个位置。|  
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|初始化框架窗口中，并根据需要使其可见。|  
|[CDocTemplate::LoadTemplate](#loadtemplate)|加载的资源给定`CDocTemplate`或派生类。|  
|[CDocTemplate::MatchDocType](#matchdoctype)|确定在文档类型与此模板之间的匹配的置信度。|  
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|打开文件指定的路径名。|  
|[CDocTemplate::RemoveDocument](#removedocument)|从模板中删除文档。|  
|[CDocTemplate::SaveAllModified](#saveallmodified)|保存与此模板关联的已修改的所有文档。|  
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|在编辑就地 OLE 项时，请确定 OLE 容器的资源。|  
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|在文档窗口的标题栏中显示的默认标题。|  
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|设置进程外的预览处理程序。|  
|[CDocTemplate::SetServerInfo](#setserverinfo)|服务器文档嵌入或就地编辑时确定的资源和类。|  
  
## <a name="remarks"></a>备注  
 通常你的应用程序的实现中创建一个或多个文档模板`InitInstance`函数。 文档模板定义了三种类型的类之间的关系：  
  
-   文档类，该类派生自**CDocument**。  
  
-   视图类，它显示从上面列出的文档类的数据。 可以派生此类从`CView`， `CScrollView`， `CFormView`，或`CEditView`。 (你还可以使用`CEditView`直接。)  
  
-   框架窗口类，包含的视图。 单文档界面 (SDI) 应用程序，派生此类从`CFrameWnd`。 对于多文档界面 (MDI) 应用程序，派生此类从`CMDIChildWnd`。 如果你不需要自定义框架窗口的行为，则可以使用`CFrameWnd`或`CMDIChildWnd`直接而不用派生您自己的类。  
  
 你的应用程序具有它支持的文档的每个类型的一个文档模板。 例如，如果你的应用程序支持电子表格和文本文档，应用程序具有两个文档模板对象。 每个文档模板负责创建和管理其类型的所有文档。  
  
 文档模板存储指向`CRuntimeClass`文档、 视图和框架窗口类的对象。 这些`CRuntimeClass`构造的文档模板时指定对象。  
  
 文档模板包含用于的文档类型 （例如菜单、 图标或快捷键对应表资源） 的资源的 ID。 文档模板还具有包含有关文档类型的其他信息的字符串。 其中包括文档类型 （例如，"工作表"） 和文件扩展名 (例如，".xls") 的名称。 （可选） 它可以包含应用程序的用户界面、 Windows 文件管理器中，和对象链接和嵌入 (OLE) 支持使用其他字符串。  
  
 如果 OLE 容器和/或服务器，你的应用程序，文档模板还定义在就地激活过程中使用的菜单的 ID。 如果你的应用程序，OLE 服务器文档模板定义的工具栏和菜单在就地激活过程中使用的 ID。 通过调用中指定这些其他 OLE 资源`SetContainerInfo`和`SetServerInfo`。  
  
 因为`CDocTemplate`是一个抽象类，不能直接使用类。 典型的应用程序使用两种状态之一`CDocTemplate`-派生类提供的 Microsoft 基础类库： `CSingleDocTemplate`，该类可实现 SDI，和`CMultiDocTemplate`，该类可实现 MDI。 有关使用文档模板，请参阅这些类，有关详细信息。  
  
 如果你的应用程序需要从根本上不同于 SDI 或 MDI 用户界面范例，你可以派生您自己的类从`CDocTemplate`。  
  
 有关详细信息`CDocTemplate`，请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## <a name="requirements"></a>惠?  
 **标头:** afxwin.h  
  
##  <a name="adddocument"></a>CDocTemplate::AddDocument  
 使用此函数将文档添加到模板。  
  
```  
virtual void AddDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>参数  
 `pDoc`  
 指向要添加的文档的指针。  
  
### <a name="remarks"></a>备注  
 派生的类[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)和[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)重写此函数。 如果派生您自己的文档模板类，从`CDocTemplate`，派生的类必须重写此函数。  
  
##  <a name="cdoctemplate"></a>CDocTemplate::CDocTemplate  
 构造 `CDocTemplate` 对象。  
  
```  
CDocTemplate (
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>参数  
 `nIDResource`  
 指定与文档类型一起使用的资源的 ID。 这可能包括菜单、 图标、 快捷键对应表和字符串资源。  
  
 字符串资源包含最多七由 \n 字符分隔的子字符串 （不包括子字符串时，需要将 \n 字符作为一个占位符; 但是，不需要尾随 \n 字符）;这些子字符串描述文档类型。 子字符串的信息，请参阅[GetDocString](#getdocstring)。 在应用程序的资源文件中找到此字符串资源。 例如:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 请注意，字符串开始使用 \n 的字符;这是因为第一个子字符串不用于 MDI 应用程序，因此不包括。 你可以编辑使用字符串编辑器中; 此字符串整个字符串会作为单个条目在字符串编辑器中，会出现不为七个不同的项。  
  
 `pDocClass`  
 指向`CRuntimeClass`文档类的对象。 此类是**CDocument**-派生类，定义来表示你的文档。  
  
 `pFrameClass`  
 指向`CRuntimeClass`的框架窗口类的对象。 此类可以是`CFrameWnd`-派生类，也可以是`CFrameWnd`本身如果你希望用于您的主框架窗口的默认行为。  
  
 `pViewClass`  
 指向`CRuntimeClass`视图类的对象。 此类是`CView`-派生类定义以显示你的文档。  
  
### <a name="remarks"></a>备注  
 使用此成员函数来构造`CDocTemplate`对象。 动态分配`CDocTemplate`对象，并将其传递到[CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate)从`InitInstance`的应用程序类的成员函数。  
  
##  <a name="closealldocuments"></a>CDocTemplate::CloseAllDocuments  
 调用此成员函数以关闭所有打开的文档。  
  
```  
virtual void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>参数  
 `bEndSession`  
 指定在正在结束会话。 它是**TRUE**如果会话正在结束; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 此成员函数通常用作文件退出命令的一部分。 此函数的默认实现调用[CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents)成员函数删除文档的数据，然后关闭所有视图的框架窗口附加到文档。  
  
 如果你希望要求用户执行的特殊清理处理关闭文档之前，重写此函数。 例如，如果文档表示数据库中的记录，你可能想要重写此函数可在关闭该数据库。  
  
##  <a name="createnewdocument"></a>CDocTemplate::CreateNewDocument  
 调用此成员函数可创建与此文档模板关联的类型的新文档。  
  
```  
virtual CDocument* CreateNewDocument();
```  
  
### <a name="return-value"></a>返回值  
 指向新创建的文档的指针或**NULL**如果发生错误。  
  
##  <a name="createnewframe"></a>CDocTemplate::CreateNewFrame  
 创建新的框架窗口包含的文档和视图。  
  
```  
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,  
    CFrameWnd* pOther);
```  
  
### <a name="parameters"></a>参数  
 `pDoc`  
 新的框架窗口应引用的文档。 可以是**NULL**。  
  
 `pOther`  
 新的框架窗口是以数据为基础框架窗口。 可以是**NULL**。  
  
### <a name="return-value"></a>返回值  
 指向新创建的框架窗口中，或**NULL**如果发生错误。  
  
### <a name="remarks"></a>备注  
 `CreateNewFrame`使用`CRuntimeClass`对象传递给构造函数来使用视图和附加的文档创建新的框架窗口。 如果`pDoc`参数是**NULL**，框架将输出跟踪消息。  
  
 `pOther`参数用于实现新建窗口命令。 它提供了用于模型的新的框架窗口的框架窗口。 新的框架窗口通常会创建不可见。 调用此函数可创建外部文件新建和打开文件的标准框架实现的框架窗口。  
  
##  <a name="createoleframe"></a>CDocTemplate::CreateOleFrame  
 创建 OLE 框架窗口。  
  
```  
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc,  
    BOOL bCreateView);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向帧的父窗口的指针。  
  
 `pDoc`  
 指向新的 OLE 框架窗口应引用的文档的指针。  
  
 `bCreateView`  
 确定是否以及框架创建视图。  
  
### <a name="return-value"></a>返回值  
 如果成功，则框架窗口指向的指针否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`bCreateView`为零，创建一个空框架。  
  
##  <a name="getdocstring"></a>CDocTemplate::GetDocString  
 检索与文档类型相关联的字符串。  
  
```  
virtual BOOL GetDocString(
    CString& rString,  
    enum DocStringIndex index) const;  
```  
  
### <a name="parameters"></a>参数  
 `rString`  
 对引用`CString`在函数返回时，将包含字符串的对象。  
  
 *索引*  
 正在检索从描述文档类型的字符串的子字符串的索引。 此参数可以具有下列值之一：  
  
- **CDocTemplate::windowTitle**出现在应用程序窗口的标题栏中 (例如，"Microsoft Excel") 的名称。 仅在 SDI 应用程序的文档模板中提供。  
  
- **CDocTemplate::docName**根 （例如，"表"） 的默认文档名称。 每当用户选择新的命令，从文件菜单 （例如，"Sheet1"或"Sheet2"），此根，加上一个数字，用于此类型的新文档的默认名称。 如果未指定，"无标题"用作默认值。  
  
- **CDocTemplate::fileNewName**此文档类型的名称。 如果应用程序支持多个文档的类型，此字符串被显示在文件新建对话框中 （例如，"工作表"）。 如果未指定，文档类型不可使用的新文件命令。  
  
- **CDocTemplate::filterName**文档类型和通配符筛选器匹配的此类型的文档的说明。 在文件打开对话框中 （例如，"工作表 (*.xls)"） 的列表文件类型下拉列表中显示此字符串。 如果未指定，文档类型不可使用文件打开命令。  
  
- **CDocTemplate::filterExt**扩展对于此类型 (例如，".xls") 的文档。 如果未指定，文档类型不可使用文件打开命令。  
  
- **CDocTemplate::regFileTypeId**要由 Windows 维护到注册数据库中存储文档类型的标识符。 此字符串是仅供内部使用 (例如，"ExcelWorksheet")。 如果未指定，则无法使用 Windows 文件管理器注册文档类型。  
  
- **CDocTemplate::regFileTypeName**要到注册数据库中存储的文档类型名称。 此字符串可能显示在对话框的应用程序访问注册数据库 （例如，"Microsoft Excel 工作表"）。  
  
### <a name="return-value"></a>返回值  
 如果指定的子字符串; 如果未找到则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索特定的子字符串，描述文档类型。 包含这些子字符串的字符串存储在文档模板，而从应用程序的资源文件中的字符串派生。 框架调用此函数可获取需要用于应用程序的用户界面的字符串。 如果已指定文件扩展名的应用程序的文档，框架还调用此函数时将项添加到 Windows 注册数据库;这样，要从 Windows 文件管理器中打开的文档。  
  
 调用此函数，仅当派生您自己的类从`CDocTemplate`。  
  
##  <a name="getfirstdocposition"></a>CDocTemplate::GetFirstDocPosition  
 检索与此模板关联的第一个文档的位置。  
  
```  
virtual POSITION GetFirstDocPosition() const = 0;  
```  
  
### <a name="return-value"></a>返回值  
 A**位置**可用于循环访问与此文档模板; 关联的文档列表的值或**NULL**如果列表为空。  
  
### <a name="remarks"></a>备注  
 使用此函数来获取与此模板关联的文档列表中的第一个文档的位置。 使用**位置**作为的自变量的值[CDocTemplate::GetNextDoc](#getnextdoc)来循环访问与模板关联的文档的列表。  
  
 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)和[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)都重写此纯虚拟函数。 派生自任何类`CDocTemplate`还必须重写此函数。  
  
##  <a name="getnextdoc"></a>CDocTemplate::GetNextDoc  
 检索标识的列表元素`rPos`，然后设置`rPos`到**位置**的列表中的下一步条目的值。  
  
```  
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;  
```  
  
### <a name="return-value"></a>返回值  
 指向与此模板关联的文档的列表中的下一步文档的指针。  
  
### <a name="parameters"></a>参数  
 `rPos`  
 对引用**位置**返回上次调用值[GetFirstDocPosition](#getfirstdocposition)或`GetNextDoc`。  
  
### <a name="remarks"></a>备注  
 如果检索的元素的是在列表中，最后然后的新值`rPos`设置为**NULL**。  
  
 你可以使用`GetNextDoc`如果建立通过调用的初始位置的向前迭代循环中[GetFirstDocPosition](#getfirstdocposition)。  
  
 你必须确保你**位置**值表示在列表中的有效位置。 如果它是无效的 Microsoft 基础类库的调试版本断言。  
  
##  <a name="initialupdateframe"></a>CDocTemplate::InitialUpdateFrame  
 初始化框架窗口中，并根据需要使其可见。  
  
```  
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,  
    CDocument* pDoc,  
    BOOL bMakeVisible = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pFrame`  
 需要初始更新框架窗口。  
  
 `pDoc`  
 框架所关联到文档。 可以是**NULL**。  
  
 `bMakeVisible`  
 表示框架应变得可见并处于活动状态。  
  
### <a name="remarks"></a>备注  
 调用**IntitialUpdateFrame**创建具有的新帧之后`CreateNewFrame`。 调用此函数会导致在接收该框架窗口视图其`OnInitialUpdate`调用。 此外，如果没有以前的活动视图，框架窗口的主视图将活动状态，则主视图是使用子 ID 的视图**AFX_IDW_PANE_FIRST**。 最后，框架窗口均可见如果`bMakeVisible`为非零。 如果`bMakeVisible`为零，当前焦点和框架窗口的可见状态将保持不变。  
  
 不需要使用框架的实现的新文件和文件打开时调用此函数。  
  
##  <a name="loadtemplate"></a>CDocTemplate::LoadTemplate  
 加载的资源给定`CDocTemplate`或派生类。  
  
```  
virtual void LoadTemplate();
```  
  
### <a name="remarks"></a>备注  
 此成员函数调用由框架加载的资源给定`CDocTemplate`或派生类。 通常它是在构造期间，除时调用全局正在构建模板。 在这种情况下，调用`LoadTemplate`延迟直至[CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate)调用。  
  
##  <a name="matchdoctype"></a>CDocTemplate::MatchDocType  
 确定在文档类型与此模板之间的匹配的置信度。  
  
```  
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,  
    CDocument*& rpDocMatch);
```  
  
### <a name="parameters"></a>参数  
 `lpszPathName`  
 要确定其类型的文件的路径名。  
  
 `rpDocMatch`  
 如果指定的文件分配匹配的文档，文档的指针`lpszPathName`已打开。  
  
### <a name="return-value"></a>返回值  
 取值范围为**置信度**枚举，定义如下：  
  
```  
enum Confidence  
    {  
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };  
```  
  
### <a name="remarks"></a>备注  
 使用此函数可确定要用于打开文件的文档模板的类型。 如果你的应用程序支持多个文件类型，例如，你可以使用此函数来确定哪一项可用的文档模板是适用于给定文件通过调用`MatchDocType`打开，并选择根据模板中每个模板返回的置信度值。  
  
 如果指定的文件`lpszPathName`已打开，此函数将返回**CDocTemplate::yesAlreadyOpen** ，并将复制文件的**CDocument**到处的对象的对象`rpDocMatch`。  
  
 如果文件不是打开中的扩展但`lpszPathName`与指定扩展名匹配**CDocTemplate::filterExt**，此函数将返回**CDocTemplate::yesAttemptNative**和设置`rpDocMatch`到**NULL**。 有关详细信息**CDocTemplate::filterExt**，请参阅[CDocTemplate::GetDocString](#getdocstring)。  
  
 如果任何情况下为 true，则该函数将返回**CDocTemplate::yesAttemptForeign**。  
  
 默认实现不返回**CDocTemplate::maybeAttemptForeign**或**CDocTemplate::maybeAttemptNative**。 重写此函数可实现适合你的应用程序，可能使用从这两个值的类型匹配的逻辑**置信度**枚举。  
  
##  <a name="opendocumentfile"></a>CDocTemplate::OpenDocumentFile  
 将打开由路径指定的文件。  
  
```  
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;  
 
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU) = 0;  
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszPathName`  
 指向包含要打开的文档的文件的路径。  
  
 [in] `bAddToMRU`  
 `TRUE`指示的文档是一个最新文件;`FALSE`指示该文档不是最新的文件之一。  
  
### <a name="return-value"></a>返回值  
 指向由名为其文件的文档的`lpszPathName`;`NULL`如果不成功。  
  
### <a name="remarks"></a>备注  
 将指定其路径的文件打开`lpszPathName`。 如果`lpszPathName`是`NULL`，创建新的文件包含与此模板关联的类型的文档。  
  
##  <a name="removedocument"></a>CDocTemplate::RemoveDocument  
 删除指向文档`pDoc`从与此模板关联的文档的列表。  
  
```  
virtual void RemoveDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>参数  
 `pDoc`  
 指向要删除的文档的指针。  
  
### <a name="remarks"></a>备注  
 派生的类`CMultiDocTemplate`和`CSingleDocTemplate`重写此函数。 如果派生您自己的文档模板类，从`CDocTemplate`，派生的类必须重写此函数。  
  
##  <a name="saveallmodified"></a>CDocTemplate::SaveAllModified  
 保存已修改的所有文档。  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>返回值  
 非零如果成功，则否则为 0。  
  
##  <a name="setcontainerinfo"></a>CDocTemplate::SetContainerInfo  
 在编辑就地 OLE 项时，请确定 OLE 容器的资源。  
  
```  
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```  
  
### <a name="parameters"></a>参数  
 `nIDOleInPlaceContainer`  
 在激活嵌入的对象时使用的资源 ID。  
  
### <a name="remarks"></a>备注  
 调用此函数可设置时就地激活的 OLE 对象时要使用的资源。 这些资源可能包括菜单和快捷键对应表。 通常在调用此函数[CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)你应用程序的功能。  
  
 与关联的菜单`nIDOleInPlaceContainer`包含允许要合并的激活就地项的容器应用程序的菜单的菜单的分隔符。 有关合并服务器和容器菜单的详细信息，请参阅文章[菜单和资源 (OLE)](../../mfc/menus-and-resources-ole.md)。  
  
##  <a name="setdefaulttitle"></a>CDocTemplate::SetDefaultTitle  
 调用此函数可加载文档的默认标题并将其显示在文档的标题栏中。  
  
```  
virtual void SetDefaultTitle(CDocument* pDocument) = 0;  
```  
  
### <a name="parameters"></a>参数  
 *pDocument*  
 指向其标题是设置文档的指针。  
  
### <a name="remarks"></a>备注  
 有关默认标题的信息，请参阅的说明**CDocTemplate::docName**中[CDocTemplate::GetDocString](#getdocstring)。  
  
##  <a name="setserverinfo"></a>CDocTemplate::SetServerInfo  
 服务器文档嵌入或就地编辑时确定的资源和类。  
  
```  
void SetServerInfo(
    UINT nIDOleEmbedding,  
    UINT nIDOleInPlaceServer = 0,  
    CRuntimeClass* pOleFrameClass = NULL,  
    CRuntimeClass* pOleViewClass = NULL);
```  
  
### <a name="parameters"></a>参数  
 *nIDOleEmbedding*  
 在单独的窗口中打开嵌入的对象时使用的资源 ID。  
  
 `nIDOleInPlaceServer`  
 就地激活嵌入的对象时使用的资源的 ID。  
  
 *pOleFrameClass*  
 指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构，它包含创建就地激活发生时的框架窗口对象的类信息。  
  
 *pOleViewClass*  
 指向`CRuntimeClass`结构，它包含创建就地激活发生时的视图对象的类信息。  
  
### <a name="remarks"></a>备注  
 调用此成员函数可确定当用户请求激活的嵌入对象时，服务器应用程序将使用的资源。 这些资源由菜单和快捷键对应表组成。 通常在调用此函数`InitInstance`的你的应用程序。  
  
 与关联的菜单`nIDOleInPlaceServer`包含允许服务器菜单合并的菜单容器的分隔符。 有关合并服务器和容器菜单的详细信息，请参阅文章[菜单和资源 (OLE)](../../mfc/menus-and-resources-ole.md)。  
  
##  <a name="createpreviewframe"></a>CDocTemplate::CreatePreviewFrame  
 创建一个子框架用于丰富预览。  
  
```  
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向父窗口 （Shell 通常提供） 的指针。  
  
 `pDoc`  
 指向其内容将预览的文档对象的指针。  
  
### <a name="return-value"></a>返回值  
 指向的有效指针`CFrameWnd`对象，或`NULL`如果创建失败。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpreviewinfo"></a>CDocTemplate::SetPreviewInfo  
 设置了外过程预览处理程序。  
  
```  
void SetPreviewInfo(
    UINT nIDPreviewFrame,  
    CRuntimeClass* pPreviewFrameClass = NULL,  
    CRuntimeClass* pPreviewViewClass = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nIDPreviewFrame`  
 指定的预览帧的资源 ID。  
  
 `pPreviewFrameClass`  
 指定指向预览帧的运行时类信息结构的指针。  
  
 `pPreviewViewClass`  
 指定指向运行时类信息结构的预览视图。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSingleDocTemplate 类](../../mfc/reference/csingledoctemplate-class.md)   
 [CMultiDocTemplate 类](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument 类](../../mfc/reference/cdocument-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CScrollView 类](../../mfc/reference/cscrollview-class.md)   
 [CEditView 类](../../mfc/reference/ceditview-class.md)   
 [CFormView 类](../../mfc/reference/cformview-class.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)
