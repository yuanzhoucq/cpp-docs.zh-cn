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
ms.openlocfilehash: 8e75ec5c00c614a225a059a2b3cf97a7a307c61c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753785"
---
# <a name="coleserverdoc-class"></a>COleServerDoc 类

OLE 服务器文档的基类。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleServerDoc：COleServerDoc](#coleserverdoc)|构造 `COleServerDoc` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleServerDoc：：激活文档对象](#activatedocobject)|激活关联的文档对象文档。|
|[COleServerDoc：：激活原位](#activateinplace)|激活文档进行就地编辑。|
|[COleServerDoc：:D](#deactivateandundo)|停用服务器的用户界面。|
|[COleServerDoc：:DiscardUndoState](#discardundostate)|丢弃撤消状态信息。|
|[COleServerDoc：获取客户端网站](#getclientsite)|检索指向基础`IOleClientSite`接口的指针。|
|[COleServerDoc：获取嵌入式项目](#getembeddeditem)|返回指向表示整个文档的项的指针。|
|[COleServerDoc：获取项目剪辑](#getitemcliprect)|返回当前裁剪矩形以进行就地编辑。|
|[COleServerDoc：获取项目位置](#getitemposition)|返回当前位置矩形（相对于容器应用程序的工作区），以便进行就地编辑。|
|[COleServerDoc：获取ZoomFactor](#getzoomfactor)|返回以像素为单位的缩放系数。|
|[COleServerDoc：isDocObject](#isdocobject)|确定文档是否为文档对象。|
|[COleServerDoc：是嵌入式的](#isembedded)|指示文档是嵌入容器文档还是独立运行。|
|[COleServerDoc：即处于主动状态](#isinplaceactive)|如果项目当前已激活到位，则返回 TRUE。|
|[COleServerDoc：通知已更改](#notifychanged)|通知容器用户已更改文档。|
|[COleServerDoc：：通知已关闭](#notifyclosed)|通知容器用户已关闭文档。|
|[COleServerDoc：通知重新命名](#notifyrename)|通知容器用户已重命名文档。|
|[COleServerDoc：通知已保存](#notifysaved)|通知容器用户已保存文档。|
|[COleServerDoc：打开激活](#ondeactivate)|当用户停用就地激活的项目时，由框架调用。|
|[COleServerDoc：：打开停用UI](#ondeactivateui)|由框架调用以销毁为就地激活创建的控件和其他用户界面元素。|
|[COleServerDoc：：在DocWindow激活](#ondocwindowactivate)|当容器的文档框窗口激活或停用时，由框架调用。|
|[COleServerDoc：：在重调整边界](#onresizeborder)|调整容器应用程序的框架窗口或文档窗口的大小时，由框架调用。|
|[COleServerDoc：：在显示控制栏](#onshowcontrolbars)|框架调用以显示或隐藏控制栏进行就地编辑。|
|[COleServerDoc：更新文档](#onupdatedocument)|在保存作为嵌入项的服务器文档时，由框架调用，更新容器的项副本。|
|[COleServerDoc：：请求位置更改](#requestpositionchange)|更改就地编辑框架的位置。|
|[COleServerDoc：：保存嵌入](#saveembedding)|告诉容器应用程序保存文档。|
|[COleServerDoc：：滚动容器By](#scrollcontainerby)|滚动容器文档。|
|[COleServerDoc：更新所有项目](#updateallitems)|通知容器用户已更改文档。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[COleServerDoc：：创建在位帧](#createinplaceframe)|框架调用以创建用于就地编辑的框架窗口。|
|[COleServerDoc：:D](#destroyinplaceframe)|框架调用以销毁用于就地编辑的框架窗口。|
|[COleServerDoc：获取Doc对象服务器](#getdocobjectserver)|重写此函数以创建新`CDocObjectServer`对象，并指示此文档是 DocObject 容器。|
|[COleServerDoc：关闭](#onclose)|当容器请求关闭文档时，由框架调用。|
|[COleServerDoc：：OnExecOleCmd](#onexecolecmd)|执行指定的命令或显示该命令的帮助。|
|[COleServerDoc：在框架窗口激活](#onframewindowactivate)|当容器的帧窗口激活或停用时，由框架调用。|
|[COleServerDoc：：在嵌入式项目上](#ongetembeddeditem)|调用 以获取`COleServerItem`表示整个文档的 ;用于获取嵌入项。 需要实施。|
|[COleServerDoc：：重新激活和Undo](#onreactivateandundo)|由框架调用以撤消在就地编辑期间所做的更改。|
|[COleServerDoc：：打开主机名](#onsethostnames)|当容器设置嵌入对象的窗口标题时，由框架调用。|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|由框架调用，将就地编辑框架窗口放置在容器应用程序的窗口内。|
|[COleServerDoc：在显示文档上](#onshowdocument)|由框架调用以显示或隐藏文档。|

## <a name="remarks"></a>备注

服务器文档可以包含[COleServerItem 对象](../../mfc/reference/coleserveritem-class.md)，这些对象表示嵌入或链接项的服务器接口。 当容器启动服务器应用程序以编辑嵌入的项目时，该项目将加载为其自己的服务器文档;当容器启动服务器应用程序以编辑嵌入项时，该项将加载为其自己的服务器文档。对象`COleServerDoc`仅包含一个`COleServerItem`对象，由整个文档组成。 当容器启动服务器应用程序以编辑链接项时，将从磁盘加载现有文档;当服务器应用程序通过容器启动时，将从磁盘加载现有文档。文档内容的一部分突出显示以指示链接项。

`COleServerDoc`对象还可以包含[COleClientItem](../../mfc/reference/coleclientitem-class.md)类的项目。 这允许您创建容器服务器应用程序。 框架提供函数，用于在为`COleClientItem``COleServerItem`对象提供服务时正确存储项。

如果服务器应用程序不支持链接，则服务器文档将始终只包含一个服务器项，该服务器项将整个嵌入对象表示为文档。 如果服务器应用程序确实支持链接，则必须在每次将所选内容复制到剪贴板时创建服务器项。

要使用`COleServerDoc`，从派生类并实现[OnGetEmbeddedItem](#ongetembeddeditem)成员函数，该函数允许服务器支持嵌入项。 派生`COleServerItem`类以实现文档中的项，并从 返回该类的对象`OnGetEmbeddedItem`。

要支持链接的项目，`COleServerDoc`提供[OnGetLinkItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem)成员功能。 如果您有自己的方法来管理文档项，则可以使用默认实现或重写它。

对于应用程序支持的`COleServerDoc`每种服务器文档类型，都需要一个派生类。 例如，如果服务器应用程序支持工作表和图表，则需要两`COleServerDoc`个派生类。

有关服务器的详细信息，请参阅文章["服务器：实现服务器](../../mfc/servers-implementing-a-server.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coleserverdocactivatedocobject"></a><a name="activatedocobject"></a>COleServerDoc：：激活文档对象

激活关联的文档对象文档。

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>备注

默认情况下，`COleServerDoc`不支持活动文档（也称为文档对象）。 要启用此支持，请参阅[GetDocObjectServer](#getdocobjectserver)和类[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)。

## <a name="coleserverdocactivateinplace"></a><a name="activateinplace"></a>COleServerDoc：：激活原位

激活项目进行就地编辑。

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>返回值

如果成功，则非零;否则 0，表示项目已完全打开。

### <a name="remarks"></a>备注

此函数执行就地激活所需的所有操作。 它创建一个就地框架窗口，激活它并将其大小调整到项目，设置共享菜单和其他控件，将项目滚动到视图中，并将焦点设置到就地框架窗口。

此函数由[COleServerItem 的默认实现调用：：OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。 如果应用程序支持另一个用于就地激活的谓词（如 Play），请调用此函数。

## <a name="coleserverdoccoleserverdoc"></a><a name="coleserverdoc"></a>COleServerDoc：COleServerDoc

构造`COleServerDoc`对象而不与 OLE 系统 DLL 连接。

```
COleServerDoc();
```

### <a name="remarks"></a>备注

您必须致电[COle链接Doc：注册](../../mfc/reference/colelinkingdoc-class.md#register)才能打开与 OLE 的通信。 如果您在应用程序中使用[COleTemplateServer，](../../mfc/reference/coletemplateserver-class.md)`COleLinkingDoc::Register`则`COleLinkingDoc`调用 的 实现`OnNewDocument`。 `OnSaveDocument` `OnOpenDocument`

## <a name="coleserverdoccreateinplaceframe"></a><a name="createinplaceframe"></a>COleServerDoc：：创建在位帧

框架调用此函数以创建用于就地编辑的框架窗口。

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向容器应用程序的父窗口的指针。

### <a name="return-value"></a>返回值

指向就地帧窗口的指针，如果失败，则指向 NULL。

### <a name="remarks"></a>备注

默认实现使用文档模板中指定的信息来创建框架。 使用的视图是为文档创建的第一个视图。 此视图暂时与原始帧分离，并附加到新创建的帧。

这是一个高级的可重写。

## <a name="coleserverdocdeactivateandundo"></a><a name="deactivateandundo"></a>COleServerDoc：:D

如果应用程序支持"撤消"，并且用户在激活项目后但在编辑项目之前选择"撤消"，请调用此函数。

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

如果容器应用程序是使用 Microsoft 基础类库编写的，则调用此函数会导致调用[COleClientItem：：ondeactivate 和Undo，](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo)从而停用服务器的用户界面。

## <a name="coleserverdocdestroyinplaceframe"></a><a name="destroyinplaceframe"></a>COleServerDoc：:D

框架调用此函数以销毁就地帧窗口，并在就地激活之前将服务器应用程序的文档窗口返回到其状态。

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>参数

*pFramewnd*<br/>
指向要销毁的就地帧窗口的指针。

### <a name="remarks"></a>备注

这是一个高级的可重写。

## <a name="coleserverdocdiscardundostate"></a><a name="discardundostate"></a>COleServerDoc：:DiscardUndoState

如果用户执行无法撤消的编辑操作，请调用此函数以强制容器应用程序放弃其撤消状态信息。

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

提供此函数，以便支持撤消的服务器可以释放资源，否则这些资源将被无法使用的撤消状态信息所消耗。

## <a name="coleserverdocgetclientsite"></a><a name="getclientsite"></a>COleServerDoc：获取客户端网站

检索指向基础`IOleClientSite`接口的指针。

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>返回值

检索指向基础[IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)接口的指针。

## <a name="coleserverdocgetdocobjectserver"></a><a name="getdocobjectserver"></a>COleServerDoc：获取Doc对象服务器

重写此函数以创建新`CDocObjectServer`项并返回指向它的指针。

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>参数

*pDocSite*<br/>
指向将此`IOleDocumentSite`文档连接到服务器的接口的指针。

### <a name="return-value"></a>返回值

指向 的`CDocObjectServer`指针 。如果操作失败，则为 NULL。

### <a name="remarks"></a>备注

激活 DocObject 服务器时，返回非 NULL 指针将显示客户端可以支持文档对象。 默认实现返回 NULL。

支持文档文档的典型实现将只分配一个新`CDocObjectServer`对象并将其返回到调用方。 例如：

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

## <a name="coleserverdocgetembeddeditem"></a><a name="getembeddeditem"></a>COleServerDoc：获取嵌入式项目

调用此函数以获取指向表示整个文档的项的指针。

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>返回值

指向表示整个文档的项的指针;如果操作失败，则为 NULL。

### <a name="remarks"></a>备注

它调用[COleServerDoc：onGetEmbeddedItem，](#ongetembeddeditem)一个没有默认实现的虚拟函数。

## <a name="coleserverdocgetitemcliprect"></a><a name="getitemcliprect"></a>COleServerDoc：获取项目剪辑

调用`GetItemClipRect`成员函数，获取正在编辑的项目的裁剪矩形坐标。

```cpp
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>参数

*lpClipRect*<br/>
指向`RECT`结构或对象以`CRect`接收项目的裁剪矩形坐标的指针。

### <a name="remarks"></a>备注

坐标相对于容器应用程序窗口的工作区以像素为单位。

不应在裁剪矩形之外进行绘图。 通常，绘图会自动受到限制。 使用此函数可以确定用户是否已在文档的可见部分之外滚动;因此，如果用户在文档的可见部分之外滚动过滚动。如果是这样，请根据需要通过调用[ScrollContainerBy](#scrollcontainerby)滚动容器文档。

## <a name="coleserverdocgetitemposition"></a><a name="getitemposition"></a>COleServerDoc：获取项目位置

调用`GetItemPosition`成员函数，获取正在编辑的项目的坐标。

```cpp
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>参数

*lpPosRect*<br/>
指向`RECT`结构或对象以`CRect`接收项坐标的指针。

### <a name="remarks"></a>备注

坐标相对于容器应用程序窗口的工作区以像素为单位。

可以将项目的位置与当前裁剪矩形进行比较，以确定项目在屏幕上可见（或不可见）的程度。

## <a name="coleserverdocgetzoomfactor"></a><a name="getzoomfactor"></a>COleServerDoc：获取ZoomFactor

成员`GetZoomFactor`函数确定已激活用于就地编辑的项目的"缩放系数"。

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>参数

*lpSizeNum*<br/>
指向将保存缩放因子分子`CSize`的类对象的指针。 可以为 NULL。

*lpSizeDenom*<br/>
指向将保存缩放因子分`CSize`母的类对象的指针。 可以为 NULL。

*lpPosRect*<br/>
指向描述项新位置的`CRect`类对象的指针。 如果此参数为 NULL，则函数使用项的当前位置。

### <a name="return-value"></a>返回值

如果项目被激活进行就地编辑，并且其缩放系数超过 100%（1：1），则非零;否则 0。

### <a name="remarks"></a>备注

缩放系数（以像素为单位）是项目大小与其当前范围的比例。 如果容器应用程序未设置项的范围，则使用其自然范围（由[COleServerItem：：onGet 范围](../../mfc/reference/coleserveritem-class.md#ongetextent)）确定。

函数将其前两个参数设置到项"缩放因子"的分子和分母。 如果未就位编辑项目，则函数将这些参数设置为默认值 100%（或 1：1），并返回零。 有关详细信息，请参阅技术说明[40、MFC/OLE 就地调整大小和缩放](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。

## <a name="coleserverdocisdocobject"></a><a name="isdocobject"></a>COleServerDoc：isDocObject

确定文档是否为文档对象。

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>返回值

如果文档是文档对象，则为 TRUE;如果文档为文档对象，则为 TRUE。否则 FALSE。

## <a name="coleserverdocisembedded"></a><a name="isembedded"></a>COleServerDoc：是嵌入式的

调用`IsEmbedded`成员函数以确定文档是否表示嵌入在容器中的对象。

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>返回值

如果对象是表示`COleServerDoc`嵌入在容器中的对象的文档，则非零;否则 0。

### <a name="remarks"></a>备注

从文件加载的文档不会嵌入，尽管容器应用程序可能会将其作为链接进行操作。 嵌入在容器文档中的文档被视为嵌入。

## <a name="coleserverdocisinplaceactive"></a><a name="isinplaceactive"></a>COleServerDoc：即处于主动状态

调用`IsInPlaceActive`成员函数以确定项目当前是否处于就地活动状态。

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>返回值

如果`COleServerDoc`对象处于活动状态，则非零;否则 0。

## <a name="coleserverdocnotifychanged"></a><a name="notifychanged"></a>COleServerDoc：通知已更改

调用此函数以通知连接到文档的所有链接项的文档已更改。

```cpp
void NotifyChanged();
```

### <a name="remarks"></a>备注

通常，在用户更改某些全局属性（如服务器文档的尺寸）后调用此函数。 如果 OLE 项链接到具有自动链接的文档，则该项将更新以反映更改。 在使用 Microsoft 基础类库编写的容器应用程序中，调用 的`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数。

> [!NOTE]
> 此函数包含在与 OLE 1 兼容时。 新应用程序应使用[UpdateAllItem](#updateallitems)。

## <a name="coleserverdocnotifyclosed"></a><a name="notifyclosed"></a>COleServerDoc：：通知已关闭

调用此函数以通知容器文档已关闭。

```cpp
void NotifyClosed();
```

### <a name="remarks"></a>备注

当用户从"文件"菜单中选择"关闭"命令时，`NotifyClosed`由`COleServerDoc` [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument)成员函数的实现调用。 在使用 Microsoft 基础类库编写的容器应用程序中，调用 的`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数。

## <a name="coleserverdocnotifyrename"></a><a name="notifyrename"></a>COleServerDoc：通知重新命名

在用户重命名服务器文档后调用此功能。

```cpp
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>参数

*lpsz 新名称*<br/>
指向指定服务器文档新名称的字符串;这通常是完全限定的路径。

### <a name="remarks"></a>备注

当用户从"文件"菜单中选择"保存为"命令时，`NotifyRename`由`COleServerDoc` [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)成员函数的实现调用。 此功能通知 OLE 系统 DLL，后者又通知容器。 在使用 Microsoft 基础类库编写的容器应用程序中，调用 的`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数。

## <a name="coleserverdocnotifysaved"></a><a name="notifysaved"></a>COleServerDoc：通知已保存

在用户保存服务器文档后调用此功能。

```cpp
void NotifySaved();
```

### <a name="remarks"></a>备注

当用户从"文件"菜单中选择"保存"命令时，`NotifySaved`由`COleServerDoc` [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)的实现来调用。 此功能通知 OLE 系统 DLL，后者又通知容器。 在使用 Microsoft 基础类库编写的容器应用程序中，调用 的`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数。

## <a name="coleserverdoconclose"></a><a name="onclose"></a>COleServerDoc：关闭

当容器请求关闭服务器文档时，由框架调用。

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>参数

*dwCloseOption*<br/>
枚举 OLECLOSE 中的值。 此参数可以具有下列值之一：

- OLECLOSE_SAVEIFDIRTY如果文件已被修改，则保存该文件。

- OLECLOSE_NOSAVE文件已关闭而不保存。

- OLECLOSE_PROMPTSAVE如果文件已被修改，系统将提示用户保存该文件。

### <a name="remarks"></a>备注

默认实现调用`CDocument::OnCloseDocument`。

有关详细信息和其他值，请参阅 Windows SDK 中的[OLECLOSE。](/windows/win32/api/oleidl/ne-oleidl-oleclose)

## <a name="coleserverdocondeactivate"></a><a name="ondeactivate"></a>COleServerDoc：打开激活

当用户停用当前处于活动状态的嵌入或链接项时，由框架调用。

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>备注

此函数将容器应用程序的用户界面还原到其原始状态，并销毁为就地激活而创建的任何菜单和其他控件。

此时应无条件释放撤消状态信息。

有关详细信息，请参阅文章["激活](../../mfc/activation-cpp.md)"。

## <a name="coleserverdocondeactivateui"></a><a name="ondeactivateui"></a>COleServerDoc：：打开停用UI

当用户停用就地激活的项目时调用。

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>参数

*不可多做*<br/>
指定是否可以撤消编辑更改。

### <a name="remarks"></a>备注

此函数将容器应用程序的用户界面还原到其原始状态，隐藏为就地激活而创建的任何菜单和其他控件。

框架始终设置*不可执行*的 FALSE。 如果服务器支持撤消，并且有一个可以撤消的操作，请调用基类实现，将*bUndo 设置为*TRUE。

## <a name="coleserverdocondocwindowactivate"></a><a name="ondocwindowactivate"></a>COleServerDoc：：在DocWindow激活

框架调用此函数以激活或停用文档窗口以进行就地编辑。

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>参数

*b 激活*<br/>
指定文档窗口是激活还是停用。

### <a name="remarks"></a>备注

默认实现根据需要删除或添加框架级用户界面元素。 如果要在激活或停用包含项目的文档时执行其他操作，请覆盖此函数。

有关详细信息，请参阅文章["激活](../../mfc/activation-cpp.md)"。

## <a name="coleserverdoconexecolecmd"></a><a name="onexecolecmd"></a>COleServerDoc：：OnExecOleCmd

框架调用此函数以执行指定的命令或显示命令的帮助。

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>参数

*普吉德集团*<br/>
指向标识一组命令的 GUID 的指针。 可以为 NULL 以指示默认命令组。

*nCmdID*<br/>
要执行的命令。 必须位于*pguidCmdGroup*标识的组中。

*nCmdExecOut*<br/>
对象执行命令的方式，从 OLECMDEXECOPT 枚举中执行以下一个或多个值：

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*普瓦拉金*<br/>
指向包含命令的输入参数的 VARIANTARG 的指针。 可以为 NULL。

*普瓦拉格*<br/>
指向 VARIANTARG 的指针，以接收命令中的输出返回值。 可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，返回S_OK;否则，以下错误代码之一：

|“值”|说明|
|-----------|-----------------|
|E_UNEXPECTED|发生意外错误|
|E_FAIL|出现错误|
|E_NOTIMPL|指示 MFC 本身应尝试转换和调度命令|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*是非 NULL，但不指定已识别的命令组|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*未在组*pguidCmdGroup*中识别为有效命令|
|OLECMDERR_DISABLED|*nCmdID*标识的命令已禁用且无法执行|
|OLECMDERR_NOHELP|呼叫者请求*nCmdID*标识的命令的帮助，但没有可用的帮助|
|OLECMDERR_CANCELED|用户取消执行|

### <a name="remarks"></a>备注

`COleCmdUI`可用于启用、更新和设置 DocObject 用户界面命令的其他属性。 初始化命令后，可以使用 执行这些命令`OnExecOleCmd`。

在尝试转换和调度 OLE 文档命令之前，框架调用该函数。 不需要重写此函数来处理标准 OLE 文档命令，但如果要处理自己的自定义命令或处理接受参数或返回结果的命令，则必须为此函数提供覆盖。

大多数命令不采用参数或返回值。 对于大多数命令，调用方可以通过*NULL进行pvarargIn*和*pvarargOut。* 对于预期输入值的命令，调用方可以声明和初始化 VARIANTARG 变量，并将指针传递给*pvarargIn*中的变量。 对于需要单个值的命令，参数可以直接存储在 VARIANTARG 中并传递给函数。 多个参数必须使用受支持的类型之一（如`IDispatch`和 SAFEARRAY）打包到 VARIANTARG 中。

同样，如果命令返回参数，则调用方应声明 VARIANTARG，将其初始化到VT_EMPTY，并在*pvarargOut*中传递其地址。 如果命令返回单个值，则对象可以直接将该值存储在*pvarargOut*中。 必须以某种方式打包多个输出值，以适合 VARIANTARG 的方式。

此函数的基类实现将遍历与命令目标关联的OLE_COMMAND_MAP结构，并尝试将命令调度到相应的处理程序。 基类实现仅适用于不接受参数或返回值的命令。 如果需要处理接受参数或返回值的命令，则必须重写此函数，并自行使用*pvarargIn*和*pvarargOut*参数。

## <a name="coleserverdoconframewindowactivate"></a><a name="onframewindowactivate"></a>COleServerDoc：在框架窗口激活

当容器应用程序的帧窗口被激活或停用时，框架将调用此功能。

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>参数

*b 激活*<br/>
指定是激活还是停用框架窗口。

### <a name="remarks"></a>备注

默认实现将取消帧窗口可能位于的任何帮助模式。 如果要在帧窗口激活或停用时执行特殊处理，则重写此函数。

有关详细信息，请参阅文章["激活](../../mfc/activation-cpp.md)"。

## <a name="coleserverdocongetembeddeditem"></a><a name="ongetembeddeditem"></a>COleServerDoc：：在嵌入式项目上

当容器应用程序调用服务器应用程序创建或编辑嵌入项时，由框架调用。

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>返回值

指向表示整个文档的项的指针;如果操作失败，则为 NULL。

### <a name="remarks"></a>备注

没有默认实现。 必须重写此函数才能返回表示整个文档的项。 此返回值应是`COleServerItem`派生类的对象。

## <a name="coleserverdoconreactivateandundo"></a><a name="onreactivateandundo"></a>COleServerDoc：：重新激活和Undo

当用户选择撤消对已激活、更改并随后停用的项所做的更改时，框架将调用此函数。

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

默认实现除了返回 FALSE 以指示失败外，不执行任何操作。

如果应用程序支持撤消，请覆盖此函数。 通常，您将执行撤消操作，然后通过调用`ActivateInPlace`来激活该项目。 如果容器应用程序是使用 Microsoft 基础类库编写的，则`COleClientItem::ReactivateAndUndo`调用会导致调用此函数。

## <a name="coleserverdoconresizeborder"></a><a name="onresizeborder"></a>COleServerDoc：：在重调整边界

当容器应用程序的框架窗口更改大小时，框架将调用此功能。

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>参数

*lprect边框*<br/>
指向指定边框`RECT`坐标的结构或`CRect`对象。

*lpUI窗口*<br/>
指向拥有当前就地编辑`IOleInPlaceUIWindow`会话的类对象的指针。

*bFrame*<br/>
如果*lpUIWindow*指向容器应用程序的顶层框架窗口，则为 TRUE，如果*lpUIWindow*指向容器应用程序的文档级框架窗口，则为 FALSE。

### <a name="remarks"></a>备注

此函数根据新的窗口大小调整和调整工具栏和其他用户界面元素。

有关详细信息，请参阅 Windows SDK 中的[IOleInPlaceUIWindow。](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow)

这是一个高级的可重写。

## <a name="coleserverdoconsethostnames"></a><a name="onsethostnames"></a>COleServerDoc：：打开主机名

当容器设置或更改本文档的主机名时，由框架调用。

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>参数

*lpszHost*<br/>
指向指定容器应用程序名称的字符串的指针。

*lpszHostObj*<br/>
指向指定文档容器名称的字符串的指针。

### <a name="remarks"></a>备注

默认实现更改引用本文档的所有视图的文档标题。

如果应用程序通过其他机制设置标题，请覆盖此函数。

## <a name="coleserverdoconsetitemrects"></a><a name="onsetitemrects"></a>COleServerDoc：：在设置项目

框架调用此函数将就地编辑帧窗口放置在容器应用程序的帧窗口中。

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>参数

*lpPosRect*<br/>
指向`RECT`指定就地帧窗口`CRect`相对于容器应用程序工作区的位置的结构或对象的指针。

*lpClipRect*<br/>
指向`RECT`指定相对于容器应用程序的工作区`CRect`的就地框架窗口的裁剪矩形的结构或对象的指针。

### <a name="remarks"></a>备注

如有必要，重写此函数以更新视图的缩放系数。

此函数通常是为了响应`RequestPositionChange`调用而调用的，尽管容器可以随时调用该函数，以请求对就地物料进行位置更改。

## <a name="coleserverdoconshowcontrolbars"></a><a name="onshowcontrolbars"></a>COleServerDoc：：在显示控制栏

框架调用此函数以显示或隐藏服务器应用程序的控制栏，这些控制栏与*pFrameWnd*标识的框架窗口相关联。

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>参数

*pFramewnd*<br/>
指向其控制栏应隐藏或显示的帧窗口的指针。

*b显示*<br/>
确定控制条是显示还是隐藏。

### <a name="remarks"></a>备注

默认实现枚举该帧窗口拥有的所有控制栏，并隐藏或显示它们。

## <a name="coleserverdoconshowdocument"></a><a name="onshowdocument"></a>COleServerDoc：在显示文档上

当必须隐藏或`OnShowDocument`显示服务器文档时，框架将调用该函数。

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
指定是显示还是隐藏文档的用户界面。

### <a name="remarks"></a>备注

如果*bShow*为 TRUE，则默认实现将激活服务器应用程序（如有必要）并导致容器应用程序滚动其窗口，以便项可见。 如果*bShow*是 FALSE，则默认实现通过 调用`OnDeactivate`停用项，然后销毁或隐藏为文档创建的所有框架窗口，但第一个窗口除外。 如果没有可见的文档保留，则默认实现将隐藏服务器应用程序。

## <a name="coleserverdoconupdatedocument"></a><a name="onupdatedocument"></a>COleServerDoc：更新文档

在将作为嵌入项的文档保存在复合文档中的文档时，由框架调用。

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>返回值

如果文档已成功更新，则非零;否则 0。

### <a name="remarks"></a>备注

默认实现调用[COleServerDoc：：通知已保存](#notifysaved)和[COleServerDoc：保存嵌入](#saveembedding)成员函数，然后将文档标记为干净。 如果要在更新嵌入项时执行特殊处理，则重写此函数。

## <a name="coleserverdocrequestpositionchange"></a><a name="requestpositionchange"></a>COleServerDoc：：请求位置更改

调用此成员函数，让容器应用程序更改项目的位置。

```cpp
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>参数

*lpPosRect*<br/>
指向包含项`RECT`新位置的结构`CRect`或对象的指针。

### <a name="remarks"></a>备注

当就地活动项中的数据发生更改`UpdateAllItems`时，通常调用（与 ） 结合。 在此调用之后，容器可能通过调用 来执行更改，也可能不`OnSetItemRects`执行更改。 结果位置可能与请求的位置不同。

## <a name="coleserverdocsaveembedding"></a><a name="saveembedding"></a>COleServerDoc：：保存嵌入

调用此函数以告诉容器应用程序保存嵌入的对象。

```cpp
void SaveEmbedding();
```

### <a name="remarks"></a>备注

此函数从`OnUpdateDocument`自动调用 。 请注意，此函数会导致在磁盘上更新项目，因此通常仅由于特定用户操作而调用该项目。

## <a name="coleserverdocscrollcontainerby"></a><a name="scrollcontainerby"></a>COleServerDoc：：滚动容器By

调用`ScrollContainerBy`成员函数按 指示的数量（以像素为单位）`sizeScroll`滚动容器文档。

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>参数

*大小滚动*<br/>
指示容器文档滚动的远。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

正值表示向下和向右滚动;负值表示向上和向左滚动。

## <a name="coleserverdocupdateallitems"></a><a name="updateallitems"></a>COleServerDoc：更新所有项目

调用此函数以通知连接到文档的所有链接项的文档已更改。

```cpp
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>参数

*pSender*<br/>
指针指向修改文档的项，如果要更新所有项目，则指向 NULL。

*lHint*<br/>
包含有关修改的信息。

*pHint*<br/>
指向存储有关修改信息的对象的指针。

*nDrawAspect*<br/>
确定如何绘制项目。 这是 DVASPECT 枚举中的值。 此参数可以具有下列值之一：

- DVASPECT_CONTENT项的表示方式可以将其显示为容器内的嵌入对象。

- DVASPECT_THUMBNAIL项目以"缩略图"表示形式呈现，以便它可以显示在浏览工具中。

- DVASPECT_ICON项由图标表示。

- DVASPECT_DOCPRINT项表示，就好像它是使用"文件"菜单中的"打印"命令一样。

### <a name="remarks"></a>备注

通常在用户更改服务器文档后调用此功能。 如果 OLE 项链接到具有自动链接的文档，则该项将更新以反映更改。 在使用 Microsoft 基础类库编写的容器应用程序中，调用 的`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数。

此函数调用除`OnUpdate`发送项、传递*pHint、lHint*和*nDrawAspect*之外的每个*lHint*文档项的成员函数。 使用这些参数将有关文档修改的信息传递给项。 您可以使用*lHint*对信息进行编码，`CObject`也可以定义派生类以存储有关修改的信息，并使用*pHint*传递该类的对象。 覆盖`COleServerItem`派生`OnUpdate`类中的成员函数，以根据项目的表示是否已更改来优化每个项目的更新。

## <a name="see-also"></a>请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COle链接文档类](../../mfc/reference/colelinkingdoc-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDocument 类](../../mfc/reference/coledocument-class.md)<br/>
[COle链接文档类](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
