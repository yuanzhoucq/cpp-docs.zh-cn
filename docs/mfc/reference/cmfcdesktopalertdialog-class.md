---
title: CMFC 桌面警报对话类
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::CreateFromParams
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::GetDlgSize
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::HasFocus
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::PreTranslateMessage
helpviewer_keywords:
- CMFCDesktopAlertDialog [MFC], CreateFromParams
- CMFCDesktopAlertDialog [MFC], GetDlgSize
- CMFCDesktopAlertDialog [MFC], HasFocus
- CMFCDesktopAlertDialog [MFC], PreTranslateMessage
ms.assetid: a53c60aa-9607-485b-b826-ec64962075f6
ms.openlocfilehash: 479959e9b021255e309caf6fee02588a8cd8f1d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367657"
---
# <a name="cmfcdesktopalertdialog-class"></a>CMFC 桌面警报对话类

该`CMFCDesktopAlertDialog`类与[CMFC DesktopAlertWnd 类](../../mfc/reference/cmfcdesktopalertwnd-class.md)一起使用，以在弹出窗口中显示自定义对话框。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCDesktopAlertDialog : public CDialogEx
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCDesktopAlertDialog::CreateFromParams](#createfromparams)||
|[CMFC 桌面警报对话：：获取Dlgsize](#getdlgsize)||
|[CMFCDesktopAlertDialog::HasFocus](#hasfocus)||
|[CMFCDesktopAlertDialog::PreTranslateMessage](#pretranslatemessage)|（重写 `CDialogEx::PreTranslateMessage`。）|

### <a name="remarks"></a>备注

执行以下步骤以在弹出窗口中显示自定义对话框：

1. 从 `CMFCDesktopAlertDialog` 派生一个类。

1. 在项目的资源中创建子对话框模板。

1. 调用[CMFCDesktopAlertwnd：：](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)使用对话框模板的资源 ID 和指向派生类的运行时类信息的指针作为参数进行创建。

1. 对自定义对话框进行编程以处理来自托管控件的所有通知，或对托管控件进行编程以直接处理这些通知。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)

## <a name="requirements"></a>要求

**标题：** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertdialogcreatefromparams"></a><a name="createfromparams"></a>CMFC 桌面警报对话：：从帕拉姆斯创建

```
BOOL CreateFromParams(
    CMFCDesktopAlertWndInfo& params,
    CMFCDesktopAlertWnd* pParent);
```

### <a name="parameters"></a>参数

[在]*参数*<br/>

[在]*p 父级*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertdialoggetdlgsize"></a><a name="getdlgsize"></a>CMFC 桌面警报对话：：获取Dlgsize

```
CSize GetDlgSize();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertdialoghasfocus"></a><a name="hasfocus"></a>CMFC 桌面警报对话：：有焦点

```
BOOL HasFocus() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertdialogpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFC 桌面警报对话：:P重新翻译消息

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>参数

[在]*pMsg*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWndInfo 类](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CDialogEx 类](../../mfc/reference/cdialogex-class.md)
