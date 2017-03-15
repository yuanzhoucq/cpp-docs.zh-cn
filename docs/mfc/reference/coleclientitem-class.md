---
title: "COleClientItem 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleClientItem
dev_langs:
- C++
helpviewer_keywords:
- OLE containers, client items
- COleClientItem class
- OLE client item class
- container interface class
- OLE containers, interface class
- client items and OLE containers
ms.assetid: 7f571b7c-2758-4839-847a-0cf1ef643128
caps.latest.revision: 24
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
ms.openlocfilehash: a200da03305c20eaf2d9c1de1ea585c82410c570
ms.lasthandoff: 02/24/2017

---
# <a name="coleclientitem-class"></a>COleClientItem 类
定义 OLE 项的容器接口。  
  
## <a name="syntax"></a>语法  
  
```  
class COleClientItem : public CDocItem  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleClientItem::COleClientItem](#coleclientitem)|构造 `COleClientItem` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleClientItem::Activate](#activate)|打开操作的 OLE 项目，然后执行指定的谓词。|  
|[COleClientItem::ActivateAs](#activateas)|将项激活为另一种类型。|  
|[COleClientItem::AttachDataObject](#attachdataobject)|访问 OLE 对象中的数据。|  
|[COleClientItem::CanCreateFromData](#cancreatefromdata)|指示容器应用程序是否可以创建嵌入的对象。|  
|[COleClientItem::CanCreateLinkFromData](#cancreatelinkfromdata)|指示容器应用程序是否可以创建链接的对象。|  
|[COleClientItem::CanPaste](#canpaste)|指示剪贴板中是否包含可嵌入或静态 OLE 项。|  
|[COleClientItem::CanPasteLink](#canpastelink)|指示剪贴板中是否包含可链接的 OLE 项。|  
|[COleClientItem::Close](#close)|关闭到服务器的链接，但不会销毁 OLE 项。|  
|[COleClientItem::ConvertTo](#convertto)|将项转换为另一种类型。|  
|[COleClientItem::CopyToClipboard](#copytoclipboard)|将 OLE 项复制到剪贴板。|  
|[COleClientItem::CreateCloneFrom](#createclonefrom)|创建现有项的副本。|  
|[COleClientItem::CreateFromClipboard](#createfromclipboard)|从剪贴板中创建嵌入的项。|  
|[COleClientItem::CreateFromData](#createfromdata)|从数据对象创建嵌入的项。|  
|[COleClientItem::CreateFromFile](#createfromfile)|通过文件创建嵌入的项。|  
|[COleClientItem::CreateLinkFromClipboard](#createlinkfromclipboard)|从剪贴板中创建链接的项。|  
|[COleClientItem::CreateLinkFromData](#createlinkfromdata)|从数据对象创建链接的项。|  
|[COleClientItem::CreateLinkFromFile](#createlinkfromfile)|通过文件创建链接的项。|  
|[COleClientItem::CreateNewItem](#createnewitem)|通过启动服务器应用程序创建一个新的嵌入的项。|  
|[COleClientItem::CreateStaticFromClipboard](#createstaticfromclipboard)|将剪贴板中创建一个静态项。|  
|[COleClientItem::CreateStaticFromData](#createstaticfromdata)|数据对象创建一个静态项。|  
|[COleClientItem::Deactivate](#deactivate)|停用该项目。|  
|[COleClientItem::DeactivateUI](#deactivateui)|将容器应用程序的用户界面还原到其原始状态。|  
|[COleClientItem::Delete](#delete)|删除或关闭 OLE 项，如果它是链接的项。|  
|[COleClientItem::DoDragDrop](#dodragdrop)|执行拖放操作。|  
|[COleClientItem::DoVerb](#doverb)|执行指定的谓词。|  
|[COleClientItem::Draw](#draw)|绘制 OLE 项。|  
|[COleClientItem::GetActiveView](#getactiveview)|获取在其就地激活项的视图。|  
|[COleClientItem::GetCachedExtent](#getcachedextent)|返回 OLE 项的矩形的边界。|  
|[COleClientItem::GetClassID](#getclassid)|获取当前项的类 id。|  
|[COleClientItem::GetClipboardData](#getclipboarddata)|获取通过调用将被放到剪贴板的数据`CopyToClipboard`成员函数。|  
|[COleClientItem::GetDocument](#getdocument)|返回`COleDocument`对象，其中包含存在的项。|  
|[COleClientItem::GetDrawAspect](#getdrawaspect)|获取项的当前视图的呈现。|  
|[COleClientItem::GetExtent](#getextent)|返回 OLE 项的矩形的边界。|  
|[COleClientItem::GetIconFromRegistry](#geticonfromregistry)|检索与特定的 CLSID 的服务器相关联的图标的句柄。|  
|[COleClientItem::GetIconicMetafile](#geticonicmetafile)|获取用于绘制项的图标的图元文件。|  
|[COleClientItem::GetInPlaceWindow](#getinplacewindow)|返回指向就地编辑窗口中的项的指针。|  
|[COleClientItem::GetItemState](#getitemstate)|获取项的当前状态。|  
|[COleClientItem::GetLastStatus](#getlaststatus)|返回最后一次 OLE 操作的状态。|  
|[COleClientItem::GetLinkUpdateOptions](#getlinkupdateoptions)|返回链接的项 （高级功能） 的更新模式。|  
|[COleClientItem::GetType](#gettype)|返回 OLE 项的类型 （嵌入、 链接或静态）。|  
|[COleClientItem::GetUserType](#getusertype)|获取一个描述项的类型的字符串。|  
|[COleClientItem::IsInPlaceActive](#isinplaceactive)|返回`TRUE`该项是否处于就地活动状态。|  
|[COleClientItem::IsLinkUpToDate](#islinkuptodate)|返回**TRUE**链接的项是否包含其源文档的最新更新。|  
|[COleClientItem::IsModified](#ismodified)|返回`TRUE`如果自上次保存后修改了该项。|  
|[COleClientItem::IsOpen](#isopen)|返回`TRUE`如果项是当前在服务器应用程序中打开。|  
|[COleClientItem::IsRunning](#isrunning)|返回`TRUE`如果项的服务器应用程序正在运行。|  
|[COleClientItem::OnActivate](#onactivate)|由框架，以向项通知激活它调用。|  
|[COleClientItem::OnActivateUI](#onactivateui)|由框架来通知该项目，它被激活，并应显示其用户界面调用。|  
|[COleClientItem::OnChange](#onchange)|服务器更改 OLE 项时调用。 所需的实现。|  
|[COleClientItem::OnDeactivate](#ondeactivate)|停用某项时，由框架调用。|  
|[COleClientItem::OnDeactivateUI](#ondeactivateui)|当服务器已删除其就地用户界面时由框架调用。|  
|[COleClientItem::OnGetClipboardData](#ongetclipboarddata)|由框架，以获取要复制到剪贴板的数据调用。|  
|[COleClientItem::OnInsertMenus](#oninsertmenus)|由框架来创建复合菜单调用。|  
|[COleClientItem::OnRemoveMenus](#onremovemenus)|由框架从复合菜单中删除该容器的菜单调用。|  
|[COleClientItem::OnSetMenu](#onsetmenu)|由框架来安装和删除复合菜单调用。|  
|[COleClientItem::OnShowControlBars](#onshowcontrolbars)|由框架来显示和隐藏控件条调用。|  
|[COleClientItem::OnUpdateFrameTitle](#onupdateframetitle)|由框架更新框架窗口的标题栏调用。|  
|[COleClientItem::ReactivateAndUndo](#reactivateandundo)|重新激活该项目并撤消上一个就地编辑操作。|  
|[COleClientItem::Release](#release)|释放与 OLE 链接项的连接，并将其关闭，如果它处于打开状态。 不会破坏客户端项。|  
|[COleClientItem::Reload](#reload)|在调用后，则重新加载该项目`ActivateAs`。|  
|[COleClientItem::Run](#run)|运行与项关联的应用程序。|  
|[COleClientItem::SetDrawAspect](#setdrawaspect)|设置项的当前视图中呈现。|  
|[COleClientItem::SetExtent](#setextent)|设置 OLE 项的边框。|  
|[COleClientItem::SetHostNames](#sethostnames)|设置服务器将在编辑 OLE 项时显示的名称。|  
|[COleClientItem::SetIconicMetafile](#seticonicmetafile)|将缓存用于绘制项的图标的图元文件。|  
|[COleClientItem::SetItemRects](#setitemrects)|设置项的边框。|  
|[COleClientItem::SetLinkUpdateOptions](#setlinkupdateoptions)|设置链接的项 （高级功能） 的更新模式。|  
|[COleClientItem::SetPrintDevice](#setprintdevice)|设置用于此客户端项目的打印目标设备。|  
|[COleClientItem::UpdateLink](#updatelink)|更新某个项的演示文稿缓存。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleClientItem::CanActivate](#canactivate)|由框架，以确定是否允许在就地激活调用。|  
|[COleClientItem::OnChangeItemPosition](#onchangeitemposition)|当某一项的位置发生更改时由框架调用。|  
|[COleClientItem::OnDeactivateAndUndo](#ondeactivateandundo)|由框架后，若要撤消在激活后调用。|  
|[COleClientItem::OnDiscardUndoState](#ondiscardundostate)|调用由框架放弃项的还原状态信息。|  
|[COleClientItem::OnGetClipRect](#ongetcliprect)|由框架后，若要获取项的剪辑矩形坐标调用。|  
|[COleClientItem::OnGetItemPosition](#ongetitemposition)|由框架来获取相对于该视图的项的位置调用。|  
|[COleClientItem::OnGetWindowContext](#ongetwindowcontext)|由框架调用，当就地激活某个项。|  
|[COleClientItem::OnScrollBy](#onscrollby)|由框架要滚动至视图项调用。|  
|[COleClientItem::OnShowItem](#onshowitem)|由框架以显示 OLE 项调用。|  
  
## <a name="remarks"></a>备注  
 OLE 项表示由服务器应用程序，可以将"无缝地"合并到一个文档，以便显示给用户以单个文档创建和维护的数据。 结果是一个"复合文档"的 OLE 项和包含文档组成。  
  
 可嵌入或链接 OLE 项。 如果嵌入，其数据存储作为复合文档的一部分。 如果链接，其数据存储为单独的文件服务器应用程序，创建数据的一部分，并仅链接到该文件将存储在复合文档。 所有 OLE 项都包含指定的服务器应用程序对其进行编辑，应调用的信息。  
  
 `COleClientItem`为响应请求从服务器应用程序; 定义调用的若干可重写函数这些 / / overridables 通常作为通知。 这使服务器应用程序以通知用户在编辑 OLE 项时所做的更改的容器，或检索在编辑过程所需的信息。  
  
 `COleClientItem`可以通过使用[COleDocument](../../mfc/reference/coledocument-class.md)， [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)，或[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)类。 若要使用`COleClientItem`、 从其派生一个类和实现[OnChange](#onchange)成员函数，定义对项所做的更改对容器的响应方式。 若要支持就地激活，重写[OnGetItemPosition](#ongetitemposition)成员函数。 此函数提供 OLE 项的显示位置有关的信息。  
  
 有关使用容器接口的详细信息，请参阅文章[容器︰ 实现容器](../../mfc/containers-implementing-a-container.md)和[激活](../../mfc/activation-cpp.md)。  
  
> [!NOTE]
>  [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]引用嵌入的和链接的项称为"对象"，并引用类型的项作为"类"。 此引用使用术语"item"来区分 OLE 实体从相应的 c + + 对象和术语"type"，以将 OLE 类别与 c + + 类区分开来。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleClientItem`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="a-nameactivatea--coleclientitemactivate"></a><a name="activate"></a>COleClientItem::Activate  
 调用此函数可执行而不是指定的谓词[DoVerb](#doverb)以便您可以执行您自己处理时将引发异常。  
  
```  
void Activate(
    LONG nVerb,  
    CView* pView,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nVerb`  
 指定要执行的谓词。 它可以是以下项之一︰  
  
|值|含义|符号|  
|-----------|-------------|------------|  
|– 0|主谓词|`OLEIVERB_PRIMARY`|  
|– 1|次要谓词|（无）|  
|– 1|显示项进行编辑|`OLEIVERB_SHOW`|  
|– 2|在单独的窗口中编辑项目|`OLEIVERB_OPEN`|  
|– 3|隐藏项|`OLEIVERB_HIDE`|  
  
 为-1 值通常是另一个谓词的别名。 如果不支持打开编辑，–&2; 具有为 –&1; 相同的效果。 有关其他值，请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pView`  
 指向包含 OLE 项; 容器视图窗口这用于服务器应用程序称为就地激活。 此参数应为**NULL**如果容器不支持就地激活。  
  
 `lpMsg`  
 指针，指向导致要激活的项的消息。  
  
### <a name="remarks"></a>备注  
 如果服务器应用程序使用 Microsoft 基础类库编写的此函数会导致[OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb)相应成员函数`COleServerItem`要执行对象。  
  
 如果为编辑主谓词以及在指定了零`nVerb`参数，服务器应用程序将启动以允许进行编辑的 OLE 项。 如果容器应用程序支持就地激活，则可以就地执行编辑。 如果容器不支持就地激活 （或如果指定动词 Open），服务器将在一个单独的窗口中启动，并可以那里完成编辑。 通常情况下，当容器应用程序的用户双击 OLE 项目，主谓词中的值时，才`nVerb`参数确定用户可以执行哪些操作。 然而，如果服务器支持多项操作，它将该操作，无论所指定值在`nVerb`参数。  
  
 有关详细信息，请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameactivateasa--coleclientitemactivateas"></a><a name="activateas"></a>COleClientItem::ActivateAs  
 使用 OLE 的对象转换工具，就好像它是由指定类型的项激活选项`clsidNew`。  
  
```  
virtual BOOL ActivateAs(
    LPCTSTR lpszUserType,  
    REFCLSID clsidOld,  
    REFCLSID clsidNew);
```  
  
### <a name="parameters"></a>参数  
 *lpszUserType*  
 指向的字符串表示的目标用户类型，如"Word 文档"。  
  
 *clsidOld*  
 对项的当前类的引用的 id。 随着存储，除非它是一个链接的类 ID 应表示实际对象的类型。 在这种情况下，它应链接引用的项的 CLSID。 [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)自动为项提供正确的类 ID。  
  
 `clsidNew`  
 对目标类 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 这称为自动[COleConvertDialog::DoConvert](../../mfc/reference/coleconvertdialog-class.md#doconvert)。 它不通常直接调用。  
  
##  <a name="a-nameattachdataobjecta--coleclientitemattachdataobject"></a><a name="attachdataobject"></a>COleClientItem::AttachDataObject  
 调用此函数可初始化[COleDataObject](../../mfc/reference/coledataobject-class.md)用于访问 OLE 项中的数据。  
  
```  
void AttachDataObject(COleDataObject& rDataObject) const;  
```  
  
### <a name="parameters"></a>参数  
 *rDataObject*  
 引用`COleDataObject`将初始化 OLE 项中允许对数据的访问的对象。  
  
##  <a name="a-namecanactivatea--coleclientitemcanactivate"></a><a name="canactivate"></a>COleClientItem::CanActivate  
 由框架调用，当用户请求的 OLE 项; 在就地激活此函数的返回值确定是否允许在就地激活。  
  
```  
virtual BOOL CanActivate();
```  
  
### <a name="return-value"></a>返回值  
 如果允许在就地激活; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现允许就地激活，如果容器具有有效的窗口。 重写此函数可实现特殊逻辑，用于接受或拒绝激活请求。 例如，OLE 项是否太小或没有当前可见，则可以拒绝激活请求。  
  
 有关详细信息，请参阅[IOleInPlaceSite::CanInPlaceActivate](http://msdn.microsoft.com/library/windows/desktop/ms691236)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecancreatefromdataa--coleclientitemcancreatefromdata"></a><a name="cancreatefromdata"></a>COleClientItem::CanCreateFromData  
 容器应用程序是否可以创建嵌入的对象将检查给定`COleDataObject`对象。  
  
```  
static BOOL PASCAL CanCreateFromData(const COleDataObject* pDataObject);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)对象是要创建 OLE 项。  
  
