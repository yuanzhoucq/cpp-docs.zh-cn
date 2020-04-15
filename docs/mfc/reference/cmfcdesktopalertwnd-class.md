---
title: CMFCDesktopAlertWnd Class
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
ms.openlocfilehash: f9c59258cf757b5468985a954640ccec1543512b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367637"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class

类`CMFCDesktopAlertWnd`实现无模式对话框的功能，该对话框出现在屏幕上，以通知用户有关事件。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 桌面警报：：创建](#create)|创建并初始化桌面警报窗口。|
|[CMFC桌面警报：：获取动画速度](#getanimationspeed)|返回动画速度。|
|[CMFC 桌面警报：：获取动画类型](#getanimationtype)|返回动画类型。|
|[CMFC 桌面警报：：获取自动关闭时间](#getautoclosetime)|返回自动关闭超时。|
|[CMFC 桌面警报：：获取标题高度](#getcaptionheight)|返回标题的高度。|
|[CMFC 桌面警报：：获取对话大小](#getdialogsize)||
|[CMFC 桌面警报：：获取最后一个Pos](#getlastpos)|返回屏幕上桌面警报窗口的最后一个有效位置。|
|[CMFC桌面警报：：获取透明度](#gettransparency)|返回透明度级别。|
|[CMFC 桌面警报：：有小标题](#hassmallcaption)|确定桌面警报窗口是否随小标题一起显示。|
|[CMFC 桌面警报：：在显示前打开](#onbeforeshow)||
|[CMFC 桌面警报：：点击链接按钮](#onclicklinkbutton)|当用户单击桌面警报菜单上的链接按钮时，由框架调用。|
|[CMFC 桌面警报：：在命令上](#oncommand)|当用户从菜单中选择项目、子控件发送通知消息或翻译快捷键时，框架将调用此成员函数。 （覆盖[CWnd：onCommand](../../mfc/reference/cwnd-class.md#oncommand).）|
|[CMFC 桌面警报：：开机](#ondraw)||
|[CMFC 桌面警报：:Process 命令](#processcommand)||
|[CMFC 桌面警报：：设置动画速度](#setanimationspeed)|设置新的动画速度。|
|[CMFC 桌面警报：：设置动画类型](#setanimationtype)|设置动画类型。|
|[CMFC 桌面警报：：设置自动关闭时间](#setautoclosetime)|设置自动关闭超时。|
|[CMFC 桌面警报：：设置小标题](#setsmallcaption)|在小标题和普通字幕之间切换。|
|[CMFC 桌面警报：：设置透明度](#settransparency)|设置透明度级别。|

## <a name="remarks"></a>备注

桌面警报窗口可以是透明的，它可以显示动画效果，并且它可以消失（在指定的延迟之后，或者当用户通过单击关闭按钮将其关闭时）。

桌面警报窗口还可以包含默认对话框，该对话框又包含图标、消息文本（标签）和链接。 或者，桌面警报窗口可以包含来自应用程序资源的自定义对话框。

分两步创建桌面警报窗口。 首先，调用构造函数构造`CMFCDesktopAlertWnd`对象。 其次，调用[CMFC DesktopAlertwnd：：创建](#create)成员函数以创建窗口并将其附加到`CMFCDesktopAlertWnd`对象。

该`CMFCDesktopAlertWnd`对象创建一个特殊的子对话框，该对话框填充桌面警报窗口的工作区。 该对话框拥有位于它上的所有控件。

要在弹出窗口上显示自定义对话框，请按照以下步骤操作：

1. 从 `CMFCDesktopAlertDialog` 派生一个类。

1. 在资源中创建子对话框模板。

1. 调用[CMFCDesktopAlertwnd：：](#create)使用对话框模板的资源 ID 和指向派生类的运行时类信息的指针进行创建。

1. 对自定义对话框进行编程，以处理来自托管控件的所有通知，或对托管控件进行编程以直接处理这些通知。

使用以下函数控制桌面警报窗口的行为：

- 通过调用[CMFC 桌面警报Wnd：：设置动画类型来设置动画类型](#setanimationtype)。 有效选项包括展开、滑动和淡入淡出。

- 通过调用[CMFC 桌面警报 Wnd 设置动画帧速度：：设置动画速度](#setanimationspeed)。

- 通过调用[CMFC 桌面AlertWnd：：设置透明度](#settransparency)来设置透明度级别。

- 通过调用[CMFCDesktopAlertwnd：：setSmallCaption，](#setsmallcaption)将标题的大小更改为小。 小标题高 7 像素。

## <a name="example"></a>示例

下面的示例说明了如何使用类中`CMFCDesktopAlertWnd`的各种方法来配置`CMFCDesktopAlertWnd`对象。 该示例演示如何设置动画类型、设置弹出窗口的透明度、指定警报窗口显示小标题以及设置警报窗口自动关闭之前经过的时间。 该示例还演示如何创建和初始化桌面警报窗口。 此代码段是[桌面警报演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>要求

**标题：** afxDesktopAlertwnd.h

## <a name="cmfcdesktopalertwndcreate"></a><a name="create"></a>CMFC 桌面警报：：创建

创建并初始化桌面警报窗口。

```
virtual BOOL Create(
    CWnd* pWndOwner,
    UINT uiDlgResID,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1),
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

virtual BOOL Create(
    CWnd* pWndOwner,
    CMFCDesktopAlertWndInfo& params,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1));
```

### <a name="parameters"></a>参数

*pwndOwner*<br/>
[进出]指定警报窗口的所有者。 然后，该所有者将收到桌面警报窗口的所有通知。 此值不能为 NULL。

*乌伊德格雷斯ID*<br/>
[在]指定警报窗口的资源 ID。

*hMenu*<br/>
[在]指定用户单击菜单按钮时显示的菜单。 如果为 NULL，则不显示菜单按钮。

*ptPos*<br/>
[在]使用屏幕坐标指定显示警报窗口的初始位置。 如果此参数为 （-1， -1），则警报窗口将显示在屏幕的右下角。

*pRTIDlgBar*<br/>
[在]自定义对话框类的运行时类信息，该类涵盖警报窗口的工作区。

*params*<br/>
[在]指定用于创建警报窗口的参数。

### <a name="return-value"></a>返回值

如果警报窗口已成功创建，则为 TRUE;如果警报窗口已成功创建，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

调用此方法以创建警报窗口。 警报窗口的工作区包含一个子对话框，该对话框承载向用户显示的所有控件。

第一个方法重载创建一个警报窗口，其中包含从应用程序的资源加载的子对话框。 第一种方法重载还可以为自定义对话框类指定运行时类信息。

第二种方法重载将创建一个包含默认控件的警报窗口。 您可以通过修改[CMFC 桌面AlertWndinfo 类](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)来指定要显示的控件。

## <a name="cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a>CMFC桌面警报：：获取动画速度

返回动画速度。

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>返回值

警报窗口的动画速度（以毫秒为单位）。

### <a name="remarks"></a>备注

动画速度描述警报窗口打开和关闭的速度。

## <a name="cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a>CMFC 桌面警报：：获取动画类型

返回动画类型。

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>返回值

以下动画类型之一：

- NO_ANIMATION

- 展开

- 幻灯片

- 褪色

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a>CMFC 桌面警报：：获取自动关闭时间

返回自动关闭超时。

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>返回值

警报窗口将自动关闭的时间（以毫秒为单位）。

### <a name="remarks"></a>备注

使用此方法可确定警报窗口自动关闭之前应经过多长时间。

## <a name="cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a>CMFC 桌面警报：：获取标题高度

返回标题的高度。

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>返回值

标题的高度（以像素为单位）。

### <a name="remarks"></a>备注

可以在派生类中重写此方法。 默认实现：如果弹出窗口应显示小标题或从 Windows API 函数`GetSystemMetrics(SM_CYSMCAPTION)`获取的值，则返回小标题高度值（7 像素）。

## <a name="cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a>CMFC 桌面警报：：获取最后一个Pos

返回屏幕上桌面警报窗口的最后位置。

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>返回值

屏幕坐标中的一个点。

### <a name="remarks"></a>备注

此方法返回屏幕上警报窗口的最后一个有效位置。

## <a name="cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a>CMFC桌面警报：：获取透明度

返回透明度级别。

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>返回值

透明度级别介于 0 和 255 之间，包括。 值越大，窗口越不透明。

### <a name="remarks"></a>备注

使用此方法检索警报窗口的当前透明度级别。

## <a name="cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a>CMFC 桌面警报：：有小标题

确定桌面警报窗口是否具有小标题或常规大小标题。

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>返回值

如果弹出窗口显示带有小标题，则为 TRUE;如果弹出窗口显示时，则为 TRUE。如果弹出窗口显示带有常规大小的标题，则 FALSE。

### <a name="remarks"></a>备注

使用此方法可确定弹出窗口是否具有小标题或常规大小标题。 默认情况下，小标题高 7 像素。 您可以通过调用 Windows API 函数`GetSystemMetrics(SM_CYCAPTION)`获得常规大小标题的高度。

## <a name="cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a>CMFC 桌面警报：：在显示前打开

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>参数

[在]*CPoint&*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a>CMFC 桌面警报：：点击链接按钮

当用户单击桌面警报菜单上的链接按钮时，由框架调用。

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>参数

*乌伊CmdID*<br/>
[在]不使用此参数。

### <a name="return-value"></a>返回值

始终为 FALSE。

### <a name="remarks"></a>备注

如果要在用户单击警报窗口中的链接时收到通知，请在派生类中覆盖此方法。

## <a name="cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a>CMFC 桌面警报：：在命令上

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

[在]*wParam*<br/>

[在]*lParam*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertwndondraw"></a><a name="ondraw"></a>CMFC 桌面警报：：开机

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a>CMFC 桌面警报：:Process 命令

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>参数

[在]*霍恩德*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a>CMFC 桌面警报：：设置动画速度

设置新的动画速度。

```
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>参数

*n速度*<br/>
[在]指定新的动画速度（以毫秒为单位）。

### <a name="remarks"></a>备注

调用此方法以设置警报窗口的动画速度。 默认动画速度为 30 毫秒。

## <a name="cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a>CMFC 桌面警报：：设置动画类型

设置动画类型。

```
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>参数

*type*<br/>
[在]指定动画类型。

### <a name="remarks"></a>备注

调用此方法以设置动画类型。 可以指定以下值之一：

- NO_ANIMATION

- 展开

- 幻灯片

- 褪色

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a>CMFC 桌面警报：：设置自动关闭时间

设置自动关闭超时。

```
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>参数

*nTime*<br/>
[在]警报窗口自动关闭之前经过的时间（以毫秒为单位）。

### <a name="remarks"></a>备注

如果用户不与窗互，警报窗口在指定时间后自动关闭。

## <a name="cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a>CMFC 桌面警报：：设置小标题

在小尺寸和常规大小字幕之间切换。

```
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>参数

*b 小标题*<br/>
[在]TRUE 指定警报窗口显示一个小标题;否则，FALSE 指定警报窗口显示常规大小的标题。

### <a name="remarks"></a>备注

调用此方法以显示小大小或常规大小的标题。 默认情况下，小标题高 7 像素。 您可以通过调用 Windows API 函数`GetSystemMetrics(SM_CYCAPTION)`来获取常规标题的大小。

## <a name="cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a>CMFC 桌面警报：：设置透明度

设置弹出窗口的透明度级别。

```
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>参数

*n 透明*<br/>
[在]指定透明度级别。 此值必须在 0 和 255 之间（包括）。 值越大，窗口越不透明。

### <a name="remarks"></a>备注

调用此函数以设置弹出窗口的透明度级别。

## <a name="cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a>CMFC 桌面警报：：获取对话大小

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo 类](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFC 桌面警报对话类](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
