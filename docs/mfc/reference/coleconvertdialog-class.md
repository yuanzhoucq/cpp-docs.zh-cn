---
title: COleConvertDialog 类
ms.date: 11/04/2016
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
ms.openlocfilehash: 6d6690b8d06df29ce9fcd323eb8724009ee3cca9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366167"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 类

有关详细信息，请参阅 Windows SDK 中的[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)结构。

## <a name="syntax"></a>语法

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle 转换对话框：：COleConvert对话](#coleconvertdialog)|构造 `COleConvertDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleConvert对话：:DoConvert](#doconvert)|执行对话框中指定的转换。|
|[COleConvert对话：:Do模态](#domodal)|显示"OLE 更改项目"对话框。|
|[COleConvert对话：获取类ID](#getclassid)|获取与所选项关联的 CLSID。|
|[COleConvert对话：：获取绘制方面](#getdrawaspect)|指定是否将项目绘制为图标。|
|[COleConvert对话：获取图标Meta文件](#geticonicmetafile)|获取与此项目的标志性形式关联的元文件的句柄。|
|[COleConvert对话：获取选择类型](#getselectiontype)|获取所选选择的类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleConvert对话：：m_cv](#m_cv)|控制对话框行为的结构。|

## <a name="remarks"></a>备注

> [!NOTE]
> 应用程序向导生成的容器代码使用此类。

有关特定于 OLE 的对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>COle 转换对话框：：COleConvert对话

仅构造对象`COleConvertDialog`。

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要转换或激活的项目。

dwFlags**<br/>
创建标志，其中包含使用位或运算符组合的以下任意数量的值：

- CF_SELECTCONVERTTO 指定在调用对话框时，最初将选择"转换为单选"按钮。 这是默认值。

- CF_SELECTACTIVATEAS 指定在调用对话框时，最初将选择"激活为单选"按钮。

- CF_SETCONVERTDEFAULT 指定选择"转换为单选"按钮时，`clsidConvertDefault`由`m_cv`结构成员指定的 CLSID 的类将作为类列表框中的默认选择。

- CF_SETACTIVATEDEFAULT 指定选择"激活为单选"按钮时`clsidActivateDefault`，由`m_cv`结构成员指定的 CLSID 的类将作为类列表框中的默认选择。

- CF_SHOWHELPBUTTON 指定在调用对话框时将显示"帮助"按钮。

*pClassID*<br/>
指向要转换或激活的项目的 CLSID。 如果为 NULL，将使用与*pItem*关联的 CLSID。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象`CWnd`（类型）。 如果为 NULL，则对话框的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

要显示对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅[CLSID 密钥](/windows/win32/com/clsid-key-hklm)和[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)结构。

## <a name="coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvert对话：:DoConvert

调用此函数，从[DoModal](#domodal)成功返回后，以转换或激活[COleClientItem](../../mfc/reference/coleclientitem-class.md)类型的对象。

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要转换或激活的项目。 不能为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

根据用户在"转换"对话框中选择的信息转换或激活该项目。

## <a name="coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvert对话：:Do模态

调用此函数以显示"OLE 转换"对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则 IDOK。

- 如果用户取消了对话框，则进行 IDCANCEL。

- 如果发生错误，则 IDABORT。 如果返回 IDABORT，请调用[COleDialog：getLastError](../../mfc/reference/coledialog-class.md#getlasterror)成员函数，以获取有关所发生错误类型的详细信息。 有关可能错误的列表，请参阅 Windows SDK 中的[OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw)函数。

### <a name="remarks"></a>备注

如果要通过设置[m_cv](#m_cv)结构的成员来初始化各种对话框控件，则应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户输入到对话框中的设置或信息。

## <a name="coleconvertdialoggetclassid"></a><a name="getclassid"></a>COleConvert对话：获取类ID

调用此函数以获取与用户在"转换"对话框中选择的项关联的 CLSID。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>返回值

与"转换"对话框中选择的项关联的 CLSID。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

有关详细信息，请参阅 Windows SDK 中的[CLSID 密钥](/windows/win32/com/clsid-key-hklm)。

## <a name="coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleConvert对话：：获取绘制方面

调用此函数以确定用户是否选择将所选项目显示为图标。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>返回值

呈现对象所需的方法。

- 如果未选中"显示为图标"复选框，则DVASPECT_CONTENT返回。

- DVASPECT_ICON如果选中"显示为图标"复选框，则返回。

### <a name="remarks"></a>备注

仅在[DoModal](#domodal)返回 IDOK 后调用此函数。

有关绘图方面的详细信息，请参阅 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)数据结构。

## <a name="coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvert对话：获取图标Meta文件

调用此函数以获取包含所选项标志性方面的元文件的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

包含选定项目标志性方面的元文件的句柄，如果通过选择"确定"在对话框被取消时选中"显示为图标"复选框;否则 NULL。

## <a name="coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvert对话：获取选择类型

调用此函数以确定在"转换"对话框中选择的转换类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

选择的类型。

### <a name="remarks"></a>备注

返回类型值由类中声明的`Selection``COleConvertDialog`枚举类型指定。

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

这些值的简要说明如下：

- `COleConvertDialog::noConversion`如果对话框已取消或用户未选择转换，则返回。 如果`COleConvertDialog::DoModal`返回 IDOK，则用户可能选择了与以前选择的图标不同的图标。

- `COleConvertDialog::convertItem`如果选中"转换为单选"按钮，则返回该用户选择了要转换为的不同项目，并`DoModal`返回 IDOK。

- `COleConvertDialog::activateAs`如果选中"激活作为单选"按钮，则返回该用户选择要激活的不同项目，并`DoModal`返回 IDOK。

## <a name="coleconvertdialogm_cv"></a><a name="m_cv"></a>COleConvert对话：：m_cv

用于控制"转换"对话框的行为的 OLEUICONVERT 类型的结构。

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>备注

此结构的成员可以直接或通过成员函数进行修改。

有关详细信息，请参阅 Windows SDK 中的[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)结构。

## <a name="see-also"></a>另请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
