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
ms.openlocfilehash: a319dc0612f68c4d513b7d5ab36ecf67a854bda9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433639"
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
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|执行在对话框中指定的更改。|
|[COleChangeIconDialog::DoModal](#domodal)|显示 OLE 2 更改图标对话框。|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|获取与此项的图标窗体相关联的图元文件的句柄。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|结构，它控制对话框的行为。|

## <a name="remarks"></a>备注

创建类的对象`COleChangeIconDialog`时您想要调用此对话框。 之后`COleChangeIconDialog`构造对象，则可以使用[m_ci](#m_ci)结构初始化的值或在对话框中的控件的状态。 `m_ci`结构属于类型 OLEUICHANGEICON。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

有关详细信息，请参阅[OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) Windows SDK 中的结构。

有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs.h

##  <a name="colechangeicondialog"></a>  COleChangeIconDialog::COleChangeIconDialog

此函数将构造仅`COleChangeIconDialog`对象。

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
使用按位组合起来，创建标记，其中包含任意数量的以下值-或运算符：

- CIF_SELECTCURRENT 指定当前的单选按钮将所选最初调用的对话框时。 这是默认设置。

- CIF_SELECTDEFAULT 指定默认单选按钮将所选最初调用的对话框时。

- CIF_SELECTFROMFILE 指定文件中的单选按钮将所选最初调用的对话框时。

- CIF_SHOWHELP 指定对话框的调用时，将显示帮助按钮。

- CIF_USEICONEXE 指定应从中指定的可执行文件中提取图标`szIconExe`字段[m_ci](#m_ci)而不是检索到的类型。 这可用于嵌入或链接到非 OLE 文件。

*pParentWnd*<br/>
指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象属于的。 如果它为 NULL，父窗口的对话框的将设置为应用程序主窗口。

### <a name="remarks"></a>备注

若要显示的对话框，请调用[DoModal](#domodal)函数。

有关详细信息，请参阅[OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) Windows SDK 中的结构。

##  <a name="dochangeicon"></a>  COleChangeIconDialog::DoChangeIcon

调用此函数可更改到对话框后中选择一个表示项的图标[DoModal](#domodal)返回 IDOK。

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>参数

*pItem*<br/>
指向以更改其图标的项。

### <a name="return-value"></a>返回值

如果成功，则更改为非零值否则为 0。

##  <a name="domodal"></a>  COleChangeIconDialog::DoModal

调用此函数可显示 OLE 更改图标对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框中的完成状态。 以下值之一：

- IDOK 如果成功显示的对话框。

- 如果用户已取消对话框的，IDCANCEL。

- IDABORT 是否发生错误。 如果返回 IDABORT，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅[OleUIChangeIcon](/windows/desktop/api/oledlg/nf-oledlg-oleuichangeicona) Windows SDK 中的函数。

### <a name="remarks"></a>备注

如果你想要通过设置的成员初始化各种对话框控件[m_ci](#m_ci)结构，应执行此操作之前调用`DoModal`，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，您可以调用其他成员函数以检索的设置或由用户输入到对话框中的信息。

##  <a name="geticonicmetafile"></a>  COleChangeIconDialog::GetIconicMetafile

调用此函数可获取包含选定项的图标方面的图元文件的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>返回值

如果通过选择解除对话框的包含新建图标，图标方面的图元文件的句柄**确定**; 否则为对话框中显示前作为它的图标。

##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci

类型 OLEUICHANGEICON 的结构，用于控制更改图标对话框中的行为。

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>备注

直接或通过成员函数，可以修改此结构的成员。

有关详细信息，请参阅[OLEUICHANGEICON](/windows/desktop/api/oledlg/ns-oledlg-tagoleuichangeicona) Windows SDK 中的结构。

## <a name="see-also"></a>请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
