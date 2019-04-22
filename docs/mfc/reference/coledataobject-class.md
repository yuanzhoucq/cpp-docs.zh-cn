---
title: COleDataObject 类
ms.date: 11/04/2016
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
ms.openlocfilehash: 24d79c684226d57839161946255781c3bdd5a043
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779087"
---
# <a name="coledataobject-class"></a>COleDataObject 类

在数据传输中用于从剪贴板、通过拖放或从嵌入 OLE 项检索各种格式的数据。

## <a name="syntax"></a>语法

```
class COleDataObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|构造 `COleDataObject` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDataObject::Attach](#attach)|将附加到指定的 OLE 数据对象`COleDataObject`。|
|[COleDataObject::AttachClipboard](#attachclipboard)|将附加剪贴板上的数据对象。|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|准备一个或更多后续`GetNextFormat`调用。|
|[COleDataObject::Detach](#detach)|分离关联`IDataObject`对象。|
|[COleDataObject::GetData](#getdata)|将数据从指定的格式中的附加 OLE 数据对象。|
|[COleDataObject::GetFileData](#getfiledata)|将数据复制到此附加 OLE 数据对象中`CFile`指针指定的格式。|
|[COleDataObject::GetGlobalData](#getglobaldata)|将数据复制到此附加 OLE 数据对象中`HGLOBAL`中指定的格式。|
|[COleDataObject::GetNextFormat](#getnextformat)|返回下一个可用的数据格式。|
|[COleDataObject::IsDataAvailable](#isdataavailable)|检查数据是否在指定的格式中可用。|
|[COleDataObject::Release](#release)|分离，并释放关联`IDataObject`对象。|

## <a name="remarks"></a>备注

`COleDataObject` 没有基类。

这些类型的数据传输包括源和目标。 数据源的对象作为实现[COleDataSource](../../mfc/reference/coledatasource-class.md)类。 只要目标应用程序已在其中放置的数据或需要从剪贴板的对象执行粘贴操作`COleDataObject`必须在创建类。

此类使您能够确定数据是否存在指定的格式。 您可以还枚举可用的数据格式或检查给定的格式是否可用，然后检索中的首选格式的数据。 可以采用多种不同的方法，包括使用完成对象检索[CFile](../../mfc/reference/cfile-class.md)、 HGLOBAL，或一个`STGMEDIUM`结构。

有关详细信息，请参阅[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) Windows SDK 中的结构。

有关在应用程序中使用数据对象的详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`COleDataObject`

## <a name="requirements"></a>要求

**标头：** afxole.h

##  <a name="attach"></a>  COleDataObject::Attach

调用此函数可将关联`COleDataObject`与 OLE 数据对象的对象。

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>参数

*lpDataObject*<br/>
指向 OLE 数据对象。

*bAutoRelease*<br/>
如果 OLE 数据对象应为 TRUE 时释放`COleDataObject`对象是销毁; 否则为 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) Windows SDK 中。

##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard

调用此函数可将附加到剪贴板上的当前数据对象`COleDataObject`对象。

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

> [!NOTE]
>  调用此函数将锁定剪贴板，直至发布此数据对象。 中的析构函数释放的数据对象`COleDataObject`。 有关详细信息，请参阅[打开剪贴板](/windows/desktop/api/winuser/nf-winuser-openclipboard)并[CloseClipboard](/windows/desktop/api/winuser/nf-winuser-closeclipboard) Win32 文档中。

##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats

调用此函数可准备对后续调用`GetNextFormat`从该项中检索的数据格式的列表。

```
void BeginEnumFormats();
```

### <a name="remarks"></a>备注

在调用`BeginEnumFormats`，存储此数据对象支持的第一种格式的位置。 连续调用`GetNextFormat`将枚举数据对象中的可用格式的列表。

若要检查给定格式的数据的可用性，请使用[COleDataObject::IsDataAvailable](#isdataavailable)。

有关详细信息，请参阅[IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) Windows SDK 中。

##  <a name="coledataobject"></a>  COleDataObject::COleDataObject

构造 `COleDataObject` 对象。

```
COleDataObject();
```

### <a name="remarks"></a>备注

调用[COleDataObject::Attach](#attach)或[COleDataObject::AttachClipboard](#attachclipboard)必须在调用其他之前进行`COleDataObject`函数。

> [!NOTE]
>  由于一个拖放处理程序的参数是一个指向`COleDataObject`，无需调用此构造函数，以支持拖放功能。

##  <a name="detach"></a>  COleDataObject::Detach

调用此函数可分离`COleDataObject`而未释放的数据对象及其相关联的 OLE 数据对象中的对象。

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>返回值

指向已分离的 OLE 数据对象的指针。

### <a name="remarks"></a>备注

##  <a name="getdata"></a>  COleDataObject::GetData

调用此函数可从指定的格式项中检索数据。

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
数据将返回格式。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函数。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)将接收数据的结构。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构描述是用来返回数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果它为 NULL，对其他字段中使用的默认值`FORMATETC`结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata)， [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)，并[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

有关详细信息，请参阅[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="getfiledata"></a>  COleDataObject::GetFileData

调用此函数可创建`CFile`或`CFile`-派生的对象和检索到指定的格式中的数据`CFile`指针。

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
数据将返回格式。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函数。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构描述是用来返回数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果它为 NULL，对其他字段中使用的默认值`FORMATETC`结构。

### <a name="return-value"></a>返回值

指向新指针`CFile`或`CFile`-派生的对象包含的数据，如果成功，否则该值为 NULL。

### <a name="remarks"></a>备注

具体取决于数据存储在介质，返回值指向的实际类型可能`CFile`， `CSharedFile`，或`COleStreamFile`。

> [!NOTE]
>  `CFile`由调用方拥有访问此函数的返回值的对象。 调用方负责**删除**`CFile`对象，从而关闭文件。

有关详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

有关详细信息，请参阅[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData

调用此函数来分配全局内存块，并将指定的格式的数据检索到 HGLOBAL。

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
数据将返回格式。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函数。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构描述是用来返回数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果它为 NULL，对其他字段中使用的默认值`FORMATETC`结构。

### <a name="return-value"></a>返回值

包含数据，如果成功，则全局内存块的句柄否则为，为 NULL。

### <a name="remarks"></a>备注

有关详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

有关详细信息，请参阅[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat

调用此函数重复可获取所有可用于从项中检索数据的格式。

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)函数调用返回时收到格式信息的结构。

### <a name="return-value"></a>返回值

如果另一个格式为可用，则非零值否则为 0。

### <a name="remarks"></a>备注

在调用[COleDataObject::BeginEnumFormats](#beginenumformats)，存储此数据对象支持的第一种格式的位置。 连续调用`GetNextFormat`将枚举数据对象中的可用格式的列表。 使用这些函数以列出可用的格式。

若要检查给定格式的可用性，请调用[COleDataObject::IsDataAvailable](#isdataavailable)。

有关详细信息，请参阅[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) Windows SDK 中。

##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable

调用此函数可确定特定的格式是否可用于从 OLE 项检索数据。

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
指向要在结构中使用的剪贴板数据格式*lpFormatEtc*。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函数。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)结构描述所需的格式。 为此参数提供一个值，仅当你想要指定超出指定的剪贴板格式的格式的其他信息*cfFormat*。 如果它为 NULL，对其他字段中使用的默认值`FORMATETC`结构。

### <a name="return-value"></a>返回值

如果指定的格式; 中有数据的非零值否则为 0。

### <a name="remarks"></a>备注

此函数很有用，然后再调用`GetData`， `GetFileData`，或`GetGlobalData`。

有关详细信息，请参阅[IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata)并[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

有关详细信息，请参阅[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata)。

##  <a name="release"></a>  COleDataObject::Release

调用此函数可释放的所有权[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)以前有关联的对象`COleDataObject`对象。

```
void Release();
```

### <a name="remarks"></a>备注

`IDataObject`与关联`COleDataObject`通过调用`Attach`或`AttachClipboard`显式或框架。 如果*bAutoRelease*的参数`Attach`为 FALSE，`IDataObject`不会释放对象。 在这种情况下，调用方负责释放`IDataObject`通过调用[iunknown:: Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)。

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource 类](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem 类](../../mfc/reference/coleserveritem-class.md)
