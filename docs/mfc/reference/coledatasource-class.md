---
title: COleDataSource 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 539f3f1611d4d9d83d37754b66986c6b4f59549c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614196"
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
|[COleDataSource::CacheData](#cachedata)|提供在指定的格式中使用的数据`STGMEDIUM`结构。|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|提供了使用 HGLOBAL 指定格式的数据。|
|[COleDataSource::DelayRenderData](#delayrenderdata)|提供了使用延迟的呈现采用指定格式数据。|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|提供在指定的格式数据`CFile`指针。|
|[COleDataSource::DelaySetData](#delaysetdata)|中支持每种格式为调用`OnSetData`。|
|[Coledatasource:: Dodragdrop](#dodragdrop)|执行与数据源拖放操作。|
|[COleDataSource::Empty](#empty)|清空`COleDataSource`的数据的对象。|
|[COleDataSource::FlushClipboard](#flushclipboard)|将所有数据都呈现到剪贴板。|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|验证放置在剪贴板上的数据仍然存在。|
|[COleDataSource::OnRenderData](#onrenderdata)|检索数据作为延迟呈现的一部分。|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|检索到的数据`CFile`延迟呈现的一部分。|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|检索到的延迟呈现一部分 HGLOBAL 数据。|
|[COleDataSource::OnSetData](#onsetdata)|调用以替换中的数据`COleDataSource`对象。|
|[COleDataSource::SetClipboard](#setclipboard)|位置`COleDataSource`剪贴板上的对象。|

## <a name="remarks"></a>备注

您可以直接创建 OLE 数据源。 或者， [COleClientItem](../../mfc/reference/coleclientitem-class.md)并[COleServerItem](../../mfc/reference/coleserveritem-class.md)类创建 OLE 数据源来响应其`CopyToClipboard`和`DoDragDrop`成员函数。 请参阅[COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard)有关的简要说明。 重写`OnGetClipboardData`若要将附加剪贴板格式添加到 OLE 数据源中的数据在客户端项目或服务器项类成员函数为创建`CopyToClipboard`或`DoDragDrop`成员函数。

只要您想要准备用于传输的数据，应创建此类的对象并填充数据针对数据使用最合适的方法。 插入到数据源的方式直接受是否立即提供数据 （立即呈现） 或按需 （延迟的呈现）。 对于每个在其中将提供数据，通过传递要使用的剪贴板格式的剪贴板格式 (和可选[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构)，调用[DelayRenderData](#delayrenderdata)。

有关数据源和数据传输的详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。 此外，本文[剪贴板主题](../../mfc/clipboard.md)描述 OLE 剪贴板机制。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>要求

**标头：** afxole.h

##  <a name="cachedata"></a>  COleDataSource::CacheData

调用此函数可指定在其中数据在提供安全更新的数据传输操作的格式。

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
剪贴板格式，数据将会提供。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函数。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)结构，它包含指定的格式中的数据。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构描述，数据将提供的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果，则为 NULL，将对其他字段中使用默认值`FORMATETC`结构。

### <a name="remarks"></a>备注

您必须提供数据，因为此函数提供了通过使用直接呈现它。 需要时才被缓存数据。

提供使用数据[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)结构。 此外可以使用`CacheGlobalData`成员函数，如果你所提供的数据量是足够小，能够有效地使用 HGLOBAL 传输。

在调用`CacheData``ptd`的成员`lpFormatEtc`的内容*lpStgMedium*所拥有的数据对象，不是由调用方。

若要使用延迟的呈现，调用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关详细信息延迟呈现为 mfc 已处理，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)并[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的结构。

有关详细信息，请参阅[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="cacheglobaldata"></a>  COleDataSource::CacheGlobalData

调用此函数可指定在其中数据在提供安全更新的数据传输操作的格式。

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
剪贴板格式，数据将会提供。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函数。

*hGlobal*<br/>
包含指定的格式中的数据的全局内存块的句柄。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构描述，数据将提供的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果，则为 NULL，将对其他字段中使用默认值`FORMATETC`结构。

### <a name="remarks"></a>备注

此函数提供了使用立即呈现，因此调用函数; 时，必须提供数据的数据需要时才被缓存数据。 使用`CacheData`成员函数，如果你所提供的大量数据，或如果需要结构化的存储介质。

若要使用延迟的呈现，调用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关详细信息延迟呈现为 mfc 已处理，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的结构。

有关详细信息，请参阅[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="coledatasource"></a>  COleDataSource::COleDataSource

构造 `COleDataSource` 对象。

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>  COleDataSource::DelayRenderData

调用此函数可指定在其中数据在提供安全更新的数据传输操作的格式。

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
剪贴板格式，数据将会提供。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函数。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构描述，数据将提供的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果，则为 NULL，将对其他字段中使用默认值`FORMATETC`结构。

### <a name="remarks"></a>备注

此函数提供了使用延迟呈现，因此不立即提供数据的数据。 [OnRenderData](#onrenderdata)或[OnRenderGlobalData](#onrenderglobaldata)成员函数调用以请求数据。

如果您不打算提供通过将数据，请使用此函数`CFile`对象。 如果想要提供的数据通过`CFile`对象，请调用[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关详细信息延迟呈现为 mfc 已处理，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

若要使用立即呈现，调用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成员函数。

有关详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的结构。

有关详细信息，请参阅[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="delayrenderfiledata"></a>  COleDataSource::DelayRenderFileData

调用此函数可指定在其中数据在提供安全更新的数据传输操作的格式。

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
剪贴板格式，数据将会提供。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函数。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构描述，数据将提供的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果，则为 NULL，将对其他字段中使用默认值`FORMATETC`结构。

### <a name="remarks"></a>备注

此函数提供了使用延迟呈现，因此不立即提供数据的数据。 [OnRenderFileData](#onrenderfiledata)成员函数调用以请求数据。

使用此函数，如果要使用`CFile`要提供的数据对象。 如果您不打算使用`CFile`对象，请调用[DelayRenderData](#delayrenderdata)成员函数。 有关详细信息延迟呈现为 mfc 已处理，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

若要使用立即呈现，调用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成员函数。

有关详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的结构。

有关详细信息，请参阅[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="delaysetdata"></a>  COleDataSource::DelaySetData

调用此函数可支持更改数据源的内容。

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
剪贴板格式，数据将放置。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函数。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构描述，数据将被替换的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果，则为 NULL，将对其他字段中使用默认值`FORMATETC`结构。

### <a name="remarks"></a>备注

[OnSetData](#onsetdata)发生此情况时由框架调用。 这仅用时则框架将返回从数据源[COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)。 如果`DelaySetData`未调用你`OnSetData`将永远不会调用的函数。 `DelaySetData` 应为每个剪贴板调用或`FORMATETC`你支持的格式。

有关详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的结构。

有关详细信息，请参阅[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="dodragdrop"></a>  Coledatasource:: Dodragdrop

调用`DoDragDrop`成员函数中通常执行此数据源，拖放操作[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)处理程序。

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>参数

*dwEffects*<br/>
拖放操作允许对此数据源。 可以是一个或多项操作：

- DROPEFFECT_COPY 无法执行复制操作。

- DROPEFFECT_MOVE 无法执行移动操作。

- 无法建立从放置的数据的原始数据的 DROPEFFECT_LINK 一个链接。

- DROPEFFECT_SCROLL 指示拖动滚动操作可能会发生的。

*lpRectStartDrag*<br/>
向定义实际开始拖动该矩形的指针。 有关更多信息，请参见下面的“备注”部分。

*pDropSource*<br/>
指向以放置源。 如果 NULL 则的默认实现[COleDropSource](../../mfc/reference/coledropsource-class.md)将使用。

### <a name="return-value"></a>返回值

删除生成的拖放操作; 的效果否则为 DROPEFFECT_NONE 如果因为用户释放鼠标按钮后才能离开所提供的矩形，永远不会以开始该操作。

### <a name="remarks"></a>备注

拖放操作不会立即启动。 它等待，直到鼠标光标离开所指定的矩形*lpRectStartDrag*或之前已通过指定的毫秒数。 如果*lpRectStartDrag*为 NULL，矩形的大小是一个像素。

注册表项设置由指定的延迟时间。 您可以通过调用来更改延迟时间[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果未指定延迟时间，使用默认值为 200 毫秒。 将延迟时间存储中，如下所示：

- Windows NT 将延迟时间将存储在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。

- Windows 3.x 拖动延迟时间将存储在 WIN。INI 文件，[Windows} 部分。

- Windows 95/98 拖动延迟时间将存储在 WIN 的缓存版本。INI。

详细了解如何将拖动的延迟信息存储在任一注册表或。INI 文件，请参阅[WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) Windows SDK 中。

有关详细信息，请参阅文章[拖放： 实现放置源](../../mfc/drag-and-drop-implementing-a-drop-source.md)。

##  <a name="empty"></a>  COleDataSource::Empty

调用此函数可对空`COleDataSource`的数据的对象。

```
void Empty();
```

### <a name="remarks"></a>备注

同时缓存，以便可以重用延迟呈现格式将清空。

有关详细信息，请参阅[ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) Windows SDK 中。

##  <a name="flushclipboard"></a>  COleDataSource::FlushClipboard

呈现数据，可在剪贴板上，然后您可以将数据从剪贴板粘贴后关闭应用程序。

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>备注

使用[设置剪贴板](#setclipboard)若要将数据放到剪贴板上。

##  <a name="getclipboardowner"></a>  COleDataSource::GetClipboardOwner

确定剪贴板中的数据已更改以来[设置剪贴板](#setclipboard)上一次调用，并且，如果是这样，标识当前所有者。

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>返回值

数据源当前在剪贴板上，或如果没有任何内容复制到剪贴板上，或如果剪贴板不归调用应用程序，则为 NULL。

##  <a name="onrenderdata"></a>  COleDataSource::OnRenderData

由框架调用以检索指定格式的数据。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构，它指定为请求信息的格式。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) ，数据将返回的结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)延迟呈现的成员函数。 此函数的默认实现将调用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)如果提供的存储介质是文件或内存，分别。 如果提供了这些格式任一的默认实现将返回 0 并不执行任何操作。 有关详细信息延迟呈现为 mfc 已处理，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如果*lpStgMedium*-> *tymed*是 TYMED_NULL，`STGMEDIUM`应分配并由指定填充*lpFormatEtc-> tymed*。 如果不是 TYMED_NULL，`STGMEDIUM`应在具有数据的位置填充。

这是一种高级可重写。 重写此函数可提供请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你的数据较小且大小固定，重写`OnRenderGlobalData`。 如果数据是在文件中，或者是大小可变的重写`OnRenderFileData`。

有关详细信息，请参阅[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)和[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构[TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed)枚举类型，以及[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata)在 Windows SDK 中。

##  <a name="onrenderfiledata"></a>  COleDataSource::OnRenderFileData

由框架调用以检索指定格式的数据时指定的存储介质是一个文件。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构，它指定为请求信息的格式。

*pFile*<br/>
指向[CFile](../../mfc/reference/cfile-class.md) ，数据将呈现的对象。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](#delayrenderdata)延迟呈现的成员函数。 此函数的默认实现只是返回 FALSE。

这是一种高级可重写。 重写此函数可提供请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你想要处理多个存储媒体，重写[OnRenderData](#onrenderdata)。 如果数据是在文件中，或者是大小可变的重写`OnRenderFileData`。 有关详细信息延迟呈现为 mfc 已处理，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构并[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) Windows SDK 中。

##  <a name="onrenderglobaldata"></a>  COleDataSource::OnRenderGlobalData

由框架调用以检索指定格式的数据时指定的存储介质是全局内存。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构，它指定为请求信息的格式。

*phGlobal*<br/>
指向全局内存，数据将返回的句柄。 如果其中一个具有尚未分配，此参数可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是一个以前放置在`COleDataSource`对象使用[DelayRenderData](#delayrenderdata)延迟呈现的成员函数。 此函数的默认实现只是返回 FALSE。

如果*phGlobal*为 NULL，则应分配并返回新 HGLOBAL *phGlobal*。 否则，HGLOBAL 指定*phGlobal*应填充数据。 在 HGLOBAL 中放置的数据量不能超过内存块的当前大小。 此外，块不能重新分配给较大的大小。

这是一种高级可重写。 重写此函数可提供请求的格式和介质中的数据。 具体取决于你的数据，你可能想要改为重写此函数的其他版本之一。 如果你想要处理多个存储媒体，重写[OnRenderData](#onrenderdata)。 如果数据是在文件中，或者是大小可变的重写[OnRenderFileData](#onrenderfiledata)。 有关详细信息延迟呈现为 mfc 已处理，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构并[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) Windows SDK 中。

##  <a name="onsetdata"></a>  COleDataSource::OnSetData

由框架调用以设置或替换中的数据`COleDataSource`中指定的格式对象。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构，它指定在其中替换数据的格式。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)结构，它包含的数据的当前内容将替换为`COleDataSource`对象。

*bRelease*<br/>
指示谁完成函数调用后有存储介质的所属权。 调用方决定由谁来负责释放存储介质代表分配的资源。 调用方通过设置执行此*bRelease*。 如果*bRelease*为非零值，数据源将获得所有权，使用它完成时释放该介质。 当*bRelease*为 0、 保留所有权，调用方和数据源可以专用于在调用期间使用的存储介质。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

它已成功地获取它，数据源才会对数据所有权。 也就是说，它不会所有权如果`OnSetData`返回 0。 如果数据源采用所有权，它通过调用释放存储介质[ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium)函数。

默认实现不执行任何操作。 重写此函数可替换指定的格式中的数据。 这是一种高级可重写。

有关详细信息，请参阅[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)并[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构并[ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium)并[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的函数。

##  <a name="setclipboard"></a>  COleDataSource::SetClipboard

中包含的数据将放`COleDataSource`调用下列函数之一后在剪贴板上的对象： [CacheData](#cachedata)， [CacheGlobalData](#cacheglobaldata)， [DelayRenderData](#delayrenderdata)，或[DelayRenderFileData](#delayrenderfiledata)。

```
void SetClipboard();
```

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../visual-cpp-samples.md)<br/>
[MFC 示例 OCLIENT](../../visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject 类](../../mfc/reference/coledataobject-class.md)
