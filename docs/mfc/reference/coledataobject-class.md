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
ms.openlocfilehash: 8b9565382de8ae731c166f60a0d1994c1b948a7b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753905"
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
|[COleData对象：COleData对象](#coledataobject)|构造 `COleDataObject` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleData对象：附加](#attach)|将指定的 OLE 数据对象附加到`COleDataObject`。|
|[COleData对象：：附加剪板](#attachclipboard)|附加剪贴板上的数据对象。|
|[COleData对象：：开始货币格式](#beginenumformats)|准备一个或多个后续`GetNextFormat`呼叫。|
|[COleData对象：:D](#detach)|分离关联的`IDataObject`对象。|
|[COleData对象：获取数据](#getdata)|以指定格式复制附加的 OLE 数据对象的数据。|
|[COleData对象：获取文件数据](#getfiledata)|以指定格式将附加的 OLE 数据`CFile`对象的数据复制到指针中。|
|[COleData对象：获取全球数据](#getglobaldata)|以指定格式将附加的 OLE 数据`HGLOBAL`对象的数据复制到 。|
|[COleData对象：获取下一个格式](#getnextformat)|返回下一种可用的数据格式。|
|[COleData对象：数据可用](#isdataavailable)|检查数据是否以指定格式可用。|
|[COleData对象：发布](#release)|分离并释放关联的`IDataObject`对象。|

## <a name="remarks"></a>备注

`COleDataObject`没有基类。

这些类型的数据传输包括源和目标。 数据源作为[COleDataSource](../../mfc/reference/coledatasource-class.md)类的对象实现。 每当目标应用程序将数据丢弃到其中或被要求从剪贴板执行粘贴操作时，必须创建`COleDataObject`类的对象。

此类使您能够确定数据是否存在指定格式。 您还可以枚举可用的数据格式或检查给定格式是否可用，然后以首选格式检索数据。 对象检索可以通过几种不同的方式完成，包括使用[CFile、HGLOBAL](../../mfc/reference/cfile-class.md)或`STGMEDIUM`结构。

有关详细信息，请参阅 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构。

有关在应用程序中使用数据对象的详细信息，请参阅文章["数据对象和数据源 （OLE）"。](../../mfc/data-objects-and-data-sources-ole.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`COleDataObject`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleData对象：附加

调用此函数将`COleDataObject`对象与 OLE 数据对象相关联。

```cpp
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>参数

*lpDataObject*<br/>
指向 OLE 数据对象。

*b自动释放*<br/>
如果应在销毁对象时释放 OLE 数据对象`COleDataObject`，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[IDataObject。](/windows/win32/api/objidl/nn-objidl-idataobject)

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleData对象：：附加剪板

调用此函数以将当前剪贴板上的数据对象附加到`COleDataObject`该对象。

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

> [!NOTE]
> 调用此函数将锁定剪贴板，直到释放此数据对象。 数据对象在 的`COleDataObject`析构函数中释放。 有关详细信息，请参阅 Win32 文档中的["打开剪板](/windows/win32/api/winuser/nf-winuser-openclipboard)"和["关闭剪贴板](/windows/win32/api/winuser/nf-winuser-closeclipboard)"。

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleData对象：：开始货币格式

调用此函数以准备后续调用，`GetNextFormat`以便从项检索数据格式的列表。

```cpp
void BeginEnumFormats();
```

### <a name="remarks"></a>备注

调用 后`BeginEnumFormats`将存储此数据对象支持的第一个格式的位置。 对 的`GetNextFormat`连续调用将枚举数据对象中可用格式的列表。

要检查给定格式的数据可用性，请使用[COleDataObject：：isData 可用](#isdataavailable)。

有关详细信息，请参阅 Windows SDK 中的[IDataObject：enumFormatEtc。](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc)

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleData对象：COleData对象

构造 `COleDataObject` 对象。

```
COleDataObject();
```

### <a name="remarks"></a>备注

调用[COleDataObject：：附加](#attach)或[COleDataObject：在](#attachclipboard)调用其他`COleDataObject`函数之前必须进行附加剪板。

> [!NOTE]
> 由于拖放处理程序的参数之一是指向 的`COleDataObject`指针，因此无需调用此构造函数来支持拖放。

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleData对象：:D

调用此函数以将其`COleDataObject`对象从其关联的 OLE 数据对象中分离出来，而不释放数据对象。

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>返回值

指向分离的 OLE 数据对象的指针。

### <a name="remarks"></a>备注

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleData对象：获取数据

调用此函数以从指定格式的项检索数据。

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
返回数据的格式。 此参数可以是预定义的剪贴板格式之一，也可以是本机 Windows[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpStg 中*<br/>
指向将接收数据的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)结构。

*lpFormatEtc*<br/>
指向描述要返回数据的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 如果要指定*cfFormat*指定的剪贴板格式之外的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于`FORMATETC`结构中的其他字段。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[IDataObject：获取数据](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)[、STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

有关详细信息，请参阅 Windows SDK 中的[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleData对象：获取文件数据

调用此函数以创建`CFile`或`CFile`派生对象，并将指定格式的数据检索到`CFile`指针中。

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
返回数据的格式。 此参数可以是预定义的剪贴板格式之一，也可以是本机 Windows[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpFormatEtc*<br/>
指向描述要返回数据的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 如果要指定*cfFormat*指定的剪贴板格式之外的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于`FORMATETC`结构中的其他字段。

### <a name="return-value"></a>返回值

指针指向包含数据`CFile`的新`CFile`对象或派生对象（如果成功）;否则 NULL。

### <a name="remarks"></a>备注

根据数据存储的介质，返回值指向的实际类型可以是`CFile`，`CSharedFile`或`COleStreamFile`。

> [!NOTE]
> 由`CFile`此函数的返回值访问的对象归调用方所有。 调用方有责任**删除**该对象，`CFile`从而关闭文件。

有关详细信息，请参阅 Windows SDK 中的[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

有关详细信息，请参阅 Windows SDK 中的[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleData对象：获取全球数据

调用此函数以分配全局内存块，并将指定格式的数据检索到 HGLOBAL 中。

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
返回数据的格式。 此参数可以是预定义的剪贴板格式之一，也可以是本机 Windows[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpFormatEtc*<br/>
指向描述要返回数据的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 如果要指定*cfFormat*指定的剪贴板格式之外的其他格式信息，请提供此参数的值。 如果为 NULL，则默认值用于`FORMATETC`结构中的其他字段。

### <a name="return-value"></a>返回值

如果成功，则包含数据的全局内存块的句柄;否则 NULL。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

有关详细信息，请参阅 Windows SDK 中的[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleData对象：获取下一个格式

重复调用此函数以获取可用于从项检索数据的所有格式。

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>参数

*lpFormatEtc*<br/>
指向在函数调用返回时接收格式信息的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

### <a name="return-value"></a>返回值

如果其他格式可用，则非零;否则 0。

### <a name="remarks"></a>备注

调用[COleDataObject：：BeginEnum格式](#beginenumformats)后，存储此数据对象支持的第一个格式的位置。 对 的`GetNextFormat`连续调用将枚举数据对象中可用格式的列表。 使用这些函数列出可用的格式。

要检查给定格式的可用性，请致电[COleDataObject：：IsData 可用](#isdataavailable)。

有关详细信息，请参阅[IEnumXXXX：：下一个](/previous-versions/ms695273\(v=vs.85\))在 Windows SDK 中。

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleData对象：数据可用

调用此函数以确定特定格式是否可用于从 OLE 项检索数据。

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>参数

*cfFormat*<br/>
剪贴板数据格式用于*lpFormatEtc*指向的结构中。 此参数可以是预定义的剪贴板格式之一，也可以是本机 Windows[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函数返回的值。

*lpFormatEtc*<br/>
指向描述所需格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。 仅当要指定*cfFormat*指定的剪贴板格式之外的其他格式信息时，才为此参数提供值。 如果为 NULL，则默认值用于`FORMATETC`结构中的其他字段。

### <a name="return-value"></a>返回值

如果数据以指定格式可用，则非零;否则 0。

### <a name="remarks"></a>备注

在调用`GetData`之前，此功能很有用`GetFileData``GetGlobalData`。

有关详细信息，请参阅[IDataObject：：在](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata)Windows SDK 中查询获取数据和[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

有关详细信息，请参阅 Windows SDK 中的[注册剪贴板格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

### <a name="example"></a>示例

  请参阅[CRichEditView 的示例：查询接受数据](../../mfc/reference/cricheditview-class.md#queryacceptdata)。

## <a name="coledataobjectrelease"></a><a name="release"></a>COleData对象：发布

调用此函数以释放以前与`COleDataObject`该对象关联的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)对象的所有权。

```cpp
void Release();
```

### <a name="remarks"></a>备注

通过调用`Attach`或`AttachClipboard`显式或由框架与 关联。 `IDataObject` `COleDataObject` 如果 的`Attach` *bAutoRelease*参数为`IDataObject`FALSE，则不会释放对象。 在这种情况下，调用方负责`IDataObject`通过调用[IUnknown：：：：释放](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)来释放 。

## <a name="see-also"></a>请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource 类](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServer 项目类](../../mfc/reference/coleserveritem-class.md)
