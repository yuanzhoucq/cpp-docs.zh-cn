---
title: COcc经理类
ms.date: 11/04/2016
f1_keywords:
- COccManager
- AFXOCC/COccManager
- AFXOCC/COccManager::CreateContainer
- AFXOCC/COccManager::CreateDlgControls
- AFXOCC/COccManager::CreateSite
- AFXOCC/COccManager::GetDefBtnCode
- AFXOCC/COccManager::IsDialogMessage
- AFXOCC/COccManager::IsLabelControl
- AFXOCC/COccManager::IsMatchingMnemonic
- AFXOCC/COccManager::OnEvent
- AFXOCC/COccManager::PostCreateDialog
- AFXOCC/COccManager::PreCreateDialog
- AFXOCC/COccManager::SetDefaultButton
- AFXOCC/COccManager::SplitDialogTemplate
helpviewer_keywords:
- COccManager [MFC], CreateContainer
- COccManager [MFC], CreateDlgControls
- COccManager [MFC], CreateSite
- COccManager [MFC], GetDefBtnCode
- COccManager [MFC], IsDialogMessage
- COccManager [MFC], IsLabelControl
- COccManager [MFC], IsMatchingMnemonic
- COccManager [MFC], OnEvent
- COccManager [MFC], PostCreateDialog
- COccManager [MFC], PreCreateDialog
- COccManager [MFC], SetDefaultButton
- COccManager [MFC], SplitDialogTemplate
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
ms.openlocfilehash: 5637a4709e90bb14caff3fe4e396487e62e213e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360352"
---
# <a name="coccmanager-class"></a>COcc经理类

管理多个自定义控件站点；通过 `COleControlContainer` 和 `COleControlSite` 对象实现。

