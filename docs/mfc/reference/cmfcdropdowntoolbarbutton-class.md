---
title: CMFCDropDownToolbarButton 类
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
ms.openlocfilehash: fcfb521e309463da81d0064451297b3b73610d2f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505322"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton 类

一种工具栏按钮，单击时其行为类似于常规按钮。 但是, 如果用户按下并按住工具栏按钮, 将打开一个下拉工具栏 ( [CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)。

## <a name="syntax"></a>语法

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|构造 `CMFCDropDownToolbarButton` 对象。|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。 (重写[CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|
|`CMFCDropDownToolbarButton::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|打开下拉工具栏。|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|将文本从工具栏按钮复制到菜单。 (重写[CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)。)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|检索与按钮关联的下拉工具栏。|
|`CMFCDropDownToolbarButton::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|确定下拉工具栏当前是否已打开。|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|确定是否可以使用扩展边框显示该按钮。 (重写[CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|由框架调用, 用于计算指定设备上下文和停靠状态的按钮大小。 (重写[CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|
|`CMFCDropDownToolbarButton::OnCancelMode`|由框架调用以处理[WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode)消息。 （重写 `CMCToolBarButton::OnCancelMode`。）|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|在将按钮插入新工具栏时由框架调用。 (重写[CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|当用户单击鼠标按钮时由框架调用。 (重写[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|当用户释放鼠标按钮时由框架调用。 (重写[CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)。)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|当父工具栏处理 WM_HELPHITTEST 消息时由框架调用。 (重写[CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)。)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|当应用程序在父工具栏上显示快捷菜单时, 修改提供的菜单。 (重写[CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)。)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|由框架调用, 用于通过使用指定的样式和选项绘制按钮。 (重写[CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由框架调用, 用于绘制 "**自定义**" 对话框的 "**命令**" 窗格中的按钮。 (重写[CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|从存档中读取此对象或将其写入存档。 (重写[CMFCToolBarButton:: 串行化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|设置当用户单击按钮时框架使用的默认命令。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|指定在下拉工具栏出现之前用户必须按下鼠标按钮的时间长度。|

## <a name="remarks"></a>备注

与`CMFCDropDownToolBarButton`普通按钮的不同之处在于, 它在按钮的右下角有一个小箭头。 用户从下拉工具栏中选择某个按钮后, 框架将在顶级工具栏按钮 (右下角带有小箭头的按钮) 上显示其图标。

有关如何实现下拉工具栏的信息, 请参阅[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)。

对象可以导出到[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象, 并显示为带有弹出菜单的菜单按钮。 `CMFCDropDownToolBarButton`

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>要求

**标头：** afxdropdowntoolbar.h

##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom

将另一个工具栏按钮的属性复制到当前按钮。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
中对要从中进行复制的源按钮的引用。

### <a name="remarks"></a>备注

调用此方法可将另一个工具栏按钮复制到此工具栏按钮。 *src*的类型`CMFCDropDownToolbarButton`必须为。

##  <a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

构造 `CMFCDropDownToolbarButton` 对象。

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
中按钮的默认文本。

*pToolBar*<br/>
中一个指针, 指向`CMFCDropDownToolBar`当用户按下按钮时显示的对象。

### <a name="remarks"></a>备注

构造函数的第二个重载将复制到下拉按钮, 该按钮位于*pToolBar*指定的工具栏中的第一个按钮。

通常, 下拉工具栏按钮使用*pToolBar*指定的工具栏中最近使用过的按钮中的文本。 当按钮转换为菜单按钮或在 "**自定义**" 对话框的 "**命令**" 选项卡中显示时, 它使用由*lpszName*指定的文本。 有关 "**自定义**" 对话框的详细信息, 请参阅[CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCDropDownToolbarButton`类的对象。 此代码片段是[Visual Studio 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar

打开下拉工具栏。

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中下拉框的父窗口, 或者为 NULL 以使用下拉工具栏按钮的父窗口。

### <a name="return-value"></a>返回值

如果方法成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

当用户按下并保持工具栏按钮时, [CMFCDropDownToolbarButton:: OnClick](#onclick)方法会调用此方法以打开下拉工具栏。

此方法使用[CMFCDropDownFrame:: Create](../../mfc/reference/cmfcdropdownframe-class.md#create)方法创建下拉工具栏。 如果父工具栏是垂直停靠的, 则此方法会将下拉工具栏定位到父工具栏的左侧或右侧, 具体取决于匹配项。 否则, 此方法会将下拉工具栏定位在父工具栏下方。

如果*pWnd*为 NULL, 并且下拉工具栏按钮没有父窗口, 则此方法将失败。

##  <a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton

将文本从工具栏按钮复制到菜单。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>参数

*menuButton*<br/>
中对 "目标" 菜单按钮的引用。

### <a name="return-value"></a>返回值

如果该方法成功，则为非零；否则为零。

### <a name="remarks"></a>备注

此方法调用基类实现 ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)), 然后在 "目标" 菜单按钮上追加一个弹出菜单, 其中包含此按钮中的每个工具栏菜单项。 此方法不会将子菜单追加到弹出菜单。

如果父工具栏、、为 NULL 或`m_pToolBar`基类实现返回 FALSE, 则此方法将失败。

##  <a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar

检索与按钮关联的下拉工具栏。

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>返回值

与按钮关联的下拉工具栏。

### <a name="remarks"></a>备注

此方法返回`m_pToolBar`数据成员。

##  <a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown

确定下拉工具栏当前是否已打开。

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>返回值

如果下拉工具栏当前处于打开状态, 则为非零值;否则为0。

### <a name="remarks"></a>备注

框架使用[CMFCDropDownToolbarButton::D ropdowntoolbar](#dropdowntoolbar)方法打开下拉工具栏。 当用户在下拉工具栏的非工作区中按下鼠标左键时, 框架将关闭下拉工具栏。

##  <a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize

确定是否可以使用扩展边框显示该按钮。

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>返回值

如果可以使用扩展边框显示工具栏按钮, 则为非零值;否则为0。

### <a name="remarks"></a>备注

有关扩展边框的详细信息, 请参阅[CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。

##  <a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

指定在下拉工具栏出现之前用户必须按下鼠标按钮的时间长度。

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>备注

延迟时间以毫秒为单位。 默认值为 500。 您可以通过更改此共享数据成员的值来设置其他延迟。

##  <a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize

由框架调用, 用于计算指定设备上下文和停靠状态的按钮大小。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中显示按钮的设备上下文。

*sizeDefault*<br/>
中按钮的默认大小。

*bHorz*<br/>
中父工具栏的停靠状态。 如果工具栏水平停靠或浮动, 则此参数为 TRUE; 如果工具栏垂直停靠, 则为 FALSE。

### <a name="return-value"></a>返回值

一个`SIZE`结构, 它包含按钮的尺寸 (以像素为单位)。

### <a name="remarks"></a>备注

此方法通过将下拉箭头的宽度添加到按钮大小的水平尺寸来扩展基类实现 ( [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize))。

##  <a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

在将按钮插入新工具栏时由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中新的父窗口。

### <a name="remarks"></a>备注

此方法通过清除文本标签 ( [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) 并设置[CMFCToolBarButton:: m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext)和 CMFCToolBarButton, 来重写基类实现 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) [:: m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton)数据成员设置为 FALSE。

##  <a name="onclick"></a>CMFCDropDownToolbarButton:: OnClick

当用户单击鼠标按钮时由框架调用。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中工具栏按钮的父窗口。

*bDelay*<br/>
中如果应使用延迟处理消息, 则为 TRUE。

### <a name="return-value"></a>返回值

如果按钮处理单击消息, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此方法通过更新下拉工具栏的状态来扩展基类实现[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。

当用户单击工具栏按钮时, 此方法将创建一个等待[CMFCDropDownToolbarButton:: m_uiShowBarDelay](#m_uishowbardelay)数据成员所指定时间长度的计时器, 然后使用 CMFCDropDownToolbarButton 打开下拉工具栏。 [::D ropDownToolbar](#dropdowntoolbar)方法。 此方法会在用户第二次单击工具栏按钮时关闭下拉工具栏。

##  <a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

当用户释放鼠标按钮时由框架调用。

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>返回值

如果按钮处理单击消息, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此方法通过更新下拉工具栏的状态来扩展基类实现, [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)。

如果下拉工具栏计时器处于活动状态, 此方法将停止它。 如果下拉工具栏处于打开状态, 则会将其关闭。

有关下拉工具栏和下拉工具栏计时器的详细信息, 请参阅[CMFCDropDownToolbarButton:: OnClick](#onclick)。

##  <a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp

当父工具栏处理 WM_HELPHITTEST 消息时由框架调用。

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中工具栏按钮的父窗口。

### <a name="return-value"></a>返回值

如果按钮处理帮助消息, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此方法通过调用[CMFCDropDownToolbarButton:: OnClick](#onclick)方法来扩展基类实现 ( [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)), 并将*bDelay*设置为 FALSE。 此方法返回由[CMFCDropDownToolbarButton:: OnClick](#onclick)返回的值。

有关 WM_HELPHITTEST 消息的详细信息, 请参阅[TN028:区分上下文的帮助支持](../../mfc/tn028-context-sensitive-help-support.md)。

##  <a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu

当应用程序在父工具栏上显示快捷菜单时, 修改提供的菜单。

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>参数

*pMenu*<br/>
中要自定义的菜单。

### <a name="return-value"></a>返回值

此方法返回 TRUE。

### <a name="remarks"></a>备注

此方法通过禁用以下菜单项来扩展基类实现 ( [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)):

- **复制按钮图像**

- **按钮外观**

- **Image**

- **文本**

- **图像和文本**

重写此方法以修改框架在自定义模式下显示的快捷菜单。

##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw

由框架调用, 用于通过使用指定的样式和选项绘制按钮。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中显示按钮的设备上下文。

*rect*<br/>
中按钮的边框。

*pImages*<br/>
中与按钮相关联的工具栏图像的集合。

*bHorz*<br/>
中父工具栏的停靠状态。 当按钮水平停靠时, 此参数为 TRUE, 当按钮垂直停靠时, 此参数为 FALSE。

*bCustomizeMode*<br/>
中指定工具栏是否处于自定义模式。 此参数在工具栏处于自定义模式时为 TRUE, 当工具栏未处于自定义模式时为 FALSE。

*bHighlight*<br/>
中指定按钮是否突出显示。 当按钮突出显示时, 此参数为 TRUE; 如果未突出显示该按钮, 则为 FALSE。

*bDrawBorder*<br/>
中指定按钮是否应显示其边框。 当按钮应显示其边框时, 此参数为 TRUE, 当按钮不应显示边框时, 此参数为 FALSE。

*bGrayDisabledButtons*<br/>
中指定是对禁用的按钮进行着色还是使用禁用的图像集合。 如果禁用的按钮应为灰显, 此参数为 TRUE, 此方法应使用禁用的图像集合。

### <a name="remarks"></a>备注

重写此方法以自定义工具栏按钮绘图。

##  <a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

由框架调用, 用于绘制 "**自定义**" 对话框的 "**命令**" 窗格中的按钮。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中显示按钮的设备上下文。

*rect*<br/>
中按钮的边框。

*bSelected*<br/>
中按钮是否处于选中状态。 如果此参数为 TRUE, 则选择此按钮。 如果此参数为 FALSE, 则不选择此按钮。

### <a name="return-value"></a>返回值

指定的设备上下文上的按钮的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

"自定义" 对话框 ("**命令**" 选项卡) 调用此方法, 以便在所有者描述列表框中显示自身。

此方法通过将按钮的文本标签更改为按钮的名称 (即, 传递给构造函数的*lpszName*参数的值) 来扩展基类实现 ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist))).

##  <a name="serialize"></a>CMFCDropDownToolbarButton:: 串行化

从存档中读取此对象或将其写入存档。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
中要从其进行序列化的对象。`CArchive`

### <a name="remarks"></a>备注

此方法通过序列化父工具栏的资源 ID 来扩展基类实现 ( [CMFCToolBarButton:: 串行化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize))。 加载存档时 ( [CArchive:: IsLoading](../../mfc/reference/carchive-class.md#isloading)返回非零值), 此方法将`m_pToolBar`数据成员设置为包含序列化资源 ID 的工具栏。

##  <a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand

设置当用户单击按钮时框架使用的默认命令。

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中默认命令的 ID。

### <a name="remarks"></a>备注

调用此方法可指定用户单击按钮时框架执行的默认命令。 具有*uiCmd*指定的命令 ID 的项必须位于父下拉工具栏中。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[演练：将控件添加到工具栏](../../mfc/walkthrough-putting-controls-on-toolbars.md)
