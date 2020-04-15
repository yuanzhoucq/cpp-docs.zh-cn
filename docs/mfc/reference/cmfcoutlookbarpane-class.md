---
title: CMFCOutlookBarPane 类
ms.date: 11/04/2016
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
ms.openlocfilehash: 82d8f1da0640e5b487a06585c72279e7d7ffdf99
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369642"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 类

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

从[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)派生的控件，可以插入到 Outlook 栏[（CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)）。 Outlook 栏窗格包含一列大按钮。 如果按钮列表大于窗格，用户可以上下滚动按钮列表。 当用户将 Outlook 栏中的一个窗格与 Outlook 栏分离时，此窗格可以浮动或停靠在主框架窗口中。

## <a name="syntax"></a>语法

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|默认构造函数。|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCOutlookBarPane：：添加按钮](#addbutton)|向 Outlook 栏窗格添加一个按钮。|
|[CMFCOutlookbarPane：：可以附加](#canbeattached)|确定窗格是否可以停靠到另一个窗格或框架窗口。 （覆盖[CBasePane：：可以附加](../../mfc/reference/cbasepane-class.md#canbeattached).）|
|`CMFCOutlookBarPane::CanBeRestored`|确定系统在自定义后是否可以将工具栏还原到其原始状态。 （覆盖[CMFCTool 栏：可以还原](../../mfc/reference/cmfctoolbar-class.md#canberestored).）|
|[CMFCOutlookBarPane：清除所有](#clearall)|释放 Outlook 栏窗格中图像使用的资源。|
|[CMFCOutlookBarPane：创建](#create)|创建 Outlook 栏窗格。|
|`CMFCOutlookBarPane::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCOutlookBarPane::Dock`|由框架调用以停靠 Outlook 栏窗格。 （重写 `CPane::Dock`。）|
|[CMFCOutlookbarPane：：启用页面滚动模式](#enablepagescrollmode)|指定"Outlook"栏窗格上的滚动箭头是按页面或按按钮前进按钮列表的。|
|[CMFCOutlookBarPane：获取常规颜色](#getregularcolor)|返回 Outlook 栏窗格的常规（未选中）文本颜色。|
|`CMFCOutlookBarPane::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCOutlookBarPane：是背景纹理](#isbackgroundtexture)|确定是否为 Outlook 栏窗格加载了背景图像。|
|`CMFCOutlookBarPane::IsChangeState`|确定是否可以停靠浮动窗格。 （重写 `CPane::IsChangeState`。）|
|[CMFCOutlookBarPane：：绘制高光](#isdrawshadedhighlight)|确定在突出显示按钮和显示背景图像时，按钮边框是否已呈现。|
|`CMFCOutlookBarPane::OnBeforeFloat`|当窗格即将浮动时，由框架调用。 （覆盖[CPane：：在浮动之前](../../mfc/reference/cpane-class.md#onbeforefloat)打开 。|
|[CMFCOutlook 栏：：删除按钮](#removebutton)|删除具有指定命令 ID 的按钮。|
|`CMFCOutlookBarPane::RestoreOriginalstate`|还原工具栏的原始状态。 （覆盖[CMFCTool 栏：还原原始状态](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)。）|
|[CMFCOutlookbarPane：：设置回彩](#setbackcolor)|设置背景颜色。|
|[CMFCOutlookBarPane：：设置返回图像](#setbackimage)|设置背景图像。|
|[CMFCOutlook 栏：：设置默认状态](#setdefaultstate)|将 Outlook 栏窗格重置为原始按钮集。|
|[CMFCOutlookbarPane：设置额外空间](#setextraspace)|设置 Outlook 栏窗格中按钮周围使用的填充像素数。|
|[CMFCOutlookbarPane：：设置文本颜色](#settextcolor)|在 Outlook 栏窗格中设置常规文本和突出显示文本的颜色。|
|[CMFCOutlook 栏：：设置透明色](#settransparentcolor)|设置 Outlook 栏窗格的透明颜色。|
|`CMFCOutlookBarPane::SmartUpdate`|在内部用于更新 Outlook 栏。 （重写 `CMFCToolBar::SmartUpdate`。）|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFCOutlook 栏：：启用上下文菜单项目](#enablecontextmenuitems)|指定在自定义模式下显示的快捷菜单项。|
|[CMFCOutlookBarPane：：删除所有按钮](#removeallbuttons)|从 Outlook 栏窗格中删除所有按钮。 （覆盖[CMFCTool 栏：删除所有按钮](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).）|

## <a name="remarks"></a>备注

有关如何实现 Outlook 栏的信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。

有关 Outlook 栏的示例，请参阅 OutlookDemo 示例项目。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCOutlookBarPane`类的各种方法。 该示例演示如何创建 Outlook 栏窗格、启用页面滚动模式、启用停靠以及设置 Outlook 栏的背景颜色。 此代码段是 Outlook[多视图示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具栏](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>要求

**标题：** afxoutlookbarpane.h

## <a name="cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarPane：：添加按钮

向 Outlook 栏窗格添加一个按钮。

```
BOOL AddButton(
    UINT uiImage,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    UINT uiImage,
    UINT uiLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    LPCTSTR szBmpFileName,
    LPCTSTR szLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HBITMAP hBmp,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HICON hIcon,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1,
    BOOL bAlphaBlend=FALSE);
```

### <a name="parameters"></a>参数

*uiImage*<br/>
[在]指定位图的资源标识符。

*lpszLabel*<br/>
[在]指定按钮的文本。

*iIdCommand*<br/>
[在]指定按钮控件的 ID。

*iInsertAt*<br/>
[在]指定要插入按钮的 Outlook 栏页面上的零索引。

*乌伊标签*<br/>
[在]字符串资源 ID。

*szBmpFile名称*<br/>
[在]指定要加载的磁盘映像文件的名称。

*szLabel*<br/>
[在]指定按钮的文本。

*hBmp*<br/>
[在]按钮位图的句柄。

*hIcon*<br/>
[在]按钮图标的句柄。

### <a name="return-value"></a>返回值

如果已成功添加按钮，则为 TRUE;如果已成功添加按钮，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

使用此方法将新按钮插入到 Outlook 栏的页面。 可以从应用程序资源或磁盘文件加载按钮的图像。

如果*uiPageID*指定的页面 ID 为 -1，则该按钮将插入到第一页。

如果*iInsertAt*指定的索引为 -1，则按钮将添加到页面末尾。

## <a name="cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookbarPane：：可以附加

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane：清除所有

释放 Outlook 栏窗格上图像使用的资源。

```
void ClearAll();
```

### <a name="remarks"></a>备注

此方法直接调用[CMFCToolBarImages：：Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear)，它调用 Outlook 栏窗格使用的图像。

## <a name="cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane：创建

创建 Outlook 栏窗格。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
[在]指定 Outlook 栏窗格控件的父窗口。 不能为 NULL。

*dwStyle*<br/>
[在]窗口样式。  有关窗口样式的列表，请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*uiID*<br/>
[在]控件 ID。 必须是唯一的才能保存控件的状态。

*dwControlBar样式*<br/>
[在]指定定义 Outlook 栏窗格控件与 Outlook 栏分离时的行为的特殊样式。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

要构造对象`CMFCOutlookBarPane`，请先调用构造函数，然后调用`Create`，这将创建 Outlook 栏窗格控件并将其附加到`CMFCOutlookBarPane`对象。

有关有关的详细信息`dwControlBarStyle`，请参阅[CBasePane：：创建 Ex](../../mfc/reference/cbasepane-class.md#createex)。

## <a name="cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlook 栏：：启用上下文菜单项目

指定在自定义模式下显示的快捷菜单项。

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>参数

*pButton*<br/>
[在]指向用户单击的工具栏按钮的指针。

*pPopup*<br/>
[在]指向快捷菜单的指针。

### <a name="return-value"></a>返回值

如果应显示快捷菜单，则返回 TRUE;如果应显示快捷方式菜单，则返回 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

重写此方法以修改框架在自定义模式下显示的框架标准快捷菜单。

默认实现检查自定义模式[（CMFCToolBar：：是自定义模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)），如果设置为 TRUE，则禁用**除删除**之外的所有快捷菜单项。 然后，它只是将输入参数传递给`CMFCToolBar::EnableContextMenuItems`。

> [!NOTE]
> *上下文菜单*是快捷菜单的同义词。

## <a name="cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookbarPane：：启用页面滚动模式

指定 Outlook 栏窗格上的滚动箭头是逐页前进按钮列表，还是按按钮前进。

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>参数

*bPageScroll*<br/>
[在]如果为 TRUE，则启用页面滚动模式。 如果 FALSE，则禁用页面滚动模式。

## <a name="cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarPane：获取常规颜色

返回 Outlook 栏窗格的常规（即未选中）文本颜色。

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>返回值

当前文本颜色作为 RGB 颜色值。

### <a name="remarks"></a>备注

使用[CMFCOutlookBarPane：SetTextColor](#settextcolor)设置 Outlook 栏的当前（常规和选定）文本颜色。 您可以通过使用COLOR_WINDOW索引调用[GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor)函数来获取默认文本颜色。

## <a name="cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane：是背景纹理

确定是否为 Outlook 栏窗格加载了背景图像。

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>返回值

如果有要显示的背景图像，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

您可以通过调用[CMFCOutlookBarPane：：设置返回图像](#setbackimage)功能来添加背景图像。

如果没有背景图像，则使用[CMFCOutlookBarPane 指定的颜色绘制背景：：设置返回颜色](#setbackcolor)。

## <a name="cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane：：绘制高光

确定在突出显示按钮和显示背景图像时，按钮边框是否已呈现。

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>返回值

如果按钮的边框被带过，则为 TRUE;否则 FALSE。

## <a name="cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane：：删除所有按钮

从 Outlook 栏窗格中删除所有按钮。

```
virtual void RemoveAllButtons();
```

## <a name="cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlook 栏：：删除按钮

删除具有指定命令 ID 的按钮。

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>参数

*iIdCommand*<br/>
[在]指定要删除的按钮的命令 ID。

### <a name="return-value"></a>返回值

如果按钮已成功删除，则为 TRUE;如果指定的命令 ID 无效，则 FALSE。

## <a name="cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookbarPane：：设置回彩

设置 Outlook 栏的背景颜色。

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]指定新的背景颜色。

### <a name="remarks"></a>备注

调用此函数以设置 Outlook 栏的当前背景颜色。 仅当没有背景图像时，才使用背景颜色。

## <a name="cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarPane：：设置返回图像

设置背景图像。

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>参数

*uiImageID*<br/>
[在]指定图像资源 ID。

### <a name="remarks"></a>备注

调用此方法以设置 Outlook 栏的背景图像。 背景图像列表由嵌入的[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)对象管理。

## <a name="cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlook 栏：：设置默认状态

将 Outlook 栏窗格重置为原始按钮集。

```
void SetDefaultState();
```

### <a name="remarks"></a>备注

此方法将 Outlook 栏按钮还原到原始集。 此方法类似于`CMFCOutlookBarPane::RestoreOriginalstate`，只不过它不会触发 Outlook 栏窗格的重绘。

## <a name="cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookbarPane：设置额外空间

设置 Outlook 栏窗格中按钮周围使用的填充像素数。

```
void SetExtraSpace()
```

## <a name="cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookbarPane：：设置文本颜色

在 Outlook 栏窗格中设置常规文本和突出显示文本的颜色。

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>参数

*clrRegText*<br/>
[在]指定非选定文本的新颜色。

*clrSelText*<br/>
[在]指定所选文本的新颜色。

## <a name="cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlook 栏：：设置透明色

设置 Outlook 栏窗格的透明颜色。

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
指定新的透明颜色。

### <a name="remarks"></a>备注

显示透明图像需要透明颜色。 图像中此颜色的任何出现都用背景颜色绘制。  背景图像和前景图像没有混合。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
