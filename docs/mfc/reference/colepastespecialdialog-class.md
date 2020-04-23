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
ms.openlocfilehash: 47fb421ef9dedcae7f92d33f55988dbbc2ea452d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753826"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog 类

用于 OLE“选择性粘贴”对话框。

## <a name="syntax"></a>语法

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COlePaste 特殊对话：：COlePaste 特殊对话](#colepastespecialdialog)|构造 `COlePasteSpecialDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COlePaste 特别对话：：添加格式](#addformat)|将自定义格式添加到应用程序可以粘贴的格式列表中。|
|[COlePaste 特殊对话：：添加链接输入](#addlinkentry)|向受支持的剪贴板格式列表添加新条目。|
|[COlePaste 特别对话：：添加标准格式](#addstandardformats)|将CF_BITMAP、CF_DIB、CF_METAFILEPICT以及可选CF_LINKSOURCE添加到应用程序可以粘贴的格式列表中。|
|[COlePaste 特殊对话：：创建项目](#createitem)|使用指定的格式在容器文档中创建项。|
|[COlePaste特殊对话：:Do模态](#domodal)|显示"OLE 粘贴特殊"对话框。|
|[COlePaste 特别对话：：获取绘制Aspect](#getdrawaspect)|是否将项目绘制为图标。|
|[COlePaste 特别对话：：获取图标Meta文件](#geticonicmetafile)|获取与此项目的标志性形式关联的元文件的句柄。|
|[COlePaste 特别对话：：获取粘贴索引](#getpasteindex)|获取用户选择的可用粘贴选项的索引。|
|[COlePaste 特殊对话：：获取选择类型](#getselectiontype)|获取所选选择的类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COlePaste 特别对话：：m_ps](#m_ps)|控制对话框功能的 OLEUIPASTE 特别类型的结构。|

## <a name="remarks"></a>备注

要调用此对话框时`COlePasteSpecialDialog`，请创建类的对象。 构造`COlePasteSpecialDialog`对象后，可以使用[AddFormat](#addformat)和[AddStandard格式](#addstandardformats)成员函数将剪贴板格式添加到对话框中。 您还可以使用[m_ps](#m_ps)结构在对话框中初始化控件的值或状态。 结构`m_ps`为"奥莱图斯特"型。

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTE 特别](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw)结构。

有关特定于 OLE 的对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="colepastespecialdialogaddformat"></a><a name="addformat"></a>COlePaste 特别对话：：添加格式

调用此函数以将新格式添加到应用程序在 Paste 特殊操作中可以支持的格式列表中。

```cpp
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

*Fmt*<br/>
引用要添加的数据类型。

*lpsz格式*<br/>
向用户描述格式的字符串。

*lpszResult*<br/>
如果在对话框中选择此格式，则描述结果的字符串。

*flag*<br/>
可用于此格式的不同链接和嵌入选项。 此标志是 OLEUIPASTEFLAG 枚举类型中一个或多个不同值的位形组合。

*Cf*<br/>
要添加的剪贴板格式。

*泰梅德*<br/>
此格式可用的媒体类型。 这是 TYMED 枚举类型中一个或多个值的位组合。

*nFormatID*<br/>
标识此格式的字符串的 ID。 此字符串的格式是两个单独的字符串，由"\n"字符分隔。 第一个字符串与*lpstrFormat*参数中传递的字符串相同，第二个字符串与*lpstrResult*参数相同。

*bEnableIcon*<br/>
在列表框中选择此格式时确定是否启用"显示为图标"复选框的标志。

*眨眼*<br/>
在列表框中选择此格式时确定是否启用"粘贴链接"单选按钮的标志。

### <a name="remarks"></a>备注

可以调用此功能来添加标准格式，如CF_TEXT或CF_TIFF或自定义格式，应用程序已在系统中注册。 有关将数据对象粘贴到应用程序中的详细信息，请参阅文章["数据对象和数据源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)"。

有关详细信息，请参阅 Windows SDK 中的[TYMED](/windows/win32/api/objidl/ne-objidl-tymed)枚举类型和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)枚举类型。

## <a name="colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a>COlePaste 特殊对话：：添加链接输入

向受支持的剪贴板格式列表添加新条目。

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>参数

*Cf*<br/>
要添加的剪贴板格式。

### <a name="return-value"></a>返回值

包含新链接条目信息的[OLEUIPASTEFLAG 结构](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)。

## <a name="colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a>COlePaste 特别对话：：添加标准格式

调用此函数将以下剪贴板格式添加到应用程序在粘贴特殊操作中可以支持的格式列表中：

```cpp
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>参数

*b 启用链接*<br/>
确定是否将CF_LINKSOURCE添加到应用程序可以粘贴的格式列表中的标志。

### <a name="remarks"></a>备注

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"嵌入对象"**

- （可选）**"链接源"**

这些格式用于支持嵌入和链接。

## <a name="colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a>COlePaste 特殊对话：：COlePaste 特殊对话

构造 `COlePasteSpecialDialog` 对象。

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

dwFlags**<br/>
创建标志，包含使用位-OR 运算符组合的以下标志的任意数量的：

- PSF_SELECTPASTE 指定在调用对话框时，最初将选中"粘贴单选"按钮。 不能与PSF_SELECTPASTELINK结合使用。 这是默认值。

- PSF_SELECTPASTELINK 指定在调用对话框时，最初将选中"粘贴链接"单选按钮。 不能与PSF_SELECTPASTE结合使用。

- PSF_CHECKDISPLAYASICON 指定在调用对话框时，将首先选中"显示为图标"复选框。

- PSF_SHOWHELP 指定在调用对话框时将显示"帮助"按钮。

*pDataObject*<br/>
指向用于粘贴的[COleData 对象](../../mfc/reference/coledataobject-class.md)。 如果此值为 NULL，则从剪`COleDataObject`贴板获取 。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象`CWnd`（类型）。 如果为 NULL，则对话框的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

此函数仅构造对象`COlePasteSpecialDialog`。 要显示对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)枚举类型。

## <a name="colepastespecialdialogcreateitem"></a><a name="createitem"></a>COlePaste 特殊对话：：创建项目

创建在"粘贴特殊"对话框中选择的新项。

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>参数

*p 新项目*<br/>
指向实例`COleClientItem`。 不能为 NULL。

### <a name="return-value"></a>返回值

如果项目已成功创建，则非零;否则 0。

### <a name="remarks"></a>备注

只有在[DoModal](#domodal)返回 IDOK 后才能调用此功能。

## <a name="colepastespecialdialogdomodal"></a><a name="domodal"></a>COlePaste特殊对话：:Do模态

显示"OLE 粘贴特殊"对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则 IDOK。

- 如果用户取消了对话框，则进行 IDCANCEL。

- 如果发生错误，则 IDABORT。 如果返回 IDABORT，请调用`COleDialog::GetLastError`成员函数以获取有关所发生错误类型的详细信息。 有关可能错误的列表，请参阅 Windows SDK 中的[OleUIPaste 特别](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw)功能。

### <a name="remarks"></a>备注

如果要通过设置[m_ps](#m_ps)结构的成员来初始化各种对话框控件，则应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户输入到对话框中的设置或信息。

## <a name="colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COlePaste 特别对话：：获取绘制Aspect

确定用户是否选择将所选项目显示为图标。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>返回值

呈现对象所需的方法。

- DVASPECT_CONTENT如果对话框已取消时未选中"显示为图标"复选框，则返回。

- DVASPECT_ICON在对话框取消时选中"显示为图标"复选框时返回。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

有关绘图方面的详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)结构。

## <a name="colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COlePaste 特别对话：：获取图标Meta文件

获取与用户选择的项目关联的元文件。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

包含选定项目标志性方面的元文件的句柄，如果选择"显示为图标"复选框，则对话框通过选择 **"确定**"而取消;否则 NULL。

## <a name="colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a>COlePaste 特别对话：：获取粘贴索引

获取与用户所选条目关联的索引值。

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>返回值

用户选择的结构数组中的`OLEUIPASTEENTRY`索引。 执行粘贴操作时，应使用对应于所选索引的格式。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTEENTRY 结构](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw)。

## <a name="colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a>COlePaste 特殊对话：：获取选择类型

确定用户所做的选择类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

返回所做的选择类型。

### <a name="remarks"></a>备注

返回类型值由类中声明的`Selection``COlePasteSpecialDialog`枚举类型指定。

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

这些值的简短去功能如下：

- `COlePasteSpecialDialog::pasteLink`已选中"粘贴链接"单选按钮，所选格式为标准 OLE 格式。

- `COlePasteSpecialDialog::pasteNormal`已选中"粘贴单选"按钮，所选格式为标准 OLE 格式。

- `COlePasteSpecialDialog::pasteOther`所选格式不是标准 OLE 格式。

- `COlePasteSpecialDialog::pasteStatic`所选格式为元文件。

## <a name="colepastespecialdialogm_ps"></a><a name="m_ps"></a>COlePaste 特别对话：：m_ps

用于控制粘贴特殊对话框的行为的 OLEUIPASTE 特别类型的结构。

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>备注

此结构的成员可以直接或通过成员函数进行修改。

有关详细信息，请参阅 Windows SDK 中的[OLEUIPASTE 特别](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw)结构。

## <a name="see-also"></a>请参阅

[MFC 样品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
