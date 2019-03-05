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
ms.openlocfilehash: 08e482e6900e96f1d02c34efddc7635bb8e0120e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304660"
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
|[COleBusyDialog::DoModal](#domodal)|显示 OLE 服务器忙对话框。|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|确定在对话框中所做的选择。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|类型 OLEUIBUSY 控制对话框的行为的结构。|

## <a name="remarks"></a>备注

创建类的对象`COleBusyDialog`时您想要调用这些对话框。 之后`COleBusyDialog`构造对象，则可以使用[m_bz](#m_bz)结构初始化的值或在对话框中的控件的状态。 `m_bz`结构属于类型 OLEUIBUSY。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

> [!NOTE]
>  应用程序向导生成的容器的代码使用此类。

有关详细信息，请参阅[OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) Windows SDK 中的结构。

特定于 OLE 的对话框的详细信息，请参阅文章[OLE 中的对话框](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>要求

**标头：** afxodlgs.h

##  <a name="colebusydialog"></a>  COleBusyDialog::COleBusyDialog

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
服务器任务处于繁忙状态的句柄。

*bNotResponding*<br/>
如果为 TRUE，而不是服务器忙对话框中调用未响应对话框。 未响应对话框中的用语是略有不同于在服务器忙对话框中，用词和取消按钮处于禁用状态。

*dwFlags*<br/>
创建标记。 可以包含零个或多个与按位 OR 运算符合并的以下值：

- BZ_DISABLECANCELBUTTON 禁用取消按钮时调用的对话框。

- BZ_DISABLESWITCHTOBUTTON 禁用切换到按钮时调用的对话框。

- BZ_DISABLERETRYBUTTON 禁用重试按钮时调用的对话框。

*pParentWnd*<br/>
指向父或所有者窗口对象 (类型的`CWnd`) 对话框对象属于的。 如果它为 NULL，对话框对象的父窗口设置为应用程序主窗口。

### <a name="remarks"></a>备注

若要显示的对话框，请调用[DoModal](#domodal)。

有关详细信息，请参阅[OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) Windows SDK 中的结构。

##  <a name="domodal"></a>  COleBusyDialog::DoModal

调用此函数可显示 OLE 服务器忙或服务器未响应对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框中的完成状态。 以下值之一：

- IDOK 如果成功显示的对话框。

- 如果用户已取消对话框的，IDCANCEL。

- IDABORT 是否发生错误。 如果返回 IDABORT，调用`COleDialog::GetLastError`成员函数以获取有关发生的错误类型的详细信息。 有关可能的错误的列表，请参阅[OleUIBusy](/windows/desktop/api/oledlg/nf-oledlg-oleuibusya) Windows SDK 中的函数。

### <a name="remarks"></a>备注

如果你想要通过设置的成员初始化各种对话框控件[m_bz](#m_bz)结构，应执行此操作之前调用`DoModal`，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，您可以调用其他成员函数以检索的设置或由用户输入到对话框中的信息。

##  <a name="getselectiontype"></a>  COleBusyDialog::GetSelectionType

调用此函数可获取用户在服务器忙对话框中选择的所选内容类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

所做选择的类型。

### <a name="remarks"></a>备注

通过指定返回类型值`Selection`枚举类型中声明`COleBusyDialog`类。

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

请按照这些值的简短说明：

- `COleBusyDialog::switchTo` 切换到按钮曾按下。

- `COleBusyDialog::retry` 重试按钮曾按下。

- `COleBusyDialog::callUnblocked` 调用以激活服务器现已取消阻止。

##  <a name="m_bz"></a>  COleBusyDialog::m_bz

类型 OLEUIBUSY 的结构，用于控制的服务器忙对话框中的行为。

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>备注

直接或通过成员函数，可以修改此结构的成员。

有关详细信息，请参阅[OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) Windows SDK 中的结构。

## <a name="see-also"></a>请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
