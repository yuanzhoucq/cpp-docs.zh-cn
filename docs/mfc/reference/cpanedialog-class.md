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
ms.openlocfilehash: e7ff55e37194d0fa405925e4b3895428cfcaf9eb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502984"
---
# <a name="cpanedialog-class"></a>CPaneDialog 类

`CPaneDialog`类支持无模式的可停靠对话框。

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
|[CPaneDialog::Create](#create)|创建可停靠对话框, 并将其附加到`CPaneDialog`对象。|
|`CPaneDialog::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CPaneDialog::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|处理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息。 (重新`CBasePane::HandleInitDialog`定义。)|
|`CPaneDialog::OnEraseBkgnd`|处理[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)消息。 (重定义[CWnd:: OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)。)|
|`CPaneDialog::OnLButtonDblClk`|处理[WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk)消息。 (重定义[CWnd:: OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)。)|
|`CPaneDialog::OnLButtonDown`|处理[WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown)消息。 (重定义[CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)。)|
|`CPaneDialog::OnUpdateCmdUI`|由框架调用以更新对话框窗口。 (重写[CDockablePane:: OnUpdateCmdUI](cdockablepane-class.md)。)|
|`CPaneDialog::OnWindowPosChanging`|处理[WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging)消息。 (重定义[CWnd:: OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)。)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|为作为 OLE 控件容器的对话框指定模板。|

## <a name="remarks"></a>备注

按两个步骤构造对象。`CPaneDialog` 首先, 在代码中构造对象。 然后调用[CPaneDialog:: Create](#create)。 必须指定有效的资源模板名称或模板 ID, 并向父窗口传递指针。 否则, 创建过程将失败。 此对话框必须指定 WS_CHILD 和 WS_VISIBLE 样式。 建议你同时指定 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS 样式。 有关详细信息, 请参阅[窗口样式](styles-used-by-mfc.md#window-styles)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>要求

**标头:** afxpanedialog

##  <a name="create"></a>CPaneDialog:: Create

创建一个停靠对话框, 并将其附加到`CPaneDialog`对象。

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
中停靠对话框的名称。

*pParentWnd*<br/>
中指向父窗口。

*bHasGripper*<br/>
中若要创建带标题的停靠对话框 (手柄), 则为 TRUE;否则为 FALSE。

*lpszTemplateName*<br/>
中资源对话框模板的名称。

*nStyle*<br/>
中Windows 样式。

*nID*<br/>
中控件 ID。

*nIDTemplate*<br/>
中对话框模板的资源 ID。

*dwTabbedStyle*<br/>
中当用户将其他控件窗格拖动到此控件窗格的标题上时产生的选项卡式窗口的样式。 默认值为 AFX_CBRS_REGULAR_TABS。 有关详细信息, 请参阅[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)方法的 "备注" 部分。

*dwControlBarStyle*<br/>
中其他样式属性。 默认值为 AFX_DEFAULT_DOCKING_PANE_STYLE。 有关详细信息, 请参阅[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)方法的 "备注" 部分。

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

下面的示例演示如何使用`Create` `CPaneDialog`类中的方法。 此示例是[集窗格大小示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog

处理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息。

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*wParam*<br/>
中用于接收默认键盘焦点的控件的句柄。

*lParam*<br/>
中指定额外的初始化数据。

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。 此外, 如果为 TRUE, 则将键盘焦点设置到由*wParam*参数指定的控件;FALSE 阻止设置默认键盘焦点。

### <a name="remarks"></a>备注

框架使用此方法来初始化控件和对话框的外观。 框架在显示对话框之前调用此方法。

##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo

为作为 OLE 控件容器的对话框指定模板。

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>参数

*pOccDialogInfo*<br/>
中指向用于创建对话框对象的对话框模板的指针。 此参数的值随后会传递到[COccManager:: CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)方法。

### <a name="return-value"></a>返回值

始终为 TRUE。

### <a name="remarks"></a>备注

此方法支持[COccManager](../../mfc/reference/coccmanager-class.md)类, 该类用于管理 OLE 控件站点和 ActiveX 控件。 _AFX_OCC_DIALOG_INFO 结构在 afxocc 头文件中定义。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)<br/>
[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)
