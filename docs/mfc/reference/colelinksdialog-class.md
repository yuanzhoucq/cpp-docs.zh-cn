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
ms.openlocfilehash: 911108f9a231b752790abfdf86d1b4042d30b149
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504110"
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
|[COleLinksDialog::DoModal](#domodal)|显示 OLE "编辑链接" 对话框。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|控制对话框行为的 OLEUIEDITLINKS 类型的结构。|

## <a name="remarks"></a>备注

如果要调用此对话框`COleLinksDialog` ，请创建类的对象。 构造`COleLinksDialog`对象后，可以使用 [m_el](#m_el) 结构在对话框中初始化控件的值或状态。 `m_el`结构的类型为 OLEUIEDITLINKS。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

> [!NOTE]
>  应用程序向导生成的容器代码使用此类。

有关详细信息，请参阅 Windows SDK 中的[OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw)结构。

有关特定于 OLE 的对话框的详细信息，请参阅[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs

##  <a name="domodal"></a>COleLinksDialog：:D oModal

显示 OLE "编辑链接" 对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则为 IDOK。

- 如果用户取消了对话框，则为 IDCANCEL。

- 如果发生错误，则为 IDABORT。 如果返回 IDABORT，则调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅 Windows SDK 中的[OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw)函数。

### <a name="remarks"></a>备注

如果希望通过设置[m_el](#m_el)结构的成员来初始化各种对话框控件，应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

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

*dwFlags*<br/>
创建标志，其中包含0或 ELF_SHOWHELP，用于指定显示对话框时是否显示 "帮助" 按钮。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象`CWnd`（类型为）。 如果为 NULL，则对话框的父窗口设置为主应用程序窗口。

### <a name="remarks"></a>备注

此函数仅`COleLinksDialog`构造对象。 若要显示该对话框，请调用[DoModal](#domodal)函数。

##  <a name="m_el"></a>COleLinksDialog::m_el

用于控制 "编辑链接" 对话框的行为的 OLEUIEDITLINKS 类型的结构。

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>备注

可以直接或通过成员函数修改此结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw)结构。

## <a name="see-also"></a>请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
