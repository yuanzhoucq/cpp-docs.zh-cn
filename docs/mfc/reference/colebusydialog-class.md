---
title: COleBusyDialog 类
ms.date: 11/04/2016
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
ms.openlocfilehash: aa3f0d85bcbf34d325125187b22b38c4da01fb43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504404"
---
# <a name="colebusydialog-class"></a>COleBusyDialog 类

用于 OLE“服务器未响应”或“服务器忙”对话框。

## <a name="syntax"></a>语法

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|构造 `COleBusyDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleBusyDialog::DoModal](#domodal)|显示 "OLE 服务器忙" 对话框。|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|确定在对话框中所做的选择。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|控制对话框行为的 OLEUIBUSY 类型的结构。|

## <a name="remarks"></a>备注

如果要调用这些对话框`COleBusyDialog` ，请创建类的对象。 构造`COleBusyDialog`对象后，可以使用 [m_bz](#m_bz) 结构在对话框中初始化控件的值或状态。 `m_bz`结构的类型为 OLEUIBUSY。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

> [!NOTE]
>  应用程序向导生成的容器代码使用此类。

有关详细信息，请参阅 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)结构。

有关特定于 OLE 的对话框的详细信息，请参阅[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs

##  <a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog

此函数仅构造`COleBusyDialog`对象。

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*htaskBusy*<br/>
正在忙于服务器任务的句柄。

*bNotResponding*<br/>
如果为 TRUE，则调用 "无响应" 对话框而不是 "服务器忙" 对话框。 "无响应" 对话框中的措辞与 "服务器忙" 对话框中的措辞略有不同，"取消" 按钮被禁用。

*dwFlags*<br/>
创建标志。 可以包含与按位 "或" 运算符组合的以下零个或多个值：

- BZ_DISABLECANCELBUTTON 在调用对话框时禁用 "取消" 按钮。

- BZ_DISABLESWITCHTOBUTTON 在调用对话框时禁用切换到按钮。

- BZ_DISABLERETRYBUTTON 在调用对话框时禁用 "重试" 按钮。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象`CWnd`（类型为）。 如果为 NULL，则对话框对象的父窗口设置为主应用程序窗口。

### <a name="remarks"></a>备注

若要显示该对话框，请调用[DoModal](#domodal)。

有关详细信息，请参阅 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)结构。

##  <a name="domodal"></a>  COleBusyDialog::DoModal

调用此函数可显示 OLE 服务器繁忙或服务器未响应对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则为 IDOK。

- 如果用户取消了对话框，则为 IDCANCEL。

- 如果发生错误，则为 IDABORT。 如果返回 IDABORT，则调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅 Windows SDK 中的[OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw)函数。

### <a name="remarks"></a>备注

如果希望通过设置[m_bz](#m_bz)结构的成员来初始化各种对话框控件，应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户在对话框中输入的设置或信息。

##  <a name="getselectiontype"></a>COleBusyDialog::GetSelectionType

调用此函数可获取用户在 "服务器忙" 对话框中选择的选择类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

所选对象的类型。

### <a name="remarks"></a>备注

返回类型值由`Selection` `COleBusyDialog`类中声明的枚举类型指定。

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

这些值的简要说明如下所示：

- `COleBusyDialog::switchTo`按下了切换按钮。

- `COleBusyDialog::retry`按下了 "重试" 按钮。

- `COleBusyDialog::callUnblocked`用于激活服务器的调用现在被取消阻止。

##  <a name="m_bz"></a>  COleBusyDialog::m_bz

用于控制 "服务器忙" 对话框的行为的 OLEUIBUSY 类型的结构。

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>备注

可以直接修改或通过成员函数修改此结构的成员。

有关详细信息，请参阅 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)结构。

## <a name="see-also"></a>请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
