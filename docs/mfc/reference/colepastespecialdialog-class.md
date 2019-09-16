---
title: COlePasteSpecialDialog 类
ms.date: 11/04/2016
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
ms.openlocfilehash: f4174369620f14f2d1ac410aa5d756c75097ad0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503769"
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
|[COlePasteSpecialDialog::AddFormat](#addformat)|将自定义格式添加到您的应用程序可以粘贴的格式列表中。|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|将新条目添加到支持的剪贴板格式列表中。|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|将 CF_BITMAP、CF_DIB、CF_METAFILEPICT 和（可选） CF_LINKSOURCE 添加到应用程序可以粘贴的格式列表中。|
|[COlePasteSpecialDialog::CreateItem](#createitem)|使用指定的格式在容器文档中创建项。|
|[COlePasteSpecialDialog::DoModal](#domodal)|显示 OLE "选择性粘贴" 对话框。|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|指示是否将项绘制为图标。|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标形式关联的图元文件的句柄。|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|获取用户选择的可用粘贴选项的索引。|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|获取所选选择的类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|控制对话框功能的 OLEUIPASTESPECIAL 类型的结构。|

## <a name="remarks"></a>备注

如果要调用此对话框`COlePasteSpecialDialog` ，请创建类的对象。 构造`COlePasteSpecialDialog`对象后，可以使用 [AddFormat](#addformat) 和[AddStandardFormats](#addstandardformats)成员函数将剪贴板格式添加到对话框中。 还可以使用[m_ps](#m_ps)结构在对话框中初始化控件的值或状态。 `m_ps`结构的类型为 OLEUIPASTESPECIAL。

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw)结构。

有关特定于 OLE 的对话框的详细信息，请参阅[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs

##  <a name="addformat"></a>COlePasteSpecialDialog::AddFormat

调用此函数可将新格式添加到您的应用程序在粘贴特殊操作中可以支持的格式列表中。

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
要添加的数据类型的引用。

*lpszFormat*<br/>
描述用户格式的字符串。

*lpszResult*<br/>
描述在对话框中选择此格式时的结果的字符串。

*flags*<br/>
此格式可用的不同链接和嵌入选项。 此标志是 OLEUIPASTEFLAG 枚举类型中的一个或多个不同值的按位组合。

*cf*<br/>
要添加的剪贴板格式。

*tymed*<br/>
此格式可用的媒体类型。 这是 TYMED 枚举类型中一个或多个值的按位组合。

*nFormatID*<br/>
标识此格式的字符串的 ID。 此字符串的格式是以 "\n" 字符分隔的两个单独的字符串。 第一个字符串与在*lpstrFormat*参数中传递的字符串相同，第二个字符串与*lpstrResult*参数相同。

*bEnableIcon*<br/>
一个标志，用于确定在列表框中选择此格式时是否启用了 "显示为图标" 复选框。

*bLink*<br/>
一个标志，该标志确定在列表框中选择此格式时是否启用 "粘贴链接" 单选按钮。

### <a name="remarks"></a>备注

可以调用此函数来添加标准格式，如 CF_TEXT 或 CF_TIFF，或者应用程序已向系统注册的自定义格式。 有关将数据对象粘贴到应用程序中的详细信息，请[参阅文章数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

有关详细信息，请参阅[TYMED](/windows/win32/api/objidl/ne-objidl-tymed)枚举类型和 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)枚举类型。

##  <a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry

将新条目添加到支持的剪贴板格式列表中。

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>参数

*cf*<br/>
要添加的剪贴板格式。

### <a name="return-value"></a>返回值

包含新链接项的信息的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)结构。

##  <a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats

调用此函数可将以下剪贴板格式添加到您的应用程序在粘贴特殊操作中可以支持的格式列表中：

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>参数

*bEnableLink*<br/>
一个标志，该标志确定是否将 CF_LINKSOURCE 添加到你的应用程序可以粘贴的格式列表中。

### <a name="remarks"></a>备注

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Embedded Object"**

- 同时 **"链接源"**

这些格式用于支持嵌入和链接。

##  <a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog

构造 `COlePasteSpecialDialog` 对象。

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
创建标志：包含使用按位 "或" 运算符组合的下列任意数量的标志：

- PSF_SELECTPASTE 指定最初在调用对话框时将检查 "粘贴" 单选按钮。 不能与 PSF_SELECTPASTELINK 结合使用。 这是默认设置。

- PSF_SELECTPASTELINK 指定最初在调用对话框时将检查 "粘贴链接" 单选按钮。 不能与 PSF_SELECTPASTE 结合使用。

- PSF_CHECKDISPLAYASICON 指定最初在调用对话框时将检查 "显示为图标" 复选框。

- PSF_SHOWHELP 指定在调用对话框时将显示 "帮助" 按钮。

*pDataObject*<br/>
指向[COleDataObject](../../mfc/reference/coledataobject-class.md)进行粘贴。 如果此值为 NULL，则它`COleDataObject`从剪贴板中获取。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象`CWnd`（类型为）。 如果为 NULL，则对话框的父窗口设置为主应用程序窗口。

### <a name="remarks"></a>备注

此函数仅构造`COlePasteSpecialDialog`对象。 若要显示该对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)枚举类型。

##  <a name="createitem"></a>COlePasteSpecialDialog：： CreateItem

创建在 "选择性粘贴" 对话框中选择的新项。

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>参数

*pNewItem*<br/>
`COleClientItem`指向实例。 不能为 NULL。

### <a name="return-value"></a>返回值

如果成功创建了项，则为非零值;否则为0。

### <a name="remarks"></a>备注

仅应在[DoModal](#domodal)返回 IDOK 后调用此函数。

##  <a name="domodal"></a>COlePasteSpecialDialog：:D oModal

显示 OLE "选择性粘贴" 对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则为 IDOK。

- 如果用户取消了对话框，则为 IDCANCEL。

- 如果发生错误，则为 IDABORT。 如果返回 IDABORT，则调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅 Windows SDK 中的[OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw)函数。

### <a name="remarks"></a>备注

如果希望通过设置[m_ps](#m_ps)结构的成员来初始化各种对话框控件，应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户在对话框中输入的设置或信息。

##  <a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect

确定用户是否选择将选定项显示为图标。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>返回值

呈现对象所需的方法。

- 如果在关闭对话框时未选中 "显示为图标" 复选框，则返回 DVASPECT_CONTENT。

- 如果在关闭对话框时选中了 "显示为图标" 复选框，则返回 DVASPECT_ICON。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

有关绘制方面的详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile

获取与用户选定的项关联的图元文件。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

如果在通过选择 **"确定"** 关闭对话框时选中了 "显示为图标" 复选框，则为包含选定项的图标方面的图元文件的句柄;否则为 NULL。

##  <a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex

获取与用户选定的项关联的索引值。

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>返回值

用户选择的`OLEUIPASTEENTRY`结构数组中的索引。 执行粘贴操作时，应使用与所选索引对应的格式。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw)结构。

##  <a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType

确定用户进行的选择的类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

返回所做选择的类型。

### <a name="remarks"></a>备注

返回类型值由`Selection` `COlePasteSpecialDialog`类中声明的枚举类型指定。

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

下面简要 desccriptions 这些值：

- `COlePasteSpecialDialog::pasteLink`"粘贴链接" 单选按钮已选中，并且所选格式为标准 OLE 格式。

- `COlePasteSpecialDialog::pasteNormal`"粘贴" 单选按钮已选中，并且所选格式为标准 OLE 格式。

- `COlePasteSpecialDialog::pasteOther`所选格式不是标准 OLE 格式。

- `COlePasteSpecialDialog::pasteStatic`所选格式为图元文件。

##  <a name="m_ps"></a>COlePasteSpecialDialog::m_ps

用于控制 "选择性粘贴" 对话框的行为的 OLEUIPASTESPECIAL 类型的结构。

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>备注

可以直接修改或通过成员函数修改此结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw)结构。

## <a name="see-also"></a>请参阅

[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
