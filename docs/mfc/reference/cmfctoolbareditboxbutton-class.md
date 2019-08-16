---
title: CMFCToolBarEditBoxButton 类
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarEditBoxButton [MFC], CMFCToolBarEditBoxButton
- CMFCToolBarEditBoxButton [MFC], CanBeStretched
- CMFCToolBarEditBoxButton [MFC], CopyFrom
- CMFCToolBarEditBoxButton [MFC], GetByCmd
- CMFCToolBarEditBoxButton [MFC], GetContentsAll
- CMFCToolBarEditBoxButton [MFC], GetContextMenuID
- CMFCToolBarEditBoxButton [MFC], GetEditBorder
- CMFCToolBarEditBoxButton [MFC], GetHwnd
- CMFCToolBarEditBoxButton [MFC], GetInvalidateRect
- CMFCToolBarEditBoxButton [MFC], HaveHotBorder
- CMFCToolBarEditBoxButton [MFC], IsFlatMode
- CMFCToolBarEditBoxButton [MFC], NotifyCommand
- CMFCToolBarEditBoxButton [MFC], OnAddToCustomizePage
- CMFCToolBarEditBoxButton [MFC], OnChangeParentWnd
- CMFCToolBarEditBoxButton [MFC], OnClick
- CMFCToolBarEditBoxButton [MFC], OnCtlColor
- CMFCToolBarEditBoxButton [MFC], OnGlobalFontsChanged
- CMFCToolBarEditBoxButton [MFC], OnMove
- CMFCToolBarEditBoxButton [MFC], OnShow
- CMFCToolBarEditBoxButton [MFC], OnSize
- CMFCToolBarEditBoxButton [MFC], OnUpdateToolTip
- CMFCToolBarEditBoxButton [MFC], SetContextMenuID
- CMFCToolBarEditBoxButton [MFC], SetFlatMode
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
ms.openlocfilehash: 3e988d789ca6a038ce41bca829850f6509fd9df1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504733"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton 类

包含编辑控件 ( [CEdit 类](../../mfc/reference/cedit-class.md)) 的工具栏按钮。

