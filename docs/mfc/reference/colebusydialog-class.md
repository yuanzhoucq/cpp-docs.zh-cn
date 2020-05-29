---
title: COleBusy对话类
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
ms.openlocfilehash: 5be42463c08cacd83de84900fb4d98771774e897
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364245"
---
# <a name="colebusydialog-class"></a>COleBusy对话类

用于 OLE“服务器未响应”或“服务器忙”对话框。

## <a name="syntax"></a>语法

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleBusy对话：：COleBusy对话](#colebusydialog)|构造 `COleBusyDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleBusyDialog：:Do模态](#domodal)|显示"OLE 服务器忙"对话框。|
|[COleBusy对话：获取选择类型](#getselectiontype)|确定在对话框中所做的选择。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleBusy对话：：m_bz](#m_bz)|控制对话框行为的 OLEUIBUSY 类型的结构。|

## <a name="remarks"></a>备注

如果要调用这些对话框，`COleBusyDialog`请创建类的对象。 构造`COleBusyDialog`对象后，可以使用[m_bz](#m_bz)结构在对话框中初始化控件的值或状态。 结构`m_bz`为奥莱布布。 有关使用此对话框类的详细信息，请参阅[DoModal](#domodal)成员函数。

> [!NOTE]
> 应用程序向导生成的容器代码使用此类。

有关详细信息，请参阅 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)结构。

有关特定于 OLE 的对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="colebusydialogcolebusydialog"></a><a name="colebusydialog"></a>COleBusy对话：：COleBusy对话

此函数仅构造对象`COleBusyDialog`。

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*htaskBusy*<br/>
处理忙的服务器任务。

*b 不响应*<br/>
如果为 TRUE，则调用"不响应"对话框，而不是"服务器忙"对话框。 "不响应"对话框中的措辞与"服务器忙"对话框中的措词略有不同，并且禁用"取消"按钮。

dwFlags**<br/>
创建标志。 可以包含与位-OR 运算符结合的以下零个或多个值：

- BZ_DISABLECANCELBUTTON调用对话框时禁用"取消"按钮。

- BZ_DISABLESWITCHTOBUTTON在调用对话框时禁用"切换到"按钮。

- BZ_DISABLERETRYBUTTON调用对话框时禁用重试按钮。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象`CWnd`（类型）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

要显示对话框，请调用[DoModal](#domodal)。

有关详细信息，请参阅 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)结构。

## <a name="colebusydialogdomodal"></a><a name="domodal"></a>COleBusyDialog：:Do模态

调用此函数以显示"OLE 服务器忙"或"服务器未响应"对话框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

对话框的完成状态。 以下值之一：

- 如果对话框已成功显示，则 IDOK。

- 如果用户取消了对话框，则进行 IDCANCEL。

- 如果发生错误，则 IDABORT。 如果返回 IDABORT，请调用`COleDialog::GetLastError`成员函数以获取有关所发生错误类型的详细信息。 有关可能错误的列表，请参阅 Windows SDK 中的[OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw)函数。

### <a name="remarks"></a>备注

如果要通过设置[m_bz](#m_bz)结构的成员来初始化各种对话框控件，则应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户输入到对话框中的设置或信息。

## <a name="colebusydialoggetselectiontype"></a><a name="getselectiontype"></a>COleBusy对话：获取选择类型

调用此函数以获取用户在"服务器忙"对话框中选择的选择类型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>返回值

选择的类型。

### <a name="remarks"></a>备注

返回类型值由类中声明的`Selection``COleBusyDialog`枚举类型指定。

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

这些值的简要说明如下：

- `COleBusyDialog::switchTo`按下"切换到"按钮。

- `COleBusyDialog::retry`按下重试按钮。

- `COleBusyDialog::callUnblocked`现在，启动服务器的呼叫已解除阻止。

## <a name="colebusydialogm_bz"></a><a name="m_bz"></a>COleBusy对话：：m_bz

用于控制服务器忙对话框的行为的 OLEUIBUSY 类型的结构。

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>备注

此结构的成员可以直接或通过成员函数进行修改。

有关详细信息，请参阅 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)结构。

## <a name="see-also"></a>另请参阅

[COleDialog 类](../../mfc/reference/coledialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 类](../../mfc/reference/coledialog-class.md)