## <a name="syntax"></a>语法

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COcc管理器：创建容器](#createcontainer)|创建一个 `COleContainer` 对象。|
|[COcc管理器：：创建Dlg控制](#createdlgcontrols)|创建由关联`COleContainer`对象托管的 ActiveX 控件。|
|[COcc经理：创建网站](#createsite)|创建一个 `COleClientSite` 对象。|
|[COcc经理：获取DefBtn代码](#getdefbtncode)|检索默认按钮的代码。|
|[COcc经理：：对话消息](#isdialogmessage)|确定对话框消息的目标。|
|[COcc管理器：：是标签控制](#islabelcontrol)|确定指定的控件是否为标签控件。|
|[COcc经理：是匹配的Mnemonic](#ismatchingmnemonic)|确定当前助记符是否与指定控件的助记符匹配。|
|[COcc经理：在活动](#onevent)|尝试处理指定事件。|
|[COcc经理：:P创造对话](#postcreatedialog)|释放在创建对话框期间分配的资源。|
|[COcc经理：:P重新创建对话](#precreatedialog)|处理 ActiveX 控件的对话框模板。|
|[COcc管理器：设置默认按钮](#setdefaultbutton)|切换指定控件的默认状态。|
|[COcc管理器：拆分对话模板](#splitdialogtemplate)|将任何现有的 ActiveX 控件与指定对话框模板中的常用控件分开。|

## <a name="remarks"></a>备注

基类`CNoTrackObject`是未记录的基类（位于 AFXTLS 中）。H）。 设计为供 MFC 框架使用，派生自类的`CNoTrackObject`类不受内存泄漏检测。 不建议您直接从`CNoTrackObject`派生。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>要求

**标题：** afxocc.h

## <a name="coccmanagercreatecontainer"></a><a name="createcontainer"></a>COcc管理器：创建容器

由框架调用以创建控件容器。

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向与自定义网站容器关联的窗口对象的指针。

### <a name="return-value"></a>返回值

指向新创建的容器的指针;指向新创建的容器的指针。否则 NULL。

### <a name="remarks"></a>备注

有关创建自定义网站的详细信息，请参阅[COleControl 容器：：附加控制站点](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)。

## <a name="coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a>COcc管理器：：创建Dlg控制

调用此函数以创建由*pOccDialogInfo*参数指定的 ActiveX 控件。

```
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    LPCTSTR lpszResourceName,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);

virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    void* lpResource,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
指向对话框对象的父级的指针。

*lpsz 资源名称*<br/>
正在创建的资源的名称。

*pOccDialog信息*<br/>
指向用于创建对话框对象的对话框模板的指针。

*lp资源*<br/>
指向资源的指针。

### <a name="return-value"></a>返回值

如果控件已成功创建，则非零;否则为零。

## <a name="coccmanagercreatesite"></a><a name="createsite"></a>COcc经理：创建网站

由框架调用以创建一个控制站点，由*pCtrlCont*指向的容器托管。

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>参数

*pCtrlCont*<br/>
指向承载新控件站点的控件容器的指针。

### <a name="return-value"></a>返回值

指向新创建的控件站点的指针。

### <a name="remarks"></a>备注

重写此函数，使用[COleControlControlSite](../../mfc/reference/colecontrolsite-class.md)派生类创建自定义控件站点。

每个控件容器可以承载多个站点。 创建具有多个调用的其他站点`CreateSite`。

## <a name="coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a>COcc经理：获取DefBtn代码

调用此函数以确定控件是否为默认按钮。

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
包含按钮控件的窗口对象。

### <a name="return-value"></a>返回值

以下值之一：

- DLGC_DEFPUSHBUTTON控件是对话框中的默认按钮。

- DLGC_UNDEFPUSHBUTTON控件不是对话框中的默认按钮。

- **0**控件不是按钮。

## <a name="coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a>COcc经理：：对话消息

由框架调用以确定消息是否用于指定的对话框，如果是，则处理消息。

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>参数

*普恩德德格*<br/>
指向消息的预期目标对话框的指针。

*lpMsg*<br/>
指向包含要检查`MSG`的消息的结构的指针。

### <a name="return-value"></a>返回值

处理消息时非零;否则为零。

### <a name="remarks"></a>备注

的默认行为`IsDialogMessage`是检查键盘消息并将其转换为相应对话框的选择。 例如，按下 TAB 键时，选择下一个控件或控件组。

重写此函数，为发送到指定对话框的消息提供自定义行为。

## <a name="coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a>COcc管理器：：是标签控制

调用此函数以确定指定的控件是否为标签控件。

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向包含控件的窗口的指针。

### <a name="return-value"></a>返回值

如果控件是标签，则非零;否则零

### <a name="remarks"></a>备注

标签控件类似于排序中下一个控件的标签。

## <a name="coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a>COcc经理：是匹配的Mnemonic

调用此函数以确定当前助记符是否与控件表示的表示匹配。

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向包含控件的窗口的指针。

*lpMsg*<br/>
指向要匹配的助记符的消息的指针。

### <a name="return-value"></a>返回值

如果助记符与控件匹配，则非零;否则零

### <a name="remarks"></a>备注

## <a name="coccmanageronevent"></a><a name="onevent"></a>COcc经理：在活动

由框架调用以处理指定的事件。

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>参数

*pCmdTarget*<br/>
指向尝试处理事件`CCmdTarget`的对象的指针

*idCtrl*<br/>
控件的资源 ID。

*pEvent*<br/>
正在处理的事件。

*pHandlerInfo*<br/>
如果不是 NULL，`OnEvent`请填写 结构`pTarget``pmf`的 和`AFX_CMDHANDLERINFO`成员，而不是调度命令。 通常，此参数应为 NULL。

### <a name="return-value"></a>返回值

如果处理了事件，则非零，否则为零。

### <a name="remarks"></a>备注

重写此函数以自定义默认事件处理过程。

## <a name="coccmanagerprecreatedialog"></a><a name="precreatedialog"></a>COcc经理：:P重新创建对话

框架调用在创建实际对话框之前处理 ActiveX 控件的对话框模板。

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>参数

*pOccDialog信息*<br/>
包含`_AFX_OCC_DIALOG_INFO`对话框模板和对话框托管的任何 ActiveX 控件的信息的结构。

*pOrigTemplate*<br/>
指向用于创建对话框的对话框的对话框的指针。

### <a name="return-value"></a>返回值

指向用于创建对话框的对话框的对话框模板结构的指针。

### <a name="remarks"></a>备注

默认行为调用`SplitDialogTemplate`，确定是否存在任何 ActiveX 控件，然后返回由此产生的对话框模板。

重写此函数以自定义创建承载 ActiveX 控件的对话框的过程。

## <a name="coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a>COcc经理：:P创造对话

框架调用以释放分配给对话框模板的内存。

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>参数

*pOccDialog信息*<br/>
包含`_AFX_OCC_DIALOG_INFO`对话框模板和对话框托管的任何 ActiveX 控件的信息的结构。

### <a name="remarks"></a>备注

此内存由 调用`SplitDialogTemplate`分配给 分配，并用于对话框中的任何托管 ActiveX 控件。

重写此函数以自定义清理对话框对象使用的任何资源的过程。

## <a name="coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a>COcc管理器：设置默认按钮

调用此函数将控件设置为默认按钮。

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向包含控件的窗口的指针。

*b默认*<br/>
如果控件应成为默认按钮，则非零;否则为零。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

> [!NOTE]
> 控件必须设置OLEMISC_ACTSLIKEBUTTON状态位。 有关 OLEMISC 标志的详细信息，请参阅 Windows SDK 中的[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)主题。

## <a name="coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a>COcc管理器：拆分对话模板

由框架调用以从公共对话框控件拆分 ActiveX 控件。

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>参数

*pTemplate*<br/>
指向要检查的对话框模板的指针。

*ppOleDlg项目*<br/>
指向作为 ActiveX 控件的对话框项的指针列表。

### <a name="return-value"></a>返回值

指向仅包含非 ActiveX 控件的对话框模板结构的指针。 如果不存在 ActiveX 控件，则返回 NULL。

### <a name="remarks"></a>备注

如果找到任何 ActiveX 控件，将分析模板，并创建一个新模板，其中仅包含非 ActiveX 控件。 在此过程中找到的任何 ActiveX 控件都添加到*ppOleDlgItems*中。

如果模板中没有 ActiveX 控件，则返回*NULL。*

> [!NOTE]
> 为新模板分配的内存将在`PostCreateDialog`函数中释放。

重写此函数以自定义此过程。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 类](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer 类](../../mfc/reference/colecontrolcontainer-class.md)
