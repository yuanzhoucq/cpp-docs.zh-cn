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
ms.openlocfilehash: bc39a5deeb270b0426a4b199fc9ba01917c292bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496818"
---
# <a name="cdialogimpl-class"></a>CDialogImpl 类

此类提供用于创建模式对话框或无模式对话框的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`CDialogImpl`的类。

*TBase*<br/>
新类的基类。 默认基类为[CWindow](../../atl/reference/cwindow-class.md)。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[创建](#create)|创建无模式对话框。|
|[DestroyWindow](#destroywindow)|销毁无模式对话框。|
|[DoModal](#domodal)|创建模式对话框。|
|[EndDialog](#enddialog)|销毁模式对话框。|

### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT 方法

|||
|-|-|
|[GetDialogProc](#getdialogproc)|返回当前对话框的过程。|
|[MapDialogRect](#mapdialogrect)|将指定矩形的对话框单位映射到屏幕单位（像素）。|
|[OnFinalMessage](#onfinalmessage)|在收到最后一条消息后调用，通常为 WM_NCDESTROY。|

### <a name="static-functions"></a>静态函数

|||
|-|-|
|[DialogProc](#dialogproc)|处理发送到对话框的消息。|
|[StartDialogProc](#startdialogproc)|当收到第一条消息来处理发送到对话框的消息时调用。|

## <a name="remarks"></a>备注

使用`CDialogImpl`可以创建模式对话框或无模式对话框。 `CDialogImpl`提供对话框过程，该过程使用默认消息映射将消息定向到适当的处理程序。

基类析构函数`~CWindowImplRoot`确保在销毁对象之前窗口已消失。

`CDialogImpl``CWindowImplRoot`派生自`CDialogImplBaseT`，而后者又派生自。

> [!NOTE]
>  类必须定义一个`IDD`指定对话框模板资源 ID 的成员。 例如，ATL 项目向导会自动将以下行添加到类：

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

其中`MyDlg` ，是在向导的 "**名称**" 页中输入的**短名称**。

|有关以下内容的详细信息|查看|
|--------------------------------|---------|
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|
|在 ATL 中使用对话框|[ATL 窗口类](../../atl/atl-window-classes.md)|
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|
|对话框|[对话框](/windows/win32/dlgbox/dialog-boxes)和 Windows SDK 中的后续主题|

## <a name="requirements"></a>要求

**标头：** atlwin。h

##  <a name="create"></a>CDialogImpl：： Create

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

*hWndParent*<br/>
中所有者窗口的句柄。

**RECT &** *rect*中指定对话框大小和位置的[矩形](/previous-versions/dd162897\(v=vs.85\))结构。

*dwInitParam*<br/>
中在 WM_INITDIALOG 消息的*lParam*参数中指定要传递到对话框的值。

### <a name="return-value"></a>返回值

新创建的对话框的句柄。

### <a name="remarks"></a>备注

此对话框自动附加到`CDialogImpl`对象。 若要创建模式对话框，请调用[DoModal](#domodal)。 上面的第二个替代仅用于[CComControl](../../atl/reference/ccomcontrol-class.md)。

##  <a name="destroywindow"></a>CDialogImpl：:D estroyWindow

销毁无模式对话框。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>返回值

如果成功销毁对话框，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果成功销毁对话框，则返回 TRUE;否则为 FALSE。

##  <a name="dialogproc"></a>CDialogImpl：:D ialogProc

此静态函数实现对话框的过程。

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
中对话框的句柄。

*uMsg*<br/>
中发送到对话框的消息。

*wParam*<br/>
中其他特定于消息的信息。

*lParam*<br/>
中其他特定于消息的信息。

### <a name="return-value"></a>返回值

如果处理消息，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

`DialogProc`使用默认消息映射将消息定向到适当的处理程序。

可以重写`DialogProc`以提供不同的消息处理机制。

##  <a name="domodal"></a>CDialogImpl：:D oModal

创建模式对话框。

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>参数

*hWndParent*<br/>
中所有者窗口的句柄。 默认值为[GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32 函数的返回值。

*dwInitParam*<br/>
中在 WM_INITDIALOG 消息的*lParam*参数中指定要传递到对话框的值。

### <a name="return-value"></a>返回值

如果成功，则为对[EndDialog](#enddialog)的调用中指定的*nRetCode*参数的值。 否则为-1。

### <a name="remarks"></a>备注

此对话框自动附加到`CDialogImpl`对象。

若要创建无模式对话框，请调用[create](#create)。

##  <a name="enddialog"></a>CDialogImpl：： EndDialog

销毁模式对话框。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
中要由 CDialogImpl 返回的值[：:D omodal](#domodal)。

### <a name="return-value"></a>返回值

如果销毁对话框，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

`EndDialog`必须通过对话框过程调用。 销毁对话框后，Windows 会将*nRetCode*的值用作创建对话框的的返回值`DoModal`。

> [!NOTE]
>  不要调用`EndDialog`以销毁无模式对话框。 改[为调用 CWindow：:D estroywindow](../../atl/reference/cwindow-class.md#destroywindow) 。

##  <a name="getdialogproc"></a>CDialogImpl：： GetDialogProc

返回`DialogProc`当前对话框过程。

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>返回值

当前对话框的过程。

### <a name="remarks"></a>备注

重写此方法以将对话框过程替换为您自己的。

##  <a name="mapdialogrect"></a>CDialogImpl：： MapDialogRect

将指定矩形的对话框单位转换（映射）为屏幕单位（像素）。

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`CRect`对象或 [RECT](/windows/win32/api/windef/ns-windef-rect) 结构，该结构将接收包含更新区域的更新的客户端坐标。

### <a name="return-value"></a>返回值

如果更新成功，则为非零值;如果更新失败，则为0。 若要获得扩展的错误信息，请调用 `GetLastError`。

### <a name="remarks"></a>备注

函数将指定`RECT`结构中的坐标替换为转换后的坐标，这允许在对话框中使用结构来创建对话框或定位控件。

##  <a name="onfinalmessage"></a>CDialogImpl：： OnFinalMessage

在收到最后一条消息后调用`WM_NCDESTROY`（通常为）。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
中要销毁的窗口的句柄。

### <a name="remarks"></a>备注

请注意，如果想要在销毁窗口后自动删除对象，可以在此处调用**delete** 。

##  <a name="startdialogproc"></a>CDialogImpl：： StartDialogProc

接收第一条消息时，只调用一次，以处理发送到对话框的消息。

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
中对话框的句柄。

*uMsg*<br/>
中发送到对话框的消息。

*wParam*<br/>
中其他特定于消息的信息。

*lParam*<br/>
中其他特定于消息的信息。

### <a name="return-value"></a>返回值

窗口过程。

### <a name="remarks"></a>备注

初次调用`StartDialogProc`后， `DialogProc`将设置为一个对话框过程，并在此调用。

## <a name="see-also"></a>请参阅

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[类概述](../../atl/atl-class-overview.md)
