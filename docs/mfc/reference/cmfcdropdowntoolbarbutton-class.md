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
ms.openlocfilehash: f09a2f3fe66abb86a8f220dbdf6744813ad9db0d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752406"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton 类

一种工具栏按钮，单击时其行为类似于常规按钮。 但是，如果用户按下并按下工具栏按钮，它将打开下拉工具栏[（CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)）。

## <a name="syntax"></a>语法

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC向下工具栏按钮：：CMFC向下工具栏按钮](#cmfcdropdowntoolbarbutton)|构造 `CMFCDropDownToolbarButton` 对象。|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC向下拖拉工具栏按钮：：从复制](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。 （覆盖[CMFCToolBar 按钮：：从](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)复制。）|
|`CMFCDropDownToolbarButton::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFC下线工具栏按钮：:DropDown工具栏](#dropdowntoolbar)|打开下拉工具栏。|
|[CMFC向下工具栏按钮：：导出到菜单按钮](#exporttomenubutton)|将工具栏按钮中的文本复制到菜单。 （覆盖[CMFC 工具栏按钮：：导出到菜单按钮](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).）|
|[CMFC向下拖下工具栏按钮：：获取向下拖拉工具栏](#getdropdowntoolbar)|检索与按钮关联的下拉工具栏。|
|`CMFCDropDownToolbarButton::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFC向下拖下工具栏按钮：：是向下](#isdropdown)|确定下拉工具栏当前是否打开。|
|[CMFC向下工具栏按钮：：是超尺寸](#isextrasize)|确定按钮是否可以使用扩展边框显示。 （覆盖[CMFCToolBar 按钮：是超大型](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).）|
|[CMFC向下拖拉工具栏按钮：：在计算大小](#oncalculatesize)|由框架调用，以计算指定设备上下文和停靠状态的按钮大小。 （覆盖[CMFC 工具栏按钮："正在计算大小](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)"）|
|`CMFCDropDownToolbarButton::OnCancelMode`|由框架调用以处理[WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode)消息。 （重写 `CMCToolBarButton::OnCancelMode`。）|
|[CMFC下拉工具栏按钮：：打开更改家长](#onchangeparentwnd)|将按钮插入到新工具栏时由框架调用。 （覆盖[CMFC 工具栏按钮：打开更改父项](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).）|
|[CMFC向下工具栏按钮：：点击](#onclick)|当用户单击鼠标按钮时由框架调用。 （覆盖[CMFC 工具栏按钮：：单击](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).）|
|[CMFC下拉工具栏按钮：：点击向上](#onclickup)|当用户释放鼠标按钮时由框架调用。 （覆盖[CMFC 工具栏按钮：：单击 .）](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)|
|[CMFC向下工具栏按钮：：在上下文帮助](#oncontexthelp)|当父工具栏处理WM_HELPHITTEST消息时，由框架调用。 （覆盖[CMFC 工具栏按钮：打开上下文帮助](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).）|
|[CMFC向下工具栏按钮：：在自定义菜单上](#oncustomizemenu)|当应用程序在父工具栏上显示快捷方式菜单时，修改提供的菜单。 （覆盖[CMFC 工具栏按钮：：在自定义菜单](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)上 。|
|[CMFC向下工具栏按钮：：开拉](#ondraw)|框架调用使用指定的样式和选项绘制按钮。 （覆盖[CMFC 工具栏按钮：：OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).）|
|[CMFC向下拖拉工具栏按钮：：在绘制上自定义列表](#ondrawoncustomizelist)|由框架调用以在 **"自定义"** 对话框的 **"命令"** 窗格中绘制按钮。 （覆盖[CMFC 工具栏按钮：在"绘制"自定义列表](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).）|
|[CMFC下拉工具栏按钮：序列化](#serialize)|从存档中读取此对象或将其写入存档。 （覆盖[CMFCToolBarButton：序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).）|
|[CMFC下拉下工具栏按钮：：设置默认命令](#setdefaultcommand)|设置框架在用户单击按钮时使用的默认命令。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFC下拉工具栏按钮：：m_uiShowBarDelay](#m_uishowbardelay)|指定用户必须在下拉工具栏出现之前按住鼠标按钮的时间长度。|

## <a name="remarks"></a>备注

A`CMFCDropDownToolBarButton`与普通按钮不同，因为它在按钮的右下角有一个小箭头。 用户从下拉工具栏中选择一个按钮后，框架会在顶部工具栏按钮上显示其图标（右下角有小箭头的按钮）。

有关如何实现下拉工具栏的信息，请参阅[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)。

该`CMFCDropDownToolBarButton`对象可以导出到[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象，并显示为带有弹出菜单的菜单按钮。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>要求

**标头：** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarbuttoncopyfrom"></a><a name="copyfrom"></a>CMFC向下拖拉工具栏按钮：：从复制

将另一个工具栏按钮的属性复制到当前按钮。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[在]对要从中复制的源按钮的引用。

### <a name="remarks"></a>备注

调用此方法以将另一个工具栏按钮复制到此工具栏按钮。 *src*必须是 类型的`CMFCDropDownToolbarButton`。

## <a name="cmfcdropdowntoolbarbuttoncmfcdropdowntoolbarbutton"></a><a name="cmfcdropdowntoolbarbutton"></a>CMFC向下工具栏按钮：：CMFC向下工具栏按钮

构造 `CMFCDropDownToolbarButton` 对象。

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
[在]按钮的默认文本。

*pToolBar*<br/>
[在]指向`CMFCDropDownToolBar`用户按下按钮时显示的对象的指针。

### <a name="remarks"></a>备注

构造函数的第二个重载将*pToolBar*指定的工具栏中的第一个按钮复制到下拉按钮。

通常，下拉工具栏按钮使用*pToolBar*指定的工具栏中最近使用的按钮中的文本。 当按钮转换为菜单按钮或显示在 **"自定义**"对话框的 **"命令"** 选项卡中时，它使用*lpszName*指定的文本。 有关 **"自定义"** 对话框的详细信息，请参阅[CMFCToolBars 自定义对话框类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCDropDownToolbarButton`类的对象。 此代码段是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

## <a name="cmfcdropdowntoolbarbuttondropdowntoolbar"></a><a name="dropdowntoolbar"></a>CMFC下线工具栏按钮：:DropDown工具栏

打开下拉工具栏。

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]下拉框架的父窗口，或"NULL"使用下拉工具栏按钮的父窗口。

### <a name="return-value"></a>返回值

如果方法成功，则非零;否则 0。

### <a name="remarks"></a>备注

[CMFCDrop下拉工具栏按钮：OnClick](#onclick)方法调用此方法，当用户按下并按下工具栏按钮时打开下拉工具栏。

此方法使用[CMFCDrop下线：创建](../../mfc/reference/cmfcdropdownframe-class.md#create)方法创建下拉工具栏。 如果父工具栏垂直停靠，则此方法会将下拉工具栏定位到父工具栏的左侧或右侧，具体取决于拟合。 否则，此方法将下拉工具栏定位在父工具栏下方。

如果*pWnd*为 NULL 并且下拉工具栏按钮没有父窗口，则此方法将失败。

## <a name="cmfcdropdowntoolbarbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFC向下工具栏按钮：：导出到菜单按钮

将工具栏按钮中的文本复制到菜单。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>参数

*菜单按钮*<br/>
[在]对目标菜单按钮的引用。

### <a name="return-value"></a>返回值

如果该方法成功，则为非零；否则为零。

### <a name="remarks"></a>备注

此方法调用基类实现 （ [CMFCToolBarButton：：exportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)）， 然后将包含此按钮中的每个工具栏菜单项的弹出菜单追加到目标菜单按钮。 此方法不会将子菜单追加到弹出式菜单。

如果父工具栏 为 NULL 或`m_pToolBar`基类实现返回 FALSE，则此方法将失败。

## <a name="cmfcdropdowntoolbarbuttongetdropdowntoolbar"></a><a name="getdropdowntoolbar"></a>CMFC向下拖下工具栏按钮：：获取向下拖拉工具栏

检索与按钮关联的下拉工具栏。

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>返回值

与按钮关联的下拉工具栏。

### <a name="remarks"></a>备注

此方法返回`m_pToolBar`数据成员。

## <a name="cmfcdropdowntoolbarbuttonisdropdown"></a><a name="isdropdown"></a>CMFC向下拖下工具栏按钮：：是向下

确定下拉工具栏当前是否打开。

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>返回值

如果下拉工具栏当前处于打开状态，则非零;否则 0。

### <a name="remarks"></a>备注

框架使用[CMFCDropDownToolbarButton：:DropDownToolbar](#dropdowntoolbar)方法打开下拉工具栏。 当用户按下下拉工具栏的非工作区中的左鼠标按钮时，框架将关闭下拉工具栏。

## <a name="cmfcdropdowntoolbarbuttonisextrasize"></a><a name="isextrasize"></a>CMFC向下工具栏按钮：：是超尺寸

确定按钮是否可以使用扩展边框显示。

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>返回值

如果工具栏按钮可以显示扩展边框，则非零;否则 0。

### <a name="remarks"></a>备注

有关扩展边框的详细信息，请参阅[CMFCToolBarButton：：是超大型](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。

## <a name="cmfcdropdowntoolbarbuttonm_uishowbardelay"></a><a name="m_uishowbardelay"></a>CMFC下拉工具栏按钮：：m_uiShowBarDelay

指定用户必须在下拉工具栏出现之前按住鼠标按钮的时间长度。

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>备注

延迟时间以毫秒为单位。 默认值为 500。 您可以通过更改此共享数据成员的值来设置另一个延迟。

## <a name="cmfcdropdowntoolbarbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFC向下拖拉工具栏按钮：：在计算大小

由框架调用，以计算指定设备上下文和停靠状态的按钮大小。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]显示按钮的设备上下文。

*大小 默认*<br/>
[在]按钮的默认大小。

*布霍兹*<br/>
[在]父工具栏的停靠状态。 如果工具栏水平停靠或浮动，则此参数为 TRUE;如果工具栏垂直停靠，则 FALSE 为 TRUE。

### <a name="return-value"></a>返回值

包含`SIZE`按钮尺寸（以像素为单位）的结构。

### <a name="remarks"></a>备注

此方法通过将下拉箭头的宽度添加到按钮大小的水平尺寸来扩展基类实现 （ [CMFCToolBarButton：：onCalculateSize）。](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)

## <a name="cmfcdropdowntoolbarbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFC下拉工具栏按钮：：打开更改家长

将按钮插入到新工具栏时由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]新的父窗口。

### <a name="remarks"></a>备注

此方法通过清除文本标签[（CMFCToolBarButton：：m_strText）](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)并设置[CMFCToolBarButton：：m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext)和[CMFCToolBarButton：：m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton)数据成员到 FALSE 来覆盖基类实现 （ [CMFCToolBarButton：：onChangeParentwnd）。](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)

## <a name="cmfcdropdowntoolbarbuttononclick"></a><a name="onclick"></a>CMFC向下工具栏按钮：：点击

当用户单击鼠标按钮时由框架调用。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]工具栏按钮的父窗口。

*bDelay*<br/>
[在]如果消息应延迟处理，则为 TRUE。

### <a name="return-value"></a>返回值

如果按钮处理单击消息，则非零;否则 0。

### <a name="remarks"></a>备注

此方法通过更新下拉工具栏的状态扩展基类实现[CMFCToolBarButton：：onClick。](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)

当用户单击工具栏按钮时，此方法将创建一个计时器，等待[CMFCDropDownToolbarBarButton：m_uiShowBarDelay](#m_uishowbardelay)数据成员指定的时间长度，然后使用[CMFCDropDownToolbarButton：:DropDownToolbar](#dropdowntoolbar)方法打开下拉工具栏。 此方法在用户第二次单击工具栏按钮时关闭下拉工具栏。

## <a name="cmfcdropdowntoolbarbuttononclickup"></a><a name="onclickup"></a>CMFC下拉工具栏按钮：：点击向上

当用户释放鼠标按钮时由框架调用。

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>返回值

如果按钮处理单击消息，则非零;否则 0。

### <a name="remarks"></a>备注

此方法通过更新下拉工具栏的状态扩展基类实现[CMFCToolBarButton：：onClickUp。](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)

此方法将停止下拉工具栏计时器（如果处于活动状态）。 如果工具栏处于打开状态，则关闭下拉工具栏。

有关下拉工具栏和下拉工具栏计时器的详细信息，请参阅[CMFCDrop下拉工具栏按钮：：单击](#onclick)。

## <a name="cmfcdropdowntoolbarbuttononcontexthelp"></a><a name="oncontexthelp"></a>CMFC向下工具栏按钮：：在上下文帮助

当父工具栏处理WM_HELPHITTEST消息时，由框架调用。

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]工具栏按钮的父窗口。

### <a name="return-value"></a>返回值

如果按钮处理帮助消息，则非零;否则 0。

### <a name="remarks"></a>备注

此方法通过调用[CMFCDropDown 下工具栏按钮：：单击](#onclick)方法 *（bDelay*设置为 FALSE）来扩展基类实现[（CMFCToolBarButton：：onContextHelp）。](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp) 此方法返回[由 CMFCDropDown 下工具栏按钮返回的值：：单击](#onclick)。

有关WM_HELPHITTEST消息的详细信息，请参阅[TN028：上下文相关帮助支持](../../mfc/tn028-context-sensitive-help-support.md)。

## <a name="cmfcdropdowntoolbarbuttononcustomizemenu"></a><a name="oncustomizemenu"></a>CMFC向下工具栏按钮：：在自定义菜单上

当应用程序在父工具栏上显示快捷方式菜单时，修改提供的菜单。

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>参数

*pMenu*<br/>
[在]要自定义的菜单。

### <a name="return-value"></a>返回值

此方法返回 TRUE。

### <a name="remarks"></a>备注

此方法通过禁用以下菜单项来扩展基类实现 （ [CMFCToolBarButton：：on自定义菜单](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)）：

- **复制按钮图像**

- **按钮外观**

- **映像**

- **Text**

- **图像和文本**

重写此方法以修改框架在自定义模式下显示的快捷菜单。

## <a name="cmfcdropdowntoolbarbuttonondraw"></a><a name="ondraw"></a>CMFC向下工具栏按钮：：开拉

框架调用使用指定的样式和选项绘制按钮。

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
[在]显示按钮的设备上下文。

*矩形*<br/>
[在]按钮的边界矩形。

*pImage*<br/>
[在]与按钮关联的工具栏图像的集合。

*布霍兹*<br/>
[在]父工具栏的停靠状态。 当按钮水平停靠时，此参数为 TRUE;当按钮垂直停靠时，则 FALSE 为 TRUE。

*b 定制模式*<br/>
[在]指定工具栏是否处于自定义模式。 当工具栏处于自定义模式时，此参数为 TRUE;当工具栏未处于自定义模式时，则 FALSE 为 TRUE。

*b 高光*<br/>
[在]指定按钮是否突出显示。 当按钮高亮显示时，此参数为 TRUE，在按钮未突出显示时为 FALSE。

*bDraw边框*<br/>
[在]指定按钮是否应显示其边框。 当按钮不应显示其边框时，此参数为 TRUE，当按钮不应显示其边框时，则 FALSE。

*b格雷禁用按钮*<br/>
[在]指定是为禁用按钮着色还是使用禁用的图像集合。 当禁用的按钮应进行扫描时，此参数为 TRUE，当此方法应使用禁用的图像集合时，则 FALSE 为 TRUE。

### <a name="remarks"></a>备注

重写此方法以自定义工具栏按钮绘图。

## <a name="cmfcdropdowntoolbarbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFC向下拖拉工具栏按钮：：在绘制上自定义列表

由框架调用以在 **"自定义"** 对话框的 **"命令"** 窗格中绘制按钮。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]显示按钮的设备上下文。

*矩形*<br/>
[在]按钮的边界矩形。

*b选定*<br/>
[在]是否选择了按钮。 如果此参数为 TRUE，则选择该按钮。 如果此参数为 FALSE，则未选择该按钮。

### <a name="return-value"></a>返回值

指定设备上下文中按钮的宽度（以像素为单位）。

### <a name="remarks"></a>备注

当需要按钮在所有者绘制列表框中显示自身时，自定义对话框（**命令**选项卡）调用此方法。

此方法通过将按钮的文本标签更改为按钮的名称（即，将传递给构造函数的*lpszName*参数的值）来扩展基类实现[（CMFCToolBarButton：：onDrawOn自定义列表](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)）。

## <a name="cmfcdropdowntoolbarbuttonserialize"></a><a name="serialize"></a>CMFC下拉工具栏按钮：序列化

从存档中读取此对象或将其写入存档。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
[在]要`CArchive`从其序列化的对象。

### <a name="remarks"></a>备注

此方法通过序列化父工具栏的资源 ID 来扩展基类实现 （ [CMFCToolBarButton：：序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)）。 当存档正在加载时[（CArchive：：IsLoading](../../mfc/reference/carchive-class.md#isloading)返回一个非零值），此方法将`m_pToolBar`数据成员设置到包含序列化资源 ID 的工具栏。

## <a name="cmfcdropdowntoolbarbuttonsetdefaultcommand"></a><a name="setdefaultcommand"></a>CMFC下拉下工具栏按钮：：设置默认命令

设置框架在用户单击按钮时使用的默认命令。

```cpp
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]默认命令的 ID。

### <a name="remarks"></a>备注

调用此方法以指定框架在用户单击按钮时执行的默认命令。 具有*uiCmd*指定的命令 ID 的项必须位于父下拉工具栏中。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC下拉工具栏类](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenu按钮类](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
