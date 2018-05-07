---
title: COleServerItem 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
dev_langs:
- C++
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d3165a11aace54ce2062a6321acc7f911fbdc39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="coleserveritem-class"></a>COleServerItem 类
提供 OLE 项的服务器接口。  
  
## <a name="syntax"></a>语法  
  
```  
class COleServerItem : public CDocItem  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleServerItem::COleServerItem](#coleserveritem)|构造 `COleServerItem` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|将放置演示文稿和转换中的格式`COleDataSource`对象。|  
|[COleServerItem::CopyToClipboard](#copytoclipboard)|将该项目复制到剪贴板。|  
|[COleServerItem::DoDragDrop](#dodragdrop)|执行拖放操作。|  
|[COleServerItem::GetClipboardData](#getclipboarddata)|获取在数据传输 （拖放或剪贴板） 中使用的数据源。|  
|[COleServerItem::GetDocument](#getdocument)|返回包含项的服务器文档。|  
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|获取**CF_EMBEDSOURCE** OLE 项的数据。|  
|[COleServerItem::GetItemName](#getitemname)|返回项的名称。 用于链接的项。|  
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|获取`CF_LINKSOURCE`OLE 项的数据。|  
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|获取**CF_OBJECTDESCRIPTOR** OLE 项的数据。|  
|[COleServerItem::IsConnected](#isconnected)|指示项当前是否附加到活动的容器。|  
|[COleServerItem::IsLinkedItem](#islinkeditem)|指示项是否表示链接的 OLE 项。|  
|[COleServerItem::NotifyChanged](#notifychanged)|使用自动链接更新来更新所有容器。|  
|[COleServerItem::OnDoVerb](#ondoverb)|调用以执行谓词。|  
|[Coleserveritem:: Ondraw](#ondraw)|当绘制项; 容器请求时调用所需的实现。|  
|[COleServerItem::OnDrawEx](#ondrawex)|为专用的项绘图调用。|  
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|由框架调用以获取的数据，都要复制到剪贴板。|  
|[COleServerItem::OnGetExtent](#ongetextent)|由框架调用以检索 OLE 项的大小。|  
|[COleServerItem::OnInitFromData](#oninitfromdata)|由框架调用以初始化使用指定的数据传输对象的内容的 OLE 项。|  
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|调用以确定任何链接的项是否需要更新。|  
|[COleServerItem::OnRenderData](#onrenderdata)|检索属于延迟呈现的数据。|  
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|检索到的数据`CFile`延迟呈现的一部分的对象。|  
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|检索到的数据`HGLOBAL`延迟呈现的一部分。|  
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|调用来设置项的配色方案。|  
|[COleServerItem::OnSetData](#onsetdata)|调用来设置项的数据。|  
|[COleServerItem::OnSetExtent](#onsetextent)|由框架调用以将 OLE 项的大小设置。|  
|[COleServerItem::OnUpdate](#onupdate)|调用文档项的某些部分位于会更改。|  
|[COleServerItem::OnUpdateItems](#onupdateitems)|调用以更新演示文稿缓存服务器文档中的所有项。|  
|[COleServerItem::SetItemName](#setitemname)|设置项的名称。 用于链接的项。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](#getdatasource)|获取用于存储转换格式的对象。|  
|[COleServerItem::OnHide](#onhide)|由框架调用以隐藏 OLE 项。|  
|[COleServerItem::OnOpen](#onopen)|由框架调用以在其自己的顶级窗口中显示的 OLE 项。|  
|[COleServerItem::OnShow](#onshow)|当容器请求表示显示该项时调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[COleServerItem::m_sizeExtent](#m_sizeextent)|有关可见 OLE 项中有多少是通知服务器。|  
  
## <a name="remarks"></a>备注  
 链接的项可以表示某些或所有的服务器文档。 嵌入的项始终表示整个服务器文档。  
  
 `COleServerItem`类定义由 OLE 系统动态链接库 (Dll)，调用的若干可重写成员函数通常从容器应用程序响应请求。 这些成员函数允许容器应用程序操作项间接以多种方式，如： 显示它，执行其谓词，或者检索各种格式其数据。  
  
 若要使用`COleServerItem`、 从其派生一个类和实现[OnDraw](#ondraw)和[序列化](../../mfc/reference/cobject-class.md#serialize)成员函数。 `OnDraw`函数提供了某一项，使其容器应用程序打开复合文档时要显示的图元文件表示。 `Serialize`函数`CObject`提供的本机表示形式的项，请允许嵌入的项可以在服务器和容器应用程序之间传递。 [OnGetExtent](#ongetextent)提供项的容器，启用要调整大小的项的容器的自然大小。  
  
 有关服务器和相关的主题的详细信息，请参阅文章[服务器： 实现服务器](../../mfc/servers-implementing-a-server.md)和"创建容器/服务器应用程序"文章中[容器： 高级功能](../../mfc/containers-advanced-features.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="addotherclipboarddata"></a>  COleServerItem::AddOtherClipboardData  
 调用此函数可将 OLE 项的演示文稿和转换格式放入指定`COleDataSource`对象。  
  
```  
void AddOtherClipboardData(COleDataSource* pDataSource);
```  
  
### <a name="parameters"></a>参数  
 `pDataSource`  
 指向`COleDataSource`中放置数据对象。  
  
### <a name="remarks"></a>备注  
 你必须已实现[OnDraw](#ondraw)成员函数，为项提供的演示文稿格式 （图元文件图）。 若要支持其他转换格式，注册它们使用[COleDataSource](../../mfc/reference/coledatasource-class.md)返回对象[GetDataSource](#getdatasource) ，并重写[OnRenderData](#onrenderdata)到成员函数提供你想要支持的格式中的数据。  
  
##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem  
 构造`COleServerItem`对象，并将其添加到的文档项的服务器文档的集合。  
  
```  
COleServerItem(
    COleServerDoc* pServerDoc,  
    BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>参数  
 `pServerDoc`  
 指向将包含新的项的文档的指针。  
  
 `bAutoDelete`  
 指示是否可以删除此对象，链接到该发布时的标志。 将其设置为**FALSE**如果`COleServerItem`对象是不可或缺的组成部分必须删除文档的数据。 将其设置为**TRUE**如果对象是用于标识可以由框架删除的文档的数据中的范围的辅助结构。  
  
##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard  
 调用此函数可将 OLE 项复制到剪贴板。  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bIncludeLink`  
 将其设置为**TRUE**如果链接数据应复制到剪贴板。 将其设置为**FALSE**如果服务器应用程序不支持链接。  
  
### <a name="remarks"></a>备注  
 该函数使用[OnGetClipboardData](#ongetclipboarddata)成员函数来创建[COleDataSource](../../mfc/reference/coledatasource-class.md)对象，其中包含支持的格式中的 OLE 项的数据。 该函数将`COleDataSource`上使用剪贴板对象[COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函数。 `COleDataSource`对象包括项的本机数据以及其表示形式`CF_METAFILEPICT`格式，以及你选择支持任何转换格式的数据。 你必须已实现[序列化](../../mfc/reference/cobject-class.md#serialize)和[OnDraw](#ondraw)有关此成员函数以工作。  
  
##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop  
 调用`DoDragDrop`成员函数执行拖放操作。  
  
```  
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,  
    CPoint ptOffset,  
    BOOL bIncludeLink = FALSE,  
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,  
    LPCRECT lpRectStartDrag = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lpRectItem*  
 在屏幕上，以像素为单位，相对于客户端区域的项的矩形。  
  
 `ptOffset`  
 从的偏移量`lpItemRect`在拖动时所在的鼠标位置。  
  
 `bIncludeLink`  
 将其设置为**TRUE**如果链接数据应复制到剪贴板。 将其设置为**FALSE**如果你的应用程序不支持链接。  
  
 `dwEffects`  
 确定在拖动操作 （复制、 移动和链接的组合） 中将允许拖动源的效果。  
  
 `lpRectStartDrag`  
 指向定义拖动实际开始的矩形的指针。 有关更多信息，请参见下面的“备注”部分。  
  
### <a name="return-value"></a>返回值  
 `DROPEFFECT` 枚举中的一个值。 如果它是`DROPEFFECT_MOVE`，则应删除原始数据。  
  
### <a name="remarks"></a>备注  
 拖放操作不会立即开始。 它等待，直到鼠标光标离开由指定的矩形`lpRectStartDrag`或之前已通过指定的毫秒数。 如果`lpRectStartDrag`是**NULL**，使用默认矩形，以便当鼠标光标移动一个像素时，拖动启动。  
  
 注册表项设置由指定的延迟时间。 你可以通过调用来更改的延迟时间[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果未指定的延迟时间，使用默认值为 200 毫秒。 拖动延迟时间存储中，如下所示：  
  
-   Windows NT 拖延迟时间将存储在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Windows 3.x 拖延迟时间将存储在 WIN。INI 文件，[Windows} 部分。  
  
-   Windows 95/98 拖延迟时间将存储在 WIN 的缓存版本。INI。  
  
 有关深入了解如何拖动延迟信息存储在任一注册表或。INI 文件，请参阅[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) Windows SDK 中。  
  
##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData  
 调用此函数可填充指定[COleDataSource](../../mfc/reference/coledatasource-class.md)对象将复制到剪贴板中，如果调用的所有数据[CopyToClipboard](#copytoclipboard) (将还传输相同的数据，如果你调用[DoDragDrop](#dodragdrop))。  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDataSource`  
 指向`COleDataSource`将接收 OLE 项的数据的所有支持的格式中的对象。  
  
 `bIncludeLink`  
 **TRUE**如果链接数据应复制到剪贴板。 **FALSE**如果服务器应用程序不支持链接。  
  
 `lpOffset`  
 偏移量，以像素为单位，鼠标光标从该对象的原点。  
  
 `lpSize`  
 以像素为单位的对象的大小。  
  
### <a name="remarks"></a>备注  
 此函数将调用[GetEmbedSourceData](#getembedsourcedata)成员函数，若要获取的 OLE 项和调用的本机数据[AddOtherClipboardData](#addotherclipboarddata)成员函数来获取演示文稿格式和任何支持的转换格式。 如果`bIncludeLink`是**TRUE**，函数还调用[GetLinkSourceData](#getlinksourcedata)以获得该项的链接数据。  
  
 重写此函数，如果你想要置于格式`COleDataSource`对象之前或之后提供的这些格式`CopyToClipboard`。  
  
##  <a name="getdatasource"></a>  COleServerItem::GetDataSource  
 调用此函数可获取[COleDataSource](../../mfc/reference/coledatasource-class.md)用来存储服务器应用程序支持的转换格式的对象。  
  
```  
COleDataSource* GetDataSource();
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`COleDataSource`用于存储转换格式的对象。  
  
### <a name="remarks"></a>备注  
 如果你想服务器应用程序提供各种格式的数据在数据传输操作，注册与这些格式`COleDataSource`此函数返回的对象。 例如，如果你想要提供**CF_TEXT** OLE 项的剪贴板或拖放操作的表示形式，将注册与格式`COleDataSource`此函数返回时，对象，然后替代**OnRenderXxxData**成员函数以提供的数据。  
  
##  <a name="getdocument"></a>  COleServerItem::GetDocument  
 调用此函数可获取指向包含项的文档的指针。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向包含的项; 文档的指针**NULL**如果该项不是文档的一部分。  
  
### <a name="remarks"></a>备注  
 这将允许到作为参数传递的服务器文档的访问`COleServerItem`构造函数。  
  
##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData  
 调用此函数可获取**CF_EMBEDSOURCE** OLE 项的数据。  
  
```  
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构，它将接收**CF_EMBEDSOURCE** OLE 项的数据。  
  
### <a name="remarks"></a>备注  
 此格式包含项的本机数据。 你必须已实现`Serialize`成员函数，此函数可正常工作。  
  
 结果可以然后添加到数据源使用[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 自动调用此函数[COleServerItem::OnGetClipboardData](#ongetclipboarddata)。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中。  
  
##  <a name="getitemname"></a>  COleServerItem::GetItemName  
 调用此函数可获取项的名称。  
  
```  
const CString& GetItemName() const;  
```  
  
### <a name="return-value"></a>返回值  
 项的名称。  
  
### <a name="remarks"></a>备注  
 通常仅为链接的项调用此函数。  
  
##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData  
 调用此函数可获取`CF_LINKSOURCE`OLE 项的数据。  
  
```  
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构，它将接收`CF_LINKSOURCE`OLE 项的数据。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此格式包含描述的 OLE 项和定位包含 OLE 项的文档所需的信息类型的 CLSID。  
  
 随后可将结果添加到数据源与[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 自动调用此函数[OnGetClipboardData](#ongetclipboarddata)。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中。  
  
##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData  
 调用此函数可获取**CF_OBJECTDESCRIPTOR** OLE 项的数据。  
  
```  
void GetObjectDescriptorData(
    LPPOINT lpOffset,  
    LPSIZE lpSize,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 `lpOffset`  
 鼠标单击从 OLE 项的左上角的偏移量。 可以是**NULL**。  
  
 `lpSize`  
 OLE 项的大小。 可以是**NULL**。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构，它将接收**CF_OBJECTDESCRIPTOR** OLE 项的数据。  
  
### <a name="remarks"></a>备注  
 将信息复制到**STGMEDIUM**指向结构`lpStgMedium`。 此格式包括选择性粘贴对话框中所需的信息。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中。  
  
##  <a name="isconnected"></a>  COleServerItem::IsConnected  
 调用此函数，以查看是否已连接的 OLE 项。  
  
```  
BOOL IsConnected() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果项连接; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 OLE 项被视为连接如果一个或多个容器具有对项的引用。 如果引用计数大于 0，或如果它是嵌入的项目，项会连接。  
  
##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem  
 调用此函数可查看 OLE 项是否链接的项。  
  
```  
BOOL IsLinkedItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该项是链接的项; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 项已链接项有效，并且不返回的嵌入项的文档的列表中。 链接的项可能或可能未连接到容器。  
  
 很普遍使用的链接和嵌入项的同一个类。 `IsLinkedItem` 让你可以链接的项的行为不同嵌入项，尽管次数多的代码是很常见。  
  
##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent  
 此成员告知服务器多少对象是在容器文档中可见。  
  
```  
CSize m_sizeExtent;  
```  
  
### <a name="remarks"></a>备注  
 默认实现[OnSetExtent](#onsetextent)设置此成员。  
  
##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged  
 更改链接的项后，请调用此函数。  
  
```  
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>参数  
 `nDrawAspect`  
 取值范围为`DVASPECT`枚举，指示已更改的 OLE 项的方面。 此参数可以具有任何以下值：  
  
- `DVASPECT_CONTENT` 项可以显示作为嵌入到其容器内的对象的方式表示。  
  
- `DVASPECT_THUMBNAIL` 项将呈现在"缩略图"表示形式，以便它可以在浏览工具中显示。  
  
- `DVASPECT_ICON` 项由一个图标表示。  
  
- `DVASPECT_DOCPRINT` 就像它已使用文件菜单中的打印命令来打印表示项。  
  
### <a name="remarks"></a>备注  
 如果通过自动链接情况下，容器项链接到文档，更新项目以反映所做的更改。 编写使用 Microsoft 基础类库的容器应用程序中[COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange)在响应中调用。  
  
##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb  
 由框架调用以执行指定的动词。  
  
```  
virtual void OnDoVerb(LONG iVerb);
```  
  
### <a name="parameters"></a>参数  
 `iVerb`  
 指定要执行的谓词。 它可以是以下之一：  
  
|值|含义|符号|  
|-----------|-------------|------------|  
|0|主谓词|`OLEIVERB_PRIMARY`|  
|1|辅助谓词|（无）|  
|- 1|显示用于编辑的项|`OLEIVERB_SHOW`|  
|- 2|在单独的窗口中编辑项目|`OLEIVERB_OPEN`|  
|- 3|隐藏项|`OLEIVERB_HIDE`|  
  
 为-1 值通常是另一个谓词的别名。 如果不支持打开编辑，-2 将具有相同的效果-1。 其他值，请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 如果使用 Microsoft 基础类库在撰写容器应用程序时，此函数调用时[COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate)相应的成员函数`COleClientItem`调用对象。 默认实现调用[OnShow](#onshow)成员函数，如果主谓词或`OLEIVERB_SHOW`指定，则[OnOpen](#onopen)如果辅助谓词或`OLEIVERB_OPEN`指定，则和[OnHide](#onhide)如果`OLEIVERB_HIDE`指定。 默认实现调用`OnShow`如果`iVerb`不是上面列出的谓词之一。  
  
 如果主谓词未显示项，重写此函数。 例如，如果项是录音，其主谓词为播放，则你将不需要显示要播放的项的服务器应用程序。  
  
 有关详细信息，请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
##  <a name="ondraw"></a>  Coleserveritem:: Ondraw  
 由框架调用，以将 OLE 项呈现到 metafile 中。  
  
```  
virtual BOOL OnDraw(
    CDC* pDC,  
    CSize& rSize) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向的指针[CDC](../../mfc/reference/cdc-class.md)在其上绘制项的对象。 显示上下文自动连接到的属性显示上下文因此您可以调用属性函数，虽然这样会导致图元文件特定于设备的。  
  
 `rSize`  
 调整大小，请在**HIMETRIC**单位，在其中进行绘制图元文件。  
  
### <a name="return-value"></a>返回值  
 如果成功绘制项; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 OLE 项的图元文件表示用于在容器应用程序中显示的项。 如果使用 Microsoft 基础类库在撰写容器应用程序时，通过使用图元文件[绘制](../../mfc/reference/coleclientitem-class.md#draw)相应的成员函数[COleClientItem](../../mfc/reference/coleclientitem-class.md)对象。 没有默认实现。 你必须重写此函数可绘制到指定的设备上下文的项。  
  
##  <a name="ondrawex"></a>  COleServerItem::OnDrawEx  
 由框架，用于所有绘图调用。  
  
```  
virtual BOOL OnDrawEx(
    CDC* pDC,  
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向的指针[CDC](../../mfc/reference/cdc-class.md)在其上绘制项的对象。 DC 自动连接到特性 DC 因此您可以调用属性函数，虽然这样会导致图元文件特定于设备的。  
  
 `nDrawAspect`  
 `DVASPECT` 枚举中的一个值。 此参数可以具有任何以下值：  
  
- `DVASPECT_CONTENT` 项可以显示作为嵌入到其容器内的对象的方式表示。  
  
- `DVASPECT_THUMBNAIL` 项将呈现在"缩略图"表示形式，以便它可以在浏览工具中显示。  
  
- `DVASPECT_ICON` 项由一个图标表示。  
  
- `DVASPECT_DOCPRINT` 就像它已使用文件菜单中的打印命令来打印表示项。  
  
 `rSize`  
 中的项的大小**HIMETRIC**单位。  
  
### <a name="return-value"></a>返回值  
 如果成功绘制项; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现调用`OnDraw`时`DVASPECT`等同于`DVASPECT_CONTENT`; 否则它将失败。  
  
 重写此函数而不提供方面的演示文稿数据`DVASPECT_CONTENT`，如`DVASPECT_ICON`或`DVASPECT_THUMBNAIL`。  
  
##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData  
 由框架来获取调用`COleDataSource`对象，其中包含通过调用将可放置在剪贴板的所有数据[CopyToClipboard](#copytoclipboard)成员函数。  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>参数  
 `bIncludeLink`  
 将其设置为**TRUE**如果链接数据应复制到剪贴板。 将其设置为**FALSE**如果服务器应用程序不支持链接。  
  
 `lpOffset`  
 以像素为单位的对象从源鼠标光标的偏移量。  
  
 `lpSize`  
 以像素为单位的对象的大小。  
  
### <a name="return-value"></a>返回值  
 指向的指针[COleDataSource](../../mfc/reference/coledatasource-class.md)包含剪贴板数据对象。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[GetClipboardData](#getclipboarddata)。  
  
##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent  
 由框架中检索的大小，调用**HIMETRIC**单位 OLE 项。  
  
```  
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>参数  
 `nDrawAspect`  
 指定要检索其边界的 OLE 项的方面。 此参数可以具有任何以下值：  
  
- `DVASPECT_CONTENT` 项可以显示作为嵌入到其容器内的对象的方式表示。  
  
- `DVASPECT_THUMBNAIL` 项将呈现在"缩略图"表示形式，以便它可以在浏览工具中显示。  
  
- `DVASPECT_ICON` 项由一个图标表示。  
  
- `DVASPECT_DOCPRINT` 就像它已使用文件菜单中的打印命令来打印表示项。  
  
 `rSize`  
 引用`CSize`将接收 OLE 项的大小的对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果使用 Microsoft 基础类库在撰写容器应用程序时，此函数调用时[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)相应的成员函数`COleClientItem`调用对象。 默认实现不执行任何操作。 你必须自己实现它。 如果你想要执行特殊处理，处理 OLE 项的大小的请求时，重写此函数。  
  
##  <a name="onhide"></a>  COleServerItem::OnHide  
 由框架调用以隐藏 OLE 项。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>备注  
 默认调用**COleServerDoc::OnShowDocument (FALSE)**。 此外，该函数会通知容器 OLE 项已被隐藏。 如果你想要隐藏 OLE 项时执行特殊处理，重写此函数。  
  
##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData  
 由框架初始化 OLE 项使用的内容调用`pDataObject`。  
  
```  
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,  
    BOOL bCreation);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向一个包含用于初始化 OLE 项的各种格式的数据的 OLE 数据对象的指针。  
  
 `bCreation`  
 **TRUE**如果该函数调用以初始化新的容器应用程序创建一个 OLE 项。 **FALSE**如果调用该函数替换现有 OLE 项的内容。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`bCreation`是**TRUE**，如果容器实现基于当前所选内容的插入的新对象调用此函数。 创建新的 OLE 项时，使用所选的数据。 例如，当在电子表格程序中选择的一个单元范围，然后使用插入的新对象来创建一个图表基于所选范围中的值。 默认实现不执行任何操作。 重写此函数可从所提供的选择可接受的格式`pDataObject`和初始化 OLE 项基于提供的数据。 这是一个高级可重写。  
  
 有关详细信息，请参阅[IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) Windows SDK 中。  
  
##  <a name="onopen"></a>  COleServerItem::OnOpen  
 由框架调用以在单独的实例的服务器应用程序，而不是就地显示 OLE 项。  
  
```  
virtual void OnOpen();
```  
  
### <a name="remarks"></a>备注  
 默认实现激活显示包含 OLE 项; 文档的第一个框架窗口如果应用程序是最小化服务器，默认实现将显示主窗口。 此外，该函数会通知该容器已打开的 OLE 项。  
  
 如果你想要执行特殊处理，打开一个 OLE 项时，重写此函数。 这是与你想要打开时将它链接到设置所选内容的链接项尤其容易。  
  
 有关详细信息，请参阅[IOleClientSite::OnShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms688658) Windows SDK 中。  
  
##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems  
 由框架调用以确定当前的服务器文档中的任何链接的项是否为已过期。  
  
```  
virtual BOOL OnQueryUpdateItems();
```  
  
### <a name="return-value"></a>返回值  
 如果文档没有项需要更新; 则为非 0如果所有项都是最新，则为 0。  
  
### <a name="remarks"></a>备注  
 如果已更改其源文档，但链接的项未更新以反映文档中的更改，项已过期。  
  
##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData  
 由框架调用以检索指定的格式中的数据。  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定在其中请求信息的格式。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)是用要返回的数据的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是以前放置在`COleDataSource`对象使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)延迟呈现的成员函数。 此函数的默认实现调用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)分别，如果提供的存储介质是文件或内存。 如果任一这些格式提供，默认实现将返回 0，且不执行任何操作。  
  
 如果`lpStgMedium` ->  *tymed*是**TYMED_NULL**、 **STGMEDIUM**应分配和指定的填充*lpFormatEtc->tymed*。 如果不是**TYMED_NULL**、 **STGMEDIUM**应填充了具有数据的位置。  
  
 这是一个高级可重写。 重写此函数可提供的请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你的数据较小，而且固定大小，重写`OnRenderGlobalData`。 如果你的数据是在文件中，或者是大小可变的重写`OnRenderFileData`。  
  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)， [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，和[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) Windows SDK 中。  
  
##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData  
 由框架调用以检索指定的格式中的数据，当存储媒体文件。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定在其中请求信息的格式。  
  
 `pFile`  
 指向`CFile`对象是用要呈现的数据。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是以前放置在`COleDataSource`对象使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延迟呈现的成员函数。 此函数的默认实现只返回**FALSE**。  
  
 这是一个高级可重写。 重写此函数可提供的请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你想要处理多个存储媒介，重写[OnRenderData](#onrenderdata)。 如果你的数据是在文件中，或者是大小可变的重写[OnRenderFileData](#onrenderfiledata)。  
  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData  
 由框架调用以检索指定的格式中的数据时指定的存储介质是全局内存。  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定在其中请求信息的格式。  
  
 `phGlobal`  
 指向全局内存在其中的数据是要返回的句柄。 如果已不分配任何内存，此参数可以为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是以前放置在`COleDataSource`对象使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延迟呈现的成员函数。 此函数的默认实现只返回**FALSE**。  
  
 如果`phGlobal`是**NULL**，然后新`HGLOBAL`应分配，并且在返回`phGlobal`。 否则为`HGLOBAL`指定的`phGlobal`应已填满数据。 数据量置于`HGLOBAL`不能超过内存块的当前大小。 此外，块不能重新分配给了更大的大小。  
  
 这是一个高级可重写。 重写此函数可提供的请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你想要处理多个存储媒介，重写[OnRenderData](#onrenderdata)。 如果你的数据是在文件中，或者是大小可变的重写[OnRenderFileData](#onrenderfiledata)。  
  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme  
 由框架调用以指定在编辑 OLE 项时要使用的颜色调色板。  
  
```  
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```  
  
### <a name="parameters"></a>参数  
 `lpLogPalette`  
 指向 Windows [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)结构。  
  
### <a name="return-value"></a>返回值  
 如果使用调色板; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 如果使用 Microsoft 基础类库编写容器应用程序，此函数调用时[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971)相应函数`COleClientItem`调用对象。 默认实现返回**FALSE**。 如果你想要使用建议的调色板，重写此函数。 服务器应用程序不需要使用建议的调色板。  
  
 有关详细信息，请参阅[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) Windows SDK 中。  
  
##  <a name="onsetdata"></a>  COleServerItem::OnSetData  
 由框架调用以将 OLE 项的数据替换为指定的数据。  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定的数据格式。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构中的数据位于其中。  
  
 `bRelease`  
 指示有完成函数调用后的存储介质的所有权。 调用方决定谁负责释放代表的存储介质分配的资源。 通过设置的调用方执行此`bRelease`。 如果`bRelease`为非零值，服务器项将获得所有权，释放该媒体，使用它完成。 当`bRelease`为 0，调用方保留所有权并且服务器项可以仅为在调用期间使用的存储介质。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它已成功获取它，服务器项才会对数据所有权。 也就是说，它将不会所有权如果它返回 0。 如果数据源将获得所有权，它通过调用释放的存储介质[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)函数。  
  
 默认实现不执行任何操作。 重写此函数可将 OLE 项的数据替换为指定的数据。 这是一个高级可重写。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，和[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) Windows SDK 中。  
  
##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent  
 由框架调用以通知 OLE 该项是容器文档中的可用空间量。  
  
```  
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,  
    const CSize& size);
```  
  
### <a name="parameters"></a>参数  
 `nDrawAspect`  
 指定其边界正在指定的 OLE 项的方面。 此参数可以具有任何以下值：  
  
- `DVASPECT_CONTENT` 项可以显示作为嵌入到其容器内的对象的方式表示。  
  
- `DVASPECT_THUMBNAIL` 项将呈现在"缩略图"表示形式，以便它可以在浏览工具中显示。  
  
- `DVASPECT_ICON` 项由一个图标表示。  
  
- `DVASPECT_DOCPRINT` 就像它已使用文件菜单中的打印命令来打印表示项。  
  
 `size`  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)结构，它指定的 OLE 项的新大小。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果使用 Microsoft 基础类库在撰写容器应用程序时，此函数调用时[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)相应的成员函数`COleClientItem`调用对象。 默认实现集[m_sizeExtent](#m_sizeextent)为指定大小的成员如果`nDrawAspect`是`DVASPECT_CONTENT`; 否则它将返回 0。 重写此函数以执行特殊处理，当你更改的项的大小。  
  
##  <a name="onshow"></a>  COleServerItem::OnShow  
 由框架调用以指示服务器应用程序，以就地显示 OLE 项。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>备注  
 此函数通常称为容器应用程序的用户创建一项或执行动词，如编辑、 时要求要显示的项。 默认实现尝试就地激活。 如果此操作失败，此函数调用`OnOpen`成员函数在单独的窗口中显示的 OLE 项。  
  
 如果你想要执行特殊处理，显示一个 OLE 项时，重写此函数。  
  
##  <a name="onupdate"></a>  COleServerItem::OnUpdate  
 当修改的项时，由框架调用。  
  
```  
virtual void OnUpdate(
    COleServerItem* pSender,  
    LPARAM lHint,  
    CObject* pHint,  
    DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>参数  
 `pSender`  
 为修改文档的项的指针。 可以是**NULL**。  
  
 `lHint`  
 包含有关修改信息。  
  
 `pHint`  
 指针指向存储有关修改信息的对象。  
  
 `nDrawAspect`  
 `DVASPECT` 枚举中的一个值。 此参数可以具有以下值之一：  
  
- `DVASPECT_CONTENT` 项可以显示作为嵌入到其容器内的对象的方式表示。  
  
- `DVASPECT_THUMBNAIL` 项将呈现在"缩略图"表示形式，以便它可以在浏览工具中显示。  
  
- `DVASPECT_ICON` 项由一个图标表示。  
  
- `DVASPECT_DOCPRINT` 就像它已使用文件菜单中的打印命令来打印表示项。  
  
### <a name="remarks"></a>备注  
 默认实现调用[NotifyChanged](#notifychanged)，而不考虑提示或发件人。  
  
##  <a name="onupdateitems"></a>  COleServerItem::OnUpdateItems  
 由框架调用以更新服务器文档中的所有项。  
  
```  
virtual void OnUpdateItems();
```  
  
### <a name="remarks"></a>备注  
 默认实现调用[UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)所有`COleClientItem`文档中的对象。  
  
##  <a name="setitemname"></a>  COleServerItem::SetItemName  
 创建链接的项以将其名称设置时，请调用此函数。  
  
```  
void SetItemName(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>参数  
 `lpszItemName`  
 为新的名称的项的指针。  
  
### <a name="remarks"></a>备注  
 名称必须是唯一的文档中。 当调用的服务器应用程序时编辑链接的项时，应用程序将使用此名称查找该项目。 不需要用于嵌入项调用此函数。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [CDocItem 类](../../mfc/reference/cdocitem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)   
 [COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
