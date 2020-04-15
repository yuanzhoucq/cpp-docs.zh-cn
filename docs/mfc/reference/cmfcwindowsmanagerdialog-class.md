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
ms.openlocfilehash: e3928c0d3ae4f607dceb99c0762277e8ea9ddbde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319828"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog 类

该`CMFCWindowsManagerDialog`对象使用户能够在 MDI 应用程序中管理 MDI 子窗口。

## <a name="syntax"></a>语法

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCWindows管理器对话：：CMFCWindows管理器对话](#cmfcwindowsmanagerdialog)|构造 `CMFCWindowsManagerDialog` 对象。|

## <a name="remarks"></a>备注

包含`CMFCWindowsManagerDialog`当前在应用程序中打开的 MDI 子窗口的列表。 用户可以使用此对话框手动控制 MDI 子窗口的状态。

`CMFCWindowsManagerDialog`嵌入在[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)中。 `CMFCWindowsManagerDialog`不是应手动创建的类。 相反，调用函数[CMDIFrameWndEx：：ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)，它将创建并显示一个`CMFCWindowsManagerDialog`对象。

## <a name="example"></a>示例

下面的示例演示如何通过调用`CMFCWindowsManagerDialog``CMDIFrameWndEx::ShowWindowsDialog`构造对象。 此代码段是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>要求

**标题：** afxWindowsManagerDialog.h

## <a name="cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a>CMFCWindows管理器对话：：CMFCWindows管理器对话

构造[CMFCWindowsManager对话](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)对象。

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>参数

*pMDI框架*<br/>
[在]指向父窗口或所有者窗口的指针。

*b帮助按钮*<br/>
[在]指定框架是否显示 **"帮助"** 按钮的布尔参数。

### <a name="remarks"></a>备注

有关可视化管理器的详细信息，请参阅[可视化管理器](../../mfc/visualization-manager.md)。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)
