---
title: CAxDialogImpl 类
ms.date: 11/04/2016
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
ms.openlocfilehash: d8e60a817d197f67c14318a7d50ddf796e570142
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318743"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl 类

此类实现承载 ActiveX 控件的对话框（模式或无模式）。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`CAxDialogImpl`。

*TBase*<br/>
的基本窗口类`CDialogImplBaseT`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAx对话：：建议SinkMap](#advisesinkmap)|调用此方法可建议或取消通知对象接收器映射事件映射中的所有条目。|
|[CAx对话：：创建](#create)|调用此方法以创建无模式对话框。|
|[CAx对话：:D](#destroywindow)|调用此方法以销毁无模式对话框。|
|[CAx对话：:Do模态](#domodal)|调用此方法以创建模态对话框。|
|[CAx对话：：结束对话](#enddialog)|调用此方法以销毁模式对话框。|
|[CAx对话：：获取对话Proc](#getdialogproc)|调用此方法以获取指向回调函数的`DialogProc`指针。|
|[CAx对话：：获取IDD](#getidd)|调用此方法获取对话框模板资源 ID|
|[CAx对话：：对话消息](#isdialogmessage)|调用此方法以确定消息是否用于此对话框，如果是，则处理该消息。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CAx对话：：m_bModal](#m_bmodal)|仅在调试生成中存在的变量，如果对话框是模态的，则设置为 true。|

## <a name="remarks"></a>备注

`CAxDialogImpl`允许您创建模态或无模式对话框。 `CAxDialogImpl`提供对话框过程，该过程使用默认消息映射将消息定向到相应的处理程序。

`CAxDialogImpl`派生自`CDialogImplBaseT`， 它又派生自*TBase* （默认情况下）`CWindow`和`CMessageMap`。

类必须定义指定对话框模板资源 ID 的 IDD 成员。 例如，使用 **"添加类"** 对话框添加 ATL 对话框会自动将以下行添加到类：

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

ATL 对话框向导中输入`MyDialog`**的短名称**的位置。

有关详细信息[，请参阅实现对话框](../../atl/implementing-a-dialog-box.md)。

请注意，使用模式`CAxDialogImpl`对话框创建的 ActiveX 控件将不支持快捷键。 要支持使用`CAxDialogImpl`创建的对话框上的快捷键，请创建一个无模式对话框，并使用您自己的消息循环，在从队列中收到消息以处理快捷键后使用[CAxDialogImpl：isDialogMessage。](#isdialogmessage)

有关 的详细信息`CAxDialogImpl`，请参阅[ATL 控制控制控制常见问题 解答](../../atl/atl-control-containment-faq.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="caxdialogimpladvisesinkmap"></a><a name="advisesinkmap"></a>CAx对话：：建议SinkMap

调用此方法可建议或取消通知对象接收器映射事件映射中的所有条目。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>参数

*b 建议*<br/>
如果建议所有接收器条目，则设置为 true;如果所有接收器条目都是未通知的，则为 false。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="caxdialogimplcreate"></a><a name="create"></a>CAx对话：：创建

调用此方法以创建无模式对话框。

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
[在]所有者窗口的句柄。

*德维尼帕拉姆*<br/>
[在]指定要传递给WM_INITDIALOG消息的*lParam*参数中的对话框的值。

*reCT&*<br/>
未使用此参数。 此参数通过 传入`CComControl`。

### <a name="return-value"></a>返回值

新创建的对话框的句柄。

### <a name="remarks"></a>备注

此对话框会自动附加到`CAxDialogImpl`对象。 要创建模态对话框，请调用[DoModal](#domodal)。

第二个重写仅提供，因此对话框可以与[CComControl](../../atl/reference/ccomcontrol-class.md)一起使用。

## <a name="caxdialogimpldestroywindow"></a><a name="destroywindow"></a>CAx对话：:D

调用此方法以销毁无模式对话框。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>返回值

如果窗口已成功销毁，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

不要调用`DestroyWindow`以销毁模式对话框。 请改为调用[结束对话](#enddialog)。

## <a name="caxdialogimpldomodal"></a><a name="domodal"></a>CAx对话：:Do模态

调用此方法以创建模态对话框。

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
[在]所有者窗口的句柄。 默认值是[GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32 函数的返回值。

*德维尼帕拉姆*<br/>
[在]指定要传递给WM_INITDIALOG消息的*lParam*参数中的对话框的值。

### <a name="return-value"></a>返回值

如果成功，则调用[EndDialog](#enddialog)中指定的*nRetCode*参数的值。否则，-1。

### <a name="remarks"></a>备注

此对话框会自动附加到`CAxDialogImpl`对象。

要创建无模式对话框，请调用["创建](#create)"。

## <a name="caxdialogimplenddialog"></a><a name="enddialog"></a>CAx对话：：结束对话

调用此方法以销毁模式对话框。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
[在][DoModal](#domodal)要返回的值。

### <a name="return-value"></a>返回值

如果对话框已销毁，则为 TRUE;如果对话框已销毁，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

`EndDialog`必须通过对话框过程调用。 销毁对话框后，Windows 使用*nRetCode*的值作为 创建对话框的`DoModal`返回值。

> [!NOTE]
> 不要调用`EndDialog`以销毁无模式对话框。 请改为调用[销毁窗口](#destroywindow)。

## <a name="caxdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CAx对话：：获取对话Proc

调用此方法以获取指向回调函数的`DialogProc`指针。

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>返回值

返回指向回调函数的`DialogProc`指针。

### <a name="remarks"></a>备注

该`DialogProc`函数是应用程序定义的回调函数。

## <a name="caxdialogimplgetidd"></a><a name="getidd"></a>CAx对话：：获取IDD

调用此方法获取对话框模板资源 ID。

```
int GetIDD();
```

### <a name="return-value"></a>返回值

返回对话框模板资源 ID。

## <a name="caxdialogimplisdialogmessage"></a><a name="isdialogmessage"></a>CAx对话：：对话消息

调用此方法以确定消息是否用于此对话框，如果是，则处理该消息。

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>参数

*pMsg*<br/>
指向包含要检查的消息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)结构的指针。

### <a name="return-value"></a>返回值

如果消息已处理，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此方法旨在从消息循环中调用。

## <a name="caxdialogimplm_bmodal"></a><a name="m_bmodal"></a>CAx对话：：m_bModal

仅在调试生成中存在的变量，如果对话框是模态的，则设置为 true。

```
bool m_bModal;
```

## <a name="see-also"></a>另请参阅

[CDialogImpl 类](../../atl/reference/cdialogimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
