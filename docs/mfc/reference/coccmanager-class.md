---
title: COccManager 类
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
ms.openlocfilehash: c2a49e3396879e5f1e0864ab5342b57541c6b36c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504487"
---
# <a name="coccmanager-class"></a>COccManager 类

管理多个自定义控件站点；通过 `COleControlContainer` 和 `COleControlSite` 对象实现。

## <a name="syntax"></a>语法

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COccManager::CreateContainer](#createcontainer)|创建一个 `COleContainer` 对象。|
|[COccManager::CreateDlgControls](#createdlgcontrols)|创建由关联`COleContainer`的对象承载的 ActiveX 控件。|
|[COccManager::CreateSite](#createsite)|创建一个 `COleClientSite` 对象。|
|[COccManager::GetDefBtnCode](#getdefbtncode)|检索默认按钮的代码。|
|[COccManager::IsDialogMessage](#isdialogmessage)|确定对话消息的目标。|
|[COccManager::IsLabelControl](#islabelcontrol)|确定指定的控件是否为标签控件。|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|确定当前助记键是否与指定控件的助记键匹配。|
|[COccManager::OnEvent](#onevent)|尝试处理指定的事件。|
|[COccManager::PostCreateDialog](#postcreatedialog)|释放在创建对话框的过程中分配的资源。|
|[COccManager::PreCreateDialog](#precreatedialog)|处理 ActiveX 控件的对话框模板。|
|[COccManager::SetDefaultButton](#setdefaultbutton)|切换指定控件的默认状态。|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|分隔指定对话框模板中的公共控件中的任何现有 ActiveX 控件。|

## <a name="remarks"></a>备注

基类`CNoTrackObject`是未记录的基类 (位于 AFXTLS 中。H)。 旨在供 MFC 框架使用, 从`CNoTrackObject`类派生的类不受内存泄漏检测的阻止。 不建议直接从`CNoTrackObject`派生。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>要求

**标头:** afxocc

##  <a name="createcontainer"></a>COccManager:: CreateContainer

由框架调用以创建控件容器。

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向与自定义站点容器关联的窗口对象的指针。

### <a name="return-value"></a>返回值

指向新创建的容器的指针;否则为 NULL。

### <a name="remarks"></a>备注

有关创建自定义网站的详细信息, 请参阅[COleControlContainer:: AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)。

##  <a name="createdlgcontrols"></a>COccManager::CreateDlgControls

调用此函数可创建由*pOccDialogInfo*参数指定的 ActiveX 控件。

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

*pWndParent*<br/>
指向对话框对象的父对象的指针。

*lpszResourceName*<br/>
正在创建的资源的名称。

*pOccDialogInfo*<br/>
指向用于创建对话框对象的对话框模板的指针。

*lpResource*<br/>
指向资源的指针。

### <a name="return-value"></a>返回值

如果已成功创建控件, 则为非零值;否则为零。

##  <a name="createsite"></a>COccManager:: 网站

由框架调用, 以创建由*pCtrlCont*指向的容器承载的控制站点。

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>参数

*pCtrlCont*<br/>
一个指针, 指向承载新控件网站的控件容器。

### <a name="return-value"></a>返回值

指向新创建的控件站点的指针。

### <a name="remarks"></a>备注

使用[COleControlSite](../../mfc/reference/colecontrolsite-class.md)派生类重写此函数以创建自定义控件站点。

每个控件容器都可以托管多个站点。 创建具有多个调用`CreateSite`的其他站点。

##  <a name="getdefbtncode"></a>COccManager::GetDefBtnCode

调用此函数可确定控件是否为默认按钮。

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
包含 button 控件的窗口对象。

### <a name="return-value"></a>返回值

以下值之一：

- DLGC_DEFPUSHBUTTON 控件是对话框中的默认按钮。

- DLGC_UNDEFPUSHBUTTON 控件不是对话框中的默认按钮。

- **0**控件不是按钮。

##  <a name="isdialogmessage"></a>COccManager::IsDialogMessage

由框架调用, 用于确定消息是否用于指定的对话框, 如果为, 则处理消息。

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>参数

*pWndDlg*<br/>
指向消息的目标对话框的指针。

*lpMsg*<br/>
指向`MSG`结构的指针, 该结构包含要检查的消息。

### <a name="return-value"></a>返回值

如果处理消息, 则为非零值;否则为零。

### <a name="remarks"></a>备注

的`IsDialogMessage`默认行为是检查键盘消息, 并将其转换为相应对话框的选定内容。 例如, 按 TAB 键时, 将选择下一个控件或一组控件。

重写此函数以提供发送到指定对话框的消息的自定义行为。

##  <a name="islabelcontrol"></a>COccManager::IsLabelControl

调用此函数可确定指定的控件是否为标签控件。

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向包含控件的窗口的指针。

### <a name="return-value"></a>返回值

如果控件是标签, 则为非零值;否则为零

### <a name="remarks"></a>备注

"标签" 控件是一个, 它的作用类似于排序中下一控件的标签。

##  <a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic

调用此函数可确定当前助记键是否与由控件表示的助记键相匹配。

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向包含控件的窗口的指针。

*lpMsg*<br/>
指向包含要匹配的助记键的消息的指针。

### <a name="return-value"></a>返回值

如果助记键与控件匹配, 则为非零值;否则为零

### <a name="remarks"></a>备注

##  <a name="onevent"></a>COccManager:: OnEvent

由框架调用, 用于处理指定的事件。

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>参数

*pCmdTarget*<br/>
指向试图处理事件`CCmdTarget`的对象的指针

*idCtrl*<br/>
控件的资源 ID。

*pEvent*<br/>
正在处理的事件。

*pHandlerInfo*<br/>
如果不为 NULL `OnEvent` , 则填充`pTarget` `AFX_CMDHANDLERINFO`结构`pmf`的和成员, 而不是分派命令。 通常, 此参数应为 NULL。

### <a name="return-value"></a>返回值

如果已处理事件, 则为非零; 否则为零。

### <a name="remarks"></a>备注

重写此函数以自定义默认事件处理过程。

##  <a name="precreatedialog"></a>COccManager::P reCreateDialog

由框架调用, 用于在创建实际对话框之前处理 ActiveX 控件的对话框模板。

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>参数

*pOccDialogInfo*<br/>
一个`_AFX_OCC_DIALOG_INFO`结构, 该结构包含对话框所承载的对话框模板和任何 ActiveX 控件的信息。

*pOrigTemplate*<br/>
一个指针, 指向要在创建对话框时使用的对话框模板。

### <a name="return-value"></a>返回值

一个指针, 指向用于创建对话框的对话框模板结构。

### <a name="remarks"></a>备注

默认行为将调用`SplitDialogTemplate`, 从而确定是否存在任何 ActiveX 控件, 然后返回生成的对话框模板。

重写此函数以自定义用于创建承载 ActiveX 控件的对话框的过程。

##  <a name="postcreatedialog"></a>COccManager::P ostCreateDialog

由框架调用以释放为对话框模板分配的内存。

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>参数

*pOccDialogInfo*<br/>
一个`_AFX_OCC_DIALOG_INFO`结构, 该结构包含对话框所承载的对话框模板和任何 ActiveX 控件的信息。

### <a name="remarks"></a>备注

此内存由对的调用`SplitDialogTemplate`分配, 并用于对话框中的任何托管 ActiveX 控件。

重写此函数以自定义清理对话框对象所使用的任何资源的过程。

##  <a name="setdefaultbutton"></a>COccManager::SetDefaultButton

调用此函数可将控件设置为默认按钮。

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向包含控件的窗口的指针。

*bDefault*<br/>
如果控件应成为默认按钮, 则为非零值;否则为零。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

> [!NOTE]
>  控件必须设置 OLEMISC_ACTSLIKEBUTTON 状态位。 有关 OLEMISC 标志的详细信息, 请参阅 "Windows SDK 中的[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)主题。

##  <a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate

由框架调用, 用于从公共对话框控件拆分 ActiveX 控件。

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>参数

*pTemplate*<br/>
指向要检查的对话框模板的指针。

*ppOleDlgItems*<br/>
指向属于 ActiveX 控件的对话框项的指针列表。

### <a name="return-value"></a>返回值

指向仅包含非 ActiveX 控件的对话框模板结构的指针。 如果没有 ActiveX 控件, 则返回 NULL。

### <a name="remarks"></a>备注

如果找到任何 ActiveX 控件, 则会分析模板, 并创建仅包含非 ActiveX 控件的新模板。 在此过程中找到的任何 ActiveX 控件都将添加到*ppOleDlgItems*中。

如果模板中没有 ActiveX 控件, 则返回 NULL *。*

> [!NOTE]
>  为新模板分配的内存在`PostCreateDialog`函数中释放。

重写此函数以自定义此过程。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 类](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer 类](../../mfc/reference/colecontrolcontainer-class.md)
