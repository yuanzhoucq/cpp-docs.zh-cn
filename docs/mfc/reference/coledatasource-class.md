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
ms.openlocfilehash: 8746be43e3f2a31558904323392983b183d4f198
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753895"
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
|[COleData 来源：COleData 来源](#coledatasource)|构造 `COleDataSource` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleData 来源：缓存数据](#cachedata)|使用`STGMEDIUM`结构以指定格式提供数据。|
|[COleData 来源：缓存全球数据](#cacheglobaldata)|使用 HGLOBAL 以指定格式提供数据。|
|[COleData 来源：:DelayRenderData](#delayrenderdata)|使用延迟呈现以指定格式提供数据。|
|[COleData 来源：:DelayRender文件数据](#delayrenderfiledata)|在`CFile`指针中提供指定格式的数据。|
|[COleData 来源：:DelaySetData](#delaysetdata)|调用 中`OnSetData`支持的每个格式。|
|[COleData 来源：:DoDragDrop](#dodragdrop)|使用数据源执行拖放操作。|
|[COleData 来源：：空](#empty)|清空数据`COleDataSource`对象。|
|[COleData 来源：：Flush 剪板](#flushclipboard)|将所有数据渲染到剪贴板。|
|[COleData 来源：获取剪贴板所有者](#getclipboardowner)|验证放置在剪贴板上的数据是否仍然存在。|
|[COleData 来源：在渲染数据上](#onrenderdata)|检索数据作为延迟呈现的一部分。|
|[COleData 来源：在渲染文件数据上](#onrenderfiledata)|将数据检索到 作为`CFile`延迟呈现的一部分。|
|[COleData 来源：在渲染全球数据上](#onrenderglobaldata)|将数据检索到 HGLOBAL 中，作为延迟呈现的一部分。|
|[COleData 来源：OnSetData](#onsetdata)|调用以替换对象中`COleDataSource`的数据。|
|[COleData 来源：：设置剪贴板](#setclipboard)|将`COleDataSource`对象放在剪贴板上。|

## <a name="remarks"></a>备注

您可以直接创建 OLE 数据源。 或者[，COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem 类](../../mfc/reference/coleserveritem-class.md)创建 OLE 数据源以响应`CopyToClipboard`它们`DoDragDrop`和成员函数。 有关简要说明，请参阅[COleServer 项目：复制到剪贴板](../../mfc/reference/coleserveritem-class.md#copytoclipboard)。 重写客户端`OnGetClipboardData`项或服务器项类的成员函数，以向为`CopyToClipboard`或`DoDragDrop`成员函数创建的 OLE 数据源中的数据添加其他剪贴板格式。

每当您想要为传输准备数据时，都应创建此类的对象，并使用最适合数据的方法填充数据。 将数据插入到数据源的方式受是立即提供（立即呈现）还是按需（延迟呈现）的直接影响。 对于通过传递要使用的剪贴板格式（和可选[的 FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构）提供数据的每个剪贴板格式，调用[DelayRenderData](#delayrenderdata)。

有关数据源和数据传输的详细信息，请参阅文章["数据对象和数据源 （OLE）"。](../../mfc/data-objects-and-data-sources-ole.md) 此外，文章[剪贴板主题](../../mfc/clipboard.md)描述了 OLE 剪贴板机制。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coledatasourcecachedata"></a><a name="cachedata"></a>COleData 来源：缓存数据

调用此函数以指定在数据传输操作期间提供数据的格式。

```cpp
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
提供数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一，也可以是本机 Windows[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpStg 中*<br/>
指向包含指定格式数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构。

*lpFormatEtc*<br/>
指向描述提供数据的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 如果要指定*cfFormat*指定的剪贴板格式之外的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于`FORMATETC`结构中的其他字段。

### <a name="remarks"></a>备注

您必须提供数据，因为此函数使用即时呈现来提供数据。 数据将缓存到需要为止。

使用[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构提供数据。 如果提供的数据量足够`CacheGlobalData`小，可以使用 HGLOBAL 高效地传输，则可以使用成员函数。

对`CacheData` `ptd` *lpStgMedia* `lpFormatEtc`的成员和内容的调用后，由数据对象拥有，而不是由调用方拥有。

要使用延迟渲染，请致电[延迟渲染数据](#delayrenderdata)或[延迟呈现文件数据](#delayrenderfiledata)成员函数。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章["数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)"。

有关详细信息，请参阅 Windows SDK 中的[STG中](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

有关详细信息，请参阅 Windows SDK 中的[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a>COleData 来源：缓存全球数据

调用此函数以指定在数据传输操作期间提供数据的格式。

```cpp
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
提供数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一，也可以是本机 Windows[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*hGlobal*<br/>
以指定的格式处理包含数据的全局内存块。

*lpFormatEtc*<br/>
指向描述提供数据的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 如果要指定*cfFormat*指定的剪贴板格式之外的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于`FORMATETC`结构中的其他字段。

### <a name="remarks"></a>备注

此函数使用即时呈现提供数据，因此在调用 函数时必须提供数据;因此，在调用 函数时，必须提供数据。数据被缓存，直到需要为止。 如果要提供大量`CacheData`数据，或者需要结构化存储介质，请使用成员函数。

要使用延迟渲染，请致电[延迟渲染数据](#delayrenderdata)或[延迟呈现文件数据](#delayrenderfiledata)成员函数。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章["数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)"。

有关详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

有关详细信息，请参阅 Windows SDK 中的[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcecoledatasource"></a><a name="coledatasource"></a>COleData 来源：COleData 来源

构造 `COleDataSource` 对象。

```
COleDataSource();
```

## <a name="coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a>COleData 来源：:DelayRenderData

调用此函数以指定在数据传输操作期间提供数据的格式。

```cpp
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
提供数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一，也可以是本机 Windows[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpFormatEtc*<br/>
指向描述提供数据的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 如果要指定*cfFormat*指定的剪贴板格式之外的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于`FORMATETC`结构中的其他字段。

### <a name="remarks"></a>备注

此函数使用延迟呈现提供数据，因此不会立即提供数据。 调用[OnRenderData](#onrenderdata)或[OnRenderGlobalData](#onrenderglobaldata)成员函数来请求数据。

如果不通过对象提供数据，`CFile`请使用此功能。 如果要通过`CFile`对象提供数据，请调用[DelayRenderFileData](#delayrenderfiledata)成员函数。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章["数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)"。

要使用即时呈现，请调用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成员函数。

有关详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

有关详细信息，请参阅 Windows SDK 中的[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a>COleData 来源：:DelayRender文件数据

调用此函数以指定在数据传输操作期间提供数据的格式。

```cpp
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
提供数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一，也可以是本机 Windows[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpFormatEtc*<br/>
指向描述提供数据的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 如果要指定*cfFormat*指定的剪贴板格式之外的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于`FORMATETC`结构中的其他字段。

### <a name="remarks"></a>备注

此函数使用延迟呈现提供数据，因此不会立即提供数据。 调用[OnRenderFileData](#onrenderfiledata)成员函数来请求数据。

如果要使用`CFile`对象来提供数据，请使用此功能。 如果不使用对象，`CFile`请调用[DelayRenderData](#delayrenderdata)成员函数。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章["数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)"。

要使用即时呈现，请调用[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成员函数。

有关详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

有关详细信息，请参阅 Windows SDK 中的[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcedelaysetdata"></a><a name="delaysetdata"></a>COleData 来源：:DelaySetData

调用此函数以支持更改数据源的内容。

```cpp
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
要放置数据的剪贴板格式。 此参数可以是预定义的剪贴板格式之一，也可以是本机 Windows[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpFormatEtc*<br/>
指向描述要替换数据的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 如果要指定*cfFormat*指定的剪贴板格式之外的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于`FORMATETC`结构中的其他字段。

### <a name="remarks"></a>备注

发生这种情况时，框架将调用[OnSetData。](#onsetdata) 仅当框架从[COleServerItem 返回数据源时，才使用此选项：getDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)。 如果未`DelaySetData`调用，则永远不会调用`OnSetData`函数。 `DelaySetData`应针对您支持的每个剪贴板`FORMATETC`或格式调用。

有关详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

有关详细信息，请参阅 Windows SDK 中的[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledatasourcedodragdrop"></a><a name="dodragdrop"></a>COleData 来源：:DoDragDrop

调用`DoDragDrop`成员函数以对此数据源执行拖放操作，通常在[CWnd：：OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)处理程序中。

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>参数

*dwEffects*<br/>
在此数据源上允许的拖放操作。 可以是以下一种或多项：

- DROPEFFECT_COPY 可以执行复制操作。

- DROPEFFECT_MOVE可以执行移动操作。

- DROPEFFECT_LINK 可以建立从删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示可能发生拖动滚动操作。

*lpRect开始拖动*<br/>
指向定义拖动实际开始位置的矩形的指针。 有关更多信息，请参见下面的“备注”部分。

*pDrop来源*<br/>
指向放置源。 如果 NULL，则将使用[COleDropSource](../../mfc/reference/coledropsource-class.md)的默认实现。

### <a name="return-value"></a>返回值

拖放操作生成的拖放效果;否则，如果操作从未开始，则DROPEFFECT_NONE，因为用户在离开提供的矩形之前释放了鼠标按钮。

### <a name="remarks"></a>备注

拖放操作不会立即启动。 它等待鼠标光标离开*lpRectStartDrag 指定的*矩形或直到经过指定数量的毫秒。 如果*lpRectStartDrag*是 NULL，则矩形的大小为一个像素。

延迟时间由注册表键设置指定。 您可以通过调用[CWinApp：：WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[CWinApp：：WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint)来更改延迟时间。 如果不指定延迟时间，则使用默认值 200 毫秒。 拖动延迟时间存储如下：

- Windows NT 拖动延迟时间存储在HKEY_LOCAL_MACHINE_SOFTWARE_微软\Windows_NT_当前版本\iniFile映射\win.ini_Windows_Dragdelay。

- Windows 3.x 拖动延迟时间存储在 WIN 中。INI 文件，在 [Windows] 部分下。

- Windows 95/98 拖动延迟时间存储在 WIN 的缓存版本中。Ini。

有关拖动延迟信息如何存储在注册表或 中的详细信息。INI 文件，请参阅 Windows SDK 中的[写入配置文件字符串](/windows/win32/api/winbase/nf-winbase-writeprofilestringw)。

有关详细信息，请参阅文章 OLE[拖放](../../mfc/drag-and-drop-ole.md)。

## <a name="coledatasourceempty"></a><a name="empty"></a>COleData 来源：：空

调用此函数以清空数据`COleDataSource`对象。

```cpp
void Empty();
```

### <a name="remarks"></a>备注

缓存和延迟渲染格式都将清空，以便可以重复使用。

有关详细信息，请参阅 Windows SDK 中的[发布StgMedia。](/windows/win32/api/ole2/nf-ole2-releasestgmedium)

## <a name="coledatasourceflushclipboard"></a><a name="flushclipboard"></a>COleData 来源：：Flush 剪板

渲染剪贴板上的数据，然后允许您在应用程序关闭后粘贴剪贴板中的数据。

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>备注

使用[SetClip 板](#setclipboard)将数据放在剪贴板上。

## <a name="coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a>COleData 来源：获取剪贴板所有者

确定自上次调用[SetClipboard](#setclipboard)以来，剪贴板上的数据是否已更改，如果是，则标识当前所有者。

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>返回值

如果剪贴板上没有任何内容或剪贴板不是调用应用程序所有，则当前剪贴板上的数据源或 NULL。

## <a name="coledatasourceonrenderdata"></a><a name="onrenderdata"></a>COleData 来源：在渲染数据上

框架调用以检索指定格式的数据。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定请求信息的格式。

*lpStg 中*<br/>
指向要返回数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前使用`COleDataSource`[延迟渲染数据](#delayrenderdata)或[延迟渲染文件](#delayrenderfiledata)成员函数放置在对象中的格式，用于延迟渲染。 如果提供的存储介质分别是文件或内存，则此函数的默认实现将调用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData。](#onrenderglobaldata) 如果未提供这两种格式，则默认实现将返回 0，并且不执行任何操作。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章["数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)"。

如果*lpStg 中*-> *tymed* TYMED_NULL，`STGMEDIUM`则应按*lpFormatEtc->tymed*指定的分配和填充。 如果未TYMED_NULL，`STGMEDIUM`则应用数据填充 。

这是一个高级的可重写。 重写此函数以请求的格式和介质提供数据。 根据数据的不同，您可能希望重写此函数的其他版本之一。 如果数据较小且大小固定，请重写`OnRenderGlobalData`。 如果数据位于文件中，或者大小可变，请重写`OnRenderFileData`。

有关详细信息，请参阅[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构[、TYMED](/windows/win32/api/objidl/ne-objidl-tymed)枚举类型和[IDataObject：获取](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的数据。

## <a name="coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a>COleData 来源：在渲染文件数据上

当指定的存储介质是文件时，框架调用以指定格式检索数据。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定请求信息的格式。

*pFile*<br/>
指向要呈现数据的[CFile](../../mfc/reference/cfile-class.md)对象。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前使用`COleDataSource`[DelayRenderData](#delayrenderdata)成员函数放置在对象中的格式，用于延迟渲染。 此函数的默认实现仅返回 FALSE。

这是一个高级的可重写。 重写此函数以请求的格式和介质提供数据。 根据数据的不同，您可能希望重写此函数的其他版本之一。 如果要处理多个存储媒体，则重写[OnRenderData](#onrenderdata)。 如果数据位于文件中，或者大小可变，请重写`OnRenderFileData`。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章["数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)"。

有关详细信息，请参阅[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构和[IDataObject：：获取](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的数据。

## <a name="coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleData 来源：在渲染全球数据上

当指定的存储介质是全局内存时，框架调用以指定格式检索数据。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定请求信息的格式。

*phGlobal*<br/>
指向要返回数据的全局内存的句柄。 如果尚未分配，则此参数可以是 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

指定的格式是以前使用`COleDataSource`[DelayRenderData](#delayrenderdata)成员函数放置在对象中的格式，用于延迟渲染。 此函数的默认实现仅返回 FALSE。

如果*phGlobal*为 NULL，则应在 phGLOBAL 中分配并返回新的*HGLOBAL。* 否则 *，phGLOBAL*指定的 HGLOBAL 应填充数据。 放置在 HGLOBAL 中的数据量不得超过内存块的当前大小。 此外，块无法重新分配到更大的大小。

这是一个高级的可重写。 重写此函数以请求的格式和介质提供数据。 根据数据的不同，您可能希望重写此函数的其他版本之一。 如果要处理多个存储媒体，则重写[OnRenderData](#onrenderdata)。 如果数据位于文件中，或者大小可变，请覆盖[OnRenderFileData](#onrenderfiledata)。 有关 MFC 处理的延迟呈现的详细信息，请参阅文章["数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)"。

有关详细信息，请参阅[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构和[IDataObject：：获取](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的数据。

## <a name="coledatasourceonsetdata"></a><a name="onsetdata"></a>COleData 来源：OnSetData

框架调用以指定格式设置或替换对象中`COleDataSource`的数据。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，指定要替换数据的格式。

*lpStg 中*<br/>
指向包含将替换`COleDataSource`对象当前内容的数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构。

*b释放*<br/>
指示谁在完成函数调用后拥有存储介质的所有权。 调用方决定由谁负责释放代表存储介质分配的资源。 调用方通过设置*bRelease*来进行此用。 如果*bRelease*是非零，数据源将取得所有权，在它完成使用后释放媒体。 当*bRelease*为 0 时，调用方将保留所有权，数据源只能在呼叫期间使用存储介质。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

数据源在成功获取数据之前不会取得数据的所有权。 也就是说，如果`OnSetData`返回 0，它不拥有所有权。 如果数据源拥有所有权，则通过调用[ReleaseStgMedia](/windows/win32/api/ole2/nf-ole2-releasestgmedium)函数释放存储介质。

默认实现不执行任何操作。 重写此函数以替换指定格式的数据。 这是一个高级的可重写。

有关详细信息，请参阅[STGMEDIA](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构以及[发布媒体](/windows/win32/api/ole2/nf-ole2-releasestgmedium)和[IDataObject：获取 Windows](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) SDK 中的数据功能。

## <a name="coledatasourcesetclipboard"></a><a name="setclipboard"></a>COleData 来源：：设置剪贴板

调用以下函数之一后`COleDataSource`，将对象中包含的数据放在剪贴板上：[缓存数据](#cachedata)、[缓存全局数据](#cacheglobaldata)、[延迟呈现数据](#delayrenderdata)或[延迟呈现文件数据](#delayrenderfiledata)。

```cpp
void SetClipboard();
```

## <a name="see-also"></a>请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject 类](../../mfc/reference/coledataobject-class.md)
