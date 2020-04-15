---
title: COleChangeIcon对话类
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 6cdc0ed6bfa4765817de8b7628f339db5e7e5bf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369622"
---
# <a name="colechangeicondialog-class"></a>COleChangeIcon对话类

用于 OLE“更改图标”对话框。

## <a name="syntax"></a>语法

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleChangeIcon对话：：COleChangeIcon对话](#colechangeicondialog)|构造 `COleChangeIconDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleChangeIcon对话：:DoChangeIcon](#dochangeicon)|执行对话框中指定的更改。|
|[COleChangeIcon对话：:D模态](#domodal)|显示 OLE 2 更改图标对话框。|
|[COleChangeIcon对话：：获取图标Meta文件](#geticonicmetafile)|获取与此项目的标志性形式关联的元文件的句柄。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleChangeIcon对话：：m_ci](#m_ci)|控制对话框行为的结构。|

## <a name="remarks"></a>备注

要调用此对话框时`COleChangeIconDialog`，请创建类的对象。 构造`COleChangeIconDialog`对象后，可以使用[m_ci](#m_ci)结构在对话框中初始化控件的值或状态。 结构`m_ci`为奥莱维图森。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)结构。

有关特定于 OLE 的对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a>COleChangeIcon对话：：COleChangeIcon对话

此函数仅构造对象`COleChangeIconDialog`。

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要转换的项目。

dwFlags**<br/>
创建标志，其中包含使用位或运算符组合的以下任意数量的值：

- CIF_SELECTCURRENT 指定在调用对话框时最初将选择"当前单选"按钮。 这是默认值。

- CIF_SELECTDEFAULT指定在调用对话框时，最初将选择默认单选按钮。

- CIF_SELECTFROMFILE 指定在调用对话框时，最初将选择"从文件单选"按钮。

- CIF_SHOWHELP 指定在调用对话框时将显示"帮助"按钮。

- CIF_USEICONEXE 指定应从`szIconExe`[m_ci](#m_ci)字段中指定的可执行文件中提取图标，而不是从类型中检索。 这对于嵌入或链接到非 OLE 文件非常有用。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象`CWnd`（类型）。 如果为 NULL，则对话框的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

要显示对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)结构。

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a>COleChangeIcon对话：:DoChangeIcon

调用此函数以将表示项的图标更改为[DoModal](#domodal)返回 IDOK 后对话框中选择的图标。

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向其图标正在更改的项目。

### <a name="return-value"></a>返回值

如果更改成功，则非零;否则 0。

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a>COleChangeIcon对话：:D模态

调用此函数以显示"OLE 更改图标"对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则 IDOK。

- 如果用户取消了对话框，则进行 IDCANCEL。

- 如果发生错误，则 IDABORT。 如果返回 IDABORT，请调用`COleDialog::GetLastError`成员函数以获取有关所发生错误类型的详细信息。 有关可能错误的列表，请参阅 Windows SDK 中的[OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw)函数。

### <a name="remarks"></a>备注

如果要通过设置[m_ci](#m_ci)结构的成员来初始化各种对话框控件，则应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户输入到对话框中的设置或信息。

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleChangeIcon对话：：获取图标Meta文件

调用此函数以获取包含所选项标志性方面的元文件的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

包含新图标标志性方面的元文件的句柄，如果对话框通过选择 **"确定"** 而取消;否则，图标与显示对话框之前的图标相同。

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a>COleChangeIcon对话：：m_ci

用于控制更改图标对话框的行为的 OLEUICHANGEICON 类型的结构。

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>备注

此结构的成员可以直接或通过成员函数进行修改。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)结构。

## <a name="see-also"></a>另请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
