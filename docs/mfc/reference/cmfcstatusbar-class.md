---
title: CMFC状态栏类
ms.date: 11/19/2018
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
ms.openlocfilehash: 8f262d0139b6dffe54e16748ffda4938ba43fc08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366058"
---
# <a name="cmfcstatusbar-class"></a>CMFC状态栏类

类`CMFCStatusBar`实现与`CStatusBar`类类似的状态栏。 但是，`CMFCStatusBar` 类具有 `CStatusBar` 类未提供的功能，例如显示图像、动画和进度栏的功能，以及对鼠标双击作出响应的功能。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC状态栏：：钙固定布局](#calcfixedlayout)|（覆盖[CBasePane：：CalcFixed 布局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).）|
|[CMFC状态栏：：命令索引](#commandtoindex)||
|[CMFC状态栏：创建](#create)|创建控制栏并将其附加到[CPane](../../mfc/reference/cpane-class.md)对象。 （覆盖[CPane：创建](../../mfc/reference/cpane-class.md#create).）|
|[CMFC状态栏：创建Ex](#createex)|创建控制栏并将其附加到[CPane](../../mfc/reference/cpane-class.md)对象。 （覆盖[CPane：createEx](../../mfc/reference/cpane-class.md#createex).）|
|[CMFC状态栏：:D允许在之前插入](#doesallowdyninsertbefore)|确定是否可以在此窗格和父框架之间动态插入另一个窗格。 （覆盖[CBasePane：:DoesAllowDynInsert 之前](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).）|
|[CMFC状态栏：：启用窗格双击](#enablepanedoubleclick)|启用或禁用状态栏上鼠标双击的处理。|
|[CMFC状态栏：：启用窗格进度栏](#enablepaneprogressbar)|在指定的窗格上显示进度栏。|
|[CMFC状态栏：获取计数](#getcount)|返回状态栏上的窗格数。|
|[CMFC状态栏：获取 Draw 扩展区域](#getdrawextendedarea)||
|[CMFC状态栏：获取扩展区域](#getextendedarea)||
|[CMFC状态栏：获取项目ID](#getitemid)||
|[CMFC状态栏：获取项目已重新完成](#getitemrect)||
|[CMFC状态栏：获取PaneInfo](#getpaneinfo)||
|[CMFC状态栏：获取窗格进度](#getpaneprogress)||
|[CMFC状态栏：获取窗格样式](#getpanestyle)|返回窗格样式。 （覆盖[CBasePane：：获取窗格样式](../../mfc/reference/cbasepane-class.md#getpanestyle).）|
|[CMFC状态栏：获取窗格文本](#getpanetext)||
|[CMFC状态栏：获取窗格宽度](#getpanewidth)|返回状态栏指定窗格的宽度（以像素为单位）。|
|[CMFC状态栏：获取提示文本](#gettiptext)|返回状态栏指定窗格的工具提示文本。|
|[CMFC状态栏：无效窗格内容](#invalidatepanecontent)|使指定的窗格无效并重绘其内容。|
|[CMFC状态栏：:P重新创建窗口](#precreatewindow)|在创建附加到此`CWnd`对象的 Windows 窗口之前，由框架调用。 （覆盖[CWnd：:P重新创建窗口](../../mfc/reference/cwnd-class.md#precreatewindow)。）|
|[CMFC状态栏：：设置 Draw 扩展区域](#setdrawextendedarea)||
|[CMFC状态栏：设置指标](#setindicators)||
|[CMFC状态栏：设置窗格动画](#setpaneanimation)|将动画分配给指定的窗格。|
|[CMFC状态栏：设置Pane背景颜色](#setpanebackgroundcolor)|设置状态栏指定窗格的背景颜色。|
|[CMFC状态栏：设置窗格图标](#setpaneicon)|设置状态栏指定窗格的指示器图标。|
|[CMFC状态栏：设置窗格信息](#setpaneinfo)||
|[CMFC状态栏：：设置窗格进度](#setpaneprogress)|设置状态栏指定窗格的进度栏的当前进度。|
|[CMFC状态栏：设置窗格样式](#setpanestyle)|设置窗格的样式。 （覆盖[CBasePane：：设置窗格样式](../../mfc/reference/cbasepane-class.md#setpanestyle).）|
|[CMFC状态栏：设置窗格文本](#setpanetext)||
|[CMFC状态栏：设置窗格文本颜色](#setpanetextcolor)|设置状态栏指定窗格的文本颜色。|
|[CMFC状态栏：设置窗格宽度](#setpanewidth)|设置状态栏指定窗格的宽度（以像素为单位）。|
|[CMFC状态栏：设置提示文本](#settiptext)|为状态栏的指定窗格设置工具提示文本。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC状态栏：在DrawPane上](#ondrawpane)|当框架重绘状态栏的窗格时，由它调用。|

## <a name="remarks"></a>备注

下图显示了[状态栏演示示例](../../overview/visual-cpp-samples.md)应用程序中的状态栏的图形。

![CMFCStatusBar 示例](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar 示例")

## <a name="example"></a>示例

下面的示例演示了应用程序用于调用类中各种方法的`CMFCStatusBar`局部变量。 这些变量在 StatusBarDemoView.h 中声明。 主框架在 MainFrm.h 中声明，文档在 StatusBarDemoDoc.h 中声明，视图在 StatusBarDemoView.h 中声明。 此代码段是[状态栏演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>示例

下面的示例演示如何通过在 MainFrm.h`CMFCStatusBar`中引入`GetStatusBar`方法，然后从 StatusBarDemoView.h`GetStatusBar`中的方法调用此方法来获取对对象的引用。 此代码段是[状态栏演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>示例

下面的示例演示如何在 StatusBarDemoView.cpp`CMFCStatusBar`中的类中调用各种方法。 常量在 MainFrm.h 中声明。 该示例演示如何设置图标、设置状态栏窗格的工具提示文本、在指定窗格上显示进度栏、将动画分配给指定的窗格、设置文本和状态栏窗格的宽度，以及设置状态栏窗格的进度栏的当前进度指示器。 此代码段是[状态栏演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>要求

**标题：** afxstatusbar.h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFC状态栏：：钙固定布局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

[在]*b 拉伸*<br/>
[在]*布霍兹*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CMFC状态栏：：命令索引

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>参数

[在]*nIDFind*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarcreate"></a><a name="create"></a>CMFC状态栏：创建

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

[在]*pparentwnd*<br/>
[在]*dwStyle*<br/>
[在]*nID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a>CMFC状态栏：创建Ex

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>参数

[在]*pparentwnd*<br/>
[在]*dwCtrl风格*<br/>
[在]*dwStyle*<br/>
[在]*nID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFC状态栏：:D允许在之前插入

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a>CMFC状态栏：：启用窗格双击

启用或禁用状态栏上鼠标双击的处理。

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]如果为 TRUE，则启用鼠标双击处理。 否则禁用鼠标双击处理。

### <a name="remarks"></a>备注

如果启用状态栏处理双击，Windows 会在用户双击状态栏窗格时将WM_COMMAND通知以及资源 ID 一起发送给状态栏的所有者。

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a>CMFC状态栏：：启用窗格进度栏

在指定的窗格上显示进度栏。

```
void EnablePaneProgressBar(
    int nIndex,
    long nTotal=100,
    BOOL bDisplayText=FALSE,
    COLORREF clrBar=-1,
    COLORREF clrBarDest=-1,
    COLORREF clrProgressText=-1);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定要启用其进度条的窗格的索引。

*n 总计*<br/>
[在]指定进度条的最大值。

*b 显示文本*<br/>
[在]指定进度条是否应显示当前进度值。

*clrBar*<br/>
[在]指定进度栏的背景颜色。

*克拉巴尔德斯特*<br/>
[在]指定进度条背景的辅助颜色。 使用与*clrBar*不同的值以混合到渐变的颜色填充。

*clrProgressText*<br/>
[在]指定进度条文本的颜色。

### <a name="remarks"></a>备注

如果要禁用进度栏呼叫`EnablePaneProgressBar`*，nTotal*设置为 -1。 默认情况下 *，nTotal*设置为 100。 因此，您不需要任何其他计算来显示进度（百分比）。

应为*clrBar*和*clrBarDest*传递不同的值，以便进度条的背景颜色显示混合到渐变中的颜色。 .

要设置当前进度，请调用[CMFC 状态栏：：设置窗格进度](#setpaneprogress)方法。

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a>CMFC状态栏：获取计数

检索状态栏中的窗格数。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

状态栏中的窗格数。

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a>CMFC状态栏：获取 Draw 扩展区域

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFC状态栏：获取扩展区域

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>参数

[在]*rect*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a>CMFC状态栏：获取项目ID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>参数

[在]*nIndex*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a>CMFC状态栏：获取项目已重新完成

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

[在]*nIndex*<br/>
[在]*lpRect*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CMFC状态栏：获取PaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>参数

[在]*nIndex*<br/>
[在]*nID*<br/>
[在]*n样式*<br/>
[在]*cxWidth*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a>CMFC状态栏：获取窗格进度

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>参数

[在]*nIndex*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a>CMFC状态栏：获取窗格样式

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>参数

[在]*nIndex*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a>CMFC状态栏：获取窗格文本

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>参数

[在]*nIndex*<br/>
[在]*s*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a>CMFC状态栏：获取窗格宽度

检索状态栏窗格的宽度。

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定状态栏窗格的索引。

### <a name="return-value"></a>返回值

*nIndex*指定的状态栏窗格的宽度;否则，如果状态栏窗格不存在，则为零。

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a>CMFC状态栏：获取提示文本

检索状态栏窗格的工具提示文本。

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定要为其检索工具提示文本的窗格的索引。

### <a name="return-value"></a>返回值

*nIndex*指定的状态栏窗格的工具提示文本。 否则，如果指定的*nIndex*不存在状态栏窗格或其工具提示文本为空，则空字符串。

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a>CMFC状态栏：无效窗格内容

使状态栏窗格无效并重绘其内容。

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定要失效和重绘其内容的窗格的索引。

### <a name="remarks"></a>备注

当状态栏失效时，将标记为重绘。 当方法向`UpdateWindow``OnPaint`方法发送WM_PAINT消息时，Windows 会重绘它。

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a>CMFC状态栏：在DrawPane上

重绘状态栏的窗格。

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向用于绘图的设备上下文的指针。

*pPane*<br/>
[在]指向包含要重`CMFCStatusBarPaneInfo`绘的窗格信息的结构的指针。

### <a name="remarks"></a>备注

默认情况下，`OnDrawPane`使用设备上下文*pDC*根据窗格的样式和内容重绘窗格。

重写`CMFCStatusBar`派生类中的此方法以自定义窗格的外观。

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a>CMFC状态栏：:P重新创建窗口

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>参数

[在]*cs*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a>CMFC状态栏：：设置 Draw 扩展区域

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>参数

[在]*bSet*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a>CMFC状态栏：设置指标

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>参数

[在]*lpIDArray*<br/>
[在]*nIDCount*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a>CMFC状态栏：设置窗格动画

将动画分配给指定的窗格。

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定要为其分配动画的窗格的索引。

*h图像列表*<br/>
[在]指定保存动画帧的图像列表的句柄。

*nFrameRate*<br/>
[在]指定动画的帧速率（以毫秒为单位）。

*b更新*<br/>
[在]如果为 TRUE，请立即更新窗格内容。 否则，窗格内容在失效时将更新。

### <a name="remarks"></a>备注

如果要禁用当前动画，请使用`SetPaneAnimation``hImageList`设置为 NULL 进行调用。

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a>CMFC状态栏：设置Pane背景颜色

设置状态栏窗格的背景颜色。

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定为其设置新背景颜色的窗格的索引。

*clrBackground*<br/>
[在]指定新的背景颜色。

*b更新*<br/>
[在]如果为 TRUE，请立即更新窗格内容。 否则，在窗格被其他方法失效之前，不要更新窗格内容。

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a>CMFC状态栏：设置窗格图标

设置状态栏窗格的图标。

```
void SetPaneIcon(
    int nIndex,
    HICON hIcon,
    BOOL bUpdate=TRUE);

void SetPaneIcon(
    int nIndex,
    HBITMAP hBmp,
    COLORREF clrTransparent=RGB(255, 0, 255),
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定为其设置图像的窗格的索引。

*hIcon*<br/>
[在]指定要设置为窗格图像的图标的句柄。

*b更新*<br/>
[在]指定是否立即更新窗格内容。

*hBmp*<br/>
[在]指定要设置为窗格图像的位图的句柄。

*clr透明*<br/>
[在]指定*hBmp*指示的位图的透明颜色。

### <a name="remarks"></a>备注

您可以将 HICON 或 HBITMAP 与透明颜色一起传递以设置窗格的图像。 如果不想再显示图像，则将 NULL 值作为图像句柄传递。

如果[CMFC 状态栏：：SetPane 动画](#setpaneanimation)设置了任何正在运行的动画，则动画将停止。

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CMFC状态栏：设置窗格信息

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>参数

[在]*nIndex*<br/>
[在]*nID*<br/>
[在]*n样式*<br/>
[在]*cxWidth*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a>CMFC状态栏：：设置窗格进度

为指定的窗格设置进度栏的当前进度指示器。

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定要为其更新进度指示器的窗格的索引。

*n库尔*<br/>
[在]指定进度指示器的当前值。

*b更新*<br/>
[在]指定是否应立即更新窗格。

### <a name="remarks"></a>备注

如果要更新指定窗格中进度栏的进度指示器，请调用此方法。

要对给定窗格使用此函数，必须先调用[CMFC 状态栏：：启用窗格进度栏](#enablepaneprogressbar)。

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CMFC状态栏：设置窗格样式

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>参数

[在]*nIndex*<br/>
[在]*n样式*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a>CMFC状态栏：设置窗格文本

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>参数

[在]*nIndex*<br/>
[在]*lpsz 新文本*<br/>
[在]*b更新*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a>CMFC状态栏：设置窗格文本颜色

设置指定窗格的文本颜色。

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]指定要为其分配新文本颜色的窗格的索引。

*clrText*<br/>
[在]指定文本颜色。

*b更新*<br/>
[在]如果为 TRUE，请立即更新窗格内容。 否则，在窗格被其他方法失效之前，不要更新窗格内容。

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a>CMFC状态栏：设置窗格宽度

设置状态栏窗格的宽度。

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]要为其设置新宽度的状态栏窗格的索引。

*残雪*<br/>
[在]状态栏窗格的新宽度（以像素为单位）。

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a>CMFC状态栏：设置提示文本

设置状态栏窗格的工具提示文本。

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]要为其分配工具提示文本的窗格的索引。

*pssTip文本*<br/>
[在]新的工具提示文本。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar 类](../../mfc/reference/cstatusbar-class.md)
