---
title: "COleServerItem 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- servers, OLE
- OLE server applications, managing server documents
- OLE server applications, server interfaces
- OLE server documents
- COleServerItem class
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
caps.latest.revision: 23
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
ms.openlocfilehash: 49dd8cc258ebf96c91ac8ff1190f9a830b6bb5ec
ms.lasthandoff: 02/24/2017

---
# <a name="coleserveritem-class"></a>COleServerItem 类
提供 OLE 项的服务器接口。  
  
## <a name="syntax"></a>语法  
  
```  
class COleServerItem : public CDocItem  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleServerItem::COleServerItem](#coleserveritem)|构造 `COleServerItem` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|将放置在演示文稿和转换格式`COleDataSource`对象。|  
|[COleServerItem::CopyToClipboard](#copytoclipboard)|将项复制到剪贴板。|  
|[COleServerItem::DoDragDrop](#dodragdrop)|执行拖放操作。|  
|[COleServerItem::GetClipboardData](#getclipboarddata)|获取导致数据传输 （拖放或剪贴板） 使用数据源。|  
|[COleServerItem::GetDocument](#getdocument)|返回包含项的服务器文档。|  
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|获取**CF_EMBEDSOURCE** OLE 项的数据。|  
|[COleServerItem::GetItemName](#getitemname)|返回项的名称。 用于链接的项。|  
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|获取`CF_LINKSOURCE`OLE 项的数据。|  
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|获取**CF_OBJECTDESCRIPTOR** OLE 项的数据。|  
|[COleServerItem::IsConnected](#isconnected)|指示该项当前是否附加到活动的容器。|  
|[COleServerItem::IsLinkedItem](#islinkeditem)|指示项是否表示链接的 OLE 项。|  
|[COleServerItem::NotifyChanged](#notifychanged)|使用自动链接更新来更新所有容器。|  
|[COleServerItem::OnDoVerb](#ondoverb)|调用以执行谓词。|  
|[Coleserveritem:: Ondraw](#ondraw)|当绘制项; 容器请求时调用所需的实现。|  
|[COleServerItem::OnDrawEx](#ondrawex)|对于专用的项绘图调用。|  
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|由框架后，若要获取的数据，都要复制到剪贴板上调用。|  
|[COleServerItem::OnGetExtent](#ongetextent)|调用由框架来检索 OLE 项的大小。|  
|[COleServerItem::OnInitFromData](#oninitfromdata)|由框架来初始化使用指定的数据传输对象的内容将 OLE 项调用。|  
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|调用以确定是否有链接的项需要更新。|  
|[COleServerItem::OnRenderData](#onrenderdata)|检索作为延迟的呈现的一部分的数据。|  
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|检索到的数据`CFile`对象作为延迟的呈现的一部分。|  
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|检索到的数据`HGLOBAL`作为延迟的呈现的一部分。|  
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|调用以设置项的配色方案。|  
|[COleServerItem::OnSetData](#onsetdata)|调用以设置项的数据。|  
|[COleServerItem::OnSetExtent](#onsetextent)|由框架以将 OLE 项大小设置调用。|  
|[COleServerItem::OnUpdate](#onupdate)|调用文档项的某些部分中的对应时被更改。|  
|[COleServerItem::OnUpdateItems](#onupdateitems)|调用以更新演示文稿缓存服务器文档中的所有项。|  
|[COleServerItem::SetItemName](#setitemname)|设置项的名称。 用于链接的项。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](#getdatasource)|获取用来存储转换格式的对象。|  
|[COleServerItem::OnHide](#onhide)|由框架可以隐藏 OLE 项调用。|  
|[COleServerItem::OnOpen](#onopen)|由框架在其自己的顶级窗口中显示 OLE 项调用。|  
|[COleServerItem::OnShow](#onshow)|表示显示该项的容器请求时调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[COleServerItem::m_sizeExtent](#m_sizeextent)|有关 OLE 项多少是可见的通知服务器。|  
  
## <a name="remarks"></a>备注  
 链接的项可以表示部分或全部服务器文档。 嵌入的项始终表示整个服务器文档。  
  
 `COleServerItem`类定义由 OLE 系统动态链接库 (Dll) 调用的若干可重写成员函数通常以响应从容器应用程序的请求。 这些成员函数允许通过来操作项间接以各种方式，如显示它、 执行其谓词或检索其数据以各种格式的容器应用程序。  
  
 若要使用`COleServerItem`、 从其派生一个类和实现[OnDraw](#ondraw)和[Serialize](../../mfc/reference/cobject-class.md#serialize)成员函数。 `OnDraw`函数提供了一个项目，从而使其在容器应用程序打开复合文档时要显示的图元文件表示。 `Serialize`函数`CObject`提供的本机表示形式的项，请允许嵌入的项可以在服务器和容器应用程序之间传递。 [OnGetExtent](#ongetextent)提供到容器中，启用要调整大小的项的容器的项的自然大小。  
  
 有关服务器和相关的主题的详细信息，请参阅文章[服务器︰ 实现服务器](../../mfc/servers-implementing-a-server.md)和"创建容器/服务器应用程序"一文中[容器︰ 高级功能](../../mfc/containers-advanced-features.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="addotherclipboarddata"></a>COleServerItem::AddOtherClipboardData  
 调用此函数可将 OLE 项的演示文稿和转换格式放入指定`COleDataSource`对象。  
  
```  
void AddOtherClipboardData(COleDataSource* pDataSource);
```  
  
### <a name="parameters"></a>参数  
 `pDataSource`  
 指向`COleDataSource`中放置数据的对象。  
  
### <a name="remarks"></a>备注  
 您必须实现[OnDraw](#ondraw)成员函数可提供项目的显示格式 （图元文件图片）。 若要支持其他转换格式，注册它们使用[COleDataSource](../../mfc/reference/coledatasource-class.md)舱ン[GetDataSource](#getdatasource)并重写[OnRenderData](#onrenderdata)成员函数以提供您想要支持的格式中的数据。  
  
##  <a name="coleserveritem"></a>COleServerItem::COleServerItem  
 构造`COleServerItem`对象，并将其添加到服务器文档的文档项的集合。  
  
```  
COleServerItem(
    COleServerDoc* pServerDoc,  
    BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>参数  
 `pServerDoc`  
 指向将包含新的项目的文档的指针。  
  
 `bAutoDelete`  
 该标志指明链接到该发布时是否可以删除该对象。 将此设置为**FALSE**如果`COleServerItem`对象是文档的数据，您必须删除的组成部分。 将此设置为**TRUE**如果对象是用来标识在可以删除由框架的文档的数据中的范围的辅助结构。  
  
##  <a name="copytoclipboard"></a>COleServerItem::CopyToClipboard  
 调用此函数可将 OLE 项复制到剪贴板。  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bIncludeLink`  
 将此设置为**TRUE**如果将数据链接应复制到剪贴板。 将此设置为**FALSE**如果服务器应用程序不支持链接。  
  
### <a name="remarks"></a>备注  
 该函数使用[OnGetClipboardData](#ongetclipboarddata)成员函数来创建[COleDataSource](../../mfc/reference/coledatasource-class.md)对象，其中包含所支持的格式中的 OLE 项的数据。 该函数将放置`COleDataSource`上使用剪贴板对象[COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函数。 `COleDataSource`对象包括项的本机数据以及其表示形式`CF_METAFILEPICT`格式，以及您选择支持任何转换格式的数据。 您必须实现[Serialize](../../mfc/reference/cobject-class.md#serialize)和[OnDraw](#ondraw)有关此成员函数以起作用。  
  
##  <a name="dodragdrop"></a>COleServerItem::DoDragDrop  
 调用`DoDragDrop`成员函数来执行拖放操作。  
  
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
 在屏幕上，以像素为单位，相对于工作区的项的矩形。  
  
 `ptOffset`  
 与偏移量`lpItemRect`在拖动时所在的鼠标位置。  
  
 `bIncludeLink`  
 将此设置为**TRUE**如果将数据链接应复制到剪贴板。 将其设置为**FALSE**如果您的应用程序不支持链接。  
  
 `dwEffects`  
 确定拖动源允许拖放操作 （复制、 移动和链接的组合） 中的效果。  
  
 `lpRectStartDrag`  
 向定义实际开始拖动该矩形的指针。 有关更多信息，请参见下面的“备注”部分。  
  
### <a name="return-value"></a>返回值  
 `DROPEFFECT` 枚举中的一个值。 如果它是`DROPEFFECT_MOVE`，应删除的原始数据。  
  
### <a name="remarks"></a>备注  
 不立即启动拖放操作。 鼠标光标离开所指定的矩形等到`lpRectStartDrag`或直到经过指定的毫秒数。 如果`lpRectStartDrag`是**NULL**，使用默认矩形，以便拖动启动当鼠标光标移动一个像素。  
  
 注册表项设置由指定的延迟时间。 可以通过调用更改的延迟时间[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果不指定延迟时间，则使用默认值为 200 毫秒。 将延迟时间存储中，如下所示︰  
  
-   Windows NT 拖动延迟时间将存储在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Windows 3.x 拖动延迟时间将存储在 WIN。INI 文件，请在 [时段} 部分。  
  
-   Windows 95/98 拖动延迟时间存储在缓存版的 WIN。INI。  
  
 用于详细了解如何拖动延迟信息存储在注册表或。INI 文件，请参阅[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getclipboarddata"></a>COleServerItem::GetClipboardData  
 调用此函数以填充指定[COleDataSource](../../mfc/reference/coledatasource-class.md)对象将复制到剪贴板中，如果您调用的所有数据[CopyToClipboard](#copytoclipboard) (如果调用，还会传输相同的数据[DoDragDrop](#dodragdrop))。  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDataSource`  
 指向`COleDataSource`将接收所有受支持格式的 OLE 项的数据的对象。  
  
 `bIncludeLink`  
 **TRUE**如果将数据链接应复制到剪贴板。 **FALSE**如果服务器应用程序不支持链接。  
  
 `lpOffset`  
 偏移量，以像素为单位，鼠标光标从该对象的原点。  
  
 `lpSize`  
 以像素为单位的对象的大小。  
  
### <a name="remarks"></a>备注  
 此函数将调用[GetEmbedSourceData](#getembedsourcedata)成员函数来获取本机数据的 OLE 项目，然后调用[AddOtherClipboardData](#addotherclipboarddata)成员函数可获取的显示格式以及任何支持的转换格式。 如果`bIncludeLink`是**TRUE**，该函数还调用[GetLinkSourceData](#getlinksourcedata)获取项的链接数据。  
  
 重写此函数，如果您想要将格式放入`COleDataSource`对象之前还是之后提供的这些格式`CopyToClipboard`。  
  
##  <a name="getdatasource"></a>COleServerItem::GetDataSource  
 调用此函数可获取[COleDataSource](../../mfc/reference/coledatasource-class.md)用来存储服务器应用程序支持的转换格式的对象。  
  
```  
COleDataSource* GetDataSource();
```  
  
### <a name="return-value"></a>返回值  
 一个指向`COleDataSource`用来存储转换格式的对象。  
  
### <a name="remarks"></a>备注  
 如果您希望服务器应用程序提供数据传输过程中的各种格式的数据操作，注册这些格式与`COleDataSource`此函数返回的对象。 例如，如果您想要提供**CF_TEXT** OLE 项的剪贴板或拖放操作的表示形式，将注册带格式`COleDataSource`此函数返回时，对象，然后重写**OnRenderXxxData**成员函数以提供数据。  
  
##  <a name="getdocument"></a>COleServerItem::GetDocument  
 调用此函数可获取指向包含该项目的文档的指针。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向包含的项; 文档的指针**NULL**如果该项不是文档的一部分。  
  
### <a name="remarks"></a>备注  
 这将允许访问服务器文档作为参数传递到`COleServerItem`构造函数。  
  
##  <a name="getembedsourcedata"></a>COleServerItem::GetEmbedSourceData  
 调用此函数可获取**CF_EMBEDSOURCE** OLE 项的数据。  
  
```  
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构，它将接收**CF_EMBEDSOURCE** OLE 项的数据。  
  
### <a name="remarks"></a>备注  
 此格式包含项的本机数据。 您必须实现`Serialize`成员函数，此函数可正常工作。  
  
 结果可以再将添加到数据源通过使用[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 自动调用此函数[COleServerItem::OnGetClipboardData](#ongetclipboarddata)。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getitemname"></a>COleServerItem::GetItemName  
 调用此函数可获取项的名称。  
  
```  
const CString& GetItemName() const;  
```  
  
### <a name="return-value"></a>返回值  
 项的名称。  
  
### <a name="remarks"></a>备注  
 通常仅为链接项调用此函数。  
  
##  <a name="getlinksourcedata"></a>COleServerItem::GetLinkSourceData  
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
 此格式包含描述的 OLE 项目与定位包含 OLE 项的文档所需的信息类型的 CLSID。  
  
 就可以将结果添加到数据源与[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 自动调用此函数[OnGetClipboardData](#ongetclipboarddata)。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getobjectdescriptordata"></a>COleServerItem::GetObjectDescriptorData  
 调用此函数可获取**CF_OBJECTDESCRIPTOR** OLE 项的数据。  
  
```  
void GetObjectDescriptorData(
    LPPOINT lpOffset,  
    LPSIZE lpSize,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 `lpOffset`  
 鼠标单击的 OLE 项左上角的偏移量。 可以是**NULL**。  
  
 `lpSize`  
 OLE 项的大小。 可以是**NULL**。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构，它将接收**CF_OBJECTDESCRIPTOR** OLE 项的数据。  
  
### <a name="remarks"></a>备注  
 信息复制到**STGMEDIUM**指向结构`lpStgMedium`。 此格式包括选择性粘贴对话框中所需的信息。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="isconnected"></a>COleServerItem::IsConnected  
 调用此函数，以查看是否已连接 OLE 项。  
  
```  
BOOL IsConnected() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果项在连接，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 OLE 项被视为连接如果一个或多个容器具有对项的引用。 项会连接的引用计数大于 0 或是否嵌入的项。  
  
##  <a name="islinkeditem"></a>COleServerItem::IsLinkedItem  
 调用此函数可查看 OLE 项是否链接的项。  
  
```  
BOOL IsLinkedItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该项是链接的项目;否则为 0。  
  
### <a name="remarks"></a>备注  
 如果项有效，且不在的嵌入项的文档的列表中返回，链接项。 链接的项可能会或可能未连接到的容器。  
  
 很普遍链接和嵌入项使用同一个类。 `IsLinkedItem`使您可以链接的项的行为与嵌入项不同，但代码很多时候是公共。  
  
##  <a name="m_sizeextent"></a>COleServerItem::m_sizeExtent  
 此成员将告知服务器多少对象是在容器文档中可见。  
  
```  
CSize m_sizeExtent;  
```  
  
### <a name="remarks"></a>备注  
 默认实现[OnSetExtent](#onsetextent)设置此成员。  
  
##  <a name="notifychanged"></a>COleServerItem::NotifyChanged  
 更改链接的项目后，请调用此函数。  
  
```  
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>参数  
 `nDrawAspect`  
 取值范围为`DVASPECT`枚举，指示哪些方面的 OLE 项已更改。 此参数可以具有任何以下值︰  
  
- `DVASPECT_CONTENT`项可以显示为嵌入对象到其容器内的方式表示。  
  
- `DVASPECT_THUMBNAIL`项将呈现在"thumbnail"表示形式，以便它可以显示在浏览工具。  
  
- `DVASPECT_ICON`项由一个图标来表示。  
  
- `DVASPECT_DOCPRINT`就像它已打印使用打印命令从文件菜单项表示。  
  
### <a name="remarks"></a>备注  
 如果容器项与自动链接到文档链接，该项目将更新以反映所做的更改。 在容器应用程序中使用 Microsoft 基础类库编写[COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange)在响应中调用。  
  
##  <a name="ondoverb"></a>COleServerItem::OnDoVerb  
 由框架来执行指定的谓词调用。  
  
```  
virtual void OnDoVerb(LONG iVerb);
```  
  
### <a name="parameters"></a>参数  
 `iVerb`  
 指定要执行的谓词。 它可以是任何下列选项之一︰  
  
|值|含义|符号|  
|-----------|-------------|------------|  
|0|主谓词|`OLEIVERB_PRIMARY`|  
|1|次要谓词|（无）|  
|– 1|显示项进行编辑|`OLEIVERB_SHOW`|  
|– 2|在单独的窗口中编辑项目|`OLEIVERB_OPEN`|  
|– 3|隐藏项|`OLEIVERB_HIDE`|  
  
 为-1 值通常是另一个谓词的别名。 如果不支持打开编辑，–&2; 具有为 –&1; 相同的效果。 有关其他值，请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序使用 Microsoft 基础类库编写的此函数时调用[COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate)相应成员函数`COleClientItem`调用对象。 默认实现调用[OnShow](#onshow)成员函数，如果主谓词或`OLEIVERB_SHOW`指定，则[OnOpen](#onopen)如果次要谓词或`OLEIVERB_OPEN`指定，则和[į](#onhide)如果`OLEIVERB_HIDE`指定。 默认实现调用`OnShow`如果`iVerb`不是上面列出的谓词之一。  
  
 如果主谓词不会显示该项，重写此函数。 例如，如果该项录音，并且其主谓词是游戏，您将不需要显示要播放该项目的服务器应用程序。  
  
 有关详细信息，请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="ondraw"></a>Coleserveritem:: Ondraw  
 由框架调用，以将 OLE 项呈现到 metafile 中。  
  
```  
virtual BOOL OnDraw(
    CDC* pDC,  
    CSize& rSize) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 一个指向[CDC](../../mfc/reference/cdc-class.md)在其上绘制项的对象。 显示上下文将自动连接到属性显示上下文因此您可以调用特性的函数，尽管这样会导致图元文件特定于设备。  
  
 `rSize`  
 调整大小，请在**HIMETRIC**单元，在其中进行绘制图元文件。  
  
### <a name="return-value"></a>返回值  
 成功绘制项; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 OLE 项的图元文件表示用于在容器应用程序中显示的项。 如果容器应用程序使用 Microsoft 基础类库编写的通过使用图元文件[绘制](../../mfc/reference/coleclientitem-class.md#draw)相应成员函数[COleClientItem](../../mfc/reference/coleclientitem-class.md)对象。 没有默认实现。 必须重写此函数可绘制到指定的设备上下文的项。  
  
##  <a name="ondrawex"></a>COleServerItem::OnDrawEx  
 由框架，用于所有绘图调用。  
  
```  
virtual BOOL OnDrawEx(
    CDC* pDC,  
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 一个指向[CDC](../../mfc/reference/cdc-class.md)在其上绘制项的对象。 DC 将自动连接到特性 DC 因此您可以调用特性的函数，尽管这样会导致图元文件特定于设备。  
  
 `nDrawAspect`  
 `DVASPECT` 枚举中的一个值。 此参数可以具有任何以下值︰  
  
- `DVASPECT_CONTENT`项可以显示为嵌入对象到其容器内的方式表示。  
  
- `DVASPECT_THUMBNAIL`项将呈现在"thumbnail"表示形式，以便它可以显示在浏览工具。  
  
- `DVASPECT_ICON`项由一个图标来表示。  
  
- `DVASPECT_DOCPRINT`就像它已打印使用打印命令从文件菜单项表示。  
  
 `rSize`  
 中的项的大小**HIMETRIC**单位。  
  
### <a name="return-value"></a>返回值  
 成功绘制项; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现调用`OnDraw`时`DVASPECT`是否等同于`DVASPECT_CONTENT`; 否则将失败。  
  
 重写此函数而不提供方面的演示文稿数据`DVASPECT_CONTENT`，如`DVASPECT_ICON`或`DVASPECT_THUMBNAIL`。  
  
##  <a name="ongetclipboarddata"></a>COleServerItem::OnGetClipboardData  
 由框架调用以获取`COleDataSource`对象，其中包含通过调用将被放到剪贴板的所有数据[CopyToClipboard](#copytoclipboard)成员函数。  
  
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
 以像素为单位的对象的原点的鼠标光标的偏移量。  
  
 `lpSize`  
 以像素为单位的对象的大小。  
  
### <a name="return-value"></a>返回值  
 一个指向[COleDataSource](../../mfc/reference/coledatasource-class.md)对象，它包含在剪贴板数据。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现调用[GetClipboardData](#getclipboarddata)。  
  
##  <a name="ongetextent"></a>COleServerItem::OnGetExtent  
 由框架调用以检索大小， **HIMETRIC**单位 OLE 项。  
  
```  
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>参数  
 `nDrawAspect`  
 指定要从中检索其边界的 OLE 项的方面。 此参数可以具有任何以下值︰  
  
- `DVASPECT_CONTENT`项可以显示为嵌入对象到其容器内的方式表示。  
  
- `DVASPECT_THUMBNAIL`项将呈现在"thumbnail"表示形式，以便它可以显示在浏览工具。  
  
- `DVASPECT_ICON`项由一个图标来表示。  
  
- `DVASPECT_DOCPRINT`就像它已打印使用打印命令从文件菜单项表示。  
  
 `rSize`  
 引用`CSize`对象，它将接收 OLE 项的大小。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序使用 Microsoft 基础类库编写的此函数时调用[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)相应成员函数`COleClientItem`调用对象。 默认实现不执行任何操作。 您必须自己实现它。 如果你想要在处理请求的 OLE 项的大小会进行特殊处理，重写此函数。  
  
##  <a name="onhide"></a>COleServerItem::OnHide  
 由框架可以隐藏 OLE 项调用。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>备注  
 默认值调用**COleServerDoc::OnShowDocument (FALSE)**。 该函数还通知容器 OLE 项已被隐藏。 如果您想要隐藏 OLE 项时执行特殊处理，重写此函数。  
  
##  <a name="oninitfromdata"></a>COleServerItem::OnInitFromData  
 由框架调用以初始化 OLE 项使用的内容`pDataObject`。  
  
```  
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,  
    BOOL bCreation);
```  
  
### <a name="parameters"></a>参数  
 `pDataObject`  
 指向包含用于初始化 OLE 项的各种格式的数据的 OLE 数据对象的指针。  
  
 `bCreation`  
 **TRUE**如果调用该函数以初始化新由容器应用程序创建一个 OLE 项。 **FALSE**如果调用该函数以替换现有 OLE 项的内容。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`bCreation`是**TRUE**，如果容器实现根据当前选择的插入的新对象调用此函数。 创建新的 OLE 项时，使用所选的数据。 例如，当在电子表格程序中选择一个单元格区域，然后使用插入新对象来创建图表基于所选的范围内的值。 默认实现不执行任何操作。 重写此函数可供选择所提供的可接受的格式`pDataObject`和初始化基础提供的数据的 OLE 项。 这是一个高级可重写。  
  
 有关详细信息，请参阅[IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onopen"></a>COleServerItem::OnOpen  
 由框架显示 OLE 项显示在单独实例的服务器应用程序，而不是就地调用。  
  
```  
virtual void OnOpen();
```  
  
### <a name="remarks"></a>备注  
 显示文档，其中包含 OLE 项; 第一个框架窗口默认实现激活如果应用程序是最小化服务器，默认实现将显示主窗口。 该函数还通知容器已打开的 OLE 项。  
  
 如果您想要执行的特殊处理，在打开一个 OLE 项时，重写此函数。 这是与你想要将所选内容设置为链接，打开时的链接项目来说尤其常见。  
  
 有关详细信息，请参阅[IOleClientSite::OnShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms688658)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onqueryupdateitems"></a>COleServerItem::OnQueryUpdateItems  
 由框架来确定当前的服务器文档中的任何链接的项是否已过时的调用。  
  
```  
virtual BOOL OnQueryUpdateItems();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该文档具有项目需要更新;如果所有项都是最新，则为 0。  
  
### <a name="remarks"></a>备注  
 如果已更改其源文档，但链接的项目尚未更新以反映在文档中的更改，项已过期。  
  
##  <a name="onrenderdata"></a>COleServerItem::OnRenderData  
 由框架用于检索指定的格式数据调用。  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定所请求信息的格式。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)是用来返回数据的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)成员函数，延迟的呈现。 此函数的默认实现调用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)分别，如果提供的存储媒体文件或内存中。 如果提供了两种格式，则默认实现将返回 0，且不执行任何操作。  
  
 如果`lpStgMedium` ->  *tymed*是**TYMED_NULL**、 **STGMEDIUM**应分配并由指定填充*-> tymed lpFormatEtc*。 如果不是**TYMED_NULL**、 **STGMEDIUM**应填写的数据的位置。  
  
 这是一个高级可重写。 重写此函数可提供您请求的格式和介质中的数据。 具体取决于您的数据，您可能想要改为重写此函数的其他版本之一。 如果您的数据较小且大小固定，重写`OnRenderGlobalData`。 如果您的数据在文件中，或在大小可变的重写`OnRenderFileData`。  
  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)， [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，和[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onrenderfiledata"></a>COleServerItem::OnRenderFileData  
 由框架来检索指定格式的数据文件的存储介质时调用。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定所请求信息的格式。  
  
 `pFile`  
 指向`CFile`对象是用来呈现数据。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成员函数，延迟的呈现。 此函数的默认实现只是返回**FALSE**。  
  
 这是一个高级可重写。 重写此函数可提供您请求的格式和介质中的数据。 具体取决于您的数据，您可能希望改为重写此函数的其他版本之一。 如果您想要处理多个存储媒介，重写[OnRenderData](#onrenderdata)。 如果您的数据在文件中，或在大小可变的重写[OnRenderFileData](#onrenderfiledata)。  
  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onrenderglobaldata"></a>COleServerItem::OnRenderGlobalData  
 由框架来检索指定格式的数据在指定的存储介质全局内存时调用。  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定所请求信息的格式。  
  
 `phGlobal`  
 指向全局内存中数据是要返回的句柄。 如果尚未分配任何内存，此参数可以是**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成员函数，延迟的呈现。 此函数的默认实现只是返回**FALSE**。  
  
 如果`phGlobal`是**NULL**，一个新`HGLOBAL`应分配并返回以`phGlobal`。 否则为`HGLOBAL`由指定`phGlobal`应使用数据填充。 数据量置于`HGLOBAL`不能超过内存块的当前大小。 此外，块不能重新分配给较大的大小。  
  
 这是一个高级可重写。 重写此函数可提供您请求的格式和介质中的数据。 具体取决于您的数据，您可能想要改为重写此函数的其他版本之一。 如果您想要处理多个存储媒介，重写[OnRenderData](#onrenderdata)。 如果您的数据在文件中，或在大小可变的重写[OnRenderFileData](#onrenderfiledata)。  
  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onsetcolorscheme"></a>COleServerItem::OnSetColorScheme  
 由框架，以指定在编辑 OLE 项时要使用的颜色调色板调用。  
  
```  
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```  
  
### <a name="parameters"></a>参数  
 `lpLogPalette`  
 指向 Windows [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)结构。  
  
### <a name="return-value"></a>返回值  
 非零，如果使用的调色板颜色。否则为 0。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序使用 Microsoft 基础类库编写的此函数时调用[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971)相应函数`COleClientItem`调用对象。 默认实现返回**FALSE**。 如果你想要使用建议的调色板，重写此函数。 服务器应用程序不需要使用建议的调色板。  
  
 有关详细信息，请参阅[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onsetdata"></a>COleServerItem::OnSetData  
 由 OLE 项的数据替换为指定的数据连接的框架调用。  
  
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
 指示有在完成函数调用之后的存储介质的所有权。 调用方决定由谁来负责释放分配的存储介质代表的资源。 调用方进行查询时会设置`bRelease`。 如果`bRelease`为非零值，服务器项取得所有权，使用它完成释放介质。 当`bRelease`为 0、 调用方保留所有权和服务器项可以仅用于在调用期间使用的存储介质。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它已成功获取它，服务器项才会对数据所有权。 也就是说，它不会拥有如果它返回 0。 如果数据源将获得所有权，它通过调用释放存储介质[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)函数。  
  
 默认实现不执行任何操作。 重写此函数可将 OLE 项的数据替换为指定的数据。 这是一个高级可重写。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，和[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onsetextent"></a>COleServerItem::OnSetExtent  
 由框架以通知 OLE 该项多少空间可供其在容器文档中调用。  
  
```  
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,  
    const CSize& size);
```  
  
### <a name="parameters"></a>参数  
 `nDrawAspect`  
 指定的 OLE 项指定其边界的方面。 此参数可以具有任何以下值︰  
  
- `DVASPECT_CONTENT`项可以显示为嵌入对象到其容器内的方式表示。  
  
- `DVASPECT_THUMBNAIL`项将呈现在"thumbnail"表示形式，以便它可以显示在浏览工具。  
  
- `DVASPECT_ICON`项由一个图标来表示。  
  
- `DVASPECT_DOCPRINT`就像它已打印使用打印命令从文件菜单项表示。  
  
 `size`  
 一个[CSize](../../atl-mfc-shared/reference/csize-class.md)结构，它指定 OLE 项的新大小。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果容器应用程序使用 Microsoft 基础类库编写的此函数时调用[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)相应成员函数`COleClientItem`调用对象。 默认实现将设置[m_sizeExtent](#m_sizeextent)为指定大小的成员如果`nDrawAspect`是`DVASPECT_CONTENT`; 否则返回 0。 重写此函数以执行特殊处理，当您更改的项的大小。  
  
##  <a name="onshow"></a>COleServerItem::OnShow  
 由框架来指示要就地显示 OLE 项的服务器应用程序调用。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>备注  
 当容器应用程序的用户创建一个项或执行动词，如编辑时，通常调用此函数要求要显示的项。 默认实现将尝试在就地激活。 如果此操作失败，函数调用`OnOpen`成员函数以在一个单独的窗口中显示 OLE 项。  
  
 如果你想要显示一个 OLE 项时执行特殊处理，重写此函数。  
  
##  <a name="onupdate"></a>COleServerItem::OnUpdate  
 在修改的项时，由框架调用。  
  
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
 指针指向存储修改的相关信息的对象。  
  
 `nDrawAspect`  
 `DVASPECT` 枚举中的一个值。 此参数可以具有下列值之一︰  
  
- `DVASPECT_CONTENT`项可以显示为嵌入对象到其容器内的方式表示。  
  
- `DVASPECT_THUMBNAIL`项将呈现在"thumbnail"表示形式，以便它可以显示在浏览工具。  
  
- `DVASPECT_ICON`项由一个图标来表示。  
  
- `DVASPECT_DOCPRINT`就像它已打印使用打印命令从文件菜单项表示。  
  
### <a name="remarks"></a>备注  
 默认实现调用[NotifyChanged](#notifychanged)，而不管当时提示或发件人。  
  
##  <a name="onupdateitems"></a>COleServerItem::OnUpdateItems  
 由框架来更新服务器文档中的所有项调用。  
  
```  
virtual void OnUpdateItems();
```  
  
### <a name="remarks"></a>备注  
 默认实现调用[UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)所有`COleClientItem`文档中的对象。  
  
##  <a name="setitemname"></a>COleServerItem::SetItemName  
 当创建某个链接的项可将其名称设置时，请调用此函数。  
  
```  
void SetItemName(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>参数  
 `lpszItemName`  
 指针，指向该项目的新名称。  
  
### <a name="remarks"></a>备注  
 名称必须是唯一的文档中。 当调用服务器应用程序时编辑链接的项时，应用程序将使用此名称来查找项。 不需要调用此函数用于嵌入项。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [CDocItem 类](../../mfc/reference/cdocitem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)   
 [COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer 类](../../mfc/reference/coletemplateserver-class.md)

