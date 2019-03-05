---
title: CMFCRibbonStatusBarPane 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
ms.openlocfilehash: 9911672ec139ab1598db8005e9b7b909e85dd33d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265725"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane 类

`CMFCRibbonStatusBarPane`类实现可添加到功能区状态栏的功能区元素。

## <a name="syntax"></a>语法

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|构造并初始化一个 `CMFCRibbonStatusBarPane` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|返回用于定义可以而无需截断窗格中显示的最长文本字符串的字符串。|
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|返回的文本对齐方式的当前设置。|
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|确定动画是否正在进行中。|
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|确定是否窗格位于功能区状态栏扩展区域中。|
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(重写[CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder)。)|
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(重写[CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground)。)|
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|定义可以而无需截断窗格中显示的最长文本字符串。|
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|将可用于动画的图像列表分配给在窗格中。|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|设置文本对齐方式。|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|启动分配给窗格的动画。|
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|停止分配给窗格的动画。 .|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|当分配给窗格动画停止时由框架调用。|

## <a name="example"></a>示例

下面的示例演示如何使用 `CMFCRibbonStatusBarPane` 类中的各种方法。 该示例演示如何构造`CMFCRibbonStatusBarPane`对象，设置状态栏窗格的标签的文本对齐方式，定义可以显示在状态栏窗格而无需截断，将可用于图像列表附加到状态栏窗格的最长文本nimation，并开始动画。

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>要求

**标头：** afxribbonstatusbarpane.h

##  <a name="cmfcribbonstatusbarpane"></a>  CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane

构造状态栏中的窗格对象。

```
CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    BOOL bIsStatic=FALSE,
    HICON hIcon=NULL,
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);
```

### <a name="parameters"></a>参数

*nCmdID*<br/>
[in]指定在窗格的命令 ID。

*lpszText*<br/>
[in]指定要在上窗格中显示的文本字符串。

*bIsStatic*<br/>
[in]如果为 TRUE，则无法突出显示或通过单击选择状态窗格。

*hIcon*<br/>
[in]指定要在上窗格中显示的图标的句柄。

*lpszAlmostLargeText*<br/>
[in]指定可以在窗格中显示的最长文本字符串。

*hBmpAnimationList*<br/>
[in]指定用于动画的图像列表的句柄。

*cxAnimation*<br/>
[in]指定宽度，以像素为单位用于动画的图像列表中的图标。

*clrTrnsp*<br/>
[in]指定用于动画的图像列表中的图像的透明色。

*uiAnimationListResID*<br/>
[in]指定用于动画的图像列表的资源 ID。

##  <a name="getalmostlargetext"></a>  CMFCRibbonStatusBarPane::GetAlmostLargeText

获取状态栏窗格可以显示的最长文本字符串。

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>返回值

状态栏窗格可以显示最长文本字符串。

##  <a name="gettextalign"></a>  CMFCRibbonStatusBarPane::GetTextAlign

获取标签的状态栏窗格的文本对齐方式的当前设置。

```
int GetTextAlign() const;
```

### <a name="return-value"></a>返回值

当前文本对齐方式可以是以下值之一：

- TA_LEFT

- TA_CENTER

- TA_RIGHT。

##  <a name="isanimation"></a>  CMFCRibbonStatusBarPane::IsAnimation

确定动画是否正在进行中。

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>返回值

如果动画正在进行中; 则为 TRUEFALSE 否则为。

##  <a name="isextended"></a>  CMFCRibbonStatusBarPane::IsExtended

确定是否窗格位于功能区状态栏扩展区域中。

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>返回值

如果窗格上状态栏扩展区域，则为 TRUE。 FALSE 否则为。

##  <a name="ondrawborder"></a>  CMFCRibbonStatusBarPane::OnDrawBorder

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>参数

[in] *CDC&#42;*<br/>

### <a name="remarks"></a>备注

##  <a name="onfillbackground"></a>  CMFCRibbonStatusBarPane::OnFillBackground

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>参数

[in] *pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onfinishanimation"></a>  CMFCRibbonStatusBarPane::OnFinishAnimation

当分配给窗格在动画结束时，框架将调用此方法。

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>备注

`StopAnimation` 方法调用`OnFinishAnimation`方法，可用于在动画结束时清理数据。

##  <a name="setalmostlargetext"></a>  CMFCRibbonStatusBarPane::SetAlmostLargeText

定义可而无需截断状态栏窗格中显示的最长文本。

```
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>参数

*lpszAlmostLargeText*<br/>
[in]指定最长可以显示在状态栏窗格而无需截断的字符串。

### <a name="remarks"></a>备注

该库计算的文本大小， *lpszAlmostLargeText*指定并相应地调整窗格的大小。 如果仍无法容纳在窗格中，文本将被截断。

##  <a name="setanimationlist"></a>  CMFCRibbonStatusBarPane::SetAnimationList

将可用于动画的图像列表附加到状态栏窗格。

```
void SetAnimationList(
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```

### <a name="parameters"></a>参数

*hBmpAnimationList*<br/>
[in]指定的句柄的图像列表。

*cxAnimation*<br/>
[in]指定宽度，以像素为单位的图像列表中的帧。

*clrTransp*<br/>
[in]指定的图像列表的透明颜色。

*uiAnimationListResID*<br/>
[in]指定的图像列表的资源 ID。

### <a name="return-value"></a>返回值

如果图像列表已成功附加到状态栏窗格; 则为 TRUEFALSE 否则为。

##  <a name="settextalign"></a>  CMFCRibbonStatusBarPane::SetTextAlign

设置状态栏窗格的标签的文本对齐方式。

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>参数

*nAlign*<br/>
[in]指定的文本对齐方式。

### <a name="remarks"></a>备注

*nAlign*可以具有以下值之一：

- TA_LEFT： 左的对齐

- TA_CENTER： 居中对齐

- TA_RIGHT： 右对齐

##  <a name="startanimation"></a>  CMFCRibbonStatusBarPane::StartAnimation

开始分配到窗格中的动画。

```
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>参数

*nFrameDelay*<br/>
[in]指定动画帧速率，以毫秒为单位。

*nDuration*<br/>
[in]指定多长时间来播放动画，以毫秒为单位。 使用-1 表示无限循环。

### <a name="remarks"></a>备注

在调用之前，必须指定图像列表的句柄`StartAnimation`通过使用`SetAnimationList`。

##  <a name="stopanimation"></a>  CMFCRibbonStatusBarPane::StopAnimation

停止动画分配到状态栏窗格。

```
void StopAnimation();
```

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonStatusBar 类](../../mfc/reference/cmfcribbonstatusbar-class.md)
