---
title: COleServerItem 类 |Microsoft Docs
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
ms.openlocfilehash: f1da24273decbee296bfa19a5c8306cb0512e3fc
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850243"
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
  
|名称|描述|  
|----------|-----------------|  
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|将放置中的演示文稿和转换格式`COleDataSource`对象。|  
|[COleServerItem::CopyToClipboard](#copytoclipboard)|将项目复制到剪贴板。|  
|[COleServerItem::DoDragDrop](#dodragdrop)|执行拖放操作。|  
|[COleServerItem::GetClipboardData](#getclipboarddata)|获取在数据传输 （拖放或剪贴板） 中使用数据源。|  
|[COleServerItem::GetDocument](#getdocument)|返回包含项的服务器文档。|  
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|获取 OLE 项 CF_EMBEDSOURCE 数据。|  
|[COleServerItem::GetItemName](#getitemname)|返回项的名称。 用于链接的项。|  
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|获取 OLE 项 CF_LINKSOURCE 数据。|  
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|获取 OLE 项 CF_OBJECTDESCRIPTOR 数据。|  
|[COleServerItem::IsConnected](#isconnected)|指示该项当前是否附加到活动的容器。|  
|[COleServerItem::IsLinkedItem](#islinkeditem)|指示项是否表示链接的 OLE 项。|  
|[COleServerItem::NotifyChanged](#notifychanged)|使用自动链接更新更新所有容器。|  
|[COleServerItem::OnDoVerb](#ondoverb)|调用以执行谓词。|  
|[Coleserveritem:: Ondraw](#ondraw)|当容器请求绘制项; 时调用所需的实现。|  
|[COleServerItem::OnDrawEx](#ondrawex)|为专用的项绘图调用。|  
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|由框架调用以获取的数据，都要复制到剪贴板。|  
|[COleServerItem::OnGetExtent](#ongetextent)|由框架调用以检索 OLE 项的大小。|  
|[COleServerItem::OnInitFromData](#oninitfromdata)|由框架调用以初始化 OLE 项使用指定的数据传输对象的内容。|  
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|调用以确定是否有链接的项需要更新。|  
|[COleServerItem::OnRenderData](#onrenderdata)|检索数据作为延迟呈现的一部分。|  
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|检索到的数据`CFile`延迟呈现的一部分的对象。|  
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|检索到的延迟呈现一部分 HGLOBAL 数据。|  
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|调用以设置项的配色方案。|  
|[COleServerItem::OnSetData](#onsetdata)|调用以设置项的数据。|  
|[COleServerItem::OnSetExtent](#onsetextent)|由框架调用以将 OLE 项的大小设置。|  
|[COleServerItem::OnUpdate](#onupdate)|调用文档项的某些部分位于已更改。|  
|[COleServerItem::OnUpdateItems](#onupdateitems)|调用以更新服务器文档中的所有项的演示文稿缓存。|  
|[COleServerItem::SetItemName](#setitemname)|设置项的名称。 用于链接的项。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](#getdatasource)|获取用于存储转换格式的对象。|  
|[COleServerItem::OnHide](#onhide)|由框架调用以隐藏 OLE 项。|  
|[COleServerItem::OnOpen](#onopen)|由框架调用以在其自己的顶级窗口中显示 OLE 项。|  
|[COleServerItem::OnShow](#onshow)|当容器请求显示项时调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleServerItem::m_sizeExtent](#m_sizeextent)|通知服务器的 OLE 项可见。|  
  
## <a name="remarks"></a>备注  
 链接的项可以表示部分或全部服务器文档。 嵌入的项始终表示整个服务器文档。  
  
 `COleServerItem`类定义由 OLE 系统动态链接库 (Dll) 调用的多个可重写成员函数通常从容器应用程序响应请求。 这些成员函数允许容器应用程序操作项间接以各种方式，例如显示、 执行其谓词，或检索其数据采用各种格式。  
  
 若要使用`COleServerItem`、 从其派生一个类并实现[OnDraw](#ondraw)并[Serialize](../../mfc/reference/cobject-class.md#serialize)成员函数。 `OnDraw`函数提供了一个项，使其能够容器应用程序打开复合文档时显示的图元文件表示形式。 `Serialize`函数的`CObject`提供的项，请允许嵌入的项服务器和容器应用程序之间传输的本机表示形式。 [OnGetExtent](#ongetextent)提供到该容器，启用要调整大小的项的容器的项的自然大小。  
  
 有关服务器和相关的主题的详细信息，请参阅文章[服务器： 实现服务器](../../mfc/servers-implementing-a-server.md)和"创建容器/服务器应用程序"一文中[容器： 高级功能](../../mfc/containers-advanced-features.md)。  
  
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
 *pDataSource*  
 指向`COleDataSource`中放置数据的对象。  
  
### <a name="remarks"></a>备注  
 您必须实现[OnDraw](#ondraw)成员函数以提供项的显示格式 （如图元文件图片）。 若要支持其他转换格式，将其注册使用[COleDataSource](../../mfc/reference/coledatasource-class.md)返回的对象[GetDataSource](#getdatasource)并重写[OnRenderData](#onrenderdata)到成员函数提供你想要支持的格式中的数据。  
  
##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem  
 构造`COleServerItem`对象，并将其添加到文档项的服务器文档的集合。  
  
```  
COleServerItem(
    COleServerDoc* pServerDoc,  
    BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>参数  
 *pServerDoc*  
 指向将包含新项的文档的指针。  
  
 *bAutoDelete*  
 指示链接到该发布时是否可以删除该对象的标记。 将此设置为 FALSE;`COleServerItem`对象是不可或缺的一部分文档的数据，您必须删除。 将此设置为 true 的对象是用来标识文档的数据可以删除由框架中的范围的辅助结构。  
  
##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard  
 调用此函数可将 OLE 项复制到剪贴板。  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *bIncludeLink*  
 将此设置为 true 将数据链接应复制到剪贴板。 将此设置为 FALSE; 你的服务器应用程序不支持链接。  
  
### <a name="remarks"></a>备注  
 该函数使用[OnGetClipboardData](#ongetclipboarddata)成员函数来创建[COleDataSource](../../mfc/reference/coledatasource-class.md)对象，其中包含支持的格式中的 OLE 项的数据。 该函数将放置`COleDataSource`对象上使用剪贴板[COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函数。 `COleDataSource`对象 CF_METAFILEPICT 格式，以及你选择支持任何转换格式的数据中包括的项的本机数据以及它的表示形式。 您必须已实现[Serialize](../../mfc/reference/cobject-class.md#serialize)并[OnDraw](#ondraw)此成员函数才会起作用。  
  
##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop  
 调用`DoDragDrop`成员函数以执行拖放操作。  
  
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
  
 *ptOffset*  
 从偏移量*lpItemRect*在拖动时所在的鼠标位置。  
  
 *bIncludeLink*  
 将此设置为 true 将数据链接应复制到剪贴板。 将其设置为 FALSE，如果你的应用程序不支持链接。  
  
 *dwEffects*  
 确定拖动源将在拖动操作 （复制、 移动和链接的组合） 允许的效果。  
  
 *lpRectStartDrag*  
 向定义实际开始拖动该矩形的指针。 有关更多信息，请参见下面的“备注”部分。  
  
### <a name="return-value"></a>返回值  
 DROPEFFECT 枚举中的值。 如果它是 DROPEFFECT_MOVE，应删除原始数据。  
  
### <a name="remarks"></a>备注  
 拖放操作不会立即启动。 它等待，直到鼠标光标离开所指定的矩形*lpRectStartDrag*或之前已通过指定的毫秒数。 如果*lpRectStartDrag*为 NULL，使用默认矩形，以便在拖动开始时鼠标光标移动一个像素。  
  
 注册表项设置由指定的延迟时间。 您可以通过调用来更改延迟时间[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果未指定延迟时间，使用默认值为 200 毫秒。 将延迟时间存储中，如下所示：  
  
-   Windows NT 将延迟时间将存储在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Windows 3.x 拖动延迟时间将存储在 WIN。INI 文件，[Windows} 部分。  
  
-   Windows 95/98 拖动延迟时间将存储在 WIN 的缓存版本。INI。  
  
 详细了解如何将拖动的延迟信息存储在任一注册表或。INI 文件，请参阅[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) Windows SDK 中。  
  
##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData  
 调用此函数可填充指定[COleDataSource](../../mfc/reference/coledatasource-class.md)对象将复制到剪贴板中，如果您调用的所有数据[CopyToClipboard](#copytoclipboard) (将还传输相同的数据，如果你名为[DoDragDrop](#dodragdrop))。  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pDataSource*  
 指向`COleDataSource`将接收所有受支持格式的 OLE 项的数据的对象。  
  
 *bIncludeLink*  
 如果应将链接数据复制到剪贴板，则为 TRUE。 如果服务器应用程序不支持链接，则为 FALSE。  
  
 *lpOffset*  
 中的偏移量，以像素为单位从源对象的鼠标光标。  
  
 *lpSize*  
 以像素为单位的对象的大小。  
  
### <a name="remarks"></a>备注  
 此函数将调用[GetEmbedSourceData](#getembedsourcedata)成员函数以获取本机数据的 OLE 项并调用[AddOtherClipboardData](#addotherclipboarddata)成员函数以获取显示格式以及任何支持的转换格式。 如果*bIncludeLink*为 TRUE 时，该函数还调用[GetLinkSourceData](#getlinksourcedata)若要获取项的链接数据。  
  
 重写此函数，如果你想要将格式放入`COleDataSource`对象之前或之后提供的这些格式`CopyToClipboard`。  
  
##  <a name="getdatasource"></a>  COleServerItem::GetDataSource  
 调用此函数可获取[COleDataSource](../../mfc/reference/coledatasource-class.md)对象用来存储服务器应用程序支持的转换格式。  
  
```  
COleDataSource* GetDataSource();
```  
  
### <a name="return-value"></a>返回值  
 一个指向`COleDataSource`对象，用于存储转换格式。  
  
### <a name="remarks"></a>备注  
 如果你想在服务器应用程序提供数据传输过程中以不同的格式的数据操作，注册使用这些格式`COleDataSource`此函数返回的对象。 例如，如果你想要提供 OLE 项的 CF_TEXT 表示剪贴板或拖放操作，将注册使用的格式`COleDataSource`此函数返回时，对象，然后重写`OnRenderXxxData`到成员函数提供的数据。  
  
##  <a name="getdocument"></a>  COleServerItem::GetDocument  
 调用此函数可获得到的文档的包含项的指针。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向包含的项; 文档如果项不是文档的一部分，则为 NULL。  
  
### <a name="remarks"></a>备注  
 这将允许访问服务器文档作为参数传递到`COleServerItem`构造函数。  
  
##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData  
 调用此函数可获取 CF_EMBEDSOURCE 数据的 OLE 项。  
  
```  
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 *lpStgMedium*  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)将接收 OLE 项的 CF_EMBEDSOURCE 数据的结构。  
  
### <a name="remarks"></a>备注  
 此格式包含项的本机数据。 您必须已实现`Serialize`此函数可正常工作的成员函数。  
  
 结果可以然后将添加到数据源使用[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 会自动调用此函数[COleServerItem::OnGetClipboardData](#ongetclipboarddata)。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中。  
  
##  <a name="getitemname"></a>  COleServerItem::GetItemName  
 调用此函数可获取项的名称。  
  
```  
const CString& GetItemName() const;  
```  
  
### <a name="return-value"></a>返回值  
 项的名称。  
  
### <a name="remarks"></a>备注  
 通常仅为链接项调用此函数。  
  
##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData  
 调用此函数可获取 CF_LINKSOURCE 数据的 OLE 项。  
  
```  
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 *lpStgMedium*  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)将接收 OLE 项的 CF_LINKSOURCE 数据的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此格式包含描述 OLE 项和定位包含 OLE 项的文档所需的信息类型的 CLSID。  
  
 然后可以将结果添加到数据源使用[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 会自动调用此函数[OnGetClipboardData](#ongetclipboarddata)。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中。  
  
##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData  
 调用此函数可获取 CF_OBJECTDESCRIPTOR 数据的 OLE 项。  
  
```  
void GetObjectDescriptorData(
    LPPOINT lpOffset,  
    LPSIZE lpSize,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 *lpOffset*  
 鼠标单击窗口左上角的 OLE 项的偏移量。 可以为 NULL。  
  
 *lpSize*  
 OLE 项的大小。 可以为 NULL。  
  
 *lpStgMedium*  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)将接收 OLE 项的 CF_OBJECTDESCRIPTOR 数据的结构。  
  
### <a name="remarks"></a>备注  
 信息复制到`STGMEDIUM`指向结构*lpStgMedium*。 此格式包含所需的选择性粘贴对话框中的信息。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中。  
  
##  <a name="isconnected"></a>  COleServerItem::IsConnected  
 调用此函数将 OLE 项处于连接状态。  
  
```  
BOOL IsConnected() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果项在连接，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 OLE 项被视为连接如果一个或多个容器具有对项的引用。 如果其引用计数大于 0 或如果它是嵌入的项目，项会连接。  
  
##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem  
 调用此函数可将 OLE 项链接的项。  
  
```  
BOOL IsLinkedItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该项为链接的项; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果项有效，并且不会返回在文档的列表中的嵌入项，链接项。 链接的项可能会或可能未连接到的容器。  
  
 它是通常使用同一个类的链接和嵌入的项。 `IsLinkedItem` 让你可以链接的项的行为不同于嵌入项，尽管很多时候的代码很常见。  
  
##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent  
 此成员指示服务器太多的对象是在容器文档中可见。  
  
```  
CSize m_sizeExtent;  
```  
  
### <a name="remarks"></a>备注  
 默认实现[OnSetExtent](#onsetextent)设置此成员。  
  
##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged  
 链接的项发生更改后调用此函数。  
  
```  
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>参数  
 *nDrawAspect*  
 指示 OLE 项的哪个方面 DVASPECT 枚举中的值已更改。 此参数可以具有以下值之一：  
  
- DVASPECT_CONTENT 项可以显示为其容器内的嵌入对象的方式表示。  
  
- DVASPECT_THUMBNAIL 项将呈现在"缩略图"表示形式，以便它可以显示在浏览工具。  
  
- DVASPECT_ICON 项由一个图标表示。  
  
- DVASPECT_DOCPRINT 项表现为似乎打印出的使用文件菜单中的打印命令。  
  
### <a name="remarks"></a>备注  
 如果容器项与自动链接链接到文档后，更新项目以反映所做的更改。 在容器应用程序中使用 Microsoft 基础类库编写[COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange)调用以响应。  
  
##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb  
 由框架调用以执行指定的谓词。  
  
```  
virtual void OnDoVerb(LONG iVerb);
```  
  
### <a name="parameters"></a>参数  
 *iVerb*  
 指定要执行的谓词。 它可以是以下之一：  
  
|“值”|含义|符号|  
|-----------|-------------|------------|  
|0|主谓词|OLEIVERB_PRIMARY|  
|1|辅助谓词|（无）|  
|- 1|显示用于编辑的项|OLEIVERB_SHOW|  
|- 2|在单独的窗口中编辑项目|OLEIVERB_OPEN|  
|- 3|隐藏项|OLEIVERB_HIDE|  
  
 -1 值通常是另一个动作的别名。 如果不支持打开编辑，-2 将具有相同的效果-1。 其他值，请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序已使用 Microsoft 基础类库编写的调用此函数时[COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate)成员函数的相应`COleClientItem`调用对象。 默认实现调用[OnShow](#onshow)成员函数，如果指定主谓词或 OLEIVERB_SHOW [OnOpen](#onopen)如果指定了辅助谓词或 OLEIVERB_OPEN，和[OnHide](#onhide)如果 OLEIVERB_HIDE 指定。 默认实现调用`OnShow`如果*iVerb*不是上面列出的谓词之一。  
  
 如果主谓词不会显示该项，重写此函数。 例如，如果该项是录音，并且其主谓词是 Play，您将不必显示要播放该项目的服务器应用程序。  
  
 有关详细信息，请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
##  <a name="ondraw"></a>  Coleserveritem:: Ondraw  
 由框架调用以将 OLE 项渲染到图元文件。  
  
```  
virtual BOOL OnDraw(
    CDC* pDC,  
    CSize& rSize) = 0;  
```  
  
### <a name="parameters"></a>参数  
 *pDC*  
 一个指向[CDC](../../mfc/reference/cdc-class.md)在其上绘制项的对象。 显示上下文将自动连接到的属性显示上下文以便您可以调用属性的函数，尽管这样会导致图元文件特定于设备的。  
  
 *rsize，则将*  
 大小 （以 HIMETRIC 为单位，在其中绘制图元文件）。  
  
### <a name="return-value"></a>返回值  
 已成功绘制项; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 OLE 项的 metafile 表示形式用于容器应用程序中显示项。 如果容器应用程序已使用 Microsoft 基础类库编写的通过使用图元文件[绘制](../../mfc/reference/coleclientitem-class.md#draw)成员函数的相应[COleClientItem](../../mfc/reference/coleclientitem-class.md)对象。 没有默认实现。 必须重写此函数可绘制到指定的设备上下文项。  
  
##  <a name="ondrawex"></a>  COleServerItem::OnDrawEx  
 由框架，用于所有绘图调用。  
  
```  
virtual BOOL OnDrawEx(
    CDC* pDC,  
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>参数  
 *pDC*  
 一个指向[CDC](../../mfc/reference/cdc-class.md)在其上绘制项的对象。 DC 将自动连接到 DC 的属性以便您可以调用属性的函数，尽管这样会导致图元文件特定于设备。  
  
 *nDrawAspect*  
 DVASPECT 枚举中的值。 此参数可以具有以下值之一：  
  
- DVASPECT_CONTENT 项可以显示为其容器内的嵌入对象的方式表示。  
  
- DVASPECT_THUMBNAIL 项将呈现在"缩略图"表示形式，以便它可以显示在浏览工具。  
  
- DVASPECT_ICON 项由一个图标表示。  
  
- DVASPECT_DOCPRINT 项表现为似乎打印出的使用文件菜单中的打印命令。  
  
 *rsize，则将*  
 项以 HIMETRIC 为单位的大小。  
  
### <a name="return-value"></a>返回值  
 已成功绘制项; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现将调用`OnDraw`时 DVASPECT 等于 DVASPECT_CONTENT; 否则它将失败。  
  
 重写此函数可提供以外 DVASPECT_CONTENT DVASPECT_ICON 或 DVASPECT_THUMBNAIL 等方面的演示文稿数据。  
  
##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData  
 由框架调用以获取`COleDataSource`对象，其中包含所有数据将放置在剪贴板上通过调用[CopyToClipboard](#copytoclipboard)成员函数。  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>参数  
 *bIncludeLink*  
 将此设置为 true 将数据链接应复制到剪贴板。 将此设置为 FALSE; 你的服务器应用程序不支持链接。  
  
 *lpOffset*  
 以像素为单位对象从源鼠标光标的偏移量。  
  
 *lpSize*  
 以像素为单位的对象的大小。  
  
### <a name="return-value"></a>返回值  
 一个指向[COleDataSource](../../mfc/reference/coledatasource-class.md)对象，其中包含剪贴板数据。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[GetClipboardData](#getclipboarddata)。  
  
##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent  
 由框架调用以检索中的 OLE 项的 HIMETRIC 单位的大小。  
  
```  
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>参数  
 *nDrawAspect*  
 指定要从中检索其边界的 OLE 项的方面。 此参数可以具有以下值之一：  
  
- DVASPECT_CONTENT 项可以显示为其容器内的嵌入对象的方式表示。  
  
- DVASPECT_THUMBNAIL 项将呈现在"缩略图"表示形式，以便它可以显示在浏览工具。  
  
- DVASPECT_ICON 项由一个图标表示。  
  
- DVASPECT_DOCPRINT 项表现为似乎打印出的使用文件菜单中的打印命令。  
  
 *rsize，则将*  
 引用`CSize`对象，它将接收 OLE 项的大小。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序已使用 Microsoft 基础类库编写的调用此函数时[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)成员函数的相应`COleClientItem`调用对象。 默认实现不执行任何操作。 您必须自己实现它。 如果你想要处理的请求的大小的 OLE 项时进行特殊处理，重写此函数。  
  
##  <a name="onhide"></a>  COleServerItem::OnHide  
 由框架调用以隐藏 OLE 项。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>备注  
 默认调用`COleServerDoc::OnShowDocument( FALSE )`。 该函数也会发出通知容器已隐藏 OLE 项。 如果你想要隐藏 OLE 项时进行特殊处理，重写此函数。  
  
##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData  
 由框架调用以初始化 OLE 项使用的内容*pDataObject*。  
  
```  
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,  
    BOOL bCreation);
```  
  
### <a name="parameters"></a>参数  
 *pDataObject*  
 指向包含用于初始化 OLE 项的各种格式的数据的 OLE 数据对象的指针。  
  
 *bCreation*  
 如果该函数调用以初始化 OLE 项正在新创建的容器应用程序，则为 TRUE。 如果该函数调用以替换现有的 OLE 项的内容，则为 FALSE。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果*bCreation*为 TRUE，如果容器实现基于当前所选内容上插入新对象将调用此函数。 创建新的 OLE 项时，使用所选的数据。 例如，当在电子表格程序中选择一系列单元格，然后使用插入新对象创建一个图表基于所选范围内的值。 默认实现不执行任何操作。 重写此函数以选择从所提供的可接受的格式*pDataObject*并初始化 OLE 项基于提供的数据。 这是一种高级可重写。  
  
 有关详细信息，请参阅[IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) Windows SDK 中。  
  
##  <a name="onopen"></a>  COleServerItem::OnOpen  
 由框架调用以在单独实例的服务器应用程序，而不是就地显示 OLE 项。  
  
```  
virtual void OnOpen();
```  
  
### <a name="remarks"></a>备注  
 默认实现将激活第一个框架窗口中显示文档，其中包含 OLE 项;如果应用程序是最小化服务器，默认实现将显示主窗口。 该函数也会发出通知容器已打开的 OLE 项。  
  
 如果你想要打开 OLE 项时进行特殊处理，重写此函数。 这是与你想要它打开时链接到设置所选内容的链接项尤为常见。  
  
 有关详细信息，请参阅[IOleClientSite::OnShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms688658) Windows SDK 中。  
  
##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems  
 由框架调用以确定当前的服务器文档中的任何链接的项目是否过期。  
  
```  
virtual BOOL OnQueryUpdateItems();
```  
  
### <a name="return-value"></a>返回值  
 如果该文档具有项需要更新; 非零值如果所有项都是最新，则为 0。  
  
### <a name="remarks"></a>备注  
 如果已更改其源文档，但未更新链接的项以反映文档中的更改，项已过期。  
  
##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData  
 由框架调用以检索指定格式的数据。  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定为请求信息的格式。  
  
 *lpStgMedium*  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) ，数据将返回的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)延迟呈现的成员函数。 此函数的默认实现调用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)分别，如果提供的存储介质是文件或内存。 如果提供了任一这些格式，则默认实现将返回 0，且不执行任何操作。  
  
 如果*lpStgMedium*-> *tymed*是 TYMED_NULL，STGMEDIUM 应分配和填充由指定*lpFormatEtc-> tymed*。 如果不应在具有数据的位置填充 TYMED_NULL、 STGMEDIUM。  
  
 这是一种高级可重写。 重写此函数可提供请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你的数据较小且大小固定，重写`OnRenderGlobalData`。 如果数据是在文件中，或者是大小可变的重写`OnRenderFileData`。  
  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)， [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，以及[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) Windows SDK 中。  
  
##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData  
 由框架调用以检索指定格式的数据的存储介质是文件时。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>参数  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定为请求信息的格式。  
  
 *pFile*  
 指向`CFile`，数据将呈现的对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延迟呈现的成员函数。 此函数的默认实现只是返回 FALSE。  
  
 这是一种高级可重写。 重写此函数可提供请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你想要处理多个存储媒介，重写[OnRenderData](#onrenderdata)。 如果数据是在文件中，或者是大小可变的重写[OnRenderFileData](#onrenderfiledata)。  
  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)并[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData  
 由框架调用以检索指定格式的数据时指定的存储介质是全局内存。  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>参数  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定为请求信息的格式。  
  
 *phGlobal*  
 指向全局内存，数据将返回的句柄。 如果已不分配任何内存，则此参数可以为 NULL。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延迟呈现的成员函数。 此函数的默认实现只是返回 FALSE。  
  
 如果*phGlobal*为 NULL，则应分配并返回新 HGLOBAL *phGlobal*。 否则，HGLOBAL 指定*phGlobal*应填充数据。 在 HGLOBAL 中放置的数据量不能超过内存块的当前大小。 此外，块不能重新分配给较大的大小。  
  
 这是一种高级可重写。 重写此函数可提供请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你想要处理多个存储媒介，重写[OnRenderData](#onrenderdata)。 如果数据是在文件中，或者是大小可变的重写[OnRenderFileData](#onrenderfiledata)。  
  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)并[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme  
 由框架调用以指定编辑 OLE 项时要使用的颜色调色板。  
  
```  
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```  
  
### <a name="parameters"></a>参数  
 *lpLogPalette*  
 指向 Windows [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)结构。  
  
### <a name="return-value"></a>返回值  
 如果使用的颜色调色板; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序使用 Microsoft 基础类库编写的调用此函数时[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971)函数的相应`COleClientItem`调用对象。 默认实现将返回 FALSE。 如果你想要使用建议的调色板，重写此函数。 服务器应用程序不需要使用建议的调色板。  
  
 有关详细信息，请参阅[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) Windows SDK 中。  
  
##  <a name="onsetdata"></a>  COleServerItem::OnSetData  
 由框架调用以 OLE 项的数据替换为指定的数据。  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>参数  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定数据的格式。  
  
 *lpStgMedium*  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)所在数据结构。  
  
 *bRelease*  
 指示谁完成函数调用后有存储介质的所属权。 调用方决定由谁来负责释放存储介质代表分配的资源。 调用方通过设置执行此*bRelease*。 如果*bRelease*是为非零，服务器项将获得所有权，使用它完成时释放该介质。 当*bRelease*为 0、 保留所有权，调用方和服务器项可以专用于在调用期间使用的存储介质。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它已成功地获取它，服务器项才会对数据所有权。 也就是说，它不会不获得所有权，如果它返回 0。 如果数据源采用所有权，它通过调用释放存储介质[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)函数。  
  
 默认实现不执行任何操作。 重写此函数将 OLE 项的数据替换为指定的数据。 这是一种高级可重写。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，并[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) Windows SDK 中。  
  
##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent  
 由框架调用以通知 OLE 该项是容器文档中的可用空间量。  
  
```  
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,  
    const CSize& size);
```  
  
### <a name="parameters"></a>参数  
 *nDrawAspect*  
 指定的 OLE 项指定了其边界的方面。 此参数可以具有以下值之一：  
  
- DVASPECT_CONTENT 项可以显示为其容器内的嵌入对象的方式表示。  
  
- DVASPECT_THUMBNAIL 项将呈现在"缩略图"表示形式，以便它可以显示在浏览工具。  
  
- DVASPECT_ICON 项由一个图标表示。  
  
- DVASPECT_DOCPRINT 项表现为似乎打印出的使用文件菜单中的打印命令。  
  
 *size*  
 一个[CSize](../../atl-mfc-shared/reference/csize-class.md)结构，它指定 OLE 项的新大小。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序已使用 Microsoft 基础类库编写的调用此函数时[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)成员函数的相应`COleClientItem`调用对象。 默认实现集[m_sizeExtent](#m_sizeextent)成员添加到指定的大小如果*nDrawAspect*是 DVASPECT_CONTENT; 否则返回 0。 重写此函数以执行特殊处理，当您更改项的大小。  
  
##  <a name="onshow"></a>  COleServerItem::OnShow  
 由框架调用以指示要就地显示 OLE 项的服务器应用程序。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>备注  
 这就需要此函数通常称为容器应用程序的用户创建一个项或执行动词，如编辑、 时要显示的项。 默认实现会尝试就地激活。 如果此操作失败，则函数调用`OnOpen`成员函数的单独窗口中显示 OLE 项。  
  
 如果你想要执行特殊处理，显示 OLE 项时，重写此函数。  
  
##  <a name="onupdate"></a>  COleServerItem::OnUpdate  
 在修改项时由框架调用。  
  
```  
virtual void OnUpdate(
    COleServerItem* pSender,  
    LPARAM lHint,  
    CObject* pHint,  
    DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>参数  
 *pSender*  
 为修改文档的项的指针。 可以为 NULL。  
  
 *lHint*  
 包含有关修改信息。  
  
 *pHint*  
 指针指向的对象存储有关修改信息。  
  
 *nDrawAspect*  
 DVASPECT 枚举中的值。 此参数可以具有以下值之一：  
  
- DVASPECT_CONTENT 项可以显示为其容器内的嵌入对象的方式表示。  
  
- DVASPECT_THUMBNAIL 项将呈现在"缩略图"表示形式，以便它可以显示在浏览工具。  
  
- DVASPECT_ICON 项由一个图标表示。  
  
- DVASPECT_DOCPRINT 项表现为似乎打印出的使用文件菜单中的打印命令。  
  
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
 调用此函数时创建链接的项目，才能将其名称设置。  
  
```  
void SetItemName(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>参数  
 *lpszItemName*  
 为新名称的项的指针。  
  
### <a name="remarks"></a>备注  
 名称必须是唯一的文档中。 调用服务器应用程序时编辑链接的项，应用程序将使用此名称来查找项。 不需要调用此函数用于嵌入项。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [CDocItem 类](../../mfc/reference/cdocitem-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)   
 [COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)
