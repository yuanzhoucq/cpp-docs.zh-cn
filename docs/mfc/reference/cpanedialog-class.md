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
ms.openlocfilehash: 16aa707792cc1289ced380e54abef3f15289e7cf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274552"
---
# <a name="cpanedialog-class"></a>CPaneDialog 类

`CPaneDialog`类支持无模式可停靠的对话框。

## <a name="syntax"></a>语法

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|默认构造函数。|
|`CPaneDialog::~CPaneDialog`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CPaneDialog::Create](#create)|创建可停靠对话框，并将其附加到`CPaneDialog`对象。|
|`CPaneDialog::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CPaneDialog::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|处理[WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog)消息。 (重定义`CBasePane::HandleInitDialog`。)|
|`CPaneDialog::OnEraseBkgnd`|处理[WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd)消息。 (重新定义[CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)。)|
|`CPaneDialog::OnLButtonDblClk`|处理[需知道 WM_LBUTTONDBLCLK](/windows/desktop/inputdev/wm-lbuttondblclk)消息。 (重新定义[CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)。)|
|`CPaneDialog::OnLButtonDown`|处理[WM_LBUTTONDOWN](/windows/desktop/inputdev/wm-lbuttondown)消息。 (重新定义[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)。)|
|`CPaneDialog::OnUpdateCmdUI`|由框架调用以更新对话框窗口。 (重写[cdockablepane:: Onupdatecmdui](cdockablepane-class.md)。)|
|`CPaneDialog::OnWindowPosChanging`|处理[WM_WINDOWPOSCHANGING](/windows/desktop/winmsg/wm-windowposchanging)消息。 (重新定义[CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)。)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|指定的 OLE 控件容器的对话框的模板。|

## <a name="remarks"></a>备注

构造`CPaneDialog`两个步骤中的对象。 首先，构建你的代码中的对象。 其次，调用[CPaneDialog::Create](#create)。 必须指定有效的资源模板或模板 ID，并将指针传递到父窗口。 否则，将创建过程失败。 对话框的必须指定 WS_CHILD 和 WS_VISIBLE 样式。 我们建议你同时指定 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS 样式。 有关详细信息，请参阅[的窗口样式](styles-used-by-mfc.md#window-styles)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>要求

**标头：** afxpanedialog.h

##  <a name="create"></a>  CPaneDialog::Create

创建停靠的对话框中，并将其附加到`CPaneDialog`对象。

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

*lpszWindowName*<br/>
[in]停靠对话框中的名称。

*pParentWnd*<br/>
[in]指向父窗口。

*bHasGripper*<br/>
[in]若要创建带有描述文字 （手柄）; 停靠对话框中，则返回 TRUE否则为 FALSE。

*lpszTemplateName*<br/>
[in]资源对话框模板的名称。

*nStyle*<br/>
[in]Windows 样式中。

*nID*<br/>
[in]控件 id。

*nIDTemplate*<br/>
[in]在对话框模板资源 ID。

*dwTabbedStyle*<br/>
[in]当用户将另一个控制窗格拖动到此控件窗格的标题上时，产生的选项卡式窗口的样式。 默认值为 AFX_CBRS_REGULAR_TABS。 有关详细信息，请参阅备注部分[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)方法。

*dwControlBarStyle*<br/>
[in]其他样式特性。 默认值为 AFX_DEFAULT_DOCKING_PANE_STYLE。 有关详细信息，请参阅备注部分[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)方法。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

下面的示例演示如何使用`Create`中的方法`CPaneDialog`类。 此示例摘自[设置窗格大小示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog

处理[WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog)消息。

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*wParam*<br/>
[in]若要接收的默认键盘焦点的控件的句柄。

*lParam*<br/>
[in]指定附加的初始化数据。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。 此外，TRUE 将键盘焦点设置为指定的控件*wParam*参数;FALSE 会阻止设置的默认键盘焦点。

### <a name="remarks"></a>备注

该框架使用此方法来初始化控件和对话框的外观。 然后再显示对话框中，框架将调用此方法。

##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo

指定的 OLE 控件容器的对话框的模板。

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>参数

*pOccDialogInfo*<br/>
[in]到对话框模板用于创建对话框对象的指针。 此参数的值随后传递到[COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)方法。

### <a name="return-value"></a>返回值

始终为 TRUE。

### <a name="remarks"></a>备注

此方法支持[COccManager](../../mfc/reference/coccmanager-class.md)类，该类管理 OLE 控件站点和 ActiveX 控件。 _AFX_OCC_DIALOG_INFO 结构 afxocc.h 标头文件中定义。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)<br/>
[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)
