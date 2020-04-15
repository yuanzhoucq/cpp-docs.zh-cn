---
title: CMFC 功能状态栏类
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
ms.openlocfilehash: 554b9fe364c6a213e038416a605c17cdd4f8e7d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368801"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFC 功能状态栏类

类`CMFCRibbonStatusBarPane`实现功能区元素，您可以将其添加到功能区状态栏中。

## <a name="syntax"></a>语法

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC 功能状态栏：：CMFC 功能状态栏窗格](#cmfcribbonstatusbarpane)|构造并初始化一个 `CMFCRibbonStatusBarPane` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 功能状态栏：：获取几乎大文本](#getalmostlargetext)|返回定义可在窗格中显示的最长文本字符串而不截断的字符串。|
|[CMFC 功能状态栏：：获取文本对齐](#gettextalign)|返回文本对齐的当前设置。|
|[CMFC 功能状态栏：：动画](#isanimation)|确定动画是否正在进行。|
|[CMFC 功能状态栏：：扩展](#isextended)|确定窗格是否位于功能区状态栏的扩展区域。|
|[CMFC 功能状态栏：：绘制边框](#ondrawborder)|（覆盖[CMFC 功能按钮：OnDraw 边框](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).）|
|[CMFC 功能状态栏：：在填充背景](#onfillbackground)|（覆盖[CMFC 功能按钮：：在填充背景](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground)上 。|
|[CMFC 功能状态栏：：设置几乎大文本](#setalmostlargetext)|定义可在窗格中显示的最长文本字符串，而不会截断。|
|[CMFC 功能状态栏：：设置动画列表](#setanimationlist)|为窗格分配可用于动画的图像列表。|
|[CMFC 功能状态栏窗格：：设置文本对齐](#settextalign)|设置文本对齐方式。|
|[CMFC 功能状态栏：：启动动画](#startanimation)|启动分配给窗格的动画。|
|[CMFC 功能状态栏：：停止动画](#stopanimation)|停止分配给窗格的动画。 .|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC 功能状态栏：：完成动画](#onfinishanimation)|当分配给窗格的动画停止时，由框架调用。|

## <a name="example"></a>示例

下面的示例演示如何使用 `CMFCRibbonStatusBarPane` 类中的各种方法。 该示例演示如何构造`CMFCRibbonStatusBarPane`对象、设置状态栏窗格标签的文本对齐方式、定义可在状态栏窗格中显示的最长文本而不截断、将可用于动画的图像列表附加到状态栏窗格以及启动动画。

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>要求

**标题：** afxribbon 状态栏栏.h

## <a name="cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a>CMFC 功能状态栏：：CMFC 功能状态栏窗格

在状态栏中构造窗格对象。

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
[在]指定窗格的命令 ID。

*lpszText*<br/>
[在]指定要显示在窗格中的文本字符串。

*bIs静态*<br/>
[在]如果为 TRUE，则无法通过单击状态窗格突出显示或选择状态窗格。

*hIcon*<br/>
[在]指定要显示在窗格上的图标的句柄。

*lpsz 几乎大文本*<br/>
[在]指定窗格可以显示的最长文本字符串。

*hBmp动画列表*<br/>
[在]指定用于动画的图像列表的句柄。

*cx动画*<br/>
[在]指定用于动画的图像列表中图标的宽度（以像素为单位）。

*克拉特恩普*<br/>
[在]指定用于动画的图像列表中图像的透明颜色。

*ui动画列表重新ID*<br/>
[在]指定用于动画的图像列表的资源 ID。

## <a name="cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a>CMFC 功能状态栏：：获取几乎大文本

获取状态栏窗格可以显示的最长文本字符串。

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>返回值

状态栏窗格可以显示的最长文本字符串。

## <a name="cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a>CMFC 功能状态栏：：获取文本对齐

获取状态栏窗格标签的文本对齐的当前设置。

```
int GetTextAlign() const;
```

### <a name="return-value"></a>返回值

当前文本对齐方式可以是以下方式之一：

- TA_LEFT

- TA_CENTER

- TA_RIGHT

## <a name="cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a>CMFC 功能状态栏：：动画

确定动画是否正在进行。

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>返回值

如果动画正在进行，则为 TRUE;否则。

## <a name="cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a>CMFC 功能状态栏：：扩展

确定窗格是否位于功能区状态栏的扩展区域。

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>返回值

如果窗格位于状态栏扩展区域上，则为 TRUE。 否则。

## <a name="cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a>CMFC 功能状态栏：：绘制边框

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>参数

[在]*CDC&#42;*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a>CMFC 功能状态栏：：在填充背景

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a>CMFC 功能状态栏：：完成动画

当分配给窗格的动画结束时，框架将调用此方法。

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>备注

`StopAnimation`方法调用`OnFinishAnimation`方法，可用于在动画结束时清理数据。

## <a name="cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a>CMFC 功能状态栏：：设置几乎大文本

定义可在状态栏窗格中显示的最长文本，而不会截断。

```
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>参数

*lpsz 几乎大文本*<br/>
[在]指定可在状态栏窗格上显示的最长字符串，而不会截断。

### <a name="remarks"></a>备注

库计算*lpszAlmostLargeText*指定的文本大小，并相应地调整窗格的大小。 如果文本仍不适合窗格，则文本将被截断。

## <a name="cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a>CMFC 功能状态栏：：设置动画列表

附加到状态栏窗格的图像列表，可用于动画。

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

*hBmp动画列表*<br/>
[在]指定图像列表的句柄。

*cx动画*<br/>
[在]指定图像列表中帧的宽度（以像素为单位）。

*clrTransp*<br/>
[在]指定图像列表的透明颜色。

*ui动画列表重新ID*<br/>
[在]指定映像列表的资源 ID。

### <a name="return-value"></a>返回值

如果图像列表已成功附加到状态栏窗格，则为 TRUE;如果图像列表已成功附加到状态栏窗格。否则。

## <a name="cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a>CMFC 功能状态栏窗格：：设置文本对齐

设置状态栏窗格标签的文本对齐方式。

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>参数

*n对齐*<br/>
[在]指定文本对齐方式。

### <a name="remarks"></a>备注

*nAlign*可以具有以下值之一：

- TA_LEFT：左对齐

- TA_CENTER：中心对齐

- TA_RIGHT：正确对齐

## <a name="cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a>CMFC 功能状态栏：：启动动画

启动分配给窗格的动画。

```
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>参数

*n 帧延迟*<br/>
[在]指定动画帧速率（以毫秒为单位）。

*nDuration*<br/>
[在]指定以毫秒为单位播放动画的时间。 将 -1 用于无限循环。

### <a name="remarks"></a>备注

在使用`StartAnimation``SetAnimationList`调用 之前，必须指定图像列表的句柄。

## <a name="cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a>CMFC 功能状态栏：：停止动画

停止分配给状态栏窗格的动画。

```
void StopAnimation();
```

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 功能按钮类](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFC 功能状态栏类](../../mfc/reference/cmfcribbonstatusbar-class.md)
