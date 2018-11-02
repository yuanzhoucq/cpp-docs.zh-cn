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
ms.openlocfilehash: 3ac8037e032112e269332d2bbf9c2065ade84ded
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572081"
---
# <a name="cdialogimpl-class"></a>CDialogImpl 类

此类提供用于创建模式对话框或无模式对话框的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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
您的新类的基类。 默认基类是[CWindow](../../atl/reference/cwindow-class.md)。

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[创建](#create)|创建无模式对话框。|
|[DestroyWindow](#destroywindow)|销毁一个无模式对话框。|
|[DoModal](#domodal)|创建模式对话框。|
|[EndDialog](#enddialog)|销毁模式对话框。|

### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT 方法

|||
|-|-|
|[GetDialogProc](#getdialogproc)|返回当前对话框过程。|
|[MapDialogRect](#mapdialogrect)|将指定矩形的对话框单位映射到屏幕单位 （像素）。|
|[OnFinalMessage](#onfinalmessage)|接收最后一条消息，通常 WM_NCDESTROY 之后调用。|

### <a name="static-functions"></a>静态函数

|||
|-|-|
|[DialogProc](#dialogproc)|处理发送到对话框中的消息。|
|[StartDialogProc](#startdialogproc)|收到第一条消息来处理发送到对话框中的消息时调用。|

## <a name="remarks"></a>备注

使用`CDialogImpl`可以创建一个模式或无模式对话框。 `CDialogImpl` 提供的对话框过程，使用默认消息映射来将消息定向到相应的处理程序。

基类析构函数`~CWindowImplRoot`可确保在窗口已销毁的对象之前。

`CDialogImpl` 派生自`CDialogImplBaseT`，它又派生`CWindowImplRoot`。

> [!NOTE]
>  您的类必须定义`IDD`成员，用于指定对话框模板资源 id。 例如，ATL 项目向导自动将以下行添加到您的类：

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

其中`MyDlg`是**短名称**在向导中输入**名称**页。

|有关以下内容的详细信息|查看|
|--------------------------------|---------|
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|
|使用 ATL 中的对话框|[ATL 窗口类](../../atl/atl-window-classes.md)|
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|
|对话框|[对话框](https://msdn.microsoft.com/library/windows/desktop/ms632588)和 Windows SDK 中的后续主题|

## <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="create"></a>  CDialogImpl::Create

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
[in]向所有者窗口句柄。

**RECT &** *rect* [in] 一个[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定对话框的大小和位置。

*dwInitParam*<br/>
[in]指定要传递到该对话框中的值*lParam* WM_INITDIALOG 消息参数。

### <a name="return-value"></a>返回值

到新创建的对话框句柄。

### <a name="remarks"></a>备注

此对话框中会自动附加到`CDialogImpl`对象。 若要创建模式对话框，请调用[DoModal](#domodal)。 上面的第二个重写只能用于[CComControl](../../atl/reference/ccomcontrol-class.md)。

##  <a name="destroywindow"></a>  CDialogImpl::DestroyWindow

销毁一个无模式对话框。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>返回值

如果成功销毁对话框; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果已成功将销毁对话框中; 将返回 TRUE否则为 FALSE。

##  <a name="dialogproc"></a>  CDialogImpl::DialogProc

此静态函数可实现对话框过程。

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
[in]为对话框的句柄。

*uMsg*<br/>
[in]发送到对话框中的消息。

*wParam*<br/>
[in]其他特定于消息的信息。

*lParam*<br/>
[in]其他特定于消息的信息。

### <a name="return-value"></a>返回值

处理该消息; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

`DialogProc` 使用默认消息映射来将消息定向到相应的处理程序。

您可以重写`DialogProc`提供不同的机制，用于处理消息。

##  <a name="domodal"></a>  CDialogImpl::DoModal

创建模式对话框。

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>参数

*hWndParent*<br/>
[in]向所有者窗口句柄。 默认值是返回的值[正在](https://msdn.microsoft.com/library/windows/desktop/ms646292)Win32 函数。

*dwInitParam*<br/>
[in]指定要传递到该对话框中的值*lParam* WM_INITDIALOG 消息参数。

### <a name="return-value"></a>返回值

如果成功，值*nRetCode*调用中指定的参数[EndDialog](#enddialog)。 否则为-1。

### <a name="remarks"></a>备注

此对话框中会自动附加到`CDialogImpl`对象。

若要创建无模式对话框，请调用[创建](#create)。

##  <a name="enddialog"></a>  CDialogImpl::EndDialog

销毁模式对话框。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>参数

*nRetCode*<br/>
[in]要返回的值[CDialogImpl::DoModal](#domodal)。

### <a name="return-value"></a>返回值

销毁对话框中; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

`EndDialog` 必须通过对话框过程调用。 销毁对话框后，Windows 将使用的值*nRetCode*作为返回值`DoModal`，其创建对话框。

> [!NOTE]
>  不要调用`EndDialog`销毁无模式对话框。 调用[CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow)相反。

##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc

返回`DialogProc`，当前对话框过程。

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>返回值

当前对话框过程。

### <a name="remarks"></a>备注

重写此方法以替换为您自己的对话框过程。

##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect

将转换 （映射） 到屏幕的指定矩形的对话框单位单位 （像素）。

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向`CRect`对象或[RECT](../../mfc/reference/rect-structure.md)结构，它是以接收包含更新区域的更新的客户端坐标。

### <a name="return-value"></a>返回值

如果更新成功，则非零值如果更新失败，则为 0。 若要获得扩展的错误信息，请调用 `GetLastError`。

### <a name="remarks"></a>备注

函数将替换中指定的对等`RECT`结构使用转换后的坐标，这允许要用来创建一个对话框，或将控件放在一个对话框内的结构。

##  <a name="onfinalmessage"></a>  CDialogImpl::OnFinalMessage

接收最后一条消息后调用 (通常`WM_NCDESTROY`)。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
[in]正在销毁窗口的句柄。

### <a name="remarks"></a>备注

请注意，是否你想要自动删除您的对象在窗口析构时，您可以调用**删除此;** 此处。

##  <a name="startdialogproc"></a>  CDialogImpl::StartDialogProc

只调用一次，收到第一条消息后，若要处理发送到对话框的消息。

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
[in]为对话框的句柄。

*uMsg*<br/>
[in]发送到对话框中的消息。

*wParam*<br/>
[in]其他特定于消息的信息。

*lParam*<br/>
[in]其他特定于消息的信息。

### <a name="return-value"></a>返回值

窗口过程。

### <a name="remarks"></a>备注

首次调用后`StartDialogProc`，`DialogProc`是设置对话框过程中，并进一步调用转到该位置。

## <a name="see-also"></a>请参阅

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[类概述](../../atl/atl-class-overview.md)