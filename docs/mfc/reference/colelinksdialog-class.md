---
title: COleLinksDialog 类
ms.date: 11/04/2016
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
ms.openlocfilehash: c5069bc63d61016e6f3c2f983de23901b9f35814
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301410"
---
# <a name="colelinksdialog-class"></a>COleLinksDialog 类

用于 OLE“编辑链接”对话框。

## <a name="syntax"></a>语法

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|构造 `COleLinksDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleLinksDialog::DoModal](#domodal)|显示 OLE 编辑链接对话框。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|类型 OLEUIEDITLINKS 控制对话框的行为的结构。|

## <a name="remarks"></a>备注

创建类的对象`COleLinksDialog`时您想要调用此对话框。 之后`COleLinksDialog`构造对象，则可以使用[m_el](#m_el)结构初始化的值或在对话框中的控件的状态。 `m_el`结构属于类型 OLEUIEDITLINKS。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

> [!NOTE]
>  应用程序向导生成的容器的代码使用此类。

有关详细信息，请参阅[OLEUIEDITLINKS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuieditlinksa) Windows SDK 中的结构。

有关特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs.h

##  <a name="domodal"></a>  COleLinksDialog::DoModal

显示 OLE 编辑链接对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框中的完成状态。 以下值之一：

- IDOK 如果成功显示的对话框。

- 如果用户已取消对话框的，IDCANCEL。

- IDABORT 是否发生错误。 如果返回 IDABORT，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅[OleUIEditLinks](/windows/desktop/api/oledlg/nf-oledlg-oleuieditlinksa) Windows SDK 中的函数。

### <a name="remarks"></a>备注

如果你想要通过设置的成员初始化各种对话框控件[m_el](#m_el)结构，你应执行此操作之前调用`DoModal`，但在构造对话框对象之后。

##  <a name="colelinksdialog"></a>  COleLinksDialog::COleLinksDialog

构造 `COleLinksDialog` 对象。

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*pDoc*<br/>
指向包含要编辑的链接的 OLE 文档。

*pView*<br/>
指向上的当前视图*pDoc*。

*dwFlags*<br/>
创建标记，包含 0 或 ELF_SHOWHELP 以指定显示的对话框时，是否将显示帮助按钮。

*pParentWnd*<br/>
指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象属于的。 如果它为 NULL，父窗口的对话框的设置为应用程序主窗口。

### <a name="remarks"></a>备注

此函数将构造仅`COleLinksDialog`对象。 若要显示的对话框，请调用[DoModal](#domodal)函数。

##  <a name="m_el"></a>  COleLinksDialog::m_el

类型 OLEUIEDITLINKS 的结构，用于控制编辑链接对话框中的行为。

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>备注

直接或通过成员函数，可以修改此结构的成员。

有关详细信息，请参阅[OLEUIEDITLINKS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuieditlinksa) Windows SDK 中的结构。

## <a name="see-also"></a>请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
