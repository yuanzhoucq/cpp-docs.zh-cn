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
ms.openlocfilehash: e706489a84ad564949e2c2d3d193173fc19b9828
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426539"
---
# <a name="coledataobject-class"></a>COleDataObject 类

在数据传输中用于从剪贴板、通过拖放或从嵌入 OLE 项检索各种格式的数据。

## <a name="syntax"></a>语法

```
class COleDataObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleDataObject：： COleDataObject](#coledataobject)|构造 `COleDataObject` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleDataObject：： Attach](#attach)|将指定的 OLE 数据对象附加到 `COleDataObject`。|
|[COleDataObject：： AttachClipboard](#attachclipboard)|附加剪贴板上的数据对象。|
|[COleDataObject：： BeginEnumFormats](#beginenumformats)|准备一个或多个后续 `GetNextFormat` 调用。|
|[COleDataObject：:D etach](#detach)|分离关联的 `IDataObject` 对象。|
|[COleDataObject：：](#getdata)|以指定格式从附加的 OLE 数据对象复制数据。|
|[COleDataObject：： GetFileData](#getfiledata)|以指定的格式将数据从附加的 OLE 数据对象复制到 `CFile` 的指针。|
|[COleDataObject：： GetGlobalData](#getglobaldata)|以指定的格式将数据从附加的 OLE 数据对象复制到 `HGLOBAL`。|
|[COleDataObject：： GetNextFormat](#getnextformat)|返回下一个可用的数据格式。|
|[COleDataObject：： IsDataAvailable](#isdataavailable)|检查数据是否可用指定的格式。|
|[COleDataObject：： Release](#release)|分离并释放关联的 `IDataObject` 对象。|

## <a name="remarks"></a>备注

`COleDataObject` 没有基类。

这类数据传输包括源和目标。 数据源实现为[COleDataSource](../../mfc/reference/coledatasource-class.md)类的对象。 无论何时在目标应用程序中放置了数据或要求从剪贴板执行粘贴操作，都必须创建一个 `COleDataObject` 类的对象。

此类使你能够确定数据是否以指定格式存在。 您还可以枚举可用的数据格式，或检查给定的格式是否可用，然后以首选格式检索数据。 可以通过几种不同的方式完成对象检索，包括使用[CFile](../../mfc/reference/cfile-class.md)、HGLOBAL 或 `STGMEDIUM` 结构。

有关详细信息，请参阅 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构。

有关在应用程序中使用数据对象的详细信息，请参阅文章[数据对象和数据源（OLE）](../../mfc/data-objects-and-data-sources-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`COleDataObject`

## <a name="requirements"></a>要求

**标头：** afxole

##  <a name="attach"></a>COleDataObject：： Attach

调用此函数可将 `COleDataObject` 对象与 OLE 数据对象相关联。

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>parameters

*lpDataObject*<br/>
指向 OLE 数据对象。

*bAutoRelease*<br/>
如果在销毁 `COleDataObject` 对象时应释放 OLE 数据对象，则为 TRUE; 否则为 false。否则为 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 。

##  <a name="attachclipboard"></a>COleDataObject：： AttachClipboard

调用此函数可将当前位于剪贴板上的数据对象附加到 `COleDataObject` 的对象。

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

> [!NOTE]
>  调用此函数将锁定剪贴板，直到此数据对象被释放。 数据对象在 `COleDataObject`的析构函数中释放。 有关详细信息，请参阅 Win32 文档中的[OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) and [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) 。

##  <a name="beginenumformats"></a>COleDataObject：： BeginEnumFormats

调用此函数可准备对 `GetNextFormat` 的后续调用，以便检索项中的数据格式列表。

```
void BeginEnumFormats();
```

### <a name="remarks"></a>备注

调用 `BeginEnumFormats`后，将存储此数据对象支持的第一个格式的位置。 对 `GetNextFormat` 的后续调用将枚举数据对象中可用格式的列表。

若要以给定格式检查数据的可用性，请使用[COleDataObject：： IsDataAvailable](#isdataavailable)。

有关详细信息，请参阅 Windows SDK 中的[IDataObject：： EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) 。

##  <a name="coledataobject"></a>COleDataObject：： COleDataObject

构造 `COleDataObject` 对象。

```
COleDataObject();
```

### <a name="remarks"></a>备注

在调用其他 `COleDataObject` 函数之前，必须先调用[COleDataObject：： Attach](#attach)或[COleDataObject：： AttachClipboard](#attachclipboard) 。

> [!NOTE]
>  由于拖放处理程序的一个参数是指向 `COleDataObject`的指针，因此不需要调用此构造函数来支持拖放。

##  <a name="detach"></a>COleDataObject：:D etach

调用此函数可从其关联的 OLE 数据对象中分离 `COleDataObject` 对象，而无需释放数据对象。

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>返回值

指向已分离的 OLE 数据对象的指针。

### <a name="remarks"></a>备注

##  <a name="getdata"></a>COleDataObject：：

调用此函数可从项中检索指定格式的数据。

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>parameters

*cfFormat*<br/>
要返回的数据的格式。 此参数可以是预定义的剪贴板格式之一或本机 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpStgMedium*<br/>
指向将接收数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，该结构描述要返回的数据的格式。 如果要指定超出*cfFormat*指定的剪贴板格式的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于 `FORMATETC` 结构中的其他字段。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[IDataObject：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) [STGMEDIUM 和](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

有关详细信息，请参阅 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="getfiledata"></a>COleDataObject：： GetFileData

调用此函数可创建 `CFile` 或 `CFile`派生的对象，并将指定格式的数据检索到 `CFile` 指针中。

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>parameters

*cfFormat*<br/>
要返回的数据的格式。 此参数可以是预定义的剪贴板格式之一或本机 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，该结构描述要返回的数据的格式。 如果要指定超出*cfFormat*指定的剪贴板格式的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于 `FORMATETC` 结构中的其他字段。

### <a name="return-value"></a>返回值

如果成功，则为包含数据的新 `CFile` 或 `CFile`派生对象的指针;否则为 NULL。

### <a name="remarks"></a>备注

根据存储数据的介质，返回值指向的实际类型可能为 `CFile`、`CSharedFile`或 `COleStreamFile`。

> [!NOTE]
>  此函数的返回值所访问 `CFile` 对象由调用方拥有。 调用方负责**删除**`CFile` 对象，从而关闭文件。

有关详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

有关详细信息，请参阅 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="getglobaldata"></a>COleDataObject：： GetGlobalData

调用此函数以分配全局内存块，并将指定格式的数据检索到 HGLOBAL。

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>parameters

*cfFormat*<br/>
要返回的数据的格式。 此参数可以是预定义的剪贴板格式之一或本机 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构，该结构描述要返回的数据的格式。 如果要指定超出*cfFormat*指定的剪贴板格式的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于 `FORMATETC` 结构中的其他字段。

### <a name="return-value"></a>返回值

如果成功，则为包含数据的全局内存块的句柄;否则为 NULL。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

有关详细信息，请参阅 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

##  <a name="getnextformat"></a>COleDataObject：： GetNextFormat

重复调用此函数以获取可用于从项中检索数据的所有格式。

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>parameters

*lpFormatEtc*<br/>
指向当函数调用返回时接收格式信息的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

### <a name="return-value"></a>返回值

如果有其他格式可用，则为非零值;否则为0。

### <a name="remarks"></a>备注

调用[COleDataObject：： BeginEnumFormats](#beginenumformats)后，将存储此数据对象支持的第一个格式的位置。 对 `GetNextFormat` 的后续调用将枚举数据对象中可用格式的列表。 使用这些函数可以列出可用的格式。

若要检查给定格式的可用性，请调用[COleDataObject：： IsDataAvailable](#isdataavailable)。

有关详细信息，请参阅 Windows SDK 中的[IEnumXXXX：： Next](/previous-versions//ms695273\(v=vs.85\)) 。

##  <a name="isdataavailable"></a>COleDataObject：： IsDataAvailable

调用此函数可确定特定格式是否可用于从 OLE 项检索数据。

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>parameters

*cfFormat*<br/>
要在*lpFormatEtc*指向的结构中使用的剪贴板数据格式。 此参数可以是预定义的剪贴板格式之一或本机 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpFormatEtc*<br/>
指向描述所需格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 仅当要指定超出*cfFormat*指定的剪贴板格式的其他格式信息时，才为此参数提供值。 如果为 NULL，则默认值用于 `FORMATETC` 结构中的其他字段。

### <a name="return-value"></a>返回值

如果数据以指定的格式提供，则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数在调用 `GetData`、`GetFileData`或 `GetGlobalData`之前非常有用。

有关详细信息，请参阅 Windows SDK 中的[IDataObject：： QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata)和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

有关详细信息，请参阅 Windows SDK 中的[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 。

### <a name="example"></a>示例

  请参阅[CRichEditView：： QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata)的示例。

##  <a name="release"></a>COleDataObject：： Release

调用此函数以释放以前与 `COleDataObject` 对象关联的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)对象的所有权。

```
void Release();
```

### <a name="remarks"></a>备注

`IDataObject` 通过显式或通过框架调用 `Attach` 或 `AttachClipboard` 来与 `COleDataObject` 相关联。 如果 `Attach` 的*bAutoRelease*参数为 FALSE，则不会释放 `IDataObject` 对象。 在这种情况下，调用方负责通过调用[IUnknown：： Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)来释放 `IDataObject`。

## <a name="see-also"></a>另请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource 类](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem 类](../../mfc/reference/coleserveritem-class.md)
