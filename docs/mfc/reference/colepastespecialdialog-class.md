---
title: COlePasteSpecialDialog 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
dev_langs:
- C++
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88f4653369b9692b7192b6a3661a00f5e3665d99
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410373"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog 类

用于 OLE“选择性粘贴”对话框。

## <a name="syntax"></a>语法

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|构造 `COlePasteSpecialDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|将自定义格式添加到你的应用程序可以将粘贴的格式的列表。|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|将新条目添加到受支持剪贴板格式的列表。|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|添加 CF_BITMAP，CF_DIB，CF_METAFILEPICT，并根据需要 CF_LINKSOURCE 格式列表到你的应用程序可以粘贴。|
|[COlePasteSpecialDialog::CreateItem](#createitem)|创建使用指定的格式在容器文档中的项。|
|[COlePasteSpecialDialog::DoModal](#domodal)|显示 OLE 选择性粘贴对话框。|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|指示是否绘制项为图标或不。|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标窗体相关联的图元文件的句柄。|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|获取用户选择可用粘贴选项的索引。|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|获取所选内容的类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|类型 OLEUIPASTESPECIAL 控制对话框的函数的结构。|

## <a name="remarks"></a>备注

创建类的对象`COlePasteSpecialDialog`时您想要调用此对话框。 之后`COlePasteSpecialDialog`构造对象，则可以使用[AddFormat](#addformat)并[AddStandardFormats](#addstandardformats)成员函数添加到对话框中的剪贴板格式。 此外可以使用[m_ps](#m_ps)结构初始化的值或在对话框中的控件的状态。 `m_ps`结构属于类型 OLEUIPASTESPECIAL。

有关详细信息，请参阅[OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) Windows SDK 中的结构。

有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs.h

##  <a name="addformat"></a>  COlePasteSpecialDialog::AddFormat

调用此函数可将新的格式添加到你的应用程序可以支持选择性粘贴操作中的格式的列表。

```
void AddFormat(
    const FORMATETC& formatEtc,
    LPTSTR lpszFormat,
    LPTSTR lpszResult,
    DWORD flags);


void AddFormat(
    UINT cf,
    DWORD tymed,
    UINT nFormatID,
    BOOL bEnableIcon,
    BOOL bLink);
