---
title: CPaneDialog 类
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: ad1225034cc5eca8ca53b042ebe3b55db4a2cf09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364128"
---
# <a name="cpanedialog-class"></a>CPaneDialog 类

该`CPaneDialog`类支持一个无模式、可停靠的对话框。

## <a name="syntax"></a>语法

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|默认构造函数。|
|`CPaneDialog::~CPaneDialog`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPane对话：创建](#create)|创建可停靠的对话框并将其附加到`CPaneDialog`对象。|
|`CPaneDialog::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CPaneDialog::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CPaneDialog：：手柄对话](#handleinitdialog)|处理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息。 （重新定义`CBasePane::HandleInitDialog`.）|
|`CPaneDialog::OnEraseBkgnd`|处理[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)消息。 （重新定义[Cwnd：onEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).）|
|`CPaneDialog::OnLButtonDblClk`|处理[WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk)消息。 （重新定义[Cwnd：onButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).）|
|`CPaneDialog::OnLButtonDown`|处理[WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown)消息。 （重新定义[Cwnd：：打开按钮](../../mfc/reference/cwnd-class.md#onlbuttondown).）|
|`CPaneDialog::OnUpdateCmdUI`|由框架调用以更新对话框窗口。 （覆盖[可停靠窗格：打开更新 CmdUI](cdockablepane-class.md)。）|
|`CPaneDialog::OnWindowPosChanging`|处理[WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging)消息。 （重新定义[Cwnd：在 WindowPos 更改](../../mfc/reference/cwnd-class.md#onwindowposchanging).）|
|[CPaneDialog：：设置OccDialog信息](#setoccdialoginfo)|指定作为 OLE 控件容器的对话框的模板。|

## <a name="remarks"></a>备注

分两`CPaneDialog`步构造对象。 首先，在代码中构造对象。 第二，调用[CPaneDialog：创建](#create)。 您必须指定有效的资源模板名称或模板 ID，并将指针传递给父窗口。 否则，创建过程将失败。 该对话框必须指定WS_CHILD和WS_VISIBLE样式。 我们建议您也指定WS_CLIPCHILDREN和WS_CLIPSIBLINGS样式。 有关详细信息，请参阅[窗口样式](styles-used-by-mfc.md#window-styles)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[可装窗格](../../mfc/reference/cdockablepane-class.md)

[CPane对话](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>要求

**标题：** afxpanedialog.h

## <a name="cpanedialogcreate"></a><a name="create"></a>CPane对话：创建

创建停靠对话框并将其附加到`CPaneDialog`对象。

```
BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID,
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>参数

*lpsz窗口名称*<br/>
[在]停靠对话框的名称。

*pparentwnd*<br/>
[在]指向父窗口。

*b哈斯格里珀*<br/>
[在]TRUE 以创建带有标题（夹持器）的停靠对话框;否则，FALSE。

*lpszTemplate 名称*<br/>
[在]资源对话框模板的名称。

*nStyle*<br/>
[在]Windows 样式。

*nID*<br/>
[在]控件 ID。

*nIDTemplate*<br/>
[在]对话框模板的资源 ID。

*dwTabbed 风格*<br/>
[在]当用户将另一个控件窗格拖动到此控件窗格的标题上时，该选项卡式窗口的样式。 默认值为AFX_CBRS_REGULAR_TABS。 有关详细信息，请参阅[CBasePane：createEx](../../mfc/reference/cbasepane-class.md#createex)方法的备注部分。

*dwControlBar样式*<br/>
[在]其他样式属性。 默认值为AFX_DEFAULT_DOCKING_PANE_STYLE。 有关详细信息，请参阅[CBasePane：createEx](../../mfc/reference/cbasepane-class.md#createex)方法的备注部分。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

下面的示例演示如何在`Create``CPaneDialog`类中使用 方法。 此示例是["设置窗格大小"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

## <a name="cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a>CPaneDialog：：手柄对话

处理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息。

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*wParam*<br/>
[在]处理接收默认键盘焦点的控件。

*lParam*<br/>
[在]指定其他初始化数据。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。 此外，TRUE 将键盘焦点设置到*wParam*参数指定的控件;FALSE 可防止设置默认键盘焦点。

### <a name="remarks"></a>备注

框架使用此方法初始化控件和对话框的外观。 框架在显示对话框之前调用此方法。

## <a name="cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a>CPaneDialog：：设置OccDialog信息

指定作为 OLE 控件容器的对话框的模板。

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>参数

*pOccDialog信息*<br/>
[在]指向用于创建对话框对象的对话框模板的指针。 此参数的值随后传递到[COccManager：createDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)方法。

### <a name="return-value"></a>返回值

始终为 TRUE。

### <a name="remarks"></a>备注

此方法支持[COccManager](../../mfc/reference/coccmanager-class.md)类，该类管理 OLE 控制站点和 ActiveX 控件。 _AFX_OCC_DIALOG_INFO结构在 afxocc.h 标头文件中定义。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)<br/>
[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)
