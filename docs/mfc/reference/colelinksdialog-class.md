---
title: COleLinks对话类
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
ms.openlocfilehash: f120678c822749c8f27c3c56c95fcdd54647aca3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374935"
---
# <a name="colelinksdialog-class"></a>COleLinks对话类

用于 OLE“编辑链接”对话框。

## <a name="syntax"></a>语法

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleLinks对话：：COleLinks对话](#colelinksdialog)|构造 `COleLinksDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleLinks对话：:Do模态](#domodal)|显示"OLE 编辑链接"对话框。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleLinks对话：：m_el](#m_el)|控制对话框行为的"OLEUIEDITLINKS"类型的结构。|

## <a name="remarks"></a>备注

要调用此对话框时`COleLinksDialog`，请创建类的对象。 构造`COleLinksDialog`对象后，可以使用[m_el](#m_el)结构在对话框中初始化控件的值或状态。 结构`m_el`为奥莱伊迪克斯型。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

> [!NOTE]
> 应用程序向导生成的容器代码使用此类。

有关详细信息，请参阅 Windows SDK 中的[OLEUIEDITLINKS 结构](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw)。

有关特定于 OLE 的对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="colelinksdialogdomodal"></a><a name="domodal"></a>COleLinks对话：:Do模态

显示"OLE 编辑链接"对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则 IDOK。

- 如果用户取消了对话框，则进行 IDCANCEL。

- 如果发生错误，则 IDABORT。 如果返回 IDABORT，请调用`COleDialog::GetLastError`成员函数以获取有关所发生错误类型的详细信息。 有关可能错误的列表，请参阅 Windows SDK 中的[OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw)函数。

### <a name="remarks"></a>备注

如果要通过设置[m_el](#m_el)结构的成员来初始化各种对话框控件，则应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

## <a name="colelinksdialogcolelinksdialog"></a><a name="colelinksdialog"></a>COleLinks对话：：COleLinks对话

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
指向*pDoc*上的当前视图。

dwFlags**<br/>
创建标志，其中包含 0 或ELF_SHOWHELP，用于指定在显示对话框时是否显示"帮助"按钮。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象`CWnd`（类型）。 如果为 NULL，则对话框的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

此函数仅构造对象`COleLinksDialog`。 要显示对话框，请调用[DoModal](#domodal)函数。

## <a name="colelinksdialogm_el"></a><a name="m_el"></a>COleLinks对话：：m_el

用于控制"编辑链接"对话框的行为的 OLEUIEDITLINKS 类型的结构。

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>备注

此结构的成员可以直接或通过成员函数进行修改。

有关详细信息，请参阅 Windows SDK 中的[OLEUIEDITLINKS 结构](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw)。

## <a name="see-also"></a>另请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
