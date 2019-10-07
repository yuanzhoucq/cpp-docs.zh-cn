---
title: COleServerDoc 类
ms.date: 11/04/2016
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
ms.openlocfilehash: eec94a32fa0963d4cf2eccae0fb9e2423e75ffdc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503814"
---
# <a name="coleserverdoc-class"></a>COleServerDoc 类

OLE 服务器文档的基类。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|构造 `COleServerDoc` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|激活关联的 DocObject 文档。|
|[COleServerDoc::ActivateInPlace](#activateinplace)|激活文档以便进行就地编辑。|
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|停用服务器的用户界面。|
|[COleServerDoc::DiscardUndoState](#discardundostate)|丢弃撤消状态信息。|
|[COleServerDoc::GetClientSite](#getclientsite)|检索指向基础`IOleClientSite`接口的指针。|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|返回一个指向表示整个文档的项的指针。|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|返回当前用于就地编辑的剪辑矩形。|
|[COleServerDoc::GetItemPosition](#getitemposition)|对于就地编辑，返回相对于容器应用程序工作区的当前位置矩形。|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|返回以像素为单位的缩放系数。|
|[COleServerDoc::IsDocObject](#isdocobject)|确定文档是否为 DocObject。|
|[COleServerDoc::IsEmbedded](#isembedded)|指示文档是嵌入到容器文档中还是独立运行。|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|如果当前正在就地激活该项，则返回 TRUE。|
|[COleServerDoc::NotifyChanged](#notifychanged)|通知容器用户已更改文档。|
|[COleServerDoc::NotifyClosed](#notifyclosed)|通知容器用户已关闭文档。|
|[COleServerDoc::NotifyRename](#notifyrename)|通知容器：用户已将文档重命名为。|
|[COleServerDoc::NotifySaved](#notifysaved)|通知容器用户用户已保存文档。|
|[COleServerDoc::OnDeactivate](#ondeactivate)|当用户停用就地激活的项时由框架调用。|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|由框架调用，用于销毁为就地激活创建的控件和其他用户界面元素。|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|当激活或停用容器的文档框架窗口时由框架调用。|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|当调整容器应用程序的框架窗口或文档窗口大小时，由框架调用。|
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|由框架调用，用于显示或隐藏用于就地编辑的控件条。|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|当保存作为嵌入项的服务器文档时由框架调用，它更新项的容器副本。|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|更改就地编辑框的位置。|
|[COleServerDoc::SaveEmbedding](#saveembedding)|通知容器应用程序保存文档。|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|滚动容器文档。|
|[COleServerDoc::UpdateAllItems](#updateallitems)|通知容器用户已更改文档。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|由框架调用，用于创建就地编辑的框架窗口。|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|由框架调用，用于销毁框架窗口以进行就地编辑。|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|重写此函数以创建新`CDocObjectServer`的对象，并指示此文档是 DocObject 容器。|
|[COleServerDoc::OnClose](#onclose)|当容器请求关闭文档时由框架调用。|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|执行指定的命令或显示该命令的帮助。|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|当激活或停用容器的框架窗口时由框架调用。|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|调用以获取一个`COleServerItem`表示整个文档的; 用于获取嵌入项。 需要实现。|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|由框架调用以撤消就地编辑过程中所做的更改。|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|当容器为嵌入的对象设置窗口标题时由框架调用。|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|由框架调用，以在容器应用程序的窗口中定位就地编辑框架窗口。|
|[COleServerDoc::OnShowDocument](#onshowdocument)|由框架调用以显示或隐藏文档。|

## <a name="remarks"></a>备注

服务器文档可以包含[COleServerItem](../../mfc/reference/coleserveritem-class.md)对象，这些对象表示嵌入或链接项的服务器接口。 如果容器启动服务器应用程序以编辑嵌入项，则会将该项作为其自己的服务器文档加载;对象只包含一个`COleServerItem`对象，其中包含整个文档。 `COleServerDoc` 当容器启动服务器应用程序以编辑链接项时，将从磁盘加载现有文档;文档内容的一部分将突出显示以指示链接项。

`COleServerDoc`对象也可以包含[COleClientItem](../../mfc/reference/coleclientitem-class.md)类的项。 这允许您创建容器-服务器应用程序。 在为`COleServerItem`对象提供服务时，框架`COleClientItem`提供用于正确存储项的函数。

如果你的服务器应用程序不支持链接，则服务器文档将始终只包含一个服务器项，这会将整个嵌入对象表示为文档。 如果你的服务器应用程序支持链接，则每次将选定内容复制到剪贴板时，它都必须创建一个服务器项。

若要`COleServerDoc`使用，请从中派生类并实现[OnGetEmbeddedItem](#ongetembeddeditem)成员函数，使服务器能够支持嵌入项。 从中`COleServerItem`派生一个类，以实现文档中的项，并从`OnGetEmbeddedItem`返回该类的对象。

为支持链接项， `COleServerDoc`提供[OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem)成员函数。 如果你有自己的管理文档项的方式，则可以使用默认实现或重写它。

您的应用`COleServerDoc`程序支持的每种服务器文档都需要一个派生类。 例如，如果您的服务器应用程序支持工作表和图表，则`COleServerDoc`需要两个派生类。

有关服务器的详细信息，请参阅文章[服务器：实现服务器](../../mfc/servers-implementing-a-server.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>要求

**标头：** afxole

##  <a name="activatedocobject"></a>  COleServerDoc::ActivateDocObject

激活关联的 DocObject 文档。

```
void ActivateDocObject();
```

### <a name="remarks"></a>备注

默认情况下`COleServerDoc` ，不支持活动文档（也称为 DocObjects）。 若要启用此支持，请参阅[GetDocObjectServer](#getdocobjectserver)和类[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)。

##  <a name="activateinplace"></a>  COleServerDoc::ActivateInPlace

为就地编辑激活该项。

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>返回值

如果成功，则为非零值;否则为0，指示该项已完全打开。

### <a name="remarks"></a>备注

此函数执行就地激活所需的所有操作。 它将创建一个就地框架窗口，将其激活并调整为该项，设置共享菜单和其他控件，将该项滚动到视图中，并将焦点设置到就地框架窗口中。

此函数由[COleServerItem：： OnShow](../../mfc/reference/coleserveritem-class.md#onshow)的默认实现调用。 如果你的应用程序支持用于就地激活（如播放）的另一个谓词，则调用此函数。

##  <a name="coleserverdoc"></a>  COleServerDoc::COleServerDoc

构造一个`COleServerDoc`对象，而不与 OLE 系统 dll 连接。

```
COleServerDoc();
```

### <a name="remarks"></a>备注

必须调用[COleLinkingDoc：： Register](../../mfc/reference/colelinkingdoc-class.md#register)才能打开与 OLE 的通信。 如果在应用程序中使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) ， `COleLinkingDoc::Register`则`OnNewDocument`通过`COleLinkingDoc`的、 `OnOpenDocument`和`OnSaveDocument`实现调用。

##  <a name="createinplaceframe"></a>  COleServerDoc::CreateInPlaceFrame

框架调用此函数来创建一个用于就地编辑的框架窗口。

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
指向容器应用程序的父窗口的指针。

### <a name="return-value"></a>返回值

指向就地框架窗口的指针，如果不成功，则为 NULL。

### <a name="remarks"></a>备注

默认实现使用文档模板中指定的信息来创建框架。 使用的视图是为文档创建的第一个视图。 此视图与原始帧暂时分离，并附加到新创建的帧。

这是一种高级的可重写。

##  <a name="deactivateandundo"></a>  COleServerDoc::DeactivateAndUndo

如果你的应用程序支持撤消，并且用户在激活项后，但在编辑之前选择 "撤消"，则调用此函数。

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

如果使用 Microsoft 基础类库编写容器应用程序，调用此函数将导致调用[COleClientItem：： OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) ，这将停用服务器的用户界面。

##  <a name="destroyinplaceframe"></a>  COleServerDoc::DestroyInPlaceFrame

框架调用此函数以销毁就地框架窗口，并将服务器应用程序的文档窗口返回到就地激活之前的状态。

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>参数

*pFrameWnd*<br/>
指向要销毁的就地框架窗口的指针。

### <a name="remarks"></a>备注

这是一种高级的可重写。

##  <a name="discardundostate"></a>COleServerDoc：:D iscardUndoState

如果用户执行的编辑操作无法撤消，请调用此函数以强制容器应用程序放弃其撤消状态信息。

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

提供此函数的目的是，支持 Undo 的服务器可以释放不能使用的撤消状态信息所使用的资源。

##  <a name="getclientsite"></a>COleServerDoc：： GetClientSite

检索指向基础`IOleClientSite`接口的指针。

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>返回值

检索指向基础[IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)接口的指针。

##  <a name="getdocobjectserver"></a>  COleServerDoc::GetDocObjectServer

重写此函数以创建新`CDocObjectServer`项并返回指向它的指针。

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>参数

*pDocSite*<br/>
指向`IOleDocumentSite`接口的指针，该接口将此文档连接到服务器。

### <a name="return-value"></a>返回值

指向的`CDocObjectServer`指针;如果操作失败，则为 NULL。

### <a name="remarks"></a>备注

激活 DocObject 服务器后，返回非 NULL 指针将显示客户端可以支持 DocObjects。 默认实现返回 NULL。

支持 DocObjects 的文档的典型实现只是分配新`CDocObjectServer`的对象并将其返回给调用方。 例如：

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>COleServerDoc：： GetEmbeddedItem

调用此函数可获取指向表示整个文档的项的指针。

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>返回值

指向表示整个文档的项的指针;如果操作失败，则为 NULL。

### <a name="remarks"></a>备注

它调用[COleServerDoc：： OnGetEmbeddedItem](#ongetembeddeditem)，这是一个没有默认实现的虚函数。

##  <a name="getitemcliprect"></a>  COleServerDoc::GetItemClipRect

`GetItemClipRect`调用成员函数以获取正在就地编辑的项的剪辑矩形坐标。

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>参数

*lpClipRect*<br/>
指向`RECT`结构的指针， `CRect`或用于接收项的剪辑矩形坐标的对象。

### <a name="remarks"></a>备注

坐标以像素为单位，相对于容器应用程序窗口的工作区。

绘图不应出现在剪辑矩形的外部。 通常，绘图会自动受到限制。 使用此函数可确定用户是否已在文档的可见部分之外滚动;如果是这样，可以通过调用[ScrollContainerBy](#scrollcontainerby)来按需滚动容器文档。

##  <a name="getitemposition"></a>  COleServerDoc::GetItemPosition

`GetItemPosition`调用成员函数以获取正在就地编辑的项的坐标。

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>参数

*lpPosRect*<br/>
指向`RECT`结构的指针， `CRect`或用于接收该项坐标的对象。

### <a name="remarks"></a>备注

坐标以像素为单位，相对于容器应用程序窗口的工作区。

项的位置可以与当前的剪辑矩形进行比较，以确定项在屏幕上可见（或不可见）的程度。

##  <a name="getzoomfactor"></a>  COleServerDoc::GetZoomFactor

`GetZoomFactor`成员函数确定已为就地编辑激活的项的 "缩放系数"。

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>参数

*lpSizeNum*<br/>
指向类`CSize`的对象的指针，它将保存缩放系数的分子。 可以为 NULL。

*lpSizeDenom*<br/>
指向类`CSize`的对象的指针，它将保存缩放系数的分母。 可以为 NULL。

*lpPosRect*<br/>
指向类的对象的指针`CRect` ，该类描述项的新位置。 如果此参数为 NULL，则函数将使用项的当前位置。

### <a name="return-value"></a>返回值

如果为就地编辑激活项并且其缩放系数不是 100% （1:1），则为非零值;否则为0。

### <a name="remarks"></a>备注

缩放系数（以像素为单位）是项大小与当前范围的比例。 如果容器应用程序未设置项的区，则使用其自然范围（如[COleServerItem：： OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)所确定）。

函数将它的前两个参数设置为项的 "缩放系数" 的分子和分母。 如果未就地编辑项，则函数会将这些参数设置为默认值 100% （或1:1），并返回零。 有关详细信息，请参阅技术说明40：[就地调整大小和缩放](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。

##  <a name="isdocobject"></a>  COleServerDoc::IsDocObject

确定文档是否为 DocObject。

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>返回值

如果文档是 DocObject，则为 TRUE;否则为 FALSE。

##  <a name="isembedded"></a>COleServerDoc：： IsEmbedded

`IsEmbedded`调用成员函数以确定文档是否表示嵌入到容器中的对象。

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>返回值

如果`COleServerDoc`对象是表示嵌入到容器中的对象的文档，则为非零; 否则为0。

### <a name="remarks"></a>备注

从文件加载的文档不是嵌入的，尽管它可能由容器应用程序作为链接进行操作。 嵌入到容器文档中的文档被视为嵌入文档。

##  <a name="isinplaceactive"></a>  COleServerDoc::IsInPlaceActive

`IsInPlaceActive`调用成员函数以确定项当前是否处于就地活动状态。

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>返回值

如果`COleServerDoc`对象处于活动状态，则为非零; 否则为0。

##  <a name="notifychanged"></a>COleServerDoc：： NotifyChanged

调用此函数可通知连接到文档的所有链接项文档已更改。

```
void NotifyChanged();
```

### <a name="remarks"></a>备注

通常，在用户更改某些全局属性（如服务器文档的维度）后，调用此函数。 如果某个 OLE 项已链接到带有自动链接的文档，则该项将更新以反映所做的更改。 在用 Microsoft 基础类库编写的容器应用程序中 `COleClientItem`，调用的 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 成员函数。

> [!NOTE]
>  提供此函数是为了与 OLE 1 兼容。 新应用程序应使用[UpdateAllItems](#updateallitems)。

##  <a name="notifyclosed"></a>  COleServerDoc::NotifyClosed

调用此函数可通知容器文档已关闭。

```
void NotifyClosed();
```

### <a name="remarks"></a>备注

当用户从 "文件" 菜单中选择 "关闭" `NotifyClosed`命令时， `COleServerDoc`将调用[OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument)成员函数的实现。 在用 Microsoft 基础类库编写的容器应用程序中 `COleClientItem`，调用的 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 成员函数。

##  <a name="notifyrename"></a>  COleServerDoc::NotifyRename

在用户重命名服务器文档后调用此函数。

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>参数

*lpszNewName*<br/>
指向指定服务器文档的新名称的字符串的指针;这通常是一个完全限定的路径。

### <a name="remarks"></a>备注

当用户从 "文件" 菜单中选择 "另存为`NotifyRename` " 命令时`COleServerDoc`，将调用[onopendocument](../../mfc/reference/cdocument-class.md#onsavedocument)成员函数的实现。 此函数通知 OLE 系统 Dll，进而通知容器。 在用 Microsoft 基础类库编写的容器应用程序中 `COleClientItem`，调用的 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 成员函数。

##  <a name="notifysaved"></a>  COleServerDoc::NotifySaved

用户保存服务器文档后调用此函数。

```
void NotifySaved();
```

### <a name="remarks"></a>备注

当用户从 "文件" 菜单中选择 "保存" `NotifySaved`命令时，将通过`COleServerDoc`的[onopendocument](../../mfc/reference/cdocument-class.md#onsavedocument)实现来调用。 此函数通知 OLE 系统 Dll，进而通知容器。 在用 Microsoft 基础类库编写的容器应用程序中 `COleClientItem`，调用的 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 成员函数。

##  <a name="onclose"></a>  COleServerDoc::OnClose

当容器请求关闭服务器文档时由框架调用。

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>参数

*dwCloseOption*<br/>
枚举 OLECLOSE 中的一个值。 此参数可以具有下列值之一：

- OLECLOSE_SAVEIFDIRTY 如果文件已被修改，则保存该文件。

- OLECLOSE_NOSAVE 文件在不保存的情况下关闭。

- OLECLOSE_PROMPTSAVE 如果文件已被修改，则系统会提示用户保存该文件。

### <a name="remarks"></a>备注

默认实现调用`CDocument::OnCloseDocument`。

有关详细信息和其他值，请参阅 Windows SDK 中的[OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) 。

##  <a name="ondeactivate"></a>  COleServerDoc::OnDeactivate

当用户停用当前就地活动的嵌入项或链接项时由框架调用。

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>备注

此函数将容器应用程序的用户界面还原到其原始状态，并销毁为就地激活创建的所有菜单和其他控件。

此时应无条件释放撤消状态信息。

有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)。

##  <a name="ondeactivateui"></a>  COleServerDoc::OnDeactivateUI

当用户停用就地激活的项时调用。

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>参数

*bUndoable*<br/>
指定是否可以撤消编辑更改。

### <a name="remarks"></a>备注

此函数将容器应用程序的用户界面还原到其原始状态，并隐藏为就地激活创建的任何菜单和其他控件。

框架始终将*bUndoable*设置为 FALSE。 如果服务器支持撤消并且有可撤消的操作，请调用*bUndoable*设置为 TRUE 的基类实现。

##  <a name="ondocwindowactivate"></a>  COleServerDoc::OnDocWindowActivate

框架调用此函数以激活或停用文档窗口进行就地编辑。

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>参数

*bActivate*<br/>
指定是否激活或停用文档窗口。

### <a name="remarks"></a>备注

默认实现将删除或添加相应的帧级用户界面元素。 如果要在包含项目的文档被激活或停用时执行其他操作，请重写此函数。

有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)。

##  <a name="onexecolecmd"></a>  COleServerDoc::OnExecOleCmd

框架调用此函数来执行指定的命令或显示该命令的帮助。

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>参数

*pguidCmdGroup*<br/>
指向标识一组命令的 GUID 的指针。 可以为 NULL，以指示默认命令组。

*nCmdID*<br/>
要执行的命令。 必须位于由*pguidCmdGroup*标识的组中。

*nCmdExecOut*<br/>
对象执行命令的方式为 OLECMDEXECOPT 枚举中的一个或多个以下值：

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
指向包含命令的输入参数的 VARIANTARG 的指针。 可以为 NULL。

*pvarargOut*<br/>
指向 VARIANTARG 的指针，用于接收来自命令的输出返回值。 可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK;否则，会出现以下错误代码之一：

|值|描述|
|-----------|-----------------|
|E_UNEXPECTED|发生了意外错误|
|E_FAIL|出现错误|
|E_NOTIMPL|指示 MFC 本身应尝试转换和调度命令|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*为非 NULL，但未指定可识别的命令组|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*未被识别为组*pguidCmdGroup*中的有效命令。|
|OLECMDERR_DISABLED|*NCmdID*标识的命令已禁用，无法执行|
|OLECMDERR_NOHELP|调用方请求有关由*nCmdID*标识的命令的帮助，但没有可用的帮助|
|OLECMDERR_CANCELED|用户取消了执行|

### <a name="remarks"></a>备注

`COleCmdUI`可用于启用、更新和设置 DocObject 用户界面命令的其他属性。 初始化命令后，可以通过`OnExecOleCmd`执行这些命令。

框架在尝试转换和调度 OLE 文档命令之前调用函数。 不需要重写此函数来处理标准 OLE 文档命令，但是，如果您想要处理您自己的自定义命令或处理接受参数或返回结果的命令，则必须提供此函数的重写。

大多数命令不采用参数或返回值。 对于大多数命令，调用方可以传递*pvarargIn*和*PvarargOut*的 null 值。 对于需要输入值的命令，调用方可以声明和初始化 VARIANTARG 变量，并将指针传递到*pvarargIn*中的变量。 对于需要单个值的命令，可以直接将参数存储在 VARIANTARG 中并将其传递给函数。 必须使用支持的类型之一（如`IDispatch`和 SAFEARRAY）在 VARIANTARG 内打包多个参数。

同样，如果命令返回参数，调用方应声明 VARIANTARG，将其初始化为 VT_EMPTY，并在*pvarargOut*中传递其地址。 如果命令返回单个值，则对象可以直接将该值存储在*pvarargOut*中。 必须以某种适用于 VARIANTARG 的方式打包多个输出值。

此函数的基类实现将遍历与命令目标相关联的 OLE_COMMAND_MAP 结构，并尝试将命令调度到适当的处理程序。 基类实现仅适用于不接受参数或返回值的命令。 如果需要处理接受参数或返回值的命令，则必须重写此函数，并自行处理*pvarargIn*和*pvarargOut*参数。

##  <a name="onframewindowactivate"></a>  COleServerDoc::OnFrameWindowActivate

当激活或停用容器应用程序的框架窗口时，框架会调用此函数。

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>参数

*bActivate*<br/>
指定是否激活或停用框架窗口。

### <a name="remarks"></a>备注

默认实现取消框架窗口可能位于的任何帮助模式。 如果要在框架窗口被激活或停用时执行特殊处理，请重写此函数。

有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)。

##  <a name="ongetembeddeditem"></a>  COleServerDoc::OnGetEmbeddedItem

当容器应用程序调用服务器应用程序以创建或编辑嵌入项时，由框架调用。

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>返回值

指向表示整个文档的项的指针;如果操作失败，则为 NULL。

### <a name="remarks"></a>备注

没有默认实现。 必须重写此函数才能返回表示整个文档的项。 此返回值应为派生类的对象`COleServerItem`。

##  <a name="onreactivateandundo"></a>  COleServerDoc::OnReactivateAndUndo

当用户选择撤消对已激活的项所做的更改时，框架会调用此函数，已更改，随后将其停用。

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

默认实现不执行任何操作，除非返回 FALSE，以指示失败。

如果你的应用程序支持撤消，则重写此函数。 通常，您将执行撤消操作，然后通过调用`ActivateInPlace`来激活该项。 如果容器应用程序是用 Microsoft 基础类库编写的，则`COleClientItem::ReactivateAndUndo`调用将导致调用此函数。

##  <a name="onresizeborder"></a>  COleServerDoc::OnResizeBorder

当容器应用程序的框架窗口更改大小时，框架将调用此函数。

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>参数

*lpRectBorder*<br/>
指向`RECT`结构的指针`CRect`或指定边框坐标的对象。

*lpUIWindow*<br/>
指向拥有当前就地编辑会话`IOleInPlaceUIWindow`的类的对象的指针。

*bFrame*<br/>
如果*lpUIWindow*指向容器应用程序的顶级框架窗口，则为 TRUE; 如果*lpUIWindow*指向容器应用程序的文档级框架窗口，则为 FALSE。

### <a name="remarks"></a>备注

此函数根据新的窗口大小调整工具栏和其他用户界面元素的大小并调整其大小。

有关详细信息，请参阅 Windows SDK 中的[IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) 。

这是一种高级的可重写。

##  <a name="onsethostnames"></a>COleServerDoc：： OnSetHostNames

当容器设置或更改此文档的主机名时由框架调用。

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>参数

*lpszHost*<br/>
指向字符串的指针，该字符串指定容器应用程序的名称。

*lpszHostObj*<br/>
指向字符串的指针，该字符串指定文档的容器名称。

### <a name="remarks"></a>备注

默认实现更改引用此文档的所有视图的文档标题。

如果你的应用程序通过其他机制设置标题，则重写此函数。

##  <a name="onsetitemrects"></a>  COleServerDoc::OnSetItemRects

框架调用此函数以将就地编辑框架窗口放置在容器应用程序的框架窗口中。

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>参数

*lpPosRect*<br/>
指向`RECT`结构的指针`CRect`或指定就地框架窗口相对于容器应用程序工作区的位置的对象。

*lpClipRect*<br/>
指向`RECT`结构的指针`CRect`或指定就地框架窗口相对于容器应用程序的工作区的剪辑矩形的对象。

### <a name="remarks"></a>备注

如果需要，请重写此函数以更新视图的缩放系数。

此函数通常是为了响应`RequestPositionChange`调用而调用的，不过，它可以随时调用此函数以请求就地项的位置更改。

##  <a name="onshowcontrolbars"></a>COleServerDoc：： OnShowControlBars

框架调用此函数以显示或隐藏与由*pFrameWnd*标识的框架窗口关联的服务器应用程序的控制条。

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>参数

*pFrameWnd*<br/>
指向其控制条应隐藏或显示的框架窗口的指针。

*bShow*<br/>
确定是显示还是隐藏控件条。

### <a name="remarks"></a>备注

默认实现将枚举该框架窗口拥有的所有控制条，并隐藏或显示它们。

##  <a name="onshowdocument"></a>COleServerDoc：： OnShowDocument

当必须隐藏或`OnShowDocument`显示服务器文档时，框架将调用函数。

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
指定是否显示或隐藏文档的用户界面。

### <a name="remarks"></a>备注

如果*bShow*为 TRUE，则默认实现将激活服务器应用程序（如有必要），并使容器应用程序滚动其窗口，使项可见。 如果*bShow*为 FALSE，则默认实现通过调用来`OnDeactivate`停用项，然后销毁或隐藏已为文档创建的所有框架窗口（第一个除外）。 如果没有任何可见文档，则默认实现将隐藏服务器应用程序。

##  <a name="onupdatedocument"></a>COleServerDoc：： OnUpdateDocument

当保存作为复合文档中嵌入项的文档时，由框架调用。

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>返回值

如果成功更新了文档，则为非零值;否则为0。

### <a name="remarks"></a>备注

默认实现将调用[COleServerDoc：： NotifySaved](#notifysaved)和[COleServerDoc：： SaveEmbedding](#saveembedding)成员函数，然后将该文档标记为 clean。 如果要在更新嵌入项时执行特殊处理，请重写此函数。

##  <a name="requestpositionchange"></a>COleServerDoc：： RequestPositionChange

调用此成员函数以使容器应用程序更改项的位置。

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>参数

*lpPosRect*<br/>
指向`RECT`结构的指针`CRect`或包含该项的新位置的对象。

### <a name="remarks"></a>备注

当就地活动项中的数据更改时`UpdateAllItems`，通常会调用此函数（与一起）。 在此调用之后，容器可能会或不会通过调用`OnSetItemRects`来执行更改。 生成的位置可能与请求的位置不同。

##  <a name="saveembedding"></a>COleServerDoc：： SaveEmbedding

调用此函数可通知容器应用程序保存嵌入的对象。

```
void SaveEmbedding();
```

### <a name="remarks"></a>备注

此函数由自动`OnUpdateDocument`调用。 请注意，此函数会导致在磁盘上更新项，因此通常仅作为特定用户操作的结果调用。

##  <a name="scrollcontainerby"></a>COleServerDoc：： ScrollContainerBy

调用成员函数以按`sizeScroll`所指示的量（以像素为单位）滚动容器文档。 `ScrollContainerBy`

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>参数

*sizeScroll*<br/>
指示容器文档滚动的距离。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

正值表示向下和向右滚动;负值指示向上和向左滚动。

##  <a name="updateallitems"></a>  COleServerDoc::UpdateAllItems

调用此函数可通知连接到文档的所有链接项文档已更改。

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>参数

*pSender*<br/>
指向修改文档的项的指针; 如果要更新所有项，则为 NULL。

*lHint*<br/>
包含有关修改的信息。

*pHint*<br/>
指向存储有关修改信息的对象的指针。

*nDrawAspect*<br/>
确定如何绘制项。 这是 DVASPECT 枚举中的一个值。 此参数可以具有下列值之一：

- DVASPECT_CONTENT 项以这种方式表示，它可以在其容器中显示为嵌入的对象。

- DVASPECT_THUMBNAIL 项以 "缩略图" 表示形式呈现，以便可以在浏览工具中显示它。

- DVASPECT_ICON 项由图标表示。

- DVASPECT_DOCPRINT 项表示为使用 "文件" 菜单中的 "打印" 命令打印项。

### <a name="remarks"></a>备注

通常在用户更改服务器文档后调用此函数。 如果某个 OLE 项已链接到带有自动链接的文档，则该项将更新以反映所做的更改。 在用 Microsoft 基础类库编写的容器应用程序中 `COleClientItem`，调用的 [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 成员函数。

此函数为文档`OnUpdate`的每个项（发送项除外，传递*pHint*、 *lHint*和*nDrawAspect*）调用成员函数。 使用这些参数将信息传递到有关对文档所做的修改的项。 您可以使用*lHint*对信息进行编码，也可以`CObject`定义一个派生类，用于存储有关修改的信息并使用*pHint*传递该类的对象。 重写`OnUpdate`派生类`COleServerItem`中的成员函数，以优化每个项的更新，具体取决于其演示是否已更改。

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc 类](../../mfc/reference/colelinkingdoc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDocument 类](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc 类](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
