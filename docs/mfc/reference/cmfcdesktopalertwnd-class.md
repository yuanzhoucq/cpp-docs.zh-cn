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
ms.openlocfilehash: 3ff74f5025d888077b51f8191f043237597dfdbe
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776968"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class

`CMFCDesktopAlertWnd`类实现功能的无模式对话框会显示在屏幕上以通知用户有关的事件。

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。
## <a name="syntax"></a>语法

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCDesktopAlertWnd::Create](#create)|创建并初始化在桌面警报窗口。|
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|返回动画速度。|
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|返回的动画类型。|
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|返回自动关闭超时。|
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|返回标题高度。|
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|在屏幕上返回桌面警报窗口的最后一个有效位置。|
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|返回的透明度级别。|
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|确定是否用较小的标题显示在桌面警报窗口。|
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|当用户单击位于桌面的警报菜单上的链接按钮时由框架调用。|
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|当用户从菜单中选择某个项，子控件将发送一条通知消息，或加速器键击转换时，框架将调用此成员函数。 (重写[CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand)。)|
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|设置新的动画速度。|
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|设置动画类型。|
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|设置自动关闭超时。|
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|小并处于正常状态的隐藏式字幕之间切换。|
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|设置的透明度级别。|

## <a name="remarks"></a>备注

桌面警报窗口可以是透明的它都可以带有动画效果，它可能会消失 （指定延迟后或当用户通过单击关闭按钮关闭它时）。

桌面警报窗口还可以包含一个默认对话框，其中又包含一个图标、 消息文本 （标签） 和链接。 或者，桌面警报窗口可以包含从应用程序的资源的自定义对话框。

在两个步骤中创建桌面警报窗口。 首先，调用构造函数来构造`CMFCDesktopAlertWnd`对象。 其次，调用[cmfcdesktopalertwnd:: Create](#create)成员函数以创建窗口，然后将其附加到`CMFCDesktopAlertWnd`对象。

`CMFCDesktopAlertWnd`对象创建填充在桌面警报窗口的客户端区域的特殊子对话框。 对话框中拥有定位在其的所有控件。

若要在弹出窗口中显示自定义对话框中，执行以下步骤：

1. 从 `CMFCDesktopAlertDialog` 派生一个类。

1. 在资源中创建子对话框模板。

1. 调用[cmfcdesktopalertwnd:: Create](#create)使用对话框模板和指向派生类的运行时类信息的资源 ID。

1. 程序自定义对话框中，以处理来自托管控件的所有通知或程序承载的控件可以直接都处理这些通知。

使用以下函数以控制在桌面警报窗口的行为：

- 通过调用设置的动画类型[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)。 有效选项包括将展开、 幻灯片，和淡出。

- 通过调用设置动画帧速度[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)。

- 通过调用设置的透明度级别[CMFCDesktopAlertWnd::SetTransparency](#settransparency)。

- 通过调用将标题的大小更改为小[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)。 小标题为 7 像素高。

## <a name="example"></a>示例

下面的示例演示如何使用中的各种方法`CMFCDesktopAlertWnd`类，以配置`CMFCDesktopAlertWnd`对象。 该示例演示如何将动画类型，将弹出窗口的透明度设置、 指定通知窗口显示小标题，并将通知窗口会自动关闭前经过的时间。 该示例还演示如何创建和初始化在桌面警报窗口。 此代码片段属于[桌面警报演示示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>要求

**标头：** afxDesktopAlertWnd.h

##  <a name="create"></a>  CMFCDesktopAlertWnd::Create

创建并初始化在桌面警报窗口。

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

*pWndOwner*<br/>
[in、 out]指定的通知窗口的所有者。 该所有者随后会收到在桌面警报窗口的所有通知。 此值不能为 NULL。

*uiDlgResID*<br/>
[in]指定通知窗口的资源的 ID。

*hMenu*<br/>
[in]指定当用户单击菜单按钮时显示的菜单。 如果为 NULL，不显示的菜单按钮。

*ptPos*<br/>
[in]指定通知窗口的显示位置的初始位置，使用屏幕坐标。 如果此参数为 （-1，-1），通知窗口显示在屏幕的右下角。

*pRTIDlgBar*<br/>
[in]介绍了警报窗口的工作区的自定义的对话框类的运行时类信息。

*params*<br/>
[in]指定用于创建警报窗口的参数。

### <a name="return-value"></a>返回值

如果通知窗口创建成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

调用此方法以创建警报窗口。 通知窗口的客户端区域包含承载的所有控件都向用户显示一个子对话框。

第一个方法重载创建一个警报窗口，其中包含从应用程序的资源加载的子对话框。 第一个方法重载还可以指定自定义对话框类的运行时类信息。

第二个方法重载将创建一个警报窗口，其中包含默认控件。 您可以指定它可以控制要显示通过修改[CMFCDesktopAlertWndInfo 类](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)。

##  <a name="getanimationspeed"></a>  CMFCDesktopAlertWnd::GetAnimationSpeed

返回动画速度。

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>返回值

动画速度的通知窗口，以毫秒为单位。

### <a name="remarks"></a>备注

动画速度介绍通知窗口打开和关闭的速度有多快。

##  <a name="getanimationtype"></a>  CMFCDesktopAlertWnd::GetAnimationType

返回的动画类型。

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>返回值

下面的动画类型之一：

- NO_ANIMATION

- 展开

- 幻灯片

- 淡入淡出

- SYSTEM_DEFAULT_ANIMATION

##  <a name="getautoclosetime"></a>  CMFCDesktopAlertWnd::GetAutoCloseTime

返回自动关闭超时。

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>返回值

以毫秒为单位，在其后通知窗口会自动关闭时间。

### <a name="remarks"></a>备注

使用此方法以确定要通知窗口将自动关闭之前应经过多长时间。

##  <a name="getcaptionheight"></a>  CMFCDesktopAlertWnd::GetCaptionHeight

返回标题高度。

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>返回值

以像素为单位的标题的高度。

### <a name="remarks"></a>备注

可以在派生类中重写此方法。 默认实现是： 如果应显示的弹出窗口中，小标题或从 Windows API 函数获取的值，则返回的小标题高度值 （7 像素为单位） `GetSystemMetrics(SM_CYSMCAPTION)`。

##  <a name="getlastpos"></a>  CMFCDesktopAlertWnd::GetLastPos

在屏幕上返回桌面警报窗口的最后一个位置。

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>返回值

屏幕坐标中的点。

### <a name="remarks"></a>备注

此方法返回在屏幕上的通知窗口的最后一个有效位置。

##  <a name="gettransparency"></a>  CMFCDesktopAlertWnd::GetTransparency

返回的透明度级别。

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>返回值

介于 0 和 255 之间，非独占透明度级别。 值越大，更多的不透明窗口。

### <a name="remarks"></a>备注

使用此方法可检索当前的通知窗口的透明度级别。

##  <a name="hassmallcaption"></a>  CMFCDesktopAlertWnd::HasSmallCaption

确定是否在桌面警报窗口具有一个小的标题或常规大小标题。

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>返回值

如果为 TRUE 的弹出窗口中显示与小标题;如果使用普通大小的标题显示的弹出窗口中，则为 FALSE。

### <a name="remarks"></a>备注

使用此方法以确定的弹出窗口中的一个小的标题或常规大小标题。 默认情况下，小标题为 7 个像素高。 你可以通过调用 Windows API 函数获取常规大小标题的高度`GetSystemMetrics(SM_CYCAPTION)`。

##  <a name="onbeforeshow"></a>  CMFCDesktopAlertWnd::OnBeforeShow

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>参数

[in]*CPoint （& a)*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onclicklinkbutton"></a>  CMFCDesktopAlertWnd::OnClickLinkButton

当用户单击位于桌面的警报菜单上的链接按钮时由框架调用。

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>参数

*uiCmdID*<br/>
[in]未使用此参数。

### <a name="return-value"></a>返回值

始终为 FALSE。

### <a name="remarks"></a>备注

如果你想要在用户单击通知窗口上的链接时收到通知，重写此方法在派生类中。

##  <a name="oncommand"></a>  CMFCDesktopAlertWnd::OnCommand

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

[in] *wParam*<br/>

[in] *lParam*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ondraw"></a>  CMFCDesktopAlertWnd::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

[in] *pDC*<br/>

### <a name="remarks"></a>备注

##  <a name="processcommand"></a>  CMFCDesktopAlertWnd::ProcessCommand

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>参数

[in] *hwnd*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="setanimationspeed"></a>  CMFCDesktopAlertWnd::SetAnimationSpeed

设置新的动画速度。

```
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>参数

*nSpeed*<br/>
[in]指定新动画速度，以毫秒为单位。

### <a name="remarks"></a>备注

调用此方法以设置通知窗口的动画速度。 默认动画速度为 30 毫秒。

##  <a name="setanimationtype"></a>  CMFCDesktopAlertWnd::SetAnimationType

设置动画类型。

```
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>参数

*type*<br/>
[in]指定的动画类型。

### <a name="remarks"></a>备注

调用此方法以设置动画类型。 可以指定以下值之一：

- NO_ANIMATION

- 展开

- 幻灯片

- 淡入淡出

- SYSTEM_DEFAULT_ANIMATION

##  <a name="setautoclosetime"></a>  CMFCDesktopAlertWnd::SetAutoCloseTime

设置自动关闭超时。

```
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>参数

*nTime*<br/>
[in]经过通知窗口会自动关闭之前的时间，以毫秒为单位。

### <a name="remarks"></a>备注

如果用户不会交互窗口在指定时间后自动关闭通知窗口。

##  <a name="setsmallcaption"></a>  CMFCDesktopAlertWnd::SetSmallCaption

小型和常规大小的隐藏式字幕之间切换。

```
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>参数

*bSmallCaption*<br/>
[in]为 TRUE，则指定通知窗口显示小标题;否则为 FALSE，则指定通知窗口显示的常规大小标题。

### <a name="remarks"></a>备注

调用此方法以显示小或常规大小标题。 默认情况下，小标题为 7 个像素高。 你可以通过调用 Windows API 函数获取的正则标题大小`GetSystemMetrics(SM_CYCAPTION)`。

##  <a name="settransparency"></a>  CMFCDesktopAlertWnd::SetTransparency

设置弹出窗口的透明度级别。

```
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>参数

*nTransparency*<br/>
[in]指定透明度级别。 此值必须介于 0 和 255 之间 （含） 之间。 值越大，更多的不透明窗口。

### <a name="remarks"></a>备注

调用此函数可设置弹出窗口的透明度级别。

##  <a name="getdialogsize"></a>  CMFCDesktopAlertWnd::GetDialogSize

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo 类](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFCDesktopAlertDialog 类](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
