---
title: CMFCWindowsManagerDialog 类
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 67fbd1ed066b47cdedf1b5ea2952b042c69bd978
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554305"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog 类

`CMFCWindowsManagerDialog`对象使用户管理 MDI 子窗口的 MDI 应用程序中。

## <a name="syntax"></a>语法

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|构造 `CMFCWindowsManagerDialog` 对象。|

## <a name="remarks"></a>备注

`CMFCWindowsManagerDialog`包含应用程序中当前打开的 MDI 子窗口的列表。 通过使用此对话框中，用户可以手动控制 MDI 子窗口的状态。

`CMFCWindowsManagerDialog` 嵌入到内部[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)。 `CMFCWindowsManagerDialog`不应手动创建的类。 相反，调用函数[CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)，它将创建和显示`CMFCWindowsManagerDialog`对象。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCWindowsManagerDialog`对象通过调用`CMDIFrameWndEx::ShowWindowsDialog`。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>要求

**标头：** afxWindowsManagerDialog.h

##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

构造[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)对象。

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>参数

*pMDIFrame*<br/>
[in]指向父或所有者窗口的指针。

*bHelpButton*<br/>
[in]一个布尔参数，指定是否显示在框架**帮助**按钮。

### <a name="remarks"></a>备注

视觉管理器的详细信息，请参阅[可视化管理器](../../mfc/visualization-manager.md)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)