### <a name="return-value"></a>返回值  
 如果该容器可以创建嵌入的对象，则为非`COleDataObject`对象; 否则为 0。  
  
### <a name="remarks"></a>备注  
 `COleDataObject`类是数据在传输中用于从剪贴板、 通过拖放，或从嵌入 OLE 项检索各种格式的数据。  
  
 容器可以使用此函数来决定启用或禁用其编辑粘贴和编辑选择性粘贴命令。  
  
 有关详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。  
  
##  <a name="a-namecancreatelinkfromdataa--coleclientitemcancreatelinkfromdata"></a><a name="cancreatelinkfromdata"></a>COleClientItem::CanCreateLinkFromData  
 检查容器应用程序是否可以创建链接的对象从给定`COleDataObject`对象。  
  
```  
static BOOL PASCAL CanCreateLinkFromData(const COleDataObject* pDataObject);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)对象是要创建 OLE 项。  
  
### <a name="return-value"></a>返回值  
 如果该容器可以创建从链接的对象，则为非`COleDataObject`对象。  
  
### <a name="remarks"></a>备注  
 `COleDataObject`类是数据在传输中用于从剪贴板、 通过拖放，或从嵌入 OLE 项检索各种格式的数据。  
  
 容器可以使用此函数来决定启用或禁用其编辑选择性粘贴和编辑粘贴链接的命令。  
  
 有关详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。  
  
##  <a name="a-namecanpastea--coleclientitemcanpaste"></a><a name="canpaste"></a>COleClientItem::CanPaste  
 调用此函数，以查看是否可以从剪贴板中粘贴嵌入的 OLE 项。  
  
```  
static BOOL PASCAL CanPaste();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果可以从剪贴板; 粘贴嵌入的 OLE 项否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[OleGetClipboard](http://msdn.microsoft.com/library/windows/desktop/ms692778)和[OleQueryCreateFromData](http://msdn.microsoft.com/library/windows/desktop/ms683739)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecanpastelinka--coleclientitemcanpastelink"></a><a name="canpastelink"></a>COleClientItem::CanPasteLink  
 调用此函数，以查看是否可以从剪贴板中粘贴链接的 OLE 项。  
  
```  
static BOOL PASCAL CanPasteLink();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果可以从剪贴板; 粘贴链接的 OLE 项否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[OleGetClipboard](http://msdn.microsoft.com/library/windows/desktop/ms692778)和[OleQueryLinkFromData](http://msdn.microsoft.com/library/windows/desktop/ms690244)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameclosea--coleclientitemclose"></a><a name="close"></a>COleClientItem::Close  
 调用此函数可从加载在内存中与其处理程序，但不是运行的服务器的运行状态向加载状态，也就是说，更改一个 OLE 项的状态。  
  
```  
void Close(OLECLOSE dwCloseOption = OLECLOSE_SAVEIFDIRTY);
```  
  
### <a name="parameters"></a>参数  
 `dwCloseOption`  
 用于指定在什么情况下，向加载状态返回时已保存该 OLE 项的标志。 它可以具有下列值之一︰  
  
- `OLECLOSE_SAVEIFDIRTY`保存 OLE 项。  
  
- `OLECLOSE_NOSAVE`不保存 OLE 项。  
  
- `OLECLOSE_PROMPTSAVE`提示是否保存 OLE 项中的用户。  
  
### <a name="remarks"></a>备注  
 OLE 项未在运行时，此函数具有不起作用。  
  
 有关详细信息，请参阅[IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecoleclientitema--coleclientitemcoleclientitem"></a><a name="coleclientitem"></a>COleClientItem::COleClientItem  
 构造`COleClientItem`对象，并将其添加到的文档项的容器文档的集合，该构造仅 c + + 对象，并且不执行任何 OLE 初始化。  
  
```  
COleClientItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pContainerDoc`  
 指向将包含此项的容器文档的指针。 这可以是任何[COleDocument](../../mfc/reference/coledocument-class.md)派生类。  
  
### <a name="remarks"></a>备注  
 如果您通过**NULL**指针，没有添加对容器文档。 您必须显式调用[COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem)。  
  
 使用 OLE 项之前，必须调用以下创建成员函数之一︰  
  
- [CreateFromClipboard](#createfromclipboard)  
  
- [CreateFromData](#createfromdata)  
  
- [CreateFromFile](#createfromfile)  
  
- [CreateStaticFromClipboard](#createstaticfromclipboard)  
  
- [CreateStaticFromData](#createstaticfromdata)  
  
- [CreateLinkFromClipboard](#createlinkfromclipboard)  
  
- [CreateLinkFromData](#createlinkfromdata)  
  
- [CreateLinkFromFile](#createlinkfromfile)  
  
- [CreateNewItem](#createnewitem)  
  
- [CreateCloneFrom](#createclonefrom)  
  
##  <a name="a-nameconverttoa--coleclientitemconvertto"></a><a name="convertto"></a>COleClientItem::ConvertTo  
 调用此成员函数以将该项目转换为指定的类型`clsidNew`。  
  
```  
virtual BOOL ConvertTo(REFCLSID clsidNew);
```  
  
### <a name="parameters"></a>参数  
 `clsidNew`  
 目标类型的类 ID。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 这称为自动[COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)。 不需要直接调用。  
  
##  <a name="a-namecopytoclipboarda--coleclientitemcopytoclipboard"></a><a name="copytoclipboard"></a>COleClientItem::CopyToClipboard  
 调用此函数可将 OLE 项复制到剪贴板。  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bIncludeLink`  
 **TRUE**链接信息应复制到剪贴板中，如果允许链接的项粘贴; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 通常情况下，从编辑菜单编写消息处理程序的复制或剪切命令时调用此函数。 如果您想要实现的复制或剪切命令，则必须在容器应用程序中实现所选择的项目。  
  
 有关详细信息，请参阅[OleSetClipboard](http://msdn.microsoft.com/library/windows/desktop/ms686623)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreateclonefroma--coleclientitemcreateclonefrom"></a><a name="createclonefrom"></a>COleClientItem::CreateCloneFrom  
 调用此函数可创建指定的 OLE 项的副本。  
  
```  
BOOL CreateCloneFrom(const COleClientItem* pSrcItem);
```  
  
### <a name="parameters"></a>参数  
 *pSrcItem*  
 指向要复制的 OLE 项的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 副本是相同的源项。 此函数可用于支持撤消操作。  
  
##  <a name="a-namecreatefromclipboarda--coleclientitemcreatefromclipboard"></a><a name="createfromclipboard"></a>COleClientItem::CreateFromClipboard  
 调用此函数可从剪贴板中的内容创建嵌入的项。  
  
```  
BOOL CreateFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 *呈现器*  
 用于指定服务器的 OLE 项呈现方式的标志。 有关可能的值，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `cfFormat`  
 指定要创建 OLE 项时缓存的剪贴板数据格式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)时使用的结构*呈现*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果省略此参数，默认值将用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 通常需要调用此函数从消息处理程序的编辑菜单上粘贴命令。 (如果粘贴命令由框架启用[CanPaste](#canpaste)成员函数将返回非零值。)  
  
 有关详细信息，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatefromdataa--coleclientitemcreatefromdata"></a><a name="createfromdata"></a>COleClientItem::CreateFromData  
 调用此函数可创建嵌入的项从`COleDataObject`对象。  
  
```  
BOOL CreateFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)对象是要创建 OLE 项。  
  
 *呈现器*  
 用于指定服务器的 OLE 项呈现方式的标志。 有关可能的值，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `cfFormat`  
 指定要创建 OLE 项时缓存的剪贴板数据格式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)时使用的结构*呈现*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果省略此参数，默认值将用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 数据传输操作，如粘贴从剪贴板或拖放操作，提供`COleDataObject`对象包含的信息提供的服务器应用程序。 它通常用于在重写中的[CView::OnDrop](../../mfc/reference/cview-class.md#ondrop)。  
  
 有关详细信息，请参阅[OleCreateFromData](http://msdn.microsoft.com/library/windows/desktop/ms691211)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatefromfilea--coleclientitemcreatefromfile"></a><a name="createfromfile"></a>COleClientItem::CreateFromFile  
 调用此函数可从文件中创建嵌入的 OLE 项。  
  
```  
BOOL CreateFromFile(
    LPCTSTR lpszFileName,  
    REFCLSID clsid = CLSID_NULL,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszFileName`  
 一个指针，指向要创建 OLE 项的文件名称。  
  
 `clsid`  
 留待将来使用。  
  
 *呈现器*  
 用于指定服务器的 OLE 项呈现方式的标志。 有关可能的值，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `cfFormat`  
 指定要创建 OLE 项时缓存的剪贴板数据格式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)时使用的结构*呈现*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果省略此参数，默认值将用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 框架将调用该函数从[COleInsertDialog::CreateItem](../../mfc/reference/coleinsertdialog-class.md#createitem)如果用户在选择文件按钮从创建时从插入对象对话框中选择确定。  
  
 有关详细信息，请参阅[OleCreateFromFile](http://msdn.microsoft.com/library/windows/desktop/ms690116)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatelinkfromclipboarda--coleclientitemcreatelinkfromclipboard"></a><a name="createlinkfromclipboard"></a>COleClientItem::CreateLinkFromClipboard  
 调用此函数可从剪贴板中的内容创建链接的项。  
  
```  
BOOL CreateLinkFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 *呈现器*  
 用于指定服务器的 OLE 项呈现方式的标志。 有关可能的值，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `cfFormat`  
 指定要创建 OLE 项时缓存的剪贴板数据格式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)时使用的结构*呈现*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果省略此参数，默认值将用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 通常需要调用此函数从消息处理程序的编辑菜单上的粘贴链接命令。 (粘贴链接命令启用的默认实现中[COleDocument](../../mfc/reference/coledocument-class.md)如果剪贴板中包含可链接到一个 OLE 项。)  
  
 有关详细信息，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatelinkfromdataa--coleclientitemcreatelinkfromdata"></a><a name="createlinkfromdata"></a>COleClientItem::CreateLinkFromData  
 调用此函数可创建链接的项从`COleDataObject`对象。  
  
```  
BOOL CreateLinkFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)对象是要创建 OLE 项。  
  
 *呈现器*  
 用于指定服务器的 OLE 项呈现方式的标志。 有关可能的值，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `cfFormat`  
 指定要创建 OLE 项时缓存的剪贴板数据格式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)时使用的结构*呈现*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果省略此参数，默认值将用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此方法在拖放操作期间时用户可以指示应创建的链接。 此外可以用于处理编辑粘贴命令。 中的框架调用`COleClientItem::CreateLinkFromClipboard`并在[COlePasteSpecialDialog::CreateItem](../../mfc/reference/colepastespecialdialog-class.md#createitem)链接选项选择时。  
  
 有关详细信息，请参阅[OleCreateLinkFromData](http://msdn.microsoft.com/library/windows/desktop/ms680731)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatelinkfromfilea--coleclientitemcreatelinkfromfile"></a><a name="createlinkfromfile"></a>COleClientItem::CreateLinkFromFile  
 调用此函数可从文件中创建链接的 OLE 项。  
  
```  
BOOL CreateLinkFromFile(
    LPCTSTR lpszFileName,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszFileName`  
 一个指针，指向要创建 OLE 项的文件名称。  
  
 *呈现器*  
 用于指定服务器的 OLE 项呈现方式的标志。 有关可能的值，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `cfFormat`  
 指定要创建 OLE 项时缓存的剪贴板数据格式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)时使用的结构*呈现*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果省略此参数，默认值将用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 框架调用此函数，如果用户在选择从文件按钮创建和链接复选框被选中时从插入对象对话框中选择确定。 从调用[COleInsertDialog::CreateItem](../../mfc/reference/coleinsertdialog-class.md#createitem)。  
  
 有关详细信息，请参阅[OleCreateLinkToFile](http://msdn.microsoft.com/library/windows/desktop/ms678434)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatenewitema--coleclientitemcreatenewitem"></a><a name="createnewitem"></a>COleClientItem::CreateNewItem  
 调用此函数可创建嵌入的项;此函数将启动服务器应用程序，用户可以创建 OLE 项。  
  
```  
BOOL CreateNewItem(
    REFCLSID clsid,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 唯一标识要创建的 OLE 项的类型的 ID。  
  
 *呈现器*  
 用于指定服务器的 OLE 项呈现方式的标志。 有关可能的值，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `cfFormat`  
 指定要创建 OLE 项时缓存的剪贴板数据格式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)时使用的结构*呈现*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果省略此参数，默认值将用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 框架调用此函数，如果用户在选择新建按钮时从插入对象对话框中选择确定。  
  
 有关详细信息，请参阅[OleCreate](http://msdn.microsoft.com/library/windows/desktop/ms678409)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatestaticfromclipboarda--coleclientitemcreatestaticfromclipboard"></a><a name="createstaticfromclipboard"></a>COleClientItem::CreateStaticFromClipboard  
 调用此函数可从剪贴板中的内容创建静态项。  
  
```  
BOOL CreateStaticFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 *呈现器*  
 用于指定服务器的 OLE 项呈现方式的标志。 有关可能的值，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `cfFormat`  
 指定要创建 OLE 项时缓存的剪贴板数据格式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)时使用的结构*呈现*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果省略此参数，默认值将用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 静态项包含演示文稿数据但不是纯数据;因此不能编辑它。 如果通常调用此函数[CreateFromClipboard](#createfromclipboard)成员函数将失败。  
  
 有关详细信息，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatestaticfromdataa--coleclientitemcreatestaticfromdata"></a><a name="createstaticfromdata"></a>COleClientItem::CreateStaticFromData  
 调用此函数可创建从静态项`COleDataObject`对象。  
  
```  
BOOL CreateStaticFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)对象是要创建 OLE 项。  
  
 *呈现器*  
 用于指定服务器的 OLE 项呈现方式的标志。 有关可能的值，请参阅[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `cfFormat`  
 指定要创建 OLE 项时缓存的剪贴板数据格式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)时使用的结构*呈现*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果省略此参数，默认值将用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 静态项包含演示文稿数据但不是纯数据;因此，不能编辑它。 这是实质上是相同[CreateStaticFromClipboard](#createstaticfromclipboard)之处在于可以从任意创建一个静态项`COleDataObject`，而不只是从剪贴板。  
  
 在中使用[COlePasteSpecialDialog::CreateItem](../../mfc/reference/colepastespecialdialog-class.md#createitem)选中静态。  
  
 有关详细信息，请参阅[OleCreateStaticFromData](http://msdn.microsoft.com/library/windows/desktop/ms687290)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedeactivatea--coleclientitemdeactivate"></a><a name="deactivate"></a>COleClientItem::Deactivate  
 调用此函数可停用 OLE 项并释放任何关联的资源。  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>备注  
 您通常在用户单击鼠标停留在项边界外部的客户端区域上时停用处于就地活动 OLE 项。 请注意停用 OLE 项将放弃其还原状态，从而导致无法调用[ReactivateAndUndo](#reactivateandundo)成员函数。  
  
 如果您的应用程序支持撤消，不要调用`Deactivate`; 相反，调用[DeactivateUI](#deactivateui)。  
  
 有关详细信息，请参阅[IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedeactivateuia--coleclientitemdeactivateui"></a><a name="deactivateui"></a>COleClientItem::DeactivateUI  
 当用户停用在就地激活项时调用此函数。  
  
```  
void DeactivateUI();
```  
  
### <a name="remarks"></a>备注  
 此函数将还原到其原始状态，隐藏任何菜单和其他已由称为就地激活的控件的容器应用程序的用户界面。  
  
 此函数不刷新该项目的还原状态信息。 信息将保留，以便[ReactivateAndUndo](#reactivateandundo)可以以后可用于执行撤消命令在服务器应用程序，以防在停用项后立即选择容器的撤消命令。  
  
 有关详细信息，请参阅[IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedeletea--coleclientitemdelete"></a><a name="delete"></a>COleClientItem::Delete  
 调用此函数可从容器文档中删除 OLE 项。  
  
```  
void Delete(BOOL bAutoDelete = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bAutoDelete`  
 指定是否要从文档中移除项。  
  
### <a name="remarks"></a>备注  
 此函数将调用[版本](#release)成员函数，进而删除项，并永久 OLE 项从文档中移除的 c + + 对象。 如果嵌入 OLE 项时，删除的项的本机数据。 它总是会关闭正在运行的服务器;因此，如果该项是打开的链接，此函数将其关闭。  
  
##  <a name="a-namedodragdropa--coleclientitemdodragdrop"></a><a name="dodragdrop"></a>COleClientItem::DoDragDrop  
 调用`DoDragDrop`成员函数来执行拖放操作。  
  
```  
DROPEFFECT DoDragDrop(
    LPCRECT lpItemRect,  
    CPoint ptOffset,  
    BOOL bIncludeLink = FALSE,  
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,  
    LPCRECT lpRectStartDrag = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpItemRect`  
 在工作区坐标 （像素） 的屏幕上的项的矩形。  
  
 `ptOffset`  
 与偏移量`lpItemRect`在拖动时所在的鼠标位置。  
  
 `bIncludeLink`  
 将此设置为**TRUE**如果链接数据应复制到剪贴板。 将其设置为**FALSE**如果服务器应用程序不支持链接。  
  
 `dwEffects`  
 确定拖动源允许拖放操作中的效果。  
  
 `lpRectStartDrag`  
 向定义实际开始拖动该矩形的指针。 有关更多信息，请参见下面的“备注”部分。  
  
### <a name="return-value"></a>返回值  
 一个 `DROPEFFECT` 值。 如果它是`DROPEFFECT_MOVE`，应删除的原始数据。  
  
### <a name="remarks"></a>备注  
 不立即启动拖放操作。 鼠标光标离开所指定的矩形等到`lpRectStartDrag`或直到经过指定的毫秒数。 如果`lpRectStartDrag`是**NULL**，矩形的大小是一个像素。  
  
 注册表项设置由指定的延迟时间。 可以通过调用更改的延迟时间[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果不指定延迟时间，则使用默认值为 200 毫秒。 将延迟时间存储中，如下所示︰  
  
-   Windows NT 拖动延迟时间将存储在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Windows 3.x 拖动延迟时间将存储在 WIN。INI 文件，请在 [时段} 部分。  
  
-   Windows 95/98 拖动延迟时间存储在缓存版的 WIN。INI。  
  
 用于详细了解如何拖动延迟信息存储在注册表或。INI 文件，请参阅[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedoverba--coleclientitemdoverb"></a><a name="doverb"></a>COleClientItem::DoVerb  
 调用`DoVerb`执行指定的谓词。  
  
```  
virtual BOOL DoVerb(
    LONG nVerb,  
    CView* pView,
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nVerb`  
 指定要执行的谓词。 它可以包括以下项之一︰  
  
|值|含义|符号|  
|-----------|-------------|------------|  
|– 0|主谓词|`OLEIVERB_PRIMARY`|  
|– 1|次要谓词|（无）|  
|– 1|显示项进行编辑|`OLEIVERB_SHOW`|  
|– 2|在单独的窗口中编辑项目|`OLEIVERB_OPEN`|  
|– 3|隐藏项|`OLEIVERB_HIDE`|  
  
 为-1 值通常是另一个谓词的别名。 如果不支持打开编辑，–&2; 具有为 –&1; 相同的效果。 有关其他值，请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pView`  
 指针，指向视图窗口中;这用于服务器称为就地激活。 此参数应为**NULL**如果容器应用程序不允许在就地激活。  
  
 `lpMsg`  
 指针，指向导致要激活的项的消息。  
  
### <a name="return-value"></a>返回值  
 如果已成功执行该谓词; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数将调用[激活](#activate)成员函数以执行谓词。 此外将捕获异常，并为用户显示一个消息框，如果引发一。  
  
 如果为编辑主谓词以及在指定了零`nVerb`参数，服务器应用程序将启动以允许进行编辑的 OLE 项。 如果容器应用程序支持就地激活，则可以就地执行编辑。 如果容器不支持就地激活 （或如果指定动词 Open），服务器将在一个单独的窗口中启动，并可以那里完成编辑。 通常情况下，当容器应用程序的用户双击 OLE 项目，主谓词中的值时，才`nVerb`参数确定用户可以执行哪些操作。 然而，如果服务器支持多项操作，它将该操作，无论所指定值在`nVerb`参数。  
  
##  <a name="a-namedrawa--coleclientitemdraw"></a><a name="draw"></a>COleClientItem::Draw  
 调用此函数可绘制到使用指定的设备上下文的指定边框的 OLE 项。  
  
```  
BOOL Draw(
    CDC* pDC,  
    LPCRECT lpBounds,  
    DVASPECT nDrawAspect = (DVASPECT)-1);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向[CDC](../../mfc/reference/cdc-class.md)用于绘制 OLE 项的对象。  
  
 `lpBounds`  
 指向[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或`RECT`结构，它定义要在其中绘制 （使用逻辑单位由设备上下文） 的 OLE 项的边框。  
  
 `nDrawAspect`  
 指定的方面的 OLE 项，即，它的显示方式。 如果`nDrawAspect`为 –&1;，通过设置的最后一个方面[SetDrawAspect](#setdrawaspect)使用。 有关此标志的可能值的详细信息，请参阅[SetDrawAspect](#setdrawaspect)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 该函数可能使用的图元文件表示形式创建的 OLE 项[OnDraw](../../mfc/reference/coleserveritem-class.md#ondraw)成员函数`COleServerItem`。  
  
 通常，可以使用**绘制**屏幕显示，并传递屏幕设备上下文作为`pDC`。 在这种情况下，您需要指定只有前两个参数。  
  
 `lpBounds`参数标识 （相对于其当前的映射模式） 的目标设备上下文中的矩形。 呈现可能涉及到缩放图片和容器应用程序可以用于施加之间显示的视图和最终打印的图像进行缩放的视图。  
  
 有关详细信息，请参阅[iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetactiveviewa--coleclientitemgetactiveview"></a><a name="getactiveview"></a>COleClientItem::GetActiveView  
 返回在其的项是就地激活的视图。  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向该视图;否则为**NULL**如果此项不是就地激活。  
  
##  <a name="a-namegetcachedextenta--coleclientitemgetcachedextent"></a><a name="getcachedextent"></a>COleClientItem::GetCachedExtent  
 调用此函数可检索 OLE 项的大小。  
  
```  
BOOL GetCachedExtent(
    LPSIZE lpSize,  
    DVASPECT nDrawAspect = (DVASPECT)-1);
```  
  
### <a name="parameters"></a>参数  
 `lpSize`  
 指向**大小**结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)将会收到大小信息的对象。  
  
 `nDrawAspect`  
 指定要从中检索其边界的 OLE 项的方面。 有关可能的值，请参阅[SetDrawAspect](#setdrawaspect)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值如果 OLE 项为空，则为 0。  
  
### <a name="remarks"></a>备注  
 此函数提供的相同信息[GetExtent](#getextent)。 但是，你可以调用`GetCachedExtent`以获取扩展盘区的信息处理过程中发生的其他 OLE 处理程序，如[OnChange](#onchange)。 维度是在`MM_HIMETRIC`单位。  
  
 这可能是因为`GetCachedExtent`使用[IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)接口，而不是使用[IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709)接口，以获取此项目的范围。 **IViewObject2** COM 对象缓存到前面的调用中使用的扩展盘区信息[iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)。  
  
 有关详细信息，请参阅[IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetclassida--coleclientitemgetclassid"></a><a name="getclassid"></a>COleClientItem::GetClassID  
 返回到所指向的内存中的项的类 ID `pClassID`。  
  
```  
void GetClassID(CLSID* pClassID) const;  
```  
  
### <a name="parameters"></a>参数  
 `pClassID`  
 指向类型的标识符[CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424)来检索类 id。 如需有关**CLSID**，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 类 ID 是一个 128 位数字，用于唯一标识的应用程序可编辑的项。  
  
 有关详细信息，请参阅[IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetclipboarddataa--coleclientitemgetclipboarddata"></a><a name="getclipboarddata"></a>COleClientItem::GetClipboardData  
 调用此函数可获取`COleDataSource`对象，其中包含通过调用将被放到剪贴板的所有数据[CopyToClipboard](#copytoclipboard)成员函数。  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDataSource`  
 指向[COleDataSource](../../mfc/reference/coledatasource-class.md)将 OLE 项中收到包含的数据的对象。  
  
 `bIncludeLink`  
 **TRUE**链接数据应包括; 否则为如果**FALSE**。  
  
 `lpOffset`  
 以像素为单位的对象的原点的鼠标光标的偏移量。  
  
 `lpSize`  
 以像素为单位的对象的大小。  
  
### <a name="remarks"></a>备注  
 `GetClipboardData`作为的默认实现调用[OnGetClipboardData](#ongetclipboarddata)。 重写`OnGetClipboardData`仅当你想要提供除了所提供的数据格式`CopyToClipboard`。 将放置在这些格式`COleDataSource`对象之前还是之后调用`CopyToClipboard`，然后将传递`COleDataSource`对象传递给[COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函数。 例如，如果您希望在其容器文档伴随放到剪贴板中的 OLE 项的位置，您将定义您自己的格式传递该信息并将它放入`COleDataSource`之前调用`CopyToClipboard`。  
  
##  <a name="a-namegetdocumenta--coleclientitemgetdocument"></a><a name="getdocument"></a>COleClientItem::GetDocument  
 调用此函数可获取指向文档，其中包含 OLE 项的指针。  
  
```  
COleDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向包含 OLE 项的文档的指针。 **NULL**如果该项不是文档的一部分。  
  
### <a name="remarks"></a>备注  
 此指针允许访问`COleDocument`作为参数传递的对象`COleClientItem`构造函数。  
  
##  <a name="a-namegetdrawaspecta--coleclientitemgetdrawaspect"></a><a name="getdrawaspect"></a>COleClientItem::GetDrawAspect  
 调用`GetDrawAspect`成员函数可确定当前"方面，"或查看的项。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>返回值  
 取值范围为`DVASPECT`枚举，参考 》 中列出了其值[SetDrawAspect](#setdrawaspect)。  
  
### <a name="remarks"></a>备注  
 该方面指定项的呈现方式。  
  
##  <a name="a-namegetextenta--coleclientitemgetextent"></a><a name="getextent"></a>COleClientItem::GetExtent  
 调用此函数可检索 OLE 项的大小。  
  
```  
BOOL GetExtent(
    LPSIZE lpSize,  
    DVASPECT nDrawAspect = (DVASPECT)- 1);
```  
  
### <a name="parameters"></a>参数  
 `lpSize`  
 指向**大小**结构或`CSize`将会收到大小信息的对象。  
  
 `nDrawAspect`  
 指定要从中检索其边界的 OLE 项的方面。 有关可能的值，请参阅[SetDrawAspect](#setdrawaspect)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值如果 OLE 项为空，则为 0。  
  
### <a name="remarks"></a>备注  
 如果服务器应用程序使用 Microsoft 基础类库编写的此函数会导致[OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)相应成员函数`COleServerItem`要调用的对象。 请注意检索到的大小可能不同于上次设置的大小[SetExtent](#setextent)成员函数; 指定的大小`SetExtent`将被视为一项建议。 维度是在`MM_HIMETRIC`单位。  
  
> [!NOTE]
>  不要调用`GetExtent`处理过程中的 OLE 一个处理程序，如[OnChange](#onchange)。 调用[GetCachedExtent](#getcachedextent)相反。  
  
 有关详细信息，请参阅[IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegeticonfromregistrya--coleclientitemgeticonfromregistry"></a><a name="geticonfromregistry"></a>COleClientItem::GetIconFromRegistry  
 调用此成员函数以检索与特定的 CLSID 服务器关联的图标资源的句柄。  
  
```  
HICON GetIconFromRegistry() const;  
  
static HICON GetIconFromRegistry(CLSID& clsid);
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 对与图标关联的服务器的 CLSID 的引用。  
  
### <a name="return-value"></a>返回值  
 图标资源的有效句柄或**NULL**如果无法找到服务器的图标或默认图标。  
  
### <a name="remarks"></a>备注  
 此成员函数将无法启动服务器或动态，获取一个图标，即使服务器已正在运行。 相反，此成员函数打开服务器的可执行文件映像，然后检索与服务器关联，因为它已注册的静态图标。  
  
##  <a name="a-namegeticonicmetafilea--coleclientitemgeticonicmetafile"></a><a name="geticonicmetafile"></a>COleClientItem::GetIconicMetafile  
 检索用于绘制项的图标的图元文件。  
  
```  
HGLOBAL GetIconicMetafile();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则的图元文件句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 如果没有当前的图标，则返回默认图标。 这由 MFC/OLE 对话框自动调用，并且通常不直接调用。  
  
 此函数还调用[SetIconicMetafile](#seticonicmetafile)缓存以供以后使用图元文件。  
  
##  <a name="a-namegetinplacewindowa--coleclientitemgetinplacewindow"></a><a name="getinplacewindow"></a>COleClientItem::GetInPlaceWindow  
 调用`GetInPlaceWindow`成员函数以获取指向在其中打开该项目的窗口的指针，用于就地编辑。  
  
```  
CWnd* GetInPlaceWindow();
```  
  
### <a name="return-value"></a>返回值  
 一个指向就地编辑窗口中的项;**NULL**如果该项未处于活动状态，或者其服务器不可用。  
  
### <a name="remarks"></a>备注  
 仅为是处于就地活动状态的项，应调用此函数。  
  
##  <a name="a-namegetitemstatea--coleclientitemgetitemstate"></a><a name="getitemstate"></a>COleClientItem::GetItemState  
 调用此函数可获取 OLE 项的当前状态。  
  
```  
UINT GetItemState() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**COleClientItem::ItemState**枚举值，该值可以是以下之一︰ `emptyState`， **loadedState**， `openState`， `activeState`， `activeUIState`。 有关这些状态信息，请参阅文章[容器︰ 客户端项状态](../../mfc/containers-client-item-states.md)。  
  
### <a name="remarks"></a>备注  
 若要在得到通知 OLE 项的状态更改时，使用[OnChange](#onchange)成员函数。  
  
 有关详细信息，请参阅文章[容器︰ 客户端项状态](../../mfc/containers-client-item-states.md)。  
  
##  <a name="a-namegetlaststatusa--coleclientitemgetlaststatus"></a><a name="getlaststatus"></a>COleClientItem::GetLastStatus  
 返回最后一次 OLE 操作的状态代码。  
  
```  
SCODE GetLastStatus() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个 `SCODE` 值。  
  
### <a name="remarks"></a>备注  
 成员函数，可返回**BOOL**值**FALSE**，或其他成员函数，可返回**NULL**，`GetLastStatus`返回更详细的失败信息。 请注意，大多数 OLE 成员函数将引发更严重的错误的异常。 上的解释的特定信息`SCODE`取决于最后一次返回的基础 OLE 调用`SCODE`值。  
  
 有关详细信息`SCODE`，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]文档。  
  
##  <a name="a-namegetlinkupdateoptionsa--coleclientitemgetlinkupdateoptions"></a><a name="getlinkupdateoptions"></a>COleClientItem::GetLinkUpdateOptions  
 调用此函数可获取 OLE 项的链接更新选项的当前值。  
  
```  
OLEUPDATE GetLinkUpdateOptions();
```  
  
### <a name="return-value"></a>返回值  
 以下值之一：  
  
- `OLEUPDATE_ALWAYS`更新链接的项只要有可能。 在链接对话框中，此选项支持自动链接更新单选按钮。  
  
- `OLEUPDATE_ONCALL`更新仅根据请求从容器应用程序的链接的项 (当[UpdateLink](#updatelink)调用成员函数)。 在链接对话框中，此选项支持手动链接更新单选按钮。  
  
### <a name="remarks"></a>备注  
 这是一项高级的操作。  
  
 自动调用此函数[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)类。  
  
 有关详细信息，请参阅[IOleLink::GetUpdateOptions](http://msdn.microsoft.com/library/windows/desktop/ms680100)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettypea--coleclientitemgettype"></a><a name="gettype"></a>COleClientItem::GetType  
 调用此函数可确定是否 OLE 项嵌入或链接，或静态。  
  
```  
OLE_OBJTYPE GetType() const;  
```  
  
### <a name="return-value"></a>返回值  
 无符号的整数，下列值之一︰  
  
- `OT_LINK`OLE 项是一个链接。  
  
- `OT_EMBEDDED`嵌入 OLE 项。  
  
- `OT_STATIC`OLE 项是静态的也就是说，只包含演示文稿数据，不是 native 数据，并因此不能编辑。  
  
##  <a name="a-namegetusertypea--coleclientitemgetusertype"></a><a name="getusertype"></a>COleClientItem::GetUserType  
 调用此函数可获取用户可见的字符串，描述 OLE 项的类型，例如"Word 文档"。  
  
```  
void GetUserType(
    USERCLASSTYPE nUserClassType,  
    CString& rString);
```  
  
### <a name="parameters"></a>参数  
 *nUserClassType*  
 一个值，该值描述 OLE 项的类型的字符串所需变体。 这可能具有下列值之一︰  
  
- `USERCLASSTYPE_FULL`向用户显示的完整类型名称。  
  
- `USERCLASSTYPE_SHORT`在弹出菜单和编辑链接对话框中使用短名称 （最多&15; 个字符）。  
  
- `USERCLASSTYPE_APPNAME`为类提供服务的应用程序名称。  
  
 `rString`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)描述 OLE 项的类型的字符串是要返回的对象。  
  
### <a name="remarks"></a>备注  
 这通常是在系统注册数据库中的条目。  
  
 如果完整类型名称已请求但不可用，使用短名称。 如果在注册数据库中，如果未找到的类型的 OLE 项条目，或者如果 OLE 项的类型注册的用户类型，然后用户类型当前存储在使用的 OLE 项。 如果该用户的类型名称为空字符串，则使用"未知对象"。  
  
 有关详细信息，请参阅[IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisinplaceactivea--coleclientitemisinplaceactive"></a><a name="isinplaceactive"></a>COleClientItem::IsInPlaceActive  
 调用此函数可查看 OLE 项是否处于就地活动状态。  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>返回值  
 OLE 项处于就地活动状态; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 常见执行不同的逻辑，具体取决于就地中编辑该项目是否是。 该函数检查当前的项状态是否为相等`activeState`或`activeUIState`。  
  
##  <a name="a-nameislinkuptodatea--coleclientitemislinkuptodate"></a><a name="islinkuptodate"></a>COleClientItem::IsLinkUpToDate  
 调用此函数以确定是否为最新的 OLE 项。  
  
```  
BOOL IsLinkUpToDate() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果 OLE 项是最新。否则为 0。  
  
### <a name="remarks"></a>备注  
 链接的项可以是过期如果已更新其源文档。 嵌入的项包含在其中的链接可能同样会变得过期。 该函数执行 OLE 项的递归检查。 请注意，确定一个 OLE 项是否过期的开销可能会为作为实际执行更新。  
  
 这称为自动[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)实现。  
  
 有关详细信息，请参阅[IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameismodifieda--coleclientitemismodified"></a><a name="ismodified"></a>COleClientItem::IsModified  
 调用此函数可看到 OLE 项是脏的 （自上次保存以来修改）。  
  
```  
BOOL IsModified() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果 OLE 项已更新; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[IPersistStorage::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisopena--coleclientitemisopen"></a><a name="isopen"></a>COleClientItem::IsOpen  
 调用此函数，以查看是否已打开，则 OLE 项也就是说，在服务器应用程序在一个单独的窗口中运行的实例中打开。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果 OLE 项已打开，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 它用于确定何时绘制该对象具有阴影模式。 打开的对象应具有在该对象之上绘制阴影图案。 您可以使用[CRectTracker](../../mfc/reference/crecttracker-class.md)对象来实现此目的。  
  
##  <a name="a-nameisrunninga--coleclientitemisrunning"></a><a name="isrunning"></a>COleClientItem::IsRunning  
 调用此函数，以查看是否正在运行的 OLE 项;也就是说，项是否已加载并运行在服务器应用程序。  
  
```  
BOOL IsRunning() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果正在运行的 OLE 项; 则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[OleIsRunning](http://msdn.microsoft.com/library/windows/desktop/ms688705)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonactivatea--coleclientitemonactivate"></a><a name="onactivate"></a>COleClientItem::OnActivate  
 由框架来通知该项目，它只是已激活就地调用。  
  
```  
virtual void OnActivate();
```  
  
### <a name="remarks"></a>备注  
 请注意，此函数调用以指示服务器正在运行，不是为了反映其用户界面已安装程序位于容器应用程序。 此时，该对象没有活动的用户界面 (不是`activeUIState`)。 尚未安装其菜单或工具栏。 [OnActivateUI](#onactivateui)调用成员函数时，在这种情况。  
  
 默认实现调用[OnChange](#onchange)成员函数时**OLE_CHANGEDSTATE**作为参数。 重写此函数以执行自定义处理某项处于就地活动状态时。  
  
##  <a name="a-nameonactivateuia--coleclientitemonactivateui"></a><a name="onactivateui"></a>COleClientItem::OnActivateUI  
 框架将调用`OnActivateUI`当对象已进入活动 UI 状态。  
  
```  
virtual void OnActivateUI();
```  
  
### <a name="remarks"></a>备注  
 对象现在已安装其工具栏和菜单。  
  
 默认实现会记住该服务器的`HWND`以供将来**GetServerWindow**调用。  
  
##  <a name="a-nameonchangea--coleclientitemonchange"></a><a name="onchange"></a>COleClientItem::OnChange  
 当用户修改、 保存，或关闭 OLE 项时，由框架调用。  
  
```  
virtual void OnChange(
    OLE_NOTIFICATION nCode,  
    DWORD dwParam);
```  
  
### <a name="parameters"></a>参数  
 `nCode`  
 服务器的原因更改此项。 它可以具有下列值之一︰  
  
- `OLE_CHANGED`OLE 项的外观发生了更改。  
  
- `OLE_SAVED`已保存的 OLE 项。  
  
- `OLE_CLOSED`OLE 项已关闭。  
  
- `OLE_CHANGED_STATE`OLE 项已从一个状态更改为另一个。  
  
 `dwParam`  
 如果`nCode`是`OLE_SAVED`或`OLE_CLOSED`，未使用此参数。 如果`nCode`是`OLE_CHANGED`，此参数指定的 OLE 项的已更改的方面。 有关可能的值，请参阅`dwParam`参数[COleClientItem::Draw](#draw)。 如果`nCode`是`OLE_CHANGED_STATE`，此参数是**COleClientItem::ItemState**枚举值，并描述要进入的状态。 它可以具有下列值之一︰ `emptyState`， **loadedState**， `openState`， `activeState`，或`activeUIState`。  
  
### <a name="remarks"></a>备注  
 (如果服务器应用程序使用 Microsoft 基础类库编写的此函数调用以响应`Notify`的成员函数`COleServerDoc`或`COleServerItem`。)默认实现将该容器文档标记为已修改，如果`nCode`是`OLE_CHANGED`或`OLE_SAVED`。  
  
 有关`OLE_CHANGED_STATE`，从返回的当前状态[GetItemState](#getitemstate)仍将原来的状态，这意味着在此状态更改之前的当前状态。  
  
 重写此函数可对 OLE 项的状态变化作出响应。 通常通过使失效，显示该项的区域更新项的外观。 重写的开头调用基类实现。  
  
##  <a name="a-nameonchangeitempositiona--coleclientitemonchangeitemposition"></a><a name="onchangeitemposition"></a>COleClientItem::OnChangeItemPosition  
 由框架以通知容器 OLE 项的作用域已更改的就地激活期间调用。  
  
```  
virtual BOOL OnChangeItemPosition(const CRect& rectPos);
```  
  
### <a name="parameters"></a>参数  
 *rectPos*  
 指示项的位置相对于容器应用程序的工作区。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功更改项的位置;否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现确定 OLE 项目与调用的新可见矩形[SetItemRects](#setitemrects)用新值。 默认实现计算该项的可见矩形，并将该信息传递到服务器。  
  
 重写此函数可将特殊的规则应用于调整大小/移动操作。 如果编写应用程序在 MFC 中，此调用产生，因为服务器称为[COleServerDoc::RequestPositionChange](../../mfc/reference/coleserverdoc-class.md#requestpositionchange)。  
  
##  <a name="a-nameondeactivatea--coleclientitemondeactivate"></a><a name="ondeactivate"></a>COleClientItem::OnDeactivate  
 由框架调用，当从处于就地活动状态转换的 OLE 项 ( `activeState`) 向加载状态，这意味着它将停在就地激活后用。  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>备注  
 请注意，此函数调用以指示 OLE 项已关闭，未从容器应用程序中其用户界面已被移走。 在这种情况， [OnDeactivateUI](#ondeactivateui)调用成员函数。  
  
 默认实现调用[OnChange](#onchange)成员函数时**OLE_CHANGEDSTATE**作为参数。 重写此函数以执行自定义处理处于就地活动项被停用时。 例如，如果在容器应用程序中支持撤消命令，您可以覆盖放弃还原状态，此函数，指出执行 OLE 项的最后一个操作无法撤消后停用该项目。  
  
##  <a name="a-nameondeactivateandundoa--coleclientitemondeactivateandundo"></a><a name="ondeactivateandundo"></a>COleClientItem::OnDeactivateAndUndo  
 由框架调用，当用户激活位置中的 OLE 项后调用撤消命令。  
  
```  
virtual void OnDeactivateAndUndo();
```  
  
### <a name="remarks"></a>备注  
 默认实现调用[DeactivateUI](#deactivateui)停用服务器的用户界面。 如果您要在容器应用程序中实现撤消命令，重写此函数。 在您重写时，调用该函数的基类版本，然后撤消在您的应用程序中执行的最后一个命令。  
  
 有关详细信息，请参阅[IOleInPlaceSite::DeactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms683743)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameondeactivateuia--coleclientitemondeactivateui"></a><a name="ondeactivateui"></a>COleClientItem::OnDeactivateUI  
 当用户停用在就地激活项时调用。  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>参数  
 `bUndoable`  
 指定是否可撤消编辑的更改。  
  
### <a name="remarks"></a>备注  
 此函数将还原到其原始状态，隐藏任何菜单和其他已由称为就地激活的控件的容器应用程序的用户界面。  
  
 如果`bUndoable`是**FALSE**，容器应禁用撤消命令，实际上放弃容器的撤消状态，因为它表示由服务器执行的最后一个操作是不可撤消。  
  
##  <a name="a-nameondiscardundostatea--coleclientitemondiscardundostate"></a><a name="ondiscardundostate"></a>COleClientItem::OnDiscardUndoState  
 当用户执行的操作将撤消状态放弃在编辑 OLE 项时，由框架调用。  
  
```  
virtual void OnDiscardUndoState();
```  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。 如果您要在容器应用程序中实现撤消命令，重写此函数。 在您重写时，放弃容器应用程序的还原状态。  
  
 如果服务器而编写的 Microsoft 基础类库，服务器可能会导致调用通过调用此函数[COleServerDoc::DiscardUndoState](../../mfc/reference/coleserverdoc-class.md#discardundostate)。  
  
 有关详细信息，请参阅[IOleInPlaceSite::DiscardUndoState](http://msdn.microsoft.com/library/windows/desktop/ms688642)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameongetclipboarddataa--coleclientitemongetclipboarddata"></a><a name="ongetclipboarddata"></a>COleClientItem::OnGetClipboardData  
 由框架调用以获取`COleDataSource`对象，其中包含通过任何一个调用将被放到剪贴板的所有数据[CopyToClipboard](#copytoclipboard)或[DoDragDrop](#dodragdrop)成员函数。  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>参数  
 `bIncludeLink`  
 将此设置为**TRUE**如果将数据链接应复制到剪贴板。 将此设置为**FALSE**如果服务器应用程序不支持链接。  
  
 `lpOffset`  
 指向鼠标光标的偏移量中的源以像素为单位的对象的指针。  
  
 `lpSize`  
 以像素为单位的对象的大小的指针。  
  
### <a name="return-value"></a>返回值  
 一个指向[COleDataSource](../../mfc/reference/coledatasource-class.md)对象，它包含在剪贴板数据。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[GetClipboardData](#getclipboarddata)。  
  
##  <a name="a-nameongetcliprecta--coleclientitemongetcliprect"></a><a name="ongetcliprect"></a>COleClientItem::OnGetClipRect  
 框架将调用`OnGetClipRect`成员函数以获取正在编辑的项的剪辑矩形坐标中的位置。  
  
```  
virtual void OnGetClipRect(CRect& rClipRect);
```  
  
### <a name="parameters"></a>参数  
 *rClipRect*  
 指向类的对象指针[CRect](../../atl-mfc-shared/reference/crect-class.md) ，将存放的项的剪辑矩形坐标。  
  
### <a name="remarks"></a>备注  
 坐标是以相对于容器应用程序窗口工作区的像素为单位。  
  
 默认实现只是返回项处于就地活动状态的视图在其上的客户端矩形。  
  
##  <a name="a-nameongetitempositiona--coleclientitemongetitemposition"></a><a name="ongetitemposition"></a>COleClientItem::OnGetItemPosition  
 框架将调用`OnGetItemPosition`成员函数以获取就地正在编辑的项的坐标。  
  
```  
virtual void OnGetItemPosition(CRect& rPosition);
```  
  
### <a name="parameters"></a>参数  
 `rPosition`  
 引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它将包含项的位置坐标。  
  
### <a name="remarks"></a>备注  
 坐标是以相对于容器应用程序窗口工作区的像素为单位。  
  
 此函数的默认实现不执行任何操作。 支持就地编辑的应用程序需要它的实现。  
  
##  <a name="a-nameongetwindowcontexta--coleclientitemongetwindowcontext"></a><a name="ongetwindowcontext"></a>COleClientItem::OnGetWindowContext  
 由框架调用，当就地激活某个项。  
  
```  
virtual BOOL OnGetWindowContext(
    CFrameWnd** ppMainFrame,  
    CFrameWnd** ppDocFrame,  
    LPOLEINPLACEFRAMEINFO lpFrameInfo);
```  
  
### <a name="parameters"></a>参数  
 `ppMainFrame`  
 指针到指向主框架窗口。  
  
 `ppDocFrame`  
 指针到指向文档框架窗口。  
  
 `lpFrameInfo`  
 指向[OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737)结构，它将会收到框架窗口信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数用于检索有关 OLE 项的父窗口的信息。  
  
 如果容器是 MDI 应用程序中，默认实现将返回一个指向[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)对象在`ppMainFrame`和活动的指针[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象在`ppDocFrame`。 如果容器是 SDI 应用程序，则默认实现返回一个指向[CFrameWnd](../../mfc/reference/cframewnd-class.md)对象在`ppMainFrame`，并返回**NULL**中`ppDocFrame`。 默认实现中的成员还填充`lpFrameInfo`。  
  
 默认实现不能满足您的应用程序; 如果仅重写此函数例如，如果您的应用程序具有不同于 SDI 还是 MDI 用户界面模式。 这是一个高级可重写。  
  
 有关详细信息，请参阅[IOleInPlaceSite::GetWindowContext](http://msdn.microsoft.com/library/windows/desktop/ms694366)和[OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameoninsertmenusa--coleclientitemoninsertmenus"></a><a name="oninsertmenus"></a>COleClientItem::OnInsertMenus  
 由框架调用期间在就地激活，若要将容器应用程序的菜单插入到空菜单。  
  
```  
virtual void OnInsertMenus(
    CMenu* pMenuShared,  
    LPOLEMENUGROUPWIDTHS lpMenuWidths);
```  
  
### <a name="parameters"></a>参数  
 `pMenuShared`  
 指向一个空菜单。  
  
 `lpMenuWidths`  
 指向数组的六个**长**值，该值指示菜单数每个以下的菜单组中︰ 文件、 编辑容器对象，窗口中，帮助。 容器应用程序负责文件、 容器和窗口菜单组，对应于 0、 2 和 4 此数组的元素。  
  
### <a name="remarks"></a>备注  
 此菜单然后传递到服务器，后者将插入其自己的菜单，创建一个复合菜单。 可以反复调用此函数，来构建几个复合菜单。  
  
 默认实现将插入到`pMenuShared`就地容器菜单; 即，文件、 容器中，和窗口菜单组。 [CDocTemplate::SetContainerInfo](../../mfc/reference/cdoctemplate-class.md#setcontainerinfo)用于设置此菜单资源。 默认实现也将相应的值分配给元素 0、 2 和 4 英寸`lpMenuWidths`，取决于菜单资源。 默认实现不适合于您的应用程序; 如果重写此函数例如，如果您的应用程序不使用将资源与文档类型相关联的文档模板。 如果重写此函数，还应重写[OnSetMenu](#onsetmenu)和[OnRemoveMenus](#onremovemenus)。 这是一个高级可重写。  
  
 有关详细信息，请参阅[ioleinplaceframe:: Insertmenus](http://msdn.microsoft.com/library/windows/desktop/ms683987)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonremovemenusa--coleclientitemonremovemenus"></a><a name="onremovemenus"></a>COleClientItem::OnRemoveMenus  
 由框架从指定的复合菜单删除容器的菜单，在就地激活结束时调用。  
  
```  
virtual void OnRemoveMenus(CMenu* pMenuShared);
```  
  
### <a name="parameters"></a>参数  
 `pMenuShared`  
 通过调用构造复合菜单上指向[OnInsertMenus](#oninsertmenus)成员函数。  
  
### <a name="remarks"></a>备注  
 默认实现，则删除`pMenuShared`就地容器菜单，即、 文件、 容器和窗口菜单组。 默认实现不适合于您的应用程序; 如果重写此函数例如，如果您的应用程序不使用将资源与文档类型相关联的文档模板。 如果重写此函数，则可能应重写[OnInsertMenus](#oninsertmenus)和[OnSetMenu](#onsetmenu)以及。 这是一个高级可重写。  
  
 在子菜单`pMenuShared`如果服务器已反复调用都可以由多个复合菜单共同`OnInsertMenus`。 因此不应删除任何子菜单中的重写`OnRemoveMenus`; 应仅分离它们。  
  
 有关详细信息，请参阅[IOleInPlaceFrame::RemoveMenus](http://msdn.microsoft.com/library/windows/desktop/ms688685)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonscrollbya--coleclientitemonscrollby"></a><a name="onscrollby"></a>COleClientItem::OnScrollBy  
 由框架滚动 OLE 项以响应从服务器请求调用。  
  
```  
virtual BOOL OnScrollBy(CSize sizeExtent);
```  
  
### <a name="parameters"></a>参数  
 *sizeExtent*  
 指定的距离，以像素为单位，在进行滚动的 x 和 y 方向。  
  
### <a name="return-value"></a>返回值  
 非零，如果项滚动区;如果项可能不滚动区为 0。  
  
### <a name="remarks"></a>备注  
 例如，如果 OLE 项显示了一部分，并且用户将鼠标移在可视区域以外执行就地编辑时，此函数调用保持游标可见。 默认实现不执行任何操作。 重写此函数可将该项滚按指定的量。 请注意由于滚动，可以更改 OLE 项的可见部分。 调用[SetItemRects](#setitemrects)更新项的可见矩形。  
  
 有关详细信息，请参阅[IOleInPlaceSite::Scroll](http://msdn.microsoft.com/library/windows/desktop/ms690291)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonsetmenua--coleclientitemonsetmenu"></a><a name="onsetmenu"></a>COleClientItem::OnSetMenu  
 由框架调用两次时就地激活的开始和结束;第一次安装复合菜单和第二次 (与`holemenu`等于**NULL**) 将其删除。  
  
```  
virtual void OnSetMenu(
    CMenu* pMenuShared,  
    HOLEMENU holemenu,  
    HWND hwndActiveObject);
```  
  
### <a name="parameters"></a>参数  
 `pMenuShared`  
 通过调用构造复合菜单上的指向[OnInsertMenus](#oninsertmenus)成员函数和`InsertMenu`函数。  
  
 `holemenu`  
 返回菜单描述符句柄**OleCreateMenuDescriptor**函数，或**NULL**调度代码是否要删除。  
  
 *hwndActiveObject*  
 OLE 项的编辑窗口的句柄。 这是将接收来自 OLE 的编辑命令窗口。  
  
### <a name="remarks"></a>备注  
 默认实现将安装或删除复合菜单，然后调用[OleSetMenuDescriptor](http://msdn.microsoft.com/library/windows/desktop/ms692831)函数来安装或删除调度代码。 如果默认实现不适合于您的应用程序，重写此函数。 如果重写此函数，则可能应重写[OnInsertMenus](#oninsertmenus)和[OnRemoveMenus](#onremovemenus)以及。 这是一个高级可重写。  
  
 有关详细信息，请参阅[OleCreateMenuDescriptor](http://msdn.microsoft.com/library/windows/desktop/ms691415)， [OleSetMenuDescriptor](http://msdn.microsoft.com/library/windows/desktop/ms692831)，和[ioleinplaceframe:: Setmenu](http://msdn.microsoft.com/library/windows/desktop/ms693713)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonshowcontrolbarsa--coleclientitemonshowcontrolbars"></a><a name="onshowcontrolbars"></a>COleClientItem::OnShowControlBars  
 由框架来显示和隐藏容器应用程序的控件条调用。  
  
```  
virtual BOOL OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 `pFrameWnd`  
 到容器应用程序的框架窗口的指针。 这可以是主框架窗口或 MDI 子窗口。  
  
 `bShow`  
 指定控件条是显示还是隐藏。  
  
### <a name="return-value"></a>返回值  
 非零，如果函数调用中的控制条的状态，则将导致更改0 如果该调用会导致不改变，或者如果`pFrameWnd`不指向容器的框架窗口。  
  
### <a name="remarks"></a>备注  
 如果控件条已处于指定状态，此函数将返回 0 *bShow。* 出现这种，例如，如果隐藏的控件条和`bShow`是**FALSE**。  
  
 默认实现从顶级框架窗口中移除工具栏。  
  
##  <a name="a-nameonshowitema--coleclientitemonshowitem"></a><a name="onshowitem"></a>COleClientItem::OnShowItem  
 调用由框架以显示 OLE 项目，使其编辑过程中完全可见。  
  
```  
virtual void OnShowItem();
```  
  
### <a name="remarks"></a>备注  
 当容器应用程序支持链接到嵌入项时，使用 (也就是说，如果有派生文档类从[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md))。 就地激活或当 OLE 项是链接源时，用户想要对其进行编辑期间调用此函数。 默认实现将激活在容器文档的第一个视图。 重写此函数可滚动文档，以便 OLE 项可见。  
  
##  <a name="a-nameonupdateframetitlea--coleclientitemonupdateframetitle"></a><a name="onupdateframetitle"></a>COleClientItem::OnUpdateFrameTitle  
 由框架调用期间在就地激活更新框架窗口的标题栏。  
  
```  
virtual BOOL OnUpdateFrameTitle();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果此函数已成功更新的框架标题，否则为零。  
  
### <a name="remarks"></a>备注  
 默认实现不会更改框架窗口标题。 重写此函数，如果您需要不同的帧标题应用程序，例如"*服务器应用程序* - *项*中*docname*"（如下所示，"Microsoft Excel 的报表中的电子表格。文档"）。 这是一个高级可重写。  
  
##  <a name="a-namereactivateandundoa--coleclientitemreactivateandundo"></a><a name="reactivateandundo"></a>COleClientItem::ReactivateAndUndo  
 调用此函数以重新激活 OLE 项并撤消上一期间进行就地编辑由用户执行的操作。  
  
```  
BOOL ReactivateAndUndo();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序支持撤消命令，如果用户选择撤消命令在停用 OLE 项后立即调用此函数。  
  
 如果服务器应用程序与 Microsoft 基础类库编写的此函数会导致服务器调用[COleServerDoc::OnReactivateAndUndo](../../mfc/reference/coleserverdoc-class.md#onreactivateandundo)。  
  
 有关详细信息，请参阅[IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namereleasea--coleclientitemrelease"></a><a name="release"></a>COleClientItem::Release  
 调用此函数来清理资源使用的 OLE 项。  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>参数  
 `dwCloseOption`  
 用于指定在什么情况下，向加载状态返回时已保存该 OLE 项的标志。 有关可能的值的列表，请参阅[COleClientItem::Close](#close)。  
  
### <a name="remarks"></a>备注  
 **版本**由调用`COleClientItem`析构函数。  
  
 有关详细信息，请参阅[iunknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namereloada--coleclientitemreload"></a><a name="reload"></a>COleClientItem::Reload  
 关闭然后重新加载该项目。  
  
```  
BOOL Reload();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 调用`Reload`函数之后，通过调用作为另一种类型的项激活项[ActivateAs](#activateas)。  
  
##  <a name="a-nameruna--coleclientitemrun"></a><a name="run"></a>COleClientItem::Run  
 运行此项目关联的应用程序。  
  
```  
void Run();
```  
  
### <a name="remarks"></a>备注  
 调用**运行**成员函数以启动服务器应用程序，然后激活该项目。 这就会自动完成[激活](#activate)和[DoVerb](#doverb)，因此通常需要调用此函数。 调用此函数，如有必要运行服务器，以便设置项属性，如[SetExtent](#setextent)，在执行前[DoVerb](#doverb)。  
  
##  <a name="a-namesetdrawaspecta--coleclientitemsetdrawaspect"></a><a name="setdrawaspect"></a>COleClientItem::SetDrawAspect  
 调用`SetDrawAspect`成员函数以将设置为"方面"或视图的项。  
  
```  
virtual void SetDrawAspect(DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>参数  
 `nDrawAspect`  
 `DVASPECT` 枚举中的一个值。 此参数可以具有下列值之一：  
  
- `DVASPECT_CONTENT`项可以显示为嵌入对象到其容器内的方式表示。  
  
- `DVASPECT_THUMBNAIL`项将呈现在"thumbnail"表示形式，以便它可以显示在浏览工具。  
  
- `DVASPECT_ICON`项由一个图标来表示。  
  
- `DVASPECT_DOCPRINT`就像它已打印使用打印命令从文件菜单项表示。  
  
### <a name="remarks"></a>备注  
 该方面指定如何对项目进行呈现的[绘制](#draw)时的默认值为该函数的`nDrawAspect`参数才有用。  
  
 通过更改图标 （和其他直接调用更改图标对话框中的对话框） 自动调用此函数以便在用户请求时的图标显示方面。  
  
##  <a name="a-namesetextenta--coleclientitemsetextent"></a><a name="setextent"></a>COleClientItem::SetExtent  
 调用此函数可指定多少空间可供 OLE 项。  
  
```  
void SetExtent(
    const CSize& size,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，其中包含大小信息。  
  
 `nDrawAspect`  
 指定其边界是将 OLE 项的方面。 有关可能的值，请参阅[SetDrawAspect](#setdrawaspect)。  
  
### <a name="remarks"></a>备注  
 如果服务器应用程序使用 Microsoft 基础类库编写的这将导致[OnSetExtent](../../mfc/reference/coleserveritem-class.md#onsetextent)相应成员函数`COleServerItem`要调用的对象。 OLE 项然后可以相应调整其显示。 维度都必须是在`MM_HIMETRIC`单位。 当用户调整 OLE 项或支持某种形式的布局协商，则调用此函数。  
  
 有关详细信息，请参阅[IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesethostnamesa--coleclientitemsethostnames"></a><a name="sethostnames"></a>COleClientItem::SetHostNames  
 调用此函数可指定的容器应用程序的名称和嵌入 OLE 项的容器的名称。  
  
```  
void SetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>参数  
 `lpszHost`  
 为容器应用程序的用户可见名称的指针。  
  
 `lpszHostObj`  
 指向包含 OLE 项的容器的标识字符串的指针。  
  
### <a name="remarks"></a>备注  
 如果服务器应用程序使用 Microsoft 基础类库编写的此函数将调用[OnSetHostNames](../../mfc/reference/coleserverdoc-class.md#onsethostnames)成员函数`COleServerDoc`文档，其中包含 OLE 项。 在编辑 OLE 项时，将在窗口标题中使用此信息。 每次加载容器文档时，框架在文档中的所有 OLE 项都调用此函数。 `SetHostNames`功能仅适用于嵌入的项。 不需要调用此函数每次激活嵌入的 OLE 项以进行编辑。  
  
 这也称为自动具有应用程序名称和文档的名称或使用其他名称保存文件时加载对象。 因此，不直接调用此函数通常都有必要。  
  
 有关详细信息，请参阅[IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameseticonicmetafilea--coleclientitemseticonicmetafile"></a><a name="seticonicmetafile"></a>COleClientItem::SetIconicMetafile  
 将缓存用于绘制项的图标的图元文件。  
  
```  
BOOL SetIconicMetafile(HGLOBAL hMetaPict);
```  
  
### <a name="parameters"></a>参数  
 `hMetaPict`  
 用于绘制项的图标的图元文件句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用[GetIconicMetafile](#geticonicmetafile)来检索图元文件。  
  
 `hMetaPict`参数复制到该项目中; 因此，`hMetaPict`必须由调用方释放。  
  
##  <a name="a-namesetitemrectsa--coleclientitemsetitemrects"></a><a name="setitemrects"></a>COleClientItem::SetItemRects  
 调用此函数可设置的边框或 OLE 项的可见矩形。  
  
```  
BOOL SetItemRects(
    LPCRECT lpPosRect = NULL,  
    LPCRECT lpClipRect = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lprcPosRect*  
 指向包含相对于其父窗口，工作区坐标中的 OLE 项的边界的矩形的指针。  
  
 *lprcClipRect*  
 指向包含相对于其父窗口，工作区坐标中的 OLE 项的可见部分的边界的矩形的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现调用此函数[OnChangeItemPosition](#onchangeitemposition)成员函数。 每当的位置或可见部分 OLE 项的更改时，应调用此函数。 通常，这意味着您的视图从调用它[OnSize](../../mfc/reference/cwnd-class.md#onsize)和[OnScrollBy](../../mfc/reference/cview-class.md#onscrollby)成员函数。  
  
 有关详细信息，请参阅[IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetlinkupdateoptionsa--coleclientitemsetlinkupdateoptions"></a><a name="setlinkupdateoptions"></a>COleClientItem::SetLinkUpdateOptions  
 调用此函数可设置指定的链接项的演示文稿的链接更新选项。  
  
```  
void SetLinkUpdateOptions(OLEUPDATE dwUpdateOpt);
```  
  
### <a name="parameters"></a>参数  
 *dwUpdateOpt*  
 此项的链接更新选项的值。 此值必须是以下项之一︰  
  
- `OLEUPDATE_ALWAYS`更新链接的项只要有可能。 在链接对话框中，此选项支持自动链接更新单选按钮。  
  
- `OLEUPDATE_ONCALL`更新仅根据请求从容器应用程序的链接的项 (当[UpdateLink](#updatelink)调用成员函数)。 在链接对话框中，此选项支持手动链接更新单选按钮。  
  
### <a name="remarks"></a>备注  
 通常情况下，不应更改由用户在链接对话框中选择的更新选项。  
  
 有关详细信息，请参阅[IOleLink::SetUpdateOptions](http://msdn.microsoft.com/library/windows/desktop/ms680120)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetprintdevicea--coleclientitemsetprintdevice"></a><a name="setprintdevice"></a>COleClientItem::SetPrintDevice  
 调用此函数可更改此项的打印目标设备。  
  
```  
BOOL SetPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL SetPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>参数  
 `ptd`  
 指向[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)数据结构，其中包含有关新的打印目标设备的信息。 可以是**NULL**。  
  
 `ppd`  
 指向[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646940)数据结构，其中包含有关新的打印目标设备的信息。 可以是**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数更新该项目的打印目标设备，而不会刷新的演示文稿缓存。 若要更新某个项的演示文稿缓存，请调用[UpdateLink](#updatelink)。  
  
 对此函数的参数包含 OLE 系统用以标识目标设备的信息。 **PRINTDLG**结构包含 Windows 用来初始化常见打印对话框中的信息。 用户关闭对话框后，Windows 将在此结构中返回有关用户的选择信息。 `m_pd`的成员[CPrintDialog](../../mfc/reference/cprintdialog-class.md)对象是**PRINTDLG**结构。  
  
 有关此结构的详细信息，请参阅[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameupdatelinka--coleclientitemupdatelink"></a><a name="updatelink"></a>COleClientItem::UpdateLink  
 调用此函数可立即更新 OLE 项的演示文稿数据。  
  
```  
BOOL UpdateLink();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 对于链接项，该函数查找链接源以获取新的演示文稿的 OLE 项。 此过程可能需要运行一个或多个服务器应用程序，这可能需要很长时间。 对于嵌入项，函数进行操作以递归方式检查嵌入的项是否包含可能已过期的链接和对它们进行更新。 用户还可以手动更新使用链接对话框中的单个链接。  
  
 有关详细信息，请参阅[IOleLink::Update](http://msdn.microsoft.com/library/windows/desktop/ms692660)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 MFCBIND](../../visual-cpp-samples.md)   
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [CDocItem 类](../../mfc/reference/cdocitem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleServerItem 类](../../mfc/reference/coleserveritem-class.md)