## <a name="syntax"></a>语法

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|构造 `CMFCToolBarEditBoxButton` 对象。|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|指定用户是否可以在自定义过程中拉伸该按钮。 (重写[CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)。)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。 (重写[CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: CreateEdit](#createedit)|在按钮中创建新的编辑控件。|
|`CMFCToolBarEditBoxButton::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|检索应用程序`CMFCToolBarEditBoxButton`中具有指定命令 ID 的第一个对象。|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|检索具有指定命令 ID 的第一个编辑框工具栏控件的文本。|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|检索与按钮关联的快捷菜单的资源 ID。|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|检索编辑框按钮编辑部分的边框。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: GetEditBox](#geteditbox)|返回一个指针, 该指针指向嵌入在按钮中的编辑控件。|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|检索与工具栏按钮关联的窗口句柄。 (重写[CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)。)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|检索必须重绘的按钮工作区的区域。 (重写[CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)。)|
|`CMFCToolBarEditBoxButton::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|确定当用户单击按钮时, 是否显示按钮的边框。 (重写[CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|确定编辑框按钮是否具有平面样式。|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|指定按钮是否处理[WM_COMMAND](/windows/win32/menurc/wm-command)消息。 (重写[CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)。)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|在将按钮添加到 "**自定义**" 对话框时由框架调用。 (重写[CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|由框架调用, 用于计算指定设备上下文和停靠状态的按钮大小。 (重写[CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|在将按钮插入新工具栏时由框架调用。 (重写[CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|当用户单击鼠标按钮时由框架调用。 (重写[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|当父工具栏处理 WM_CTLCOLOR 消息时由框架调用。 (重写[CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。)|
|`CMFCToolBarEditBoxButton::OnDraw`|由框架调用, 用于通过使用指定的样式和选项绘制按钮。 (重写[CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|由框架调用, 用于绘制 "**自定义**" 对话框的 "**命令**" 窗格中的按钮。 (重写[CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|当全局字体已更改时由框架调用。 (重写[CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)。)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|当父工具栏移动时由框架调用。 (重写[CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)。)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|当按钮变为可见或不可见时由框架调用。 (重写[CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)。)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|当父工具栏更改其大小或位置并且此更改导致按钮更改大小时, 由框架调用。 (重写[CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|当父工具栏更新其工具提示文本时由框架调用。 (重写[CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)。)|
|`CMFCToolBarEditBoxButton::Serialize`|从存档中读取此对象或将其写入存档。 (重写[CMFCToolBarButton:: 串行化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|
|`CMFCToolBarEditBoxButton::SetACCData`|用工具栏按钮`CAccessibilityData`中的可访问性数据填充提供的对象。 (重写[CMFCToolBarButton:: SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata)。)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetContents](#setcontents)|设置按钮的编辑控件中的文本。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall)|查找具有指定命令 ID 的 "编辑控件" 按钮, 并设置该按钮的 "编辑" 控件中的文本。|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|指定与按钮关联的快捷菜单的资源 ID。|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|指定应用程序中编辑框按钮的平面样式外观。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: system.windows.forms.control.setstyle](#setstyle)|指定按钮的样式。 (重写[CMFCToolBarButton:: system.windows.forms.control.setstyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。)|

## <a name="remarks"></a>备注

若要将 "编辑框" 按钮添加到工具栏, 请执行以下步骤:

1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。

2. `CMFCToolBarEditBoxButton`构造对象。

3. 在处理 AFX_WM_RESETTOOLBAR 消息的消息处理程序中, 使用[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)将虚拟按钮替换为新组合框按钮。

有关详细信息，请参见[演练：将控件放置在](../../mfc/walkthrough-putting-controls-on-toolbars.md)工具栏上。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCToolBarEditBoxButton` 类中的各种方法。 该示例演示了如何指定用户可以在自定义过程中拉伸按钮、指定在用户单击该按钮时显示该按钮的边框、设置文本框控件中的文本、在应用中指定编辑框按钮的平面样式外观。程序, 并指定工具栏编辑框控件的样式。

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>要求

**标头:** afxtoolbareditboxbutton

##  <a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched

指定用户是否可以在自定义过程中拉伸该按钮。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>返回值

此方法返回 TRUE。

### <a name="remarks"></a>备注

默认情况下, 框架不允许用户在自定义过程中拉伸工具栏按钮。 此方法通过允许用户在自定义过程中拉伸编辑框工具栏按钮来扩展基类实现 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched))。

##  <a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

构造[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)对象。

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>参数

*uiID*<br/>
中指定控件 ID。

*iImage*<br/>
中指定工具栏图像的从零开始的索引。 该图像位于[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)维护的[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)对象中。

*dwStyle*<br/>
中指定编辑控件样式。

*iWidth*<br/>
中指定编辑控件的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

默认构造函数将编辑控件样式设置为以下组合:

WS_CHILD |WS_VISIBLE |ES_AUTOHSCROLL

控件的默认宽度为150像素。

##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton:: CopyFrom

将另一个工具栏按钮的属性复制到当前按钮。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
中对要从中进行复制的源按钮的引用。

### <a name="remarks"></a>备注

调用此方法可将另一个工具栏按钮复制到此工具栏按钮。 *src*的类型`CMFCToolBarEditBoxButton`必须为。

##  <a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit

在按钮中创建新的编辑控件。

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中指定编辑控件的父窗口。 它不能为 NULL。

*rect*<br/>
中指定编辑控件的大小和位置。

### <a name="return-value"></a>返回值

指向新创建的编辑控件的指针;如果控件的创建和附件失败, 则为 NULL。

### <a name="remarks"></a>备注

可以通过`CMFCToolBarEditBoxButton`两个步骤构造对象。 首先调用构造函数, 然后调用`CreateEdit`, 它创建 Windows 编辑控件并将其附加`CMFCToolBarEditBoxButton`到对象。

##  <a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd

检索应用程序`CMFCToolBarEditBoxButton`中具有指定命令 ID 的第一个对象。

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中要检索的按钮的命令 ID。

### <a name="return-value"></a>返回值

应用程序`CMFCToolBarEditBoxButton`中具有指定命令 ID 的第一个对象, 如果不存在这样的对象, 则为 NULL。

### <a name="remarks"></a>备注

此共享实用工具方法由[CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall)和[CMFCToolBarEditBoxButton:: GetContentsAll](#getcontentsall)等方法用来设置或获取具有指定命令 ID 的第一个编辑框工具栏控件的文本。

##  <a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll

检索具有指定命令 ID 的第一个编辑框工具栏控件的文本。

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中要从中检索内容的按钮的命令 ID。

### <a name="return-value"></a>返回值

一个`CString`对象, 该对象包含具有指定命令 ID 的第一个编辑框工具栏控件的文本。

### <a name="remarks"></a>备注

如果没有`CMFCToolBarEditBoxButton`对象具有指定的命令 ID, 则此方法返回空字符串。

##  <a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID

检索与按钮关联的快捷菜单的资源 ID。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>返回值

与按钮相关联的快捷菜单的资源 ID, 如果按钮没有关联的快捷菜单, 则为0。

### <a name="remarks"></a>备注

当用户右键单击该按钮时, 框架使用资源 ID 创建快捷菜单。

##  <a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

检索编辑框按钮编辑部分的边框。

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>参数

*rectBorder*<br/>
弄对接收边框的`CRect`对象的引用。

### <a name="remarks"></a>备注

此方法检索工作区坐标中编辑控件的边框。 它将每个方向上矩形的大小扩展一个像素。

当[CMFCVisualManager:: OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder)方法在`CMFCToolBarEditBoxButton`对象周围绘制边框时, 将调用此方法。

##  <a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

返回一个指针, 该指针指向嵌入在按钮中的[CEdit 类](../../mfc/reference/cedit-class.md)控件。

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>返回值

指向按钮包含的[CEdit 类](../../mfc/reference/cedit-class.md)控件的指针。 如果尚未创建`CEdit`控件, 则为 NULL。

### <a name="remarks"></a>备注

可以通过调用`CEdit` [CMFCToolBarEditBoxButton:: CreateEdit](#createedit)创建控件。

##  <a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd

检索与工具栏按钮关联的窗口句柄。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>返回值

与按钮关联的窗口句柄。

### <a name="remarks"></a>备注

此方法通过返回编辑框按钮的编辑控件部分的窗口句柄, 重写[CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。

##  <a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

检索必须重绘的按钮工作区的区域。

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>返回值

一个`CRect`对象, 该对象指定必须重新绘制的区域。

### <a name="remarks"></a>备注

此方法通过将文本标签区域包含在区域中来扩展基类实现, [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)。

##  <a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder

确定当用户单击按钮时, 是否显示按钮的边框。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>返回值

如果按钮在选中时显示其边框, 则为非零;否则为0。

### <a name="remarks"></a>备注

此方法通过在控件可见时返回一个非零值, 来扩展基类实现[CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。

##  <a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode

确定编辑框按钮是否具有平面样式。

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>返回值

如果按钮具有平面样式, 则为非零值;否则为0。

### <a name="remarks"></a>备注

默认情况下, 编辑框按钮具有平面样式。 使用[CMFCToolBarEditBoxButton:: SetFlatMode](#setflatmode)方法可以更改应用程序的平面样式外观。

##  <a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand

指定按钮是否处理[WM_COMMAND](/windows/win32/menurc/wm-command)消息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>参数

*iNotifyCode*<br/>
中与命令关联的通知消息。

### <a name="return-value"></a>返回值

如果按钮处理 WM_COMMAND 消息, 则为 TRUE; 如果为 FALSE, 则指示消息必须由父工具栏处理。

### <a name="remarks"></a>备注

当框架即将向父窗口发送[WM_COMMAND](/windows/win32/menurc/wm-command)消息时, 框架会调用此方法。

此方法通过处理[EN_UPDATE](/windows/win32/Controls/en-update)通知扩展基类实现 ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand))。 对于具有与此对象相同的命令 ID 的每个编辑框, 它会将其文本标签设置为此对象的文本标签。

##  <a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage

在将按钮添加到 "**自定义**" 对话框时由框架调用。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>备注

此方法通过从具有与此对象相同的命令 ID 的任何工具栏中的 "编辑框" 控件复制属性, 来扩展基类实现 ( [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage))。 如果没有任何工具栏具有与此对象相同的命令 ID, 则此方法不执行任何操作。

有关 "**自定义**" 对话框的详细信息, 请参阅[CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

##  <a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

在将按钮插入新工具栏时由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中指向新的父窗口的指针。

### <a name="remarks"></a>备注

此方法通过重新创建内部`CEdit`对象来重写基类实现 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd))。

##  <a name="onclick"></a>CMFCToolBarEditBoxButton:: OnClick

当用户单击鼠标按钮时由框架调用。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中用.

*bDelay*<br/>
中用.

### <a name="return-value"></a>返回值

如果按钮处理单击消息, 则为非零值;否则为0。

### <a name="remarks"></a>备注

如果内部`CEdit`对象可见, 则此方法将重写基类实现 ( [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)), 方法是返回一个非零值。

##  <a name="onctlcolor"></a>  CMFCToolBarEditBoxButton::OnCtlColor

当父工具栏处理 WM_CTLCOLOR 消息时由框架调用。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中显示按钮的设备上下文。

*nCtlColor*<br/>
中用.

### <a name="return-value"></a>返回值

全局窗口画笔的句柄。

### <a name="remarks"></a>备注

此方法会重写基类实现 ( [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)), 方法是将所提供的设备上下文的文本和背景色分别设置为全局文本和背景色。

有关可用于应用程序的全局选项的详细信息, 请参阅[AFX_GLOBAL_DATA 结构](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged

当全局字体已更改时由框架调用。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>备注

此方法通过将控件的字体更改为全局字体的字体来扩展基类实现 ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged))。

有关可用于应用程序的全局选项的详细信息, 请参阅[AFX_GLOBAL_DATA 结构](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove

当父工具栏移动时由框架调用。

```
virtual void OnMove();
```

### <a name="remarks"></a>备注

此方法通过更新内部`CEdit`对象的位置重写默认类实现 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove))

##  <a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow

当按钮变为可见或不可见时由框架调用。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
中指定按钮是否可见。 如果此参数为 TRUE, 则该按钮可见。 否则, 该按钮将不可见。

### <a name="remarks"></a>备注

如果*bShow*为 TRUE, 则此方法将通过显示该按钮来扩展基类实现 ( [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow))。 否则, 此方法将隐藏按钮。

##  <a name="onsize"></a>CMFCToolBarEditBoxButton:: OnSize

当父工具栏更改其大小或位置并且此更改导致按钮更改大小时, 由框架调用。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>参数

*iSize*<br/>
中按钮的新宽度 (以像素为单位)。

### <a name="remarks"></a>备注

此方法通过更新内部`CEdit`对象的大小和位置来重写默认类实现[CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。

##  <a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip

当父工具栏更新其工具提示文本时由框架调用。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中用.

*iButtonIndex*<br/>
中用.

*wndToolTip*<br/>
中用于显示工具提示文本的控件。

*str*<br/>
弄一个`CString`对象, 它接收更新的工具提示文本。

### <a name="return-value"></a>返回值

如果方法更新工具提示文本, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此方法通过显示与按钮编辑部分关联的工具提示文本, 来扩展基类实现 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip))。 如果内部`CEdit`对象为 NULL 或`CEdit`对象的窗口句柄不标识现有窗口, 则此方法不执行任何操作并返回 FALSE。

##  <a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents

设置文本框控件中的文本。

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>参数

*sContents*<br/>
中指定要设置的新文本。

##  <a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll

查找具有指定的命令 ID 的[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)对象, 并在其文本框中设置指定的文本。

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中指定将为其更改文本的控件的命令 ID。

*strContents*<br/>
中指定要设置的新文本。

### <a name="return-value"></a>返回值

如果设置了文本, 则为非零值;如果具有指定`CMFCToolBarEditBoxButton`命令 ID 的控件不存在, 则为0。

##  <a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID

指定与按钮关联的快捷菜单的资源 ID。

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中快捷菜单的资源 ID。

### <a name="remarks"></a>备注

当用户右键单击工具栏按钮时, 框架使用资源 ID 创建快捷菜单。

##  <a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode

指定应用程序中编辑框按钮的平面样式外观。

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>参数

*bFlat*<br/>
中编辑框按钮的平面样式。 如果此参数为 TRUE, 则启用平面样式外观;否则, 将禁用平面样式外观。

### <a name="remarks"></a>备注

编辑框按钮的默认平面样式为 TRUE。 使用[CMFCToolBarEditBoxButton:: IsFlatMode](#isflatmode)方法检索应用程序的平面样式外观。

##  <a name="setstyle"></a>CMFCToolBarEditBoxButton:: System.windows.forms.control.setstyle

指定工具栏编辑框控件的样式。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>参数

*nStyle*<br/>
中要设置的新样式。

### <a name="remarks"></a>备注

此方法将[CMFCToolBarButton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)设置为*nStyle* , 它还会在应用程序处于自定义模式时禁用文本框, 并在应用程序未处于自定义模式时启用它 (请参阅[CMFCToolBar:: SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode)和[CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))。 有关有效样式标志的列表, 请参阅[ToolBar 控件样式](../../mfc/reference/toolbar-control-styles.md)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[演练：将控件添加到工具栏](../../mfc/walkthrough-putting-controls-on-toolbars.md)
