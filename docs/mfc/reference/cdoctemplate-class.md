---
title: CDocTemplate 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 3376b8febe8ae4586ce649f3f83386875acb678f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375513"
---
# <a name="cdoctemplate-class"></a>CDocTemplate 类

定义文档模板基本功能的抽象基类。

## <a name="syntax"></a>语法

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CDocTemplate：CDocTemplate](#cdoctemplate)|构造 `CDocTemplate` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDocTemplate：：添加文档](#adddocument)|将文档添加到模板。|
|[CDocTemplate：：关闭所有文档](#closealldocuments)|关闭与此模板关联的所有文档。|
|[CDocTemplate：：创建新文档](#createnewdocument)|创建新文档。|
|[CDocTemplate：：创建新框架](#createnewframe)|创建新框架窗口，其中包含文档和视图。|
|[CDocTemplate：：创建OleFrame](#createoleframe)|创建启用 OLE 的框架窗口。|
|[CDocTemplate：：创建预览框架](#createpreviewframe)|创建用于"丰富预览"的子框架。|
|[CDocTemplate：：获取DocString](#getdocstring)|检索与文档类型关联的字符串。|
|[CDocTemplate：获取第一个文档位置](#getfirstdocposition)|检索与此模板关联的第一个文档的位置。|
|[CDocTemplate：：获取下一个文档](#getnextdoc)|检索文档和下一个文档的位置。|
|[CDocTemplate：：初始更新框架](#initialupdateframe)|初始化框架窗口，并选择性地使其可见。|
|[CDocTemplate：加载模板](#loadtemplate)|加载给定`CDocTemplate`类或派生类的资源。|
|[CDocTemplate：：匹配文档类型](#matchdoctype)|确定文档类型和此模板之间匹配的置信度。|
|[CDocTemplate：：打开文件文件](#opendocumentfile)|打开由路径名称指定的文件。|
|[CDocTemplate：：删除文档](#removedocument)|从模板中删除文档。|
|[CDocTemplate：：保存所有修改](#saveallmodified)|保存与此模板关联的所有已修改的文档。|
|[CDocTemplate：：设置容器信息](#setcontainerinfo)|在编辑就地 OLE 项时确定 OLE 容器的资源。|
|[CDocTemplate：：设置默认标题](#setdefaulttitle)|在文档窗口的标题栏中显示默认标题。|
|[CDocTemplate：：设置预览信息](#setpreviewinfo)|进程预览处理程序的设置。|
|[CDocTemplate：：设置服务器信息](#setserverinfo)|确定服务器文档在就地嵌入或编辑时的资源和类。|

## <a name="remarks"></a>备注

通常在应用程序`InitInstance`函数的实现中创建一个或多个文档模板。 文档模板定义三种类型的类之间的关系：

- 从 派生的文档`CDocument`类。

- 视图类，它显示来自上面列出的文档类的数据。 可以从`CView`派生此类，`CScrollView`或`CFormView`。 `CEditView` （您也可以直接使用`CEditView`。

- 包含视图的框架窗口类。 对于单个文档接口 （SDI） 应用程序，从 派生`CFrameWnd`此类。 对于多个文档接口 （MDI） 应用程序，从 派生`CMDIChildWnd`此类。 如果不需要自定义框架窗口的行为，则可以使用或直接在不`CFrameWnd`派生自己的类的情况下使用或`CMDIChildWnd`直接自定义框架窗口。

应用程序对于它支持的每种类型的文档都有一个文档模板。 例如，如果应用程序同时支持电子表格和文本文档，则应用程序有两个文档模板对象。 每个文档模板负责创建和管理其类型的所有文档。

文档模板存储指向文档、视图`CRuntimeClass`和框架窗口类对象的指针。 这些`CRuntimeClass`对象在构造文档模板时指定。

文档模板包含与文档类型（如菜单、图标或快捷表资源）一起使用的资源的 ID。 文档模板还具有包含有关其文档类型的其他信息的字符串。 其中包括文档类型的名称（例如，"工作表"）和文件扩展名（例如，".xls"）。 或者，它可以包含应用程序的用户界面、Windows 文件管理器以及对象链接和嵌入 （OLE） 支持使用的其他字符串。

如果应用程序是 OLE 容器和/或服务器，文档模板还会定义就地激活期间使用的菜单的 ID。 如果应用程序是 OLE 服务器，则文档模板将定义就地激活期间使用的工具栏和菜单的 ID。 通过调用`SetContainerInfo`和`SetServerInfo`指定这些额外的 OLE 资源。

因为`CDocTemplate`是抽象类，因此不能直接使用该类。 典型的应用程序使用 Microsoft 基础类`CDocTemplate`库提供的两派生类之一：，`CSingleDocTemplate`实现 SDI，和`CMultiDocTemplate`，实现 MDI。 有关使用文档模板的详细信息，请参阅这些类。

如果应用程序需要与 SDI 或 MDI 根本不同的用户界面范例，则可以从`CDocTemplate`派生您自己的类。

有关 的详细信息`CDocTemplate`，请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cdoctemplateadddocument"></a><a name="adddocument"></a>CDocTemplate：：添加文档

使用此函数将文档添加到模板。

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>参数

*pDoc*<br/>
指向要添加的文档的指针。

### <a name="remarks"></a>备注

派生类[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)和[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)重写此函数。 如果派生自`CDocTemplate`，派生类必须重写此函数。

## <a name="cdoctemplatecdoctemplate"></a><a name="cdoctemplate"></a>CDocTemplate：CDocTemplate

构造 `CDocTemplate` 对象。

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>参数

*nID资源*<br/>
指定与文档类型一起使用的资源的 ID。 这可能包括菜单、图标、快捷键表和字符串资源。

字符串资源由最多七个子字符串组成，由"\n"字符分隔（如果不包括子字符串，则需要"\n"字符作为占位符;但是，尾随的"\n"字符是不需要的）;这些子字符串描述文档类型。 有关子字符串的信息，请参阅[GetDocString](#getdocstring)。 此字符串资源位于应用程序的资源文件中。 例如：

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

请注意，字符串以"\n"字符开头;这是因为第一个子字符串不用于 MDI 应用程序，因此不包括。 您可以使用字符串编辑器编辑此字符串;但是，使用字符串编辑器可以编辑此字符串。整个字符串在字符串编辑器中显示为单个条目，而不是七个单独的条目。

*pDocClass*<br/>
指向文档类`CRuntimeClass`的对象。 此类是您定义的`CDocument`表示文档的派生类。

*pFrame 类*<br/>
指向框架窗口`CRuntimeClass`类的对象。 类可以是`CFrameWnd`派生类，也可以是`CFrameWnd`自己的，如果您想要主框架窗口的默认行为。

*pView 类*<br/>
指向视图类`CRuntimeClass`的对象。 此类是您为`CView`显示文档而定义的派生类。

### <a name="remarks"></a>备注

使用此成员函数构造对象`CDocTemplate`。 动态分配`CDocTemplate`对象并将其传递给[CWinApp：：](../../mfc/reference/cwinapp-class.md#adddoctemplate)从应用程序类`InitInstance`的成员函数添加DocTemplate。

## <a name="cdoctemplateclosealldocuments"></a><a name="closealldocuments"></a>CDocTemplate：：关闭所有文档

调用此成员函数关闭所有打开的文档。

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>参数

*bEndSession*<br/>
未使用。

### <a name="remarks"></a>备注

此成员函数通常用作文件退出命令的一部分。 此函数的默认实现调用[CDocument：:DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents)成员函数，以删除文档的数据，然后关闭附加到文档的所有视图的帧窗口。

如果要要求用户在文档关闭之前执行特殊的清理处理，请覆盖此函数。 例如，如果文档表示数据库中的记录，则可能需要重写此函数以关闭数据库。

## <a name="cdoctemplatecreatenewdocument"></a><a name="createnewdocument"></a>CDocTemplate：：创建新文档

调用此成员函数以创建与此文档模板关联的类型的新文档。

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>返回值

指向新创建的文档的指针，如果发生错误，则指向 NULL。

## <a name="cdoctemplatecreatenewframe"></a><a name="createnewframe"></a>CDocTemplate：：创建新框架

创建新框架窗口，其中包含文档和视图。

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>参数

*pDoc*<br/>
新框架窗口应引用的文档。 可以为 NULL。

*p其他*<br/>
新框架窗口所基于的帧窗口。 可以为 NULL。

### <a name="return-value"></a>返回值

指向新创建的帧窗口的指针，如果发生错误，则指向 NULL。

### <a name="remarks"></a>备注

`CreateNewFrame`使用传递给`CRuntimeClass`构造函数的对象创建一个附加视图和文档的新框架窗口。 如果*pDoc*参数为 NULL，则框架将输出 TRACE 消息。

*pOther*参数用于实现"窗口新"命令。 它提供了一个框架窗口，用于对新的框架窗口进行建模。 新的框架窗口通常是不可见的。 调用此函数以在文件新建和文件打开的标准框架实现之外创建框架窗口。

## <a name="cdoctemplatecreateoleframe"></a><a name="createoleframe"></a>CDocTemplate：：创建OleFrame

创建 OLE 框架窗口。

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向帧的父窗口的指针。

*pDoc*<br/>
指向新 OLE 框架窗口应引用的文档的指针。

*b创建视图*<br/>
确定是否随框架一起创建视图。

### <a name="return-value"></a>返回值

指向帧窗口的指针（如果成功）;如果成功，则指向框架窗口的指针。否则 NULL。

### <a name="remarks"></a>备注

如果*bCreateView*为零，则创建一个空帧。

## <a name="cdoctemplategetdocstring"></a><a name="getdocstring"></a>CDocTemplate：：获取DocString

检索与文档类型关联的字符串。

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>参数

*rString*<br/>
对在`CString`函数返回时将包含字符串的对象的引用。

*index*<br/>
从描述文档类型的字符串中检索的子字符串的索引。 此参数可以具有下列值之一：

- `CDocTemplate::windowTitle`显示在应用程序窗口的标题栏中的名称（例如，"Microsoft Excel"）。 仅在 SDI 应用程序的文档模板中显示。

- `CDocTemplate::docName`默认文档名称的根目录（例如，"Sheet"）。 当用户从"文件"菜单中选择"新建"命令（例如，"Sheet1"或"Sheet2"）时，此根（加上数字）用于此类型新文档的默认名称。 如果未指定，"无标题"将用作默认值。

- `CDocTemplate::fileNewName`此文档类型的名称。 如果应用程序支持多种类型的文档，则此字符串将显示在"文件新建"对话框中（例如，"工作表"）。 如果未指定，则无法使用"文件新建"命令访问文档类型。

- `CDocTemplate::filterName`文档类型的说明和匹配此类型的文档的通配符筛选器。 此字符串显示在"文件打开"对话框中的"类型列表文件"下拉列表中（例如，"工作表 （*.xls）"）。 如果未指定，则无法使用文件打开命令访问文档类型。

- `CDocTemplate::filterExt`此类型文档的扩展（例如，".xls"）。 如果未指定，则无法使用文件打开命令访问文档类型。

- `CDocTemplate::regFileTypeId`要存储在 Windows 维护的注册数据库中的文档类型的标识符。 此字符串仅供内部使用（例如，"Excel工作表"）。 如果未指定，则无法向 Windows 文件管理器注册文档类型。

- `CDocTemplate::regFileTypeName`要存储在注册数据库中的文档类型的名称。 此字符串可以显示在访问注册数据库的应用程序的对话框中（例如，"Microsoft Excel 工作表"）。

### <a name="return-value"></a>返回值

如果找到指定的子字符串，则非零;否则 0。

### <a name="remarks"></a>备注

调用此函数以检索描述文档类型的特定子字符串。 包含这些子字符串的字符串存储在文档模板中，并且派生自应用程序资源文件中的字符串。 框架调用此函数是为了获取应用程序用户界面所需的字符串。 如果为应用程序的文档指定了文件名扩展名，则在将条目添加到 Windows 注册数据库时，框架也会调用此功能;如果为应用程序的文档指定了文件名扩展名，则框架还会调用此功能。这允许从 Windows 文件管理器打开文档。

仅当从`CDocTemplate`派生自己的类时，才调用此函数。

## <a name="cdoctemplategetfirstdocposition"></a><a name="getfirstdocposition"></a>CDocTemplate：获取第一个文档位置

检索与此模板关联的第一个文档的位置。

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>返回值

可用于遍经与本文档模板关联的文档列表的"位置"值;如果列表为空，则为 NULL。

### <a name="remarks"></a>备注

使用此函数可以获取与此模板关联的文档列表中的第一个文档的位置。 使用"位置"值作为[CDocTemplate 的参数：：GetNextDoc](#getnextdoc)可以遍遍查看与模板关联的文档列表。

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)和[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)都重写了此纯虚拟函数。 派生自`CDocTemplate`的任何类也必须重写此函数。

## <a name="cdoctemplategetnextdoc"></a><a name="getnextdoc"></a>CDocTemplate：：获取下一个文档

检索*由 rPos*标识的列表元素，然后将*rPos*设置到列表中下一个条目的"位置"值。

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>返回值

指向与此模板关联的文档列表中的下一个文档的指针。

### <a name="parameters"></a>参数

*rPos*<br/>
对前一个调用[GetFirstDoc定位](#getfirstdocposition)或`GetNextDoc`返回的定位值的引用。

### <a name="remarks"></a>备注

如果检索到的元素是列表中的最后一个元素，则*rPos*的新值将设置为 NULL。

如果使用对`GetNextDoc` [GetFirstDoc定位](#getfirstdocposition)的调用建立初始位置，则可以在转发迭代循环中使用。

您必须确保您的"位置"值表示列表中的有效位置。 如果无效，则 Microsoft 基础类库的调试版本断言。

## <a name="cdoctemplateinitialupdateframe"></a><a name="initialupdateframe"></a>CDocTemplate：：初始更新框架

初始化框架窗口，并选择性地使其可见。

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>参数

*pFrame*<br/>
需要初始更新的帧窗口。

*pDoc*<br/>
框架关联的文档。 可以为 NULL。

*b使可见*<br/>
指示帧是否应变得可见和活动。

### <a name="remarks"></a>备注

使用`IntitialUpdateFrame``CreateNewFrame`创建新帧后调用 。 调用此函数会导致该帧窗口中的视图接收其`OnInitialUpdate`调用。 此外，如果以前没有活动视图，则框架窗口的主视图将变为活动视图;主视图是具有 AFX_IDW_PANE_FIRST 子 ID 的视图。 最后，如果*bMakeVisible*是非零，则帧窗口变得可见。 如果*bMakeVisible*为零，则帧窗口的当前焦点和可见状态将保持不变。

使用框架的"文件新建"和"文件打开"实现时，不必调用此功能。

## <a name="cdoctemplateloadtemplate"></a><a name="loadtemplate"></a>CDocTemplate：加载模板

加载给定`CDocTemplate`类或派生类的资源。

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>备注

框架调用此成员函数以加载给定`CDocTemplate`类或派生类的资源。 通常，在构造期间调用它，除非模板是全局构造的。 在这种情况下，调用`LoadTemplate`将延迟到[CWinApp：：AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate)调用。

## <a name="cdoctemplatematchdoctype"></a><a name="matchdoctype"></a>CDocTemplate：：匹配文档类型

确定文档类型和此模板之间匹配的置信度。

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>参数

*lpszPath名称*<br/>
要确定其类型的文件的路径名。

*rpDocMatch*<br/>
如果*lpszPathName*指定的文件已打开，则指向已分配匹配文档的文档的指针。

### <a name="return-value"></a>返回值

**"信心**"枚举中的值，定义如下：

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

使用此函数可以确定用于打开文件的文档模板的类型。 例如，如果应用程序支持多种文件类型，则可以使用此函数通过依次调用`MatchDocType`每个模板并根据返回的置信度值选择模板来确定适用于给定文件的可用文档模板。

如果*lpszPathName*指定的文件已打开，则此函数将`CDocTemplate::yesAlreadyOpen`返回该文件`CDocument`的对象并将其复制到*rpDocMatch*上的对象中。

如果文件未打开，但*lpszPathName*中的扩展名与 指定的`CDocTemplate::filterExt`扩展名匹配，则`CDocTemplate::yesAttemptNative`此函数将返回并将*rpDocMatch*设置为 NULL。 有关详细信息，`CDocTemplate::filterExt`请参阅[CDocTemplate：getDocString](#getdocstring)。

如果两种情况都不正确，则函数将`CDocTemplate::yesAttemptForeign`返回 。

默认实现不返回`CDocTemplate::maybeAttemptForeign`或`CDocTemplate::maybeAttemptNative`。 重写此函数以实现适合应用程序的类型匹配逻辑，可能使用 **"信心"** 枚举中的这两个值。

## <a name="cdoctemplateopendocumentfile"></a><a name="opendocumentfile"></a>CDocTemplate：：打开文件文件

打开路径指定的文件。

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>参数

*lpszPath名称*<br/>
[在]指向包含要打开的文档的文件的路径的指针。

*bAddtoMRU*<br/>
[在]TRUE 表示文档是最新的文件之一;FALSE 表示文档不是最新的文件之一。

### <a name="return-value"></a>返回值

指向其文件由*lpszPathName*命名的文档的指针。如果失败，则为 NULL。

### <a name="remarks"></a>备注

打开其路径由*lpszPathName*指定的文件。 如果*lpszPathName*为 NULL，则将创建一个新文件，该文件包含与此模板关联的类型的文档。

## <a name="cdoctemplateremovedocument"></a><a name="removedocument"></a>CDocTemplate：：删除文档

从与此模板关联的文档列表中删除*pDoc*指向的文档。

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>参数

*pDoc*<br/>
指向要删除的文档的指针。

### <a name="remarks"></a>备注

派生类`CMultiDocTemplate`并`CSingleDocTemplate`重写此函数。 如果派生自`CDocTemplate`，派生类必须重写此函数。

## <a name="cdoctemplatesaveallmodified"></a><a name="saveallmodified"></a>CDocTemplate：：保存所有修改

保存已修改的所有文档。

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>返回值

如果成功，则为非零;否则 0。

## <a name="cdoctemplatesetcontainerinfo"></a><a name="setcontainerinfo"></a>CDocTemplate：：设置容器信息

在编辑就地 OLE 项时确定 OLE 容器的资源。

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>参数

*nIDOleInplace容器*<br/>
激活嵌入对象时使用的资源的 ID。

### <a name="remarks"></a>备注

调用此函数以设置在 OLE 对象就地激活时要使用的资源。 这些资源可能包括菜单和加速器表。 此函数通常在应用程序的[CWinApp：：initInstance](../../mfc/reference/cwinapp-class.md#initinstance)函数中调用。

与*nIDOleInPlace 容器*关联的菜单包含分隔符，允许激活的就地项的菜单与容器应用程序的菜单合并。 有关合并服务器和容器菜单的详细信息，请参阅文章["菜单和资源 "（OLE）。](../../mfc/menus-and-resources-ole.md)

## <a name="cdoctemplatesetdefaulttitle"></a><a name="setdefaulttitle"></a>CDocTemplate：：设置默认标题

调用此函数以加载文档的默认标题，并将其显示在文档的标题栏中。

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>参数

*pDocument*<br/>
指向要设置其标题的文档的指针。

### <a name="remarks"></a>备注

有关默认标题的信息，请参阅`CDocTemplate::docName`[CDocTemplate 中的说明：：GetDocString](#getdocstring)。

## <a name="cdoctemplatesetserverinfo"></a><a name="setserverinfo"></a>CDocTemplate：：设置服务器信息

确定服务器文档在就地嵌入或编辑时的资源和类。

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>参数

*nIDOle 嵌入*<br/>
在单独的窗口中打开嵌入对象时使用的资源的 ID。

*nIDOleInplace服务器*<br/>
就地激活嵌入对象时使用的资源的 ID。

*pOleFrame 类*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针，其中包含发生就地激活时创建的帧窗口对象的类信息。

*pOleView 类*<br/>
指向包含`CRuntimeClass`发生就地激活时创建的视图对象的类信息的结构的指针。

### <a name="remarks"></a>备注

调用此成员函数以标识在用户请求激活嵌入对象时服务器应用程序将使用的资源。 这些资源由菜单和快捷键表组成。 此函数通常在应用程序中调用`InitInstance`。

与*nIDOleInPlaceServer*关联的菜单包含允许服务器菜单与容器菜单合并的分隔符。 有关合并服务器和容器菜单的详细信息，请参阅文章["菜单和资源 "（OLE）。](../../mfc/menus-and-resources-ole.md)

## <a name="cdoctemplatecreatepreviewframe"></a><a name="createpreviewframe"></a>CDocTemplate：：创建预览框架

创建用于"丰富预览"的子框架。

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向父窗口的指针（通常由 Shell 提供）。

*pDoc*<br/>
指向文档对象的指针，其内容将预览。

### <a name="return-value"></a>返回值

指向`CFrameWnd`对象的有效指针，如果创建失败，则为 NULL。

### <a name="remarks"></a>备注

## <a name="cdoctemplatesetpreviewinfo"></a><a name="setpreviewinfo"></a>CDocTemplate：：设置预览信息

设置进程外预览处理程序。

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>参数

*nID预览框架*<br/>
指定预览帧的资源 ID。

*p 预览框架类*<br/>
指定指向预览帧的运行时类信息结构的指针。

*p预览视图类*<br/>
指定指向预览视图的运行时类信息结构的指针。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate 类](../../mfc/reference/csingledoctemplate-class.md)<br/>
[C 多文档模板类](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CScrollView 类](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView 类](../../mfc/reference/ceditview-class.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)
