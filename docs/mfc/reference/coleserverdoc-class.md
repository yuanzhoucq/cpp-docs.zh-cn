---
title: COleServerDoc 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67920590979c4b9bf3099e8c64c142aeb813b1ce
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851653"
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
|[COleServerDoc::ActivateInPlace](#activateinplace)|激活就地编辑的文档。|  
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|停用服务器的用户界面。|  
|[COleServerDoc::DiscardUndoState](#discardundostate)|放弃撤消状态信息。|  
|[COleServerDoc::GetClientSite](#getclientsite)|检索指向基础`IOleClientSite`接口。|  
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|返回一个指向一个表示整个文档项。|  
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|返回当前的剪辑矩形以进行就地编辑。|  
|[COleServerDoc::GetItemPosition](#getitemposition)|返回当前 position rectangle，相对于容器应用程序的客户端区域，以进行就地编辑。|  
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|返回以像素为单位的缩放系数。|  
|[COleServerDoc::IsDocObject](#isdocobject)|确定文档是否 DocObject。|  
|[COleServerDoc::IsEmbedded](#isembedded)|指示文档是否为容器文档中嵌入的或独立运行。|  
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|如果当前就地激活项，则，返回 TRUE。|  
|[COleServerDoc::NotifyChanged](#notifychanged)|通知用户已更改文档的容器。|  
|[COleServerDoc::NotifyClosed](#notifyclosed)|通知用户已关闭文档容器。|  
|[COleServerDoc::NotifyRename](#notifyrename)|通知用户已重命名该文档的容器。|  
|[COleServerDoc::NotifySaved](#notifysaved)|通知用户已保存文档的容器。|  
|[COleServerDoc::OnDeactivate](#ondeactivate)|当用户将就地激活项，由框架调用。|  
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|由框架调用以销毁控件和创建就地激活的其他用户界面元素。|  
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|激活或停用容器的文档框架窗口时由框架调用。|  
|[COleServerDoc::OnResizeBorder](#onresizeborder)|容器应用程序的框架窗口或文档窗口调整大小时，由框架调用。|  
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|由框架调用以显示或隐藏用于就地编辑的控件条。|  
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|更新项的容器的副本保存为嵌入的项的服务器文档时，由框架调用。|  
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|更改就地编辑框的位置。|  
|[COleServerDoc::SaveEmbedding](#saveembedding)|指示要保存文档的容器应用程序。|  
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|滚动容器文档。|  
|[COleServerDoc::UpdateAllItems](#updateallitems)|通知用户已更改文档的容器。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|由框架调用以创建以进行就地编辑框架窗口。|  
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|由框架调用以销毁就地编辑框架窗口。|  
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|重写此函数可创建一个新`CDocObjectServer`对象，并指示此文档是 DocObject 容器。|  
|[COleServerDoc::OnClose](#onclose)|当容器请求关闭文档时，由框架调用。|  
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|执行指定的命令或显示有关命令的帮助。|  
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|激活或停用容器的框架窗口时由框架调用。|  
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|调用以获取`COleServerItem`，表示整个文档; 用于获取嵌入的项。 所需的实现。|  
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|由框架调用以撤消的就地编辑期间所做的更改。|  
|[COleServerDoc::OnSetHostNames](#onsethostnames)|当容器设置为嵌入对象的窗口标题时由框架调用。|  
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|由框架调用以在容器应用程序的窗口内定位就地编辑框架窗口。|  
|[COleServerDoc::OnShowDocument](#onshowdocument)|由框架调用以显示或隐藏文档。|  
  
## <a name="remarks"></a>备注  
 服务器文档可以包含[COleServerItem](../../mfc/reference/coleserveritem-class.md) ，这些对象表示对嵌入或链接项的服务器界面。 通过编辑嵌入的项的容器启动服务器应用程序时，作为其自己的服务器文档; 加载项`COleServerDoc`对象包含一个`COleServerItem`包括对整个文档的对象。 通过编辑链接的项的容器启动服务器应用程序时，从磁盘; 加载现有文档突出显示文档的内容的一部分，指示链接的项。  
  
 `COleServerDoc` 对象还可以包含的项[COleClientItem](../../mfc/reference/coleclientitem-class.md)类。 这样即可创建容器-服务器应用程序。 该框架提供了函数能正确地存储`COleClientItem`项，但服务`COleServerItem`对象。  
  
 如果服务器应用程序不支持链接，服务器文档将始终包含只有一个服务器项目，它表示为文档的整个嵌入的对象。 如果服务器应用程序不支持链接，它必须创建的服务器项每次选择复制到剪贴板。  
  
 若要使用`COleServerDoc`、 从其派生一个类并实现[OnGetEmbeddedItem](#ongetembeddeditem)成员函数，允许你的服务器以支持嵌入的项。 从派生类`COleServerItem`实现在文档中的项并返回从该类的对象`OnGetEmbeddedItem`。  
  
 若要支持链接的项`COleServerDoc`提供了[OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem)成员函数。 可以使用的默认实现，或如果你有自己的方式管理文档项的重写它。  
  
 需要一个`COleServerDoc`-对于每种类型的服务器记录您的应用程序支持派生类。 例如，如果服务器应用程序支持的工作表和图表，必须有两个`COleServerDoc`-派生的类。  
  
 服务器上的详细信息，请参阅文章[服务器： 实现服务器](../../mfc/servers-implementing-a-server.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 `COleServerDoc`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="activatedocobject"></a>  COleServerDoc::ActivateDocObject  
 激活关联的 DocObject 文档。  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>备注  
 默认情况下，`COleServerDoc`不支持活动文档 （也称为 DocObjects）。 若要启用此支持，请参阅[GetDocObjectServer](#getdocobjectserver)和类[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)。  
  
##  <a name="activateinplace"></a>  COleServerDoc::ActivateInPlace  
 激活就地编辑的项。  
  
```  
BOOL ActivateInPlace();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0，指示该项目已完全打开。  
  
### <a name="remarks"></a>备注  
 此函数执行就地激活所需的所有操作。 它创建就地框架窗口、 激活它和大小的项、 设置共享的菜单和其他控件、 将项滚动到视图，并将焦点设置到的就地框架窗口。  
  
 默认实现调用此函数[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。 如果你的应用程序支持就地激活 （如播放） 另一个谓词，则调用此函数。  
  
##  <a name="coleserverdoc"></a>  COleServerDoc::COleServerDoc  
 构造`COleServerDoc`对象而无需连接使用 OLE 系统 Dll。  
  
```  
COleServerDoc();
```  
  
### <a name="remarks"></a>备注  
 必须调用[COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) ole 打开通信。 如果使用的[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)在应用程序中`COleLinkingDoc::Register`为您通过调用`COleLinkingDoc`的实现`OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。  
  
##  <a name="createinplaceframe"></a>  COleServerDoc::CreateInPlaceFrame  
 框架调用此函数可创建以进行就地编辑框架窗口。  
  
```  
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>参数  
 *pParentWnd*  
 向容器应用程序的父窗口的指针。  
  
### <a name="return-value"></a>返回值  
 就地框架窗口中或如果不成功则为 NULL 的指针。  
  
### <a name="remarks"></a>备注  
 默认实现使用文档模板中指定的信息创建框架。 使用的视图是为文档创建的第一个视图。 此视图是暂时从原始帧中分离和附加到新创建的框架。  
  
 这是一种高级可重写。  
  
##  <a name="deactivateandundo"></a>  COleServerDoc::DeactivateAndUndo  
 如果您的应用程序支持撤消，并且用户选择撤消激活项后但在编辑之前，调用此函数。  
  
```  
BOOL DeactivateAndUndo();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序使用 Microsoft 基础类库编写的调用此函数会导致[COleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo)调用，这将停用服务器的用户界面。  
  
##  <a name="destroyinplaceframe"></a>  COleServerDoc::DestroyInPlaceFrame  
 框架调用此函数以销毁就地框架窗口，并将该服务器应用程序的文档窗口返回到之前的就地激活的状态。  
  
```  
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>参数  
 *pFrameWnd*  
 指向要销毁的就地框架窗口的指针。  
  
### <a name="remarks"></a>备注  
 这是一种高级可重写。  
  
##  <a name="discardundostate"></a>  COleServerDoc::DiscardUndoState  
 如果用户执行编辑操作无法被撤消，调用此函数可强制容器应用程序，可以放弃其撤消状态信息。  
  
```  
BOOL DiscardUndoState();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 提供此函数，以便支持撤消服务器可以释放资源，否则将由不能使用的撤消状态信息。  
  
##  <a name="getclientsite"></a>  COleServerDoc::GetClientSite  
 检索指向基础`IOleClientSite`接口。  
  
```  
LPOLECLIENTSITE GetClientSite() const;  
```  
  
### <a name="return-value"></a>返回值  
 检索对基础指针[IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706)接口。  
  
##  <a name="getdocobjectserver"></a>  COleServerDoc::GetDocObjectServer  
 重写此函数可创建一个新`CDocObjectServer`项，然后返回一个指向。  
  
```  
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```  
  
### <a name="parameters"></a>参数  
 *pDocSite*  
 指向`IOleDocumentSite`将连接到服务器的本文档的接口。  
  
### <a name="return-value"></a>返回值  
 一个指向`CDocObjectServer`;如果操作失败，则为 NULL。  
  
### <a name="remarks"></a>备注  
 激活 DocObject 服务器时，返回非 NULL 指针显示的客户端可以支持 DocObjects。 默认实现返回 NULL。  
  
 支持 DocObjects 的文档的典型实现只需将分配一个新`CDocObjectServer`对象，并将其返回给调用方。 例如：  
  
 [!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]  
  
##  <a name="getembeddeditem"></a>  COleServerDoc::GetEmbeddedItem  
 调用此函数可获得到一个表示整个文档项的指针。  
  
```  
COleServerItem* GetEmbeddedItem();
```  
  
### <a name="return-value"></a>返回值  
 一个表示整个文档; 项指向的指针如果操作失败，则为 NULL。  
  
### <a name="remarks"></a>备注  
 它将调用[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)，没有默认实现的虚拟函数。  
  
##  <a name="getitemcliprect"></a>  COleServerDoc::GetItemClipRect  
 调用`GetItemClipRect`成员函数以在位置获取正在编辑的项的剪辑矩形坐标。  
  
```  
void GetItemClipRect(LPRECT lpClipRect) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpClipRect*  
 指向`RECT`结构或`CRect`对象以接收项的剪辑矩形坐标。  
  
### <a name="remarks"></a>备注  
 坐标是相对于容器应用程序窗口的工作区以像素为单位。  
  
 剪辑矩形外，不应发生绘图。 通常情况下，绘制是自动限制。 使用此函数可确定用户是否已经滚动外部文档; 的可见部分如果是这样，滚动容器文档，根据需要通过调用[ScrollContainerBy](#scrollcontainerby)。  
  
##  <a name="getitemposition"></a>  COleServerDoc::GetItemPosition  
 调用`GetItemPosition`成员函数以获取正在就地编辑的项的坐标。  
  
```  
void GetItemPosition(LPRECT lpPosRect) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpPosRect*  
 指向`RECT`结构或`CRect`对象以接收项的坐标。  
  
### <a name="remarks"></a>备注  
 坐标是相对于容器应用程序窗口的工作区以像素为单位。  
  
 可以与当前的剪辑矩形，以确定该项可见 （或不可见） 的范围进行比较项的位置在屏幕上。  
  
##  <a name="getzoomfactor"></a>  COleServerDoc::GetZoomFactor  
 `GetZoomFactor`成员函数将确定已激活以进行就地编辑项"缩放系数"。  
  
```  
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,  
    LPSIZE lpSizeDenom = NULL,  
    LPCRECT lpPosRect = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpSizeNum*  
 指向类的对象指针`CSize`，将存放缩放系数的分子。 可以为 NULL。  
  
 *lpSizeDenom*  
 指向类的对象指针`CSize`，将存放缩放系数的分母。 可以为 NULL。  
  
 *lpPosRect*  
 指向类的对象指针`CRect`，描述项的新位置。 如果此参数为 NULL，则函数将使用项的当前位置。  
  
### <a name="return-value"></a>返回值  
 非零，如果为就地激活项编辑和其缩放系数不是 100%(1:1);否则为 0。  
  
### <a name="remarks"></a>备注  
 缩放系数，以像素为单位，为其当前范围内的项的大小的比例。 如果容器应用程序没有设置项的范围内，其原始大小 (由[COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) 使用。  
  
 该函数将其前两个参数设置为分子和分母的项的"缩放系数。" 如果未正在就地编辑项，该函数将这些参数设置为默认值为 100%（或 1:1），并将返回零。 有关详细信息，请参阅技术注意 40 [MFC/OLE 就地调整大小和缩放](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。  
  
##  <a name="isdocobject"></a>  COleServerDoc::IsDocObject  
 确定文档是否 DocObject。  
  
```  
BOOL IsDocObject() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果文档是 DocObject; 则为 TRUE否则为 FALSE。  
  
##  <a name="isembedded"></a>  COleServerDoc::IsEmbedded  
 调用`IsEmbedded`成员函数来确定文档是否表示嵌入在容器中的对象。  
  
```  
BOOL IsEmbedded() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零`COleServerDoc`对象是表示的对象的文档嵌入在容器中; 否则为 0。  
  
### <a name="remarks"></a>备注  
 尽管它可能由容器应用程序作为链接操作，不被嵌入从文件加载的文档。 容器文档中嵌入的文档被视为嵌入。  
  
##  <a name="isinplaceactive"></a>  COleServerDoc::IsInPlaceActive  
 调用`IsInPlaceActive`成员函数以确定该项当前是否处于就地活动状态。  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零`COleServerDoc`对象是就地活动状态; 否则为 0。  
  
##  <a name="notifychanged"></a>  COleServerDoc::NotifyChanged  
 调用此函数来通知所有链接的项目连接到的文档的文档已更改。  
  
```  
void NotifyChanged();
```  
  
### <a name="remarks"></a>备注  
 通常情况下，用户更改一些全局属性，例如服务器文档的维度之后调用此函数。 如果 OLE 项与自动链接到文档链接，更新项目以反映所做的更改。 在容器应用程序中使用 Microsoft 基础类库编写[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数的`COleClientItem`调用。  
  
> [!NOTE]
>  此函数是为了与 OLE 1 的兼容性。 新的应用程序应使用[UpdateAllItems](#updateallitems)。  
  
##  <a name="notifyclosed"></a>  COleServerDoc::NotifyClosed  
 调用此函数，以通知容器文档已关闭。  
  
```  
void NotifyClosed();
```  
  
### <a name="remarks"></a>备注  
 当用户从文件菜单中，选择关闭命令`NotifyClosed`由调用`COleServerDoc`的实现[OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument)成员函数。 在容器应用程序中使用 Microsoft 基础类库编写[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数的`COleClientItem`调用。  
  
##  <a name="notifyrename"></a>  COleServerDoc::NotifyRename  
 调用此函数后用户重命名服务器文档。  
  
```  
void NotifyRename(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>参数  
 *lpszNewName*  
 指定服务器文档; 的新名称的字符串指针这通常是完全限定的路径。  
  
### <a name="remarks"></a>备注  
 当用户从文件菜单中，选择另存为命令`NotifyRename`由调用`COleServerDoc`的实现[OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)成员函数。 此函数会通知 OLE 系统 Dll，又通知容器。 在容器应用程序中使用 Microsoft 基础类库编写[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数的`COleClientItem`调用。  
  
##  <a name="notifysaved"></a>  COleServerDoc::NotifySaved  
 调用此函数后在用户保存服务器文档。  
  
```  
void NotifySaved();
```  
  
### <a name="remarks"></a>备注  
 当用户从文件菜单中，选择保存命令`NotifySaved`为您通过调用`COleServerDoc`的实现[OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)。 此函数会通知 OLE 系统 Dll，又通知容器。 在容器应用程序中使用 Microsoft 基础类库编写[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数的`COleClientItem`调用。  
  
##  <a name="onclose"></a>  COleServerDoc::OnClose  
 当容器请求关闭服务器文档时，由框架调用。  
  
```  
virtual void OnClose(OLECLOSE dwCloseOption);
```  
  
### <a name="parameters"></a>参数  
 *dwCloseOption*  
 枚举 OLECLOSE 中的值。 此参数可以具有下列值之一：  
  
- OLECLOSE_SAVEIFDIRTY 文件将保存，如果已修改。  
  
- OLECLOSE_NOSAVE 文件关闭而不保存。  
  
- OLECLOSE_PROMPTSAVE 如果文件已被修改，则会提示用户有关保存它。  
  
### <a name="remarks"></a>备注  
 默认实现将调用`CDocument::OnCloseDocument`。  
  
 有关详细信息和其他值，请参阅[OLECLOSE](http://msdn.microsoft.com/library/windows/desktop/ms680623) Windows SDK 中。  
  
##  <a name="ondeactivate"></a>  COleServerDoc::OnDeactivate  
 当用户将是当前处于就地活动状态的嵌入或链接项，由框架调用。  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>备注  
 此函数将容器应用程序的用户界面还原到其原始状态，并销毁任何菜单和其他控件创建就地激活。  
  
 撤消状态信息应无条件地释放此位置。  
  
 有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)...  
  
##  <a name="ondeactivateui"></a>  COleServerDoc::OnDeactivateUI  
 当用户将就地激活项时调用。  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>参数  
 *bUndoable*  
 指定是否可撤消的编辑更改。  
  
### <a name="remarks"></a>备注  
 此函数将还原到其原始状态，隐藏任何菜单和创建就地激活其他控件的容器应用程序的用户界面。  
  
 框架将始终设置*bUndoable*为 FALSE。 如果服务器支持撤消，并且没有可撤消的操作，则调用与基类实现*bUndoable*设置为 TRUE。  
  
##  <a name="ondocwindowactivate"></a>  COleServerDoc::OnDocWindowActivate  
 框架调用此函数可激活或停用一个文档窗口，以就地编辑。  
  
```  
virtual void OnDocWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>参数  
 *bActivate*  
 指定是否要激活或停用文档窗口。  
  
### <a name="remarks"></a>备注  
 默认实现中删除，或根据需要添加框架级别的用户界面元素。 如果你想要激活或停用文档，其中包含你的项时执行其他操作，重写此函数。  
  
 有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)...  
  
##  <a name="onexecolecmd"></a>  COleServerDoc::OnExecOleCmd  
 框架调用此函数可执行指定的命令或显示有关命令的帮助。  
  
```  
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,  
    DWORD nCmdID,  
    DWORD nCmdExecOpt,  
    VARIANTARG* pvarargIn,  
    VARIANTARG* pvarargOut);
```  
  
### <a name="parameters"></a>参数  
 *pguidCmdGroup*  
 指向标识一系列命令的 GUID 的指针。 可以为 NULL 以指示默认命令组。  
  
 *nCmdID*  
 要执行的命令。 必须在由标识的组*pguidCmdGroup*。  
  
 *nCmdExecOut*  
 该对象的方法应从 OLECMDEXECOPT 枚举执行命令、 一个或多个以下值：  
  
 OLECMDEXECOPT_DODEFAULT  
  
 OLECMDEXECOPT_PROMPTUSER  
  
 OLECMDEXECOPT_DONTPROMPTUSER  
  
 OLECMDEXECOPT_SHOWHELP  
  
 *pvarargIn*  
 指向包含命令的输入的参数 VARIANTARG 指针。 可以为 NULL。  
  
 *pvarargOut*  
 指向用于接收输出 VARIANTARG 从该命令返回值。 可以为 NULL。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK 返回否则为台以下的错误代码：  
  
|“值”|描述|  
|-----------|-----------------|  
|E_UNEXPECTED|出现意外的错误|  
|E_FAIL|出现错误|  
|E_NOTIMPL|指示 MFC 本身应尝试转换并将其分派命令|  
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*非 null 值，但未指定已识别的命令组|  
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*未被识别为组中的有效命令*pguidCmdGroup*|  
|OLECMDERR_DISABLED|该命令由标识*nCmdID*被禁用，并且不能执行|  
|OLECMDERR_NOHELP|由标识命令的帮助请求调用方*nCmdID*但没有帮助可用|  
|OLECMDERR_CANCELED|用户已取消执行|  
  
### <a name="remarks"></a>备注  
 `COleCmdUI` 可用于启用、 更新和设置其他属性 DocObject 用户界面命令。 初始化命令之后，您可以执行这些与`OnExecOleCmd`。  
  
 框架尝试转换并将其分派 OLE 文档命令之前调用该函数。 无需重写此函数来处理标准 OLE 文档命令，但如果你想要处理自己的自定义命令或处理命令接受参数或返回的结果，则必须提供此函数的重写。  
  
 大多数命令执行不带参数或返回值。 调用方可以 null 值传入大部分命令*pvarargIn*并*pvarargOut*。 对于预期输入的值的命令，调用方可以声明和初始化 VARIANTARG 变量并将指针传递到该变量*pvarargIn*。 对于需要单个值的命令，可以直接存储在 VARIANTARG 并传递给函数的参数。 必须在使用受支持的类型之一 VARIANTARG 打包多个自变量 (如`IDispatch`和 SAFEARRAY)。  
  
 同样，如果命令返回调用方应声明 VARIANTARG 参数，将其初始化为 VT_EMPTY，并将在其地址传递*pvarargOut*。 如果命令返回单个值，该对象可以将该值直接在存储*pvarargOut*。 必须以某种方式适用于 VARIANTARG 打包多个输出值。  
  
 此函数的基类实现将遍历与命令目标相关联的 OLE_COMMAND_MAP 结构，并尝试调度到相应的处理程序的命令。 基类实现仅适用于命令不接受参数或返回值。 如果您需要处理命令接受参数或返回值，必须重写此函数并处理*pvarargIn*并*pvarargOut*参数自己。  
  
##  <a name="onframewindowactivate"></a>  COleServerDoc::OnFrameWindowActivate  
 激活或停用容器应用程序的框架窗口时，框架将调用此函数。  
  
```  
virtual void OnFrameWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>参数  
 *bActivate*  
 指定是否要激活或停用的框架窗口。  
  
### <a name="remarks"></a>备注  
 默认实现取消框架窗口可能在任何帮助模式。 如果你想要执行特殊处理激活或停用的框架窗口时，重写此函数。  
  
 有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)...  
  
##  <a name="ongetembeddeditem"></a>  COleServerDoc::OnGetEmbeddedItem  
 当容器应用程序调用要创建或编辑嵌入的项的服务器应用程序时由框架调用。  
  
```  
virtual COleServerItem* OnGetEmbeddedItem() = 0;  
```  
  
### <a name="return-value"></a>返回值  
 一个表示整个文档; 项指向的指针如果操作失败，则为 NULL。  
  
### <a name="remarks"></a>备注  
 没有默认实现。 必须重写此函数可返回一个表示整个文档项。 此返回值应为的对象`COleServerItem`-派生的类。  
  
##  <a name="onreactivateandundo"></a>  COleServerDoc::OnReactivateAndUndo  
 当用户选择撤消对已就地激活，更改，并且随后停用的项目所做的更改时，框架将调用此函数。  
  
```  
virtual BOOL OnReactivateAndUndo();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现没有任何影响只返回 FALSE 来指示失败。  
  
 如果你的应用程序支持撤消重写此函数。 通常您需要执行撤消操作，然后通过调用激活项`ActivateInPlace`。 如果容器应用程序使用 Microsoft 基础类库编写的则调用`COleClientItem::ReactivateAndUndo`会导致将调用此函数。  
  
##  <a name="onresizeborder"></a>  COleServerDoc::OnResizeBorder  
 当容器应用程序的框架窗口大小更改时，框架将调用此函数。  
  
```  
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,  
    LPOLEINPLACEUIWINDOW lpUIWindow,  
    BOOL bFrame);
```  
  
### <a name="parameters"></a>参数  
 *lpRectBorder*  
 指向`RECT`结构或`CRect`对象，它指定边框的坐标。  
  
 *lpUIWindow*  
 指向类的对象指针`IOleInPlaceUIWindow`拥有当前的就地编辑会话。  
  
 *bFrame*  
 则为 TRUE *lpUIWindow*指向容器应用程序的顶级框架窗口中或 false *lpUIWindow*指向容器应用程序的文档级框架窗口。  
  
### <a name="remarks"></a>备注  
 此函数调整大小，并调整工具栏和其他用户界面元素根据新的窗口大小。  
  
 有关详细信息，请参阅[IOleInPlaceUIWindow](http://msdn.microsoft.com/library/windows/desktop/ms680716) Windows SDK 中。  
  
 这是一种高级可重写。  
  
##  <a name="onsethostnames"></a>  COleServerDoc::OnSetHostNames  
 当容器设置或更改本文档的主机名时由框架调用。  
  
```  
virtual void OnSetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>参数  
 *lpszHost*  
 指定的容器应用程序名称的字符串指针。  
  
 *lpszHostObj*  
 指定文档的容器的名称的字符串指针。  
  
### <a name="remarks"></a>备注  
 默认实现更改本文档引用的所有视图的文档标题。  
  
 如果你的应用程序通过不同机制设置标题，重写此函数。  
  
##  <a name="onsetitemrects"></a>  COleServerDoc::OnSetItemRects  
 框架调用此函数可在容器应用程序的框架窗口内定位就地编辑框架窗口。  
  
```  
virtual void OnSetItemRects(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>参数  
 *lpPosRect*  
 指向`RECT`结构或`CRect`对象，它指定相对于容器应用程序的客户端区域的就地框架窗口的位置。  
  
 *lpClipRect*  
 指向`RECT`结构或`CRect`对象，它指定相对于容器应用程序的客户端区域的就地框架窗口的剪辑矩形。  
  
### <a name="remarks"></a>备注  
 如有必要，重写此函数可更新视图的缩放系数。  
  
 此函数通常调用以响应`RequestPositionChange`调用，虽然它可以调用在任何时间由容器请求的就地项的位置更改。  
  
##  <a name="onshowcontrolbars"></a>  COleServerDoc::OnShowControlBars  
 框架调用此函数可显示或隐藏与框架窗口由标识相关联的服务器应用程序的控件条*pFrameWnd*。  
  
```  
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 *pFrameWnd*  
 到框架窗口应显示或隐藏其控件条的指针。  
  
 *bShow*  
 确定是否显示或隐藏控件条。  
  
### <a name="remarks"></a>备注  
 默认实现枚举该框架窗口所拥有的所有控件条和隐藏或显示它们。  
  
##  <a name="onshowdocument"></a>  COleServerDoc::OnShowDocument  
 框架将调用`OnShowDocument`函数时必须显示或隐藏服务器文档。  
  
```  
virtual void OnShowDocument(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 *bShow*  
 指定是否对文档的用户界面是显示还是隐藏。  
  
### <a name="remarks"></a>备注  
 如果*bShow*为 TRUE 时，激活服务器应用程序，如有必要的默认实现，并会导致要滚动其窗口，以便使该项是可见的容器应用程序。 如果*bShow*为 FALSE 时，默认实现将停用的项通过调用`OnDeactivate`、 销毁或隐藏文档中，除第一个已创建的所有框架窗口。 如果没有可见的文档保持的默认实现将隐藏服务器应用程序。  
  
##  <a name="onupdatedocument"></a>  COleServerDoc::OnUpdateDocument  
 当保存的文档是嵌入复合文档项时由框架调用。  
  
```  
virtual BOOL OnUpdateDocument();
```  
  
### <a name="return-value"></a>返回值  
 已成功更新文档; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现调用[COleServerDoc::NotifySaved](#notifysaved)并[COleServerDoc::SaveEmbedding](#saveembedding)成员函数，然后将标记为干净的文档。 如果你想要执行的特殊处理更新嵌入的项时，重写此函数。  
  
##  <a name="requestpositionchange"></a>  COleServerDoc::RequestPositionChange  
 调用此成员函数可更改项的位置的容器应用程序。  
  
```  
void RequestPositionChange(LPCRECT lpPosRect);
```  
  
### <a name="parameters"></a>参数  
 *lpPosRect*  
 指向`RECT`结构或`CRect`对象，其中包含项的新位置。  
  
### <a name="remarks"></a>备注  
 此函数通常称为 (结合`UpdateAllItems`) 中的就地活动项的数据已更改时。 此调用，容器可能会或可能通过调用执行更改`OnSetItemRects`。 结果的位置可能不同于所请求。  
  
##  <a name="saveembedding"></a>  COleServerDoc::SaveEmbedding  
 调用此函数可告知容器应用程序保存嵌入的对象。  
  
```  
void SaveEmbedding();
```  
  
### <a name="remarks"></a>备注  
 从自动调用此函数`OnUpdateDocument`。 请注意，此函数会导致要更新在磁盘上，因此它通常称为仅由于特定的用户操作的项。  
  
##  <a name="scrollcontainerby"></a>  COleServerDoc::ScrollContainerBy  
 调用`ScrollContainerBy`成员函数可滚动容器文档的数量，以像素为单位，由`sizeScroll`。  
  
```  
BOOL ScrollContainerBy(CSize sizeScroll);
```  
  
### <a name="parameters"></a>参数  
 *sizeScroll*  
 指示延伸的范围容器文档是滚动。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 正值指示向下和向右; 滚动负值表示向上和向左滚动。  
  
##  <a name="updateallitems"></a>  COleServerDoc::UpdateAllItems  
 调用此函数来通知所有链接的项目连接到的文档的文档已更改。  
  
```  
void UpdateAllItems(
    COleServerItem* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>参数  
 *pSender*  
 指向的项的修改文档，则所有项都是要更新为 null。  
  
 *lHint*  
 包含有关修改信息。  
  
 *pHint*  
 指针指向的对象存储有关修改信息。  
  
 *nDrawAspect*  
 确定如何对项目进行绘制。 这是来自 DVASPECT 枚举的值。 此参数可以具有下列值之一：  
  
- DVASPECT_CONTENT 项可以显示为其容器内的嵌入对象的方式表示。  
  
- DVASPECT_THUMBNAIL 项将呈现在"缩略图"表示形式，以便它可以显示在浏览工具。  
  
- DVASPECT_ICON 项由一个图标表示。  
  
- DVASPECT_DOCPRINT 项表现为似乎打印出的使用文件菜单中的打印命令。  
  
### <a name="remarks"></a>备注  
 用户更改服务器文档之后，通常会调用此函数。 如果 OLE 项与自动链接到文档链接，更新项目以反映所做的更改。 在容器应用程序中使用 Microsoft 基础类库编写[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成员函数的`COleClientItem`调用。  
  
 此函数将调用`OnUpdate`成员函数为每个文档的项，但发送的项，传递*pHint*， *lHint*，并且*nDrawAspect*。 使用这些参数将信息传递给有关对文档进行修改的项。 您可以使用信息进行编码*lHint*也可以定义`CObject`的派生类来存储有关所做的修改的信息并传递一个对象的类使用*pHint*。 重写`OnUpdate`成员函数在你`COleServerItem`的派生类，以优化具体取决于是否已更改其表示每个项的更新。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [COleLinkingDoc 类](../../mfc/reference/colelinkingdoc-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [COleDocument 类](../../mfc/reference/coledocument-class.md)   
 [COleLinkingDoc 类](../../mfc/reference/colelinkingdoc-class.md)   
 [COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
