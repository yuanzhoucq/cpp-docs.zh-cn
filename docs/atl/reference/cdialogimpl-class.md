---
title: CDialogImpl 类
ms.date: 11/04/2016
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
ms.openlocfilehash: 900a312c97d7b83eac93a372be39a006b3c4344d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327055"
---
# <a name="cdialogimpl-class"></a>CDialogImpl 类

此类提供了创建模式或无模式对话框的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`CDialogImpl`。

*TBase*<br/>
新类的基类。 默认基类是[CWindow](../../atl/reference/cwindow-class.md)。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[创建](#create)|创建无模式对话框。|
|[销毁窗口](#destroywindow)|销毁无模式对话框。|
|[多模态](#domodal)|创建模式对话框。|
|[结束对话](#enddialog)|销毁模式对话框。|

### <a name="cdialogimplbaset-methods"></a>CDialogimplbaseT 方法

|||
|-|-|
|[获得对话](#getdialogproc)|返回当前对话框过程。|
|[映射对话](#mapdialogrect)|将指定矩形的对话框单位映射到屏幕单位（像素）。|
|[OnFinalMessage](#onfinalmessage)|收到最后一条消息后调用，通常WM_NCDESTROY。|

### <a name="static-functions"></a>静态函数

|||
|-|-|
|[DialogProc](#dialogproc)|处理发送到对话框的消息。|
|[开始对话](#startdialogproc)|收到第一条消息以处理发送到对话框的消息时调用。|

## <a name="remarks"></a>备注

有了`CDialogImpl`，您可以创建一个模态或无模式对话框。 `CDialogImpl`提供对话框过程，该过程使用默认消息映射将消息定向到相应的处理程序。

基类析构函数`~CWindowImplRoot`可确保在销毁对象之前窗口已消失。

`CDialogImpl`派生自`CDialogImplBaseT`， 而 后者又派生`CWindowImplRoot`自 。

> [!NOTE]
> 类必须定义指定对话框`IDD`模板资源 ID 的成员。 例如，ATL 项目向导会自动将以下行添加到您的类：

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

向导`MyDlg`名称页中输入的**短名称**的位置。 **Names**

|详细信息|查看|
|--------------------------------|---------|
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|
|在 ATL 中使用对话框|[ATL 窗口类](../../atl/atl-window-classes.md)|
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|
|对话框|[Windows](/windows/win32/dlgbox/dialog-boxes) SDK 中的对话框及其后续主题|

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="cdialogimplcreate"></a><a name="create"></a>CDialogImpl：：创建

创建无模式对话框。

```
HWND Create(
    HWND hWndParent,
    LPARAM dwInitParam = NULL );

HWND Create(
    HWND hWndParent,
    RECT&,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
[在]所有者窗口的句柄。

**RECT&** *rect* [in] 指定对话框大小和位置的[RECT](/previous-versions/dd162897\(v=vs.85\))结构。

*德维尼帕拉姆*<br/>
[在]指定要传递给WM_INITDIALOG消息的*lParam*参数中的对话框的值。

### <a name="return-value"></a>返回值

新创建的对话框的句柄。

### <a name="remarks"></a>备注

此对话框会自动附加到`CDialogImpl`对象。 要创建模态对话框，请调用[DoModal](#domodal)。 上面的第二个覆盖仅用于[CComControl](../../atl/reference/ccomcontrol-class.md)。

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a>CDialogimpl：:D

销毁无模式对话框。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>返回值

如果对话框已成功销毁，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

如果对话框已成功销毁，则返回 TRUE;否则 FALSE。

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a>CDialogImpl：:DialogProc

此静态函数实现对话框过程。

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
[在]对话框的句柄。

*乌姆斯格*<br/>
[在]发送到对话框的消息。

*wParam*<br/>
[在]其他特定于消息的信息。

*lParam*<br/>
[在]其他特定于消息的信息。

### <a name="return-value"></a>返回值

如果处理消息，则为 TRUE;如果消息已处理，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

`DialogProc`使用默认消息映射将消息定向到相应的处理程序。

您可以重写`DialogProc`以提供用于处理消息的不同机制。

## <a name="cdialogimpldomodal"></a><a name="domodal"></a>CDialogimpl：:Do模态

创建模式对话框。

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

如果成功，则调用[EndDialog](#enddialog)中指定的*nRetCode*参数的值。 否则，为 -1。

### <a name="remarks"></a>备注

此对话框会自动附加到`CDialogImpl`对象。

要创建无模式对话框，请调用["创建](#create)"。

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a>CDialogimpl：结束对话

销毁模式对话框。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
[在][CDialogImpl：:Do模态](#domodal)）要返回的值。

### <a name="return-value"></a>返回值

如果对话框已销毁，则为 TRUE;如果对话框已销毁，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

`EndDialog`必须通过对话过程调用。 销毁对话框后，Windows 使用*nRetCode*的值作为 创建对话框的`DoModal`返回值。

> [!NOTE]
> 不要调用`EndDialog`以销毁无模式对话框。 调用[CWindow：:D窗口](../../atl/reference/cwindow-class.md#destroywindow)。

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CDialogImpl：：获取对话Proc

返回`DialogProc`，当前对话框过程。

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>返回值

当前对话框过程。

### <a name="remarks"></a>备注

重写此方法以将对话框过程替换为您自己的对话框过程。

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a>CDialogimpl：：映射对话重新

将指定矩形的对话框单位转换为屏幕单位（像素）。

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向对象`CRect`或[RECT](/windows/win32/api/windef/ns-windef-rect)结构，该结构用于接收包含更新区域的更新的客户端坐标。

### <a name="return-value"></a>返回值

如果更新成功，则非零;如果更新失败，为 0。 若要获得扩展的错误信息，请调用 `GetLastError`。

### <a name="remarks"></a>备注

该函数将指定`RECT`结构中的坐标替换为转换的坐标，从而允许该结构用于创建对话框或在对话框中定位控件。

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a>CDialogimpl：：在最终消息

收到最后一条消息后调用 （`WM_NCDESTROY`通常 ）。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
[在]正在销毁的窗口的句柄。

### <a name="remarks"></a>备注

请注意，如果要在窗口销毁时自动删除对象，可以调用 **"删除此";** 此处。

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a>CDialogImpl：：开始对话

只调用一次，当收到第一条消息时，处理发送到对话框的消息。

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
[在]对话框的句柄。

*乌姆斯格*<br/>
[在]发送到对话框的消息。

*wParam*<br/>
[在]其他特定于消息的信息。

*lParam*<br/>
[在]其他特定于消息的信息。

### <a name="return-value"></a>返回值

窗口过程。

### <a name="remarks"></a>备注

初始调用 后，`StartDialogProc``DialogProc`设置为对话框过程，并进一步调用转到那里。

## <a name="see-also"></a>另请参阅

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[类概述](../../atl/atl-class-overview.md)
