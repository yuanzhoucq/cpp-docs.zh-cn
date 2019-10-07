---
title: COleChangeIconDialog 类
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
ms.openlocfilehash: 4cbf1137a15a9f86a6377980526e6d188f4d0a69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504785"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog 类

用于 OLE“更改图标”对话框。

## <a name="syntax"></a>语法

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|构造 `COleChangeIconDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|执行对话框中指定的更改。|
|[COleChangeIconDialog::DoModal](#domodal)|显示 OLE 2 的 "更改图标" 对话框。|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标形式关联的图元文件的句柄。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|控制对话框行为的结构。|

## <a name="remarks"></a>备注

如果要调用此对话框`COleChangeIconDialog` ，请创建类的对象。 构造`COleChangeIconDialog`对象后，可以使用 [m_ci](#m_ci) 结构在对话框中初始化控件的值或状态。 `m_ci`结构的类型为 OLEUICHANGEICON。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)结构。

有关特定于 OLE 的对话框的详细信息，请参阅[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs

##  <a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog

此函数仅`COleChangeIconDialog`构造对象。

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向要转换的项。

*dwFlags*<br/>
创建标志，其中包含使用按位 "或" 运算符组合的下列任意数量的值：

- CIF_SELECTCURRENT 指定最初在调用对话框时选择当前单选按钮。 这是默认设置。

- CIF_SELECTDEFAULT 指定最初在调用对话框时选择的默认单选按钮。

- CIF_SELECTFROMFILE 指定最初在调用对话框时选择 "从文件" 单选按钮。

- CIF_SHOWHELP 指定在调用对话框时将显示 "帮助" 按钮。

- CIF_USEICONEXE 指定应从`szIconExe` [m_ci](#m_ci)字段中指定的可执行文件中提取图标，而不是从类型中检索。 这对于嵌入或链接到非 OLE 文件很有用。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象`CWnd`（类型为）。 如果为 NULL，则对话框的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

若要显示该对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)结构。

##  <a name="dochangeicon"></a>COleChangeIconDialog：:D oChangeIcon

调用此函数可将表示项的图标更改为在[DoModal](#domodal)返回 IDOK 后在对话框中所选的项。

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向其图标正在更改的项。

### <a name="return-value"></a>返回值

如果更改成功，则为非零值;否则为0。

##  <a name="domodal"></a>COleChangeIconDialog：:D oModal

调用此函数可显示 OLE "更改图标" 对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则为 IDOK。

- 如果用户取消了对话框，则为 IDCANCEL。

- 如果发生错误，则为 IDABORT。 如果返回 IDABORT，则调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅 Windows SDK 中的[OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw)函数。

### <a name="remarks"></a>备注

如果希望通过设置[m_ci](#m_ci)结构的成员来初始化各种对话框控件，应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户在对话框中输入的设置或信息。

##  <a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

调用此函数可获取包含选定项的图标方面的图元文件的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

如果通过选择 **"确定"** 消除了对话框，则为包含新图标的图标方面的图元文件的句柄;否则，在显示对话框之前显示的图标。

##  <a name="m_ci"></a>COleChangeIconDialog::m_ci

用于控制 "更改图标" 对话框的行为的 OLEUICHANGEICON 类型的结构。

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>备注

可以直接或通过成员函数修改此结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)结构。

## <a name="see-also"></a>请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
