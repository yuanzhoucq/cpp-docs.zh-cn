---
title: COleDataSource 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
dev_langs:
- C++
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3b5060c850a1fcdba089b732d019f958f2e7410
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038547"
---
# <a name="coledatasource-class"></a>COleDataSource 类
充当应用程序将数据放置到的缓存，应用程序将在数据传输操作（如剪贴板或拖放操作）期间提供这些数据。  
  
## <a name="syntax"></a>语法  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleDataSource::COleDataSource](#coledatasource)|构造 `COleDataSource` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleDataSource::CacheData](#cachedata)|提供在指定的格式中使用的数据**STGMEDIUM**结构。|  
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|提供在指定的格式中使用的数据`HGLOBAL`。|  
|[COleDataSource::DelayRenderData](#delayrenderdata)|提供指定的格式使用延迟的呈现的数据。|  
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|提供在指定的格式的数据`CFile`指针。|  
|[COleDataSource::DelaySetData](#delaysetdata)|中支持每个格式将为调用`OnSetData`。|  
|[Coledatasource:: Dodragdrop](#dodragdrop)|执行与数据源的拖放操作。|  
|[COleDataSource::Empty](#empty)|清空`COleDataSource`的数据的对象。|  
|[COleDataSource::FlushClipboard](#flushclipboard)|呈现到剪贴板中的所有数据。|  
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|验证放到剪贴板上的数据仍然存在。|  
|[COleDataSource::OnRenderData](#onrenderdata)|检索属于延迟呈现的数据。|  
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|检索到的数据`CFile`延迟呈现的一部分。|  
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|检索到的数据`HGLOBAL`延迟呈现的一部分。|  
|[COleDataSource::OnSetData](#onsetdata)|调用以替换中的数据`COleDataSource`对象。|  
|[COleDataSource::SetClipboard](#setclipboard)|位置`COleDataSource`在剪贴板上的对象。|  
  
## <a name="remarks"></a>备注  
 你可以直接创建 OLE 数据源。 或者， [COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)类创建 OLE 数据源以响应其`CopyToClipboard`和`DoDragDrop`成员函数。 请参阅[COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard)有关的简要说明。 重写`OnGetClipboardData`为创建的客户端项或服务器项类将其他剪贴板格式添加到 OLE 数据源中的数据的成员函数`CopyToClipboard`或`DoDragDrop`成员函数。  
  
 无论何时你想要准备用于传输的数据，你应创建该类的对象，并用你使用最合适的方法为你的数据的数据填充它。 它将插入到数据源的方式直接受是否立即提供数据 （即时呈现） 或按需 （延迟呈现）。 对于每个在其中你要通过传递要使用的剪贴板格式提供数据的剪贴板格式 (和可选[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构)，调用[DelayRenderData](#delayrenderdata)。  
  
 有关数据源和数据传输的详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。 此外，本文[剪贴板主题](../../mfc/clipboard.md)描述的 OLE 剪贴板机制。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="cachedata"></a>  COleDataSource::CacheData  
 调用此函数可指定在其中数据提供在数据传输操作的格式。  
  
```  
void CacheData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 *cfFormat*  
 剪贴板格式是用来提供数据。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 *lpStgMedium*  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构，它包含指定的格式中的数据。  
  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构描述是用来提供数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果它是**NULL**，默认值用于中的其他字段中**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 您必须提供数据，因为通过使用即时呈现的此函数提供它。 直到您需要缓存数据。  
  
 提供数据使用[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构。 你还可以使用`CacheGlobalData`成员函数，如果你所提供的数据量是足够小，无法使用高效地传输`HGLOBAL`。  
  
 在调用后`CacheData` **ptd**的成员`lpFormatEtc`和内容`lpStgMedium`所拥有的数据对象，不是由调用方。  
  
 若要使用延迟的呈现，调用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关详细信息延迟呈现处理的 MFC，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的结构。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="cacheglobaldata"></a>  COleDataSource::CacheGlobalData  
 调用此函数可指定在其中数据提供在数据传输操作的格式。  
  
```  
void CacheGlobalData(
    CLIPFORMAT cfFormat,  
    HGLOBAL hGlobal,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 *cfFormat*  
 剪贴板格式是用来提供数据。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 *hGlobal*  
 包含指定的格式中的数据的全局内存块的句柄。  
  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构描述是用来提供数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果它是**NULL**，默认值用于中的其他字段中**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 此函数提供了使用即时呈现，因此调用函数; 时，必须提供数据的数据直到您需要缓存数据。 使用`CacheData`成员函数，如果你所提供的大量数据或者如果您需要的结构化的存储介质。  
  
 若要使用延迟的呈现，调用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关详细信息延迟呈现处理的 MFC，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的结构。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="coledatasource"></a>  COleDataSource::COleDataSource  
 构造 `COleDataSource` 对象。  
  
```  
COleDataSource();
```  
  
##  <a name="delayrenderdata"></a>  COleDataSource::DelayRenderData  
 调用此函数可指定在其中数据提供在数据传输操作的格式。  
  
```  
void DelayRenderData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 *cfFormat*  
 剪贴板格式是用来提供数据。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构描述是用来提供数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果它是**NULL**，默认值用于中的其他字段中**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 此函数提供了使用延迟呈现，以便不立即提供数据的数据。 [OnRenderData](#onrenderdata)或[OnRenderGlobalData](#onrenderglobaldata)成员函数调用以请求数据。  
  
 使用此函数，如果你不打算提供通过将数据`CFile`对象。 如果想要提供通过数据`CFile`对象，请调用[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关详细信息延迟呈现处理的 MFC，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 若要使用即时呈现，调用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成员函数。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的结构。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="delayrenderfiledata"></a>  COleDataSource::DelayRenderFileData  
 调用此函数可指定在其中数据提供在数据传输操作的格式。  
  
```  
void DelayRenderFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 *cfFormat*  
 剪贴板格式是用来提供数据。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构描述是用来提供数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果它是**NULL**，默认值用于中的其他字段中**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 此函数提供了使用延迟呈现，以便不立即提供数据的数据。 [OnRenderFileData](#onrenderfiledata)成员函数调用以请求数据。  
  
 使用此函数，如果想要使用`CFile`对象提供数据。 如果你不打算使用`CFile`对象，请调用[DelayRenderData](#delayrenderdata)成员函数。 有关详细信息延迟呈现处理的 MFC，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 若要使用即时呈现，调用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成员函数。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的结构。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="delaysetdata"></a>  COleDataSource::DelaySetData  
 调用此函数可支持更改数据源的内容。  
  
```  
void DelaySetData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 *cfFormat*  
 将用用于放置数据剪贴板格式。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构描述在其中的数据是要替换的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果它是**NULL**，默认值用于中的其他字段中**FORMATETC**结构。  
  
### <a name="remarks"></a>备注  
 [OnSetData](#onsetdata)这种情况下将由框架调用。 这仅框架返回的数据源时使用[COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)。 如果`DelaySetData`不调用，你`OnSetData`永远不会调用函数。 `DelaySetData` 应该为每个剪贴板调用或**FORMATETC**你支持的格式。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的结构。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="dodragdrop"></a>  Coledatasource:: Dodragdrop  
 调用`DoDragDrop`成员函数中通常执行拖放操作对此数据源， [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)处理程序。  
  
```  
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,  
    LPCRECT lpRectStartDrag = NULL,  
    COleDropSource* pDropSource = NULL);
```  
  
### <a name="parameters"></a>参数  
 *dwEffects*  
 拖放操作允许对此数据源。 可以是一个或多个以下：  
  
- `DROPEFFECT_COPY` 无法执行复制操作。  
  
- `DROPEFFECT_MOVE` 无法执行移动操作。  
  
- `DROPEFFECT_LINK` 无法建立从放置的数据到原始数据的链接。  
  
- `DROPEFFECT_SCROLL` 表示可能发生拖动滚动操作。  
  
 *lpRectStartDrag*  
 指向定义拖动实际开始的矩形的指针。 有关更多信息，请参见下面的“备注”部分。  
  
 *pDropSource*  
 指向以放置源。 如果**NULL**然后的默认实现[COleDropSource](../../mfc/reference/coledropsource-class.md)将使用。  
  
### <a name="return-value"></a>返回值  
 删除由拖放操作; 生成的影响否则为`DROPEFFECT_NONE`如果永远不会操作从开始是因为用户在离开所提供的矩形之前释放鼠标按钮。  
  
### <a name="remarks"></a>备注  
 拖放操作不会立即开始。 它等待，直到鼠标光标离开由指定的矩形*lpRectStartDrag*或之前已通过指定的毫秒数。 如果*lpRectStartDrag*是**NULL**，矩形的大小是一个像素。  
  
 注册表项设置由指定的延迟时间。 你可以通过调用来更改的延迟时间[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果未指定的延迟时间，使用默认值为 200 毫秒。 拖动延迟时间存储中，如下所示：  
  
-   Windows NT 拖延迟时间将存储在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Windows 3.x 拖延迟时间将存储在 WIN。INI 文件，[Windows} 部分。  
  
-   Windows 95/98 拖延迟时间将存储在 WIN 的缓存版本。INI。  
  
 有关深入了解如何拖动延迟信息存储在任一注册表或。INI 文件，请参阅[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) Windows SDK 中。  
  
 有关详细信息，请参阅文章[拖放： 实现放置源](../../mfc/drag-and-drop-implementing-a-drop-source.md)。  
  
##  <a name="empty"></a>  COleDataSource::Empty  
 调用此函数可对空`COleDataSource`的数据的对象。  
  
```  
void Empty();
```  
  
### <a name="remarks"></a>备注  
 同时缓存，因此可以重复使用延迟的呈现格式将清空。  
  
 有关详细信息，请参阅[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) Windows SDK 中。  
  
##  <a name="flushclipboard"></a>  COleDataSource::FlushClipboard  
 呈现数据，可在剪贴板上，然后可以在你的应用程序关闭后粘贴剪贴板中的数据。  
  
```  
static void PASCAL FlushClipboard();
```  
  
### <a name="remarks"></a>备注  
 使用[设置剪贴板](#setclipboard)以将数据放在剪贴板上。  
  
##  <a name="getclipboardowner"></a>  COleDataSource::GetClipboardOwner  
 确定是否在剪贴板上的数据已更改自[设置剪贴板](#setclipboard)上一次调用，并且，如果是这样，标识当前所有者。  
  
```  
static COleDataSource* PASCAL GetClipboardOwner();
```  
  
### <a name="return-value"></a>返回值  
 当前在剪贴板上，数据源或**NULL**如果没有任何内容复制到剪贴板上或不由调用应用程序拥有剪贴板。  
  
##  <a name="onrenderdata"></a>  COleDataSource::OnRenderData  
 由框架调用以检索指定的格式中的数据。  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>参数  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定在其中请求信息的格式。  
  
 *lpStgMedium*  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)是用要返回的数据的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是以前放置在`COleDataSource`对象使用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)延迟呈现的成员函数。 此函数的默认实现将调用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)是否提供的存储媒体文件或内存，分别。 如果提供了这些格式任一，默认实现将返回 0 并不执行任何操作。 有关详细信息延迟呈现处理的 MFC，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如果*lpStgMedium*-> *tymed*是**TYMED_NULL**、 **STGMEDIUM**应分配并填充为指定的*lpFormatEtc-> tymed*。 如果不是**TYMED_NULL**、 **STGMEDIUM**应填充了具有数据的位置。  
  
 这是一个高级可重写。 重写此函数可提供的请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你的数据较小，而且固定大小，重写`OnRenderGlobalData`。 如果你的数据是在文件中，或者是大小可变的重写`OnRenderFileData`。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构， [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227)枚举类型和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)在 Windows SDK 中。  
  
##  <a name="onrenderfiledata"></a>  COleDataSource::OnRenderFileData  
 由框架调用以检索指定的格式中的数据，当指定的存储介质文件。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>参数  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定在其中请求信息的格式。  
  
 *pFile*  
 指向[CFile](../../mfc/reference/cfile-class.md)对象是用要呈现的数据。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是以前放置在`COleDataSource`对象使用[DelayRenderData](#delayrenderdata)延迟呈现的成员函数。 此函数的默认实现只返回**FALSE**。  
  
 这是一个高级可重写。 重写此函数可提供的请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你想要处理多个存储媒体，重写[OnRenderData](#onrenderdata)。 如果你的数据是在文件中，或者是大小可变的重写`OnRenderFileData`。 有关详细信息延迟呈现处理的 MFC，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431) Windows SDK 中。  
  
##  <a name="onrenderglobaldata"></a>  COleDataSource::OnRenderGlobalData  
 由框架调用以检索指定的格式中的数据时指定的存储介质是全局内存。  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>参数  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定在其中请求信息的格式。  
  
 *phGlobal*  
 指向全局内存在其中的数据是要返回的句柄。 如果一个尚未尚未分配，此参数可以为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 指定的格式是以前放置在`COleDataSource`对象使用[DelayRenderData](#delayrenderdata)延迟呈现的成员函数。 此函数的默认实现只返回**FALSE**。  
  
 如果*phGlobal*是**NULL**，然后新`HGLOBAL`应分配，并且在返回*phGlobal*。 否则为`HGLOBAL`指定的*phGlobal*应已填满数据。 数据量置于`HGLOBAL`不能超过内存块的当前大小。 此外，块不能重新分配给了更大的大小。  
  
 这是一个高级可重写。 重写此函数可提供的请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你想要处理多个存储媒体，重写[OnRenderData](#onrenderdata)。 如果你的数据是在文件中，或者是大小可变的重写[OnRenderFileData](#onrenderfiledata)。 有关详细信息延迟呈现处理的 MFC，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431) Windows SDK 中。  
  
##  <a name="onsetdata"></a>  COleDataSource::OnSetData  
 由框架设置或替换中的数据调用`COleDataSource`中指定的格式对象。  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>参数  
 *lpFormatEtc*  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它指定在其中替换数据的格式。  
  
 *lpStgMedium*  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构，它包含的数据将替换的当前内容`COleDataSource`对象。  
  
 *bRelease*  
 指示有完成函数调用后的存储介质的所有权。 调用方决定谁负责释放代表的存储介质分配的资源。 通过设置的调用方执行此*bRelease*。 如果*bRelease*为非零值，数据源将获得所有权，释放该媒体，使用它完成。 当*bRelease*为 0，调用方保留所有权并且数据源可以仅为在调用期间使用的存储介质。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它已成功获取它，数据源不会对数据所有权。 也就是说，它才会所有权如果`OnSetData`返回 0。 如果数据源将获得所有权，它通过调用释放的存储介质[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)函数。  
  
 默认实现不执行任何操作。 重写此函数可替换指定的格式中的数据。 这是一个高级可重写。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构和[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)在 Windows SDK 中的函数。  
  
##  <a name="setclipboard"></a>  COleDataSource::SetClipboard  
 中包含的数据放入`COleDataSource`调用下列函数之一后剪贴板上的对象： [CacheData](#cachedata)， [CacheGlobalData](#cacheglobaldata)， [DelayRenderData](#delayrenderdata)，或[DelayRenderFileData](#delayrenderfiledata)。  
  
```  
void SetClipboard();
```  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDataObject 类](../../mfc/reference/coledataobject-class.md)
