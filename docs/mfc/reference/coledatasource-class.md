---
title: "COleDataSource 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDataSource
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [C++], MFC support
- Clipboard [C++], OLE support
- uniform data transfer
- OLE [C++], uniform data transfer
- Clipboard [C++], MFC support
- OLE Clipboard [C++], support
- IDataObject, MFC encapsulation
- data transfer [C++], OLE
- COleDataSource class
- OLE data transfer [C++]
- uniform data transfer, OLE
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: cd8f30c3edd7d26b254e7f4a6f153ab0b2fc96da
ms.lasthandoff: 02/24/2017

---
# <a name="coledatasource-class"></a>COleDataSource 类
充当应用程序将数据放置到的缓存，应用程序将在数据传输操作（如剪贴板或拖放操作）期间提供这些数据。  
  
## <a name="syntax"></a>语法  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleDataSource::COleDataSource](#coledatasource)|构造 `COleDataSource` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleDataSource::CacheData](#cachedata)|提供在指定的格式中使用的数据**STGMEDIUM**结构。|  
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|提供在指定的格式中使用的数据`HGLOBAL`。|  
|[COleDataSource::DelayRenderData](#delayrenderdata)|提供使用延迟的呈现指定的格式中的数据。|  
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|提供在指定的格式中的数据`CFile`指针。|  
|[COleDataSource::DelaySetData](#delaysetdata)|为每种格式支持的调用`OnSetData`。|  
|[COleDataSource::DoDragDrop](#dodragdrop)|执行与数据源拖放操作。|  
|[COleDataSource::Empty](#empty)|清空`COleDataSource`的数据的对象。|  
|[COleDataSource::FlushClipboard](#flushclipboard)|将所有数据都呈现到剪贴板。|  
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|验证仍然存在放到剪贴板上的数据。|  
|[COleDataSource::OnRenderData](#onrenderdata)|检索作为延迟的呈现的一部分的数据。|  
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|检索到的数据`CFile`作为延迟的呈现的一部分。|  
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|检索到的数据`HGLOBAL`作为延迟的呈现的一部分。|  
|[COleDataSource::OnSetData](#onsetdata)|调用以替换中的数据`COleDataSource`对象。|  
|[COleDataSource::SetClipboard](#setclipboard)|位置`COleDataSource`在剪贴板上的对象。|  
  
## <a name="remarks"></a>备注  
 您可以直接创建 OLE 数据源。 或者， [COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)类创建 OLE 数据源来响应其`CopyToClipboard`和`DoDragDrop`成员函数。 请参阅[COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard)有关的简要说明。 重写`OnGetClipboardData`为创建的客户端项目或服务器项类来添加额外的剪贴板格式的数据的 OLE 数据源中的成员函数`CopyToClipboard`或`DoDragDrop`成员函数。  
  
 只要您想要准备数据以进行传输，您应创建此类的对象，并用您使用最合适的方法为您的数据的数据填充它。 插入到数据源的方式直接受是否立即提供数据 （立即呈现） 或按需 （延迟的呈现）。 对于每种剪贴板格式，顺序通过传递要使用的剪贴板格式提供数据 (和可选[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构)，调用[DelayRenderData](#delayrenderdata)。  
  
 有关数据源和数据传输的详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。 此外，文章[剪贴板主题](../../mfc/clipboard.md)描述 OLE 剪贴板机制。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="a-namecachedataa--coledatasourcecachedata"></a><a name="cachedata"></a>COleDataSource::CacheData  
 调用此函数可指定在其中的数据在提供安全更新的数据传输操作的格式。  
  
```  
void CacheData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 剪贴板格式是用来提供数据。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构，其中包含指定的格式中的数据。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构的结构描述是用来提供数据的格式。 为此参数提供一个值，如果您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果它是**NULL**，对于其他字段中使用默认值**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 您必须提供数据，因为通过使用立即呈现的此函数提供它。 在需要时才缓存数据。  
  
 提供的数据使用[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构。 您还可以使用`CacheGlobalData`成员函数，如果您提供的数据量是足够小，能够有效地使用传输`HGLOBAL`。  
  
 在调用后`CacheData` **ptd**的成员`lpFormatEtc`和内容`lpStgMedium`所拥有的数据对象，不是由调用方。  
  
 若要使用延迟的呈现，调用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关详细信息延迟的呈现为 mfc 已处理，请参阅文章[数据对象和数据源︰ 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecacheglobaldataa--coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a>COleDataSource::CacheGlobalData  
 调用此函数可指定在其中的数据在提供安全更新的数据传输操作的格式。  
  
```  
void CacheGlobalData(
    CLIPFORMAT cfFormat,  
    HGLOBAL hGlobal,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 剪贴板格式是用来提供数据。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 *hGlobal*  
 包含指定的格式中的数据的全局内存块的句柄。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构的结构描述是用来提供数据的格式。 为此参数提供一个值，如果您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果它是**NULL**，对于其他字段中使用默认值**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 此函数提供了使用立即呈现，因此在调用函数; 时，您必须提供数据的数据在需要时才缓存数据。 使用`CacheData`成员函数，如果您提供大量的数据或者如果您需要结构化的存储介质。  
  
 若要使用延迟的呈现，调用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关详细信息延迟的呈现为 mfc 已处理，请参阅文章[数据对象和数据源︰ 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecoledatasourcea--coledatasourcecoledatasource"></a><a name="coledatasource"></a>COleDataSource::COleDataSource  
 构造 `COleDataSource` 对象。  
  
```  
COleDataSource();
```  
  
##  <a name="a-namedelayrenderdataa--coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a>COleDataSource::DelayRenderData  
 调用此函数可指定在其中的数据在提供安全更新的数据传输操作的格式。  
  
```  
void DelayRenderData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 剪贴板格式是用来提供数据。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构的结构描述是用来提供数据的格式。 为此参数提供一个值，如果您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果它是**NULL**，对于其他字段中使用默认值**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 此函数提供了使用延迟呈现，因此不立即提供数据的数据。 [OnRenderData](#onrenderdata)或[OnRenderGlobalData](#onrenderglobaldata)调用成员函数以请求数据。  
  
 如果您不打算提供您的数据通过使用此功能`CFile`对象。 如果您打算通过数据提供`CFile`对象，请调用[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关详细信息延迟的呈现为 mfc 已处理，请参阅文章[数据对象和数据源︰ 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 若要使用立即呈现，调用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成员函数。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedelayrenderfiledataa--coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a>COleDataSource::DelayRenderFileData  
 调用此函数可指定在其中的数据在提供安全更新的数据传输操作的格式。  
  
```  
void DelayRenderFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 剪贴板格式是用来提供数据。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构的结构描述是用来提供数据的格式。 为此参数提供一个值，如果您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果它是**NULL**，对于其他字段中使用默认值**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 此函数提供了使用延迟呈现，因此不立即提供数据的数据。 [OnRenderFileData](#onrenderfiledata)调用成员函数以请求数据。  
  
 使用此函数，如果您打算使用`CFile`对象提供数据。 如果您不打算使用`CFile`对象，请调用[DelayRenderData](#delayrenderdata)成员函数。 有关详细信息延迟的呈现为 mfc 已处理，请参阅文章[数据对象和数据源︰ 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 若要使用立即呈现，调用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成员函数。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedelaysetdataa--coledatasourcedelaysetdata"></a><a name="delaysetdata"></a>COleDataSource::DelaySetData  
 调用此函数可支持更改数据源的内容。  
  
```  
void DelaySetData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 剪贴板格式是用来放置数据。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构的结构描述的数据将被替换的格式。 为此参数提供一个值，如果您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果它是**NULL**，对于其他字段中使用默认值**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 [OnSetData](#onsetdata)这种情况下将由框架调用。 这仅框架返回的数据源时使用[COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)。 如果`DelaySetData`不调用，则您`OnSetData`永远不会调用函数。 `DelaySetData`应为每个剪贴板调用或**FORMATETC**您支持的格式。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedodragdropa--coledatasourcedodragdrop"></a><a name="dodragdrop"></a>COleDataSource::DoDragDrop  
 调用`DoDragDrop`成员函数以在通常执行拖放操作对此数据源， [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)处理程序。  
  
```  
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,  
    LPCRECT lpRectStartDrag = NULL,  
    COleDropSource* pDropSource = NULL);
```  
  
### <a name="parameters"></a>参数  
 `dwEffects`  
 拖放操作允许对此数据源。 可以是一个或多项操作︰  
  
- `DROPEFFECT_COPY`无法执行复制操作。  
  
- `DROPEFFECT_MOVE`无法执行移动操作。  
  
- `DROPEFFECT_LINK`无法建立到原始数据放置的数据的链接。  
  
- `DROPEFFECT_SCROLL`表示可能发生拖动滚动操作。  
  
 `lpRectStartDrag`  
 向定义实际开始拖动该矩形的指针。 有关更多信息，请参见下面的“备注”部分。  
  
 *pDropSource*  
 指向以拖放源。 如果**NULL**然后的默认实现[COleDropSource](../../mfc/reference/coledropsource-class.md)将使用。  
  
### <a name="return-value"></a>返回值  
 删除由拖放操作; 生成的效果否则为`DROPEFFECT_NONE`如果因为用户在离开所提供的矩形之前释放鼠标按钮，该操作永远不会从开始。  
  
### <a name="remarks"></a>备注  
 不立即启动拖放操作。 鼠标光标离开所指定的矩形等到`lpRectStartDrag`或直到经过指定的毫秒数。 如果`lpRectStartDrag`是**NULL**，矩形的大小是一个像素。  
  
 注册表项设置由指定的延迟时间。 可以通过调用更改的延迟时间[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果不指定延迟时间，则使用默认值为 200 毫秒。 将延迟时间存储中，如下所示︰  
  
-   Windows NT 拖动延迟时间将存储在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Windows 3.x 拖动延迟时间将存储在 WIN。INI 文件，请在 [时段} 部分。  
  
-   Windows 95/98 拖动延迟时间存储在缓存版的 WIN。INI。  
  
 用于详细了解如何拖动延迟信息存储在注册表或。INI 文件，请参阅[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅文章[将拖放︰ 实现放置源](../../mfc/drag-and-drop-implementing-a-drop-source.md)。  
  
##  <a name="a-nameemptya--coledatasourceempty"></a><a name="empty"></a>COleDataSource::Empty  
 调用此函数可对空`COleDataSource`的数据的对象。  
  
```  
void Empty();
```  
  
### <a name="remarks"></a>备注  
 同时会缓存，以便可以重用清空延迟的呈现格式。  
  
 有关详细信息，请参阅[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameflushclipboarda--coledatasourceflushclipboard"></a><a name="flushclipboard"></a>COleDataSource::FlushClipboard  
 呈现数据，可在剪贴板上，然后您可以将数据从剪贴板粘贴后关闭应用程序。  
  
```  
static void PASCAL FlushClipboard();
```  
  
### <a name="remarks"></a>备注  
 使用[设置剪贴板](#setclipboard)将数据放在剪贴板上。  
  
##  <a name="a-namegetclipboardownera--coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a>COleDataSource::GetClipboardOwner  
 确定是否在剪贴板上的数据已发生更改以来[设置剪贴板](#setclipboard)最后一次调用，并且，如果是这样，标识当前所有者。  
  
```  
static COleDataSource* PASCAL GetClipboardOwner();
```  
  
### <a name="return-value"></a>返回值  
 当前在剪贴板上的数据源或**NULL**如果没有任何内容复制到剪贴板上或剪贴板不归调用应用程序。  
  
##  <a name="a-nameonrenderdataa--coledatasourceonrenderdata"></a><a name="onrenderdata"></a>COleDataSource::OnRenderData  
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
 指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成员函数，延迟的呈现。 此函数的默认实现将调用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)是否提供的存储媒体文件或内存，分别。 如果这两种格式都不提供的默认实现将返回 0 并不执行任何操作。 有关详细信息延迟的呈现为 mfc 已处理，请参阅文章[数据对象和数据源︰ 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如果`lpStgMedium` ->  *tymed*是**TYMED_NULL**、 **STGMEDIUM**应分配并由指定填充*-> tymed lpFormatEtc*。 如果还没有**TYMED_NULL**、 **STGMEDIUM**应填写的数据的位置。  
  
 这是一个高级可重写。 重写此函数可提供您请求的格式和介质中的数据。 具体取决于您的数据，您可能想要改为重写此函数的其他版本之一。 如果您的数据较小且大小固定，重写`OnRenderGlobalData`。 如果您的数据在文件中，或在大小可变的重写`OnRenderFileData`。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227)枚举类型和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
##  <a name="a-nameonrenderfiledataa--coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a>COleDataSource::OnRenderFileData  
 由框架时指定的存储介质的文件中检索指定的格式的数据调用。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定所请求信息的格式。  
  
 `pFile`  
 指向[CFile](../../mfc/reference/cfile-class.md)对象是用来呈现数据。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](#delayrenderdata)成员函数，延迟的呈现。 此函数的默认实现只是返回**FALSE**。  
  
 这是一个高级可重写。 重写此函数可提供您请求的格式和介质中的数据。 具体取决于您的数据，您可能希望改为重写此函数的其他版本之一。 如果您想要处理多个存储介质，重写[OnRenderData](#onrenderdata)。 如果您的数据在文件中，或在大小可变的重写`OnRenderFileData`。 有关详细信息延迟的呈现为 mfc 已处理，请参阅文章[数据对象和数据源︰ 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
##  <a name="a-nameonrenderglobaldataa--coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleDataSource::OnRenderGlobalData  
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
 指向全局内存中数据是要返回的句柄。 如果其中一个具有尚未分配，此参数可以是**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](#delayrenderdata)成员函数，延迟的呈现。 此函数的默认实现只是返回**FALSE**。  
  
 如果`phGlobal`是**NULL**，一个新`HGLOBAL`应分配并返回以`phGlobal`。 否则为`HGLOBAL`由指定`phGlobal`应使用数据填充。 数据量置于`HGLOBAL`不能超过内存块的当前大小。 此外，块不能重新分配给较大的大小。  
  
 这是一个高级可重写。 重写此函数可提供您请求的格式和介质中的数据。 具体取决于您的数据，您可能想要改为重写此函数的其他版本之一。 如果您想要处理多个存储介质，重写[OnRenderData](#onrenderdata)。 如果您的数据在文件中，或在大小可变的重写[OnRenderFileData](#onrenderfiledata)。 有关详细信息延迟的呈现为 mfc 已处理，请参阅文章[数据对象和数据源︰ 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
##  <a name="a-nameonsetdataa--coledatasourceonsetdata"></a><a name="onsetdata"></a>COleDataSource::OnSetData  
 由框架调用以设置或替换中的数据`COleDataSource`中指定的格式对象。  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定在其中替换数据的格式。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构，它包含的数据，将替换的当前内容`COleDataSource`对象。  
  
 `bRelease`  
 指示有在完成函数调用之后的存储介质的所有权。 调用方决定由谁来负责释放分配的存储介质代表的资源。 调用方进行查询时会设置`bRelease`。 如果`bRelease`为非零值，数据源将获得所有权，使用它完成释放介质。 当`bRelease`为 0、 调用方保留所有权和数据源可以专用于在调用期间使用的存储介质。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它已成功获取后，数据源才能数据的所有权。 也就是说，它不会拥有如果`OnSetData`，则返回 0。 如果数据源将获得所有权，它通过调用释放存储介质[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)函数。  
  
 默认实现不执行任何操作。 重写此函数可替换中指定的格式的数据。 这是一个高级可重写。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构和[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)中函数[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
##  <a name="a-namesetclipboarda--coledatasourcesetclipboard"></a><a name="setclipboard"></a>COleDataSource::SetClipboard  
 中包含的数据将放`COleDataSource`调用下列函数之一后剪贴板上的对象︰ [CacheData](#cachedata)， [CacheGlobalData](#cacheglobaldata)， [DelayRenderData](#delayrenderdata)，或[DelayRenderFileData](#delayrenderfiledata)。  
  
```  
void SetClipboard();
```  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDataObject 类](../../mfc/reference/coledataobject-class.md)