```

### <a name="parameters"></a>参数

*fmt*<br/>
对要添加的数据类型的引用。

*lpszFormat*<br/>
描述向用户格式的字符串。

*lpszResult*<br/>
如果在对话框中选择这种格式，则说明结果的字符串。

*flags*<br/>
不同链接和嵌入选项可用于此格式。 此标志的按位组合或多个 OLEUIPASTEFLAG 中的不同值的枚举类型。

*cf*<br/>
要添加的剪贴板格式。

*tymed*<br/>
在这种格式中可用的媒体类型。 这是一个按位组合或多个 TYMED 中值的枚举类型。

*nFormatID*<br/>
用于标识此格式的字符串的 ID。 此字符串的格式为 \n 字符分隔的两个单独的字符串。 第一个字符串是相同将传入*lpstrFormat*参数，第二个是相同*lpstrResult*参数。

*bEnableIcon*<br/>
确定是否显示为图标的复选框启用时在列表框中选择此格式的标志。

*闪烁*<br/>
确定在列表框中选择这种格式时，是否启用粘贴链接单选按钮的标志。

### <a name="remarks"></a>备注

若要添加为标准格式，例如 CF_TEXT 或 CF_TIFF 或自定义格式的应用程序已注册到系统，可以调用此函数。 有关将数据对象粘贴到你的应用程序的详细信息，请参阅文章[数据对象和数据源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅[TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed)枚举类型和[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的结构。

有关详细信息，请参阅[OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag)枚举 Windows SDK 中的类型。

##  <a name="addlinkentry"></a>  COlePasteSpecialDialog::AddLinkEntry

将新条目添加到受支持剪贴板格式的列表。

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>参数

*cf*<br/>
要添加的剪贴板格式。

### <a name="return-value"></a>返回值

[OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag)结构，它包含新链接项的信息。

##  <a name="addstandardformats"></a>  COlePasteSpecialDialog::AddStandardFormats

调用此函数可将以下的剪贴板格式添加到你的应用程序可以支持选择性粘贴操作中的格式的列表：

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>参数

*bEnableLink*<br/>
可以粘贴标志，用于确定是否将 CF_LINKSOURCE 添加到的格式列表应用程序。

### <a name="remarks"></a>备注

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"嵌入的对象"**

- （可选）**"源链接"**

这些格式用于支持嵌入对象和链接。

##  <a name="colepastespecialdialog"></a>  COlePasteSpecialDialog::COlePasteSpecialDialog

构造 `COlePasteSpecialDialog` 对象。

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
创建标记，包含任意数量的使用按位 OR 运算符组合以下标志：

- 粘贴单选按钮将 PSF_SELECTPASTE 指定检查最初调用的对话框时。 不能与 PSF_SELECTPASTELINK 结合使用。 这是默认设置。

- 粘贴链接单选按钮将处于 PSF_SELECTPASTELINK 指定检查最初调用的对话框时。 不能与 PSF_SELECTPASTE 结合使用。

- PSF_CHECKDISPLAYASICON 指定显示为图标的复选框将选中最初调用的对话框时。

- PSF_SHOWHELP 指定对话框的调用时，将显示帮助按钮。

*pDataObject*<br/>
指向[COleDataObject](../../mfc/reference/coledataobject-class.md)粘贴。 如果此值为 NULL，它获取`COleDataObject`从剪贴板。

*pParentWnd*<br/>
指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象属于的。 如果它为 NULL，父窗口的对话框的设置为应用程序主窗口。

### <a name="remarks"></a>备注

此函数仅构造`COlePasteSpecialDialog`对象。 若要显示的对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅[OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag)枚举 Windows SDK 中的类型。

##  <a name="createitem"></a>  COlePasteSpecialDialog::CreateItem

创建选择性粘贴对话框中选择了新项。

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>参数

*pNewItem*<br/>
指向`COleClientItem`实例。 不能为 NULL。

### <a name="return-value"></a>返回值

非零，如果成功，则创建项否则为 0。

### <a name="remarks"></a>备注

此函数只应调用后[DoModal](#domodal)返回 IDOK。

##  <a name="domodal"></a>  COlePasteSpecialDialog::DoModal

显示 OLE 选择性粘贴对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框中的完成状态。 以下值之一：

- IDOK 如果成功显示的对话框。

- 如果用户已取消对话框的，IDCANCEL。

- IDABORT 是否发生错误。 如果返回 IDABORT，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅[OleUIPasteSpecial](/windows/desktop/api/oledlg/nf-oledlg-oleuipastespeciala) Windows SDK 中的函数。

### <a name="remarks"></a>备注

如果你想要通过设置的成员初始化各种对话框控件[m_ps](#m_ps)结构，应执行此操作之前调用`DoModal`，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，您可以调用其他成员函数来检索设置或用户的信息输入到对话框。

##  <a name="getdrawaspect"></a>  COlePasteSpecialDialog::GetDrawAspect

确定是否用户选择以图标形式显示选定的项。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>返回值

呈现对象所需的方法。

- 如果不是显示为图标的复选框返回 DVASPECT_CONTENT 检查时解除对话框的。

- 如果显示为图标复选框已选中对话框的已关闭时，将返回 DVASPECT_ICON。

### <a name="remarks"></a>备注

仅调用此函数后的[DoModal](#domodal)返回 IDOK。

绘制方面的详细信息，请参阅[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的结构。

##  <a name="geticonicmetafile"></a>  COlePasteSpecialDialog::GetIconicMetafile

获取与用户选定的项关联的图元文件。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

如果通过选择对话框的解除时选择了显示为图标复选框，其中包含选定项的图标的方面的图元文件的句柄**确定**; 否则为 NULL。

##  <a name="getpasteindex"></a>  COlePasteSpecialDialog::GetPasteIndex

获取索引值与项关联选定的用户。

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>返回值

中的数组索引`OLEUIPASTEENTRY`用户选择的结构。 执行粘贴操作时，应使用对应于所选索引的格式。

### <a name="remarks"></a>备注

有关详细信息，请参阅[OLEUIPASTEENTRY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipasteentrya) Windows SDK 中的结构。

##  <a name="getselectiontype"></a>  COlePasteSpecialDialog::GetSelectionType

确定用户所做的选择的类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

所选内容所做的返回类型。

### <a name="remarks"></a>备注

通过指定返回类型值`Selection`枚举类型中声明`COlePasteSpecialDialog`类。

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

请按照这些值的简短 desccriptions 操作：

- `COlePasteSpecialDialog::pasteLink` 粘贴链接单选按钮已选中并且所选的格式是标准的 OLE 格式。

- `COlePasteSpecialDialog::pasteNormal` 粘贴单选按钮已选中和所选的格式是标准的 OLE 格式。

- `COlePasteSpecialDialog::pasteOther` 所选的格式不是标准的 OLE 格式。

- `COlePasteSpecialDialog::pasteStatic` 所选的格式是图元文件。

##  <a name="m_ps"></a>  COlePasteSpecialDialog::m_ps

类型 OLEUIPASTESPECIAL 的结构，用于控制选择性粘贴对话框中的行为。

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>备注

直接或通过成员函数，可以修改此结构的成员。

有关详细信息，请参阅[OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) Windows SDK 中的结构。

## <a name="see-also"></a>请参阅

[MFC 示例 OCLIENT](../../visual-cpp-samples.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
