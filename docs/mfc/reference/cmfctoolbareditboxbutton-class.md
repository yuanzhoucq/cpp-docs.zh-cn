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
ms.openlocfilehash: 52989f7b523bf0ba9a00da350242a968ca0db153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360471"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton 类

包含编辑控件 （ [CEdit 类](../../mfc/reference/cedit-class.md)） 的工具栏按钮 。

## <a name="syntax"></a>语法

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCToolbar编辑盒按钮：CMFC工具栏编辑箱按钮](#cmfctoolbareditboxbutton)|构造 `CMFCToolBarEditBoxButton` 对象。|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCToolbar编辑盒按钮：：可以拉伸](#canbestretched)|指定用户是否可以在自定义期间拉伸按钮。 （覆盖[CMFC 工具栏按钮：：可以拉伸](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).）|
|[CMFCToolbar编辑盒按钮：：抄袭](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。 （覆盖[CMFCToolBar 按钮：：从](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)复制。）|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar编辑盒按钮：：创建编辑](#createedit)|在按钮中创建新的编辑控件。|
|`CMFCToolBarEditBoxButton::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCToolbar编辑盒按钮：：获取](#getbycmd)|检索应用程序中具有指定`CMFCToolBarEditBoxButton`命令 ID 的第一个对象。|
|[CMFCToolbar编辑盒按钮：：获取内容所有](#getcontentsall)|检索具有指定命令 ID 的第一个编辑框工具栏控件的文本。|
|[CMFCToolbar编辑盒按钮：：获取上下文菜单ID](#getcontextmenuid)|检索与按钮关联的快捷菜单的资源 ID。|
|[CMFCToolbar编辑盒按钮：：获取编辑边框](#geteditborder)|检索编辑框按钮编辑部分的边界矩形。|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar编辑盒按钮：：获取编辑框](#geteditbox)|返回指向嵌入在按钮中的编辑控件的指针。|
|[CMFCToolBar编辑盒按钮：：获取Hwnd](#gethwnd)|检索与工具栏按钮关联的窗口句柄。 （覆盖[CMFCToolBarButton：获取 Hwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).）|
|[CMFCToolbar编辑盒按钮：：获得验证](#getinvalidaterect)|检索必须重绘的按钮的工作区区域。 （覆盖[CMFCToolBar 按钮：获取验证重新](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)完成 。|
|`CMFCToolBarEditBoxButton::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCToolbar编辑盒按钮：：有热边框](#havehotborder)|确定当用户单击该按钮时是否显示按钮的边框。 （覆盖[CMFCToolBar 按钮：：有 Hot 边框](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).）|
|[CMFCToolbar编辑盒按钮：：是平模式](#isflatmode)|确定编辑框按钮是否具有平面样式。|
|[CMFCToolbar编辑盒按钮：：通知命令](#notifycommand)|指定按钮是否处理[WM_COMMAND](/windows/win32/menurc/wm-command)消息。 （覆盖[CMFCToolBar 按钮：通知命令](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).）|
|[CMFCToolbar编辑盒按钮：：在"添加"上自定义页面](#onaddtocustomizepage)|将按钮添加到 **"自定义"** 对话框时由框架调用。 （覆盖[CMFC 工具栏按钮：：在 Addto 自定义页](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).）|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|由框架调用，以计算指定设备上下文和停靠状态的按钮大小。 （覆盖[CMFC 工具栏按钮："正在计算大小](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)"）|
|[CMFCToolbar编辑盒按钮：：打开更改家长](#onchangeparentwnd)|将按钮插入到新工具栏时由框架调用。 （覆盖[CMFC 工具栏按钮：打开更改父项](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).）|
|[CMFCToolbar编辑盒按钮：：点击](#onclick)|当用户单击鼠标按钮时由框架调用。 （覆盖[CMFC 工具栏按钮：：单击](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).）|
|[CMFCToolbar编辑盒按钮：：在CtlColor上](#onctlcolor)|当父工具栏处理WM_CTLCOLOR消息时，框架调用。 （覆盖[CMFCToolBar 按钮：OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).）|
|`CMFCToolBarEditBoxButton::OnDraw`|框架调用使用指定的样式和选项绘制按钮。 （覆盖[CMFC 工具栏按钮：：OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).）|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|由框架调用以在 **"自定义"** 对话框的 **"命令"** 窗格中绘制按钮。 （覆盖[CMFC 工具栏按钮：在"绘制"自定义列表](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).）|
|[CMFCToolbar编辑盒按钮：：在全局字体上更改](#onglobalfontschanged)|当全局字体已更改时由框架调用。 （覆盖[CMFC 工具栏按钮：：在全局字体更改](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).）|
|[CMFCToolbar编辑盒按钮：：移动](#onmove)|当父工具栏移动时由框架调用。 （覆盖[CMFC 工具栏按钮：：打开](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)移动 .）|
|[CMFCToolbar编辑盒按钮：：上展](#onshow)|当按钮变得可见或不可见时，由框架调用。 （覆盖[CMFCToolBar 按钮：：在显示](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).）|
|[CMFCToolbar编辑盒按钮：：打开尺寸](#onsize)|当父工具栏更改其大小或位置且此更改导致按钮更改大小时，框架调用该按钮。 （覆盖[CMFC 工具栏按钮：：打开大小](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).）|
|[CMFCToolbar编辑盒按钮：：更新工具提示](#onupdatetooltip)|当父工具栏更新其工具提示文本时，由框架调用。 （覆盖[CMFC 工具栏按钮：打开更新工具提示](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).）|
|`CMFCToolBarEditBoxButton::Serialize`|从存档中读取此对象或将其写入存档。 （覆盖[CMFCToolBarButton：序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).）|
|`CMFCToolBarEditBoxButton::SetACCData`|使用工具栏按钮中的`CAccessibilityData`辅助功能数据填充提供的对象。 （覆盖[CMFC 工具栏按钮：设置ACC数据](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).）|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar编辑盒按钮：：设置内容](#setcontents)|在按钮的编辑控件中设置文本。|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar编辑盒按钮：：设置内容所有](#setcontentsall)|查找具有指定命令 ID 的编辑控件按钮，并在该按钮的编辑控件中设置文本。|
|[CMFCToolbar编辑盒按钮：：设置上下文菜单ID](#setcontextmenuid)|指定与按钮关联的快捷菜单的资源 ID。|
|[CMFCToolbar编辑盒按钮：：设置平压模式](#setflatmode)|指定应用程序中编辑框按钮的平面样式外观。|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar编辑盒按钮：：设置样式](#setstyle)|指定按钮的样式。 （覆盖[CMFC 工具栏按钮：：设置样式](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).）|

## <a name="remarks"></a>备注

要向工具栏添加编辑框按钮，请按照以下步骤操作：

1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。

2. 构造`CMFCToolBarEditBoxButton`对象。

3. 在处理AFX_WM_RESETTOOLBAR消息的消息处理程序中，使用[CMFCToolBar：：：替换Button，](../../mfc/reference/cmfctoolbar-class.md#replacebutton)将虚拟按钮替换为新的组合框按钮。

有关详细信息，请参阅[演练：将控件放在工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCToolBarEditBoxButton` 类中的各种方法。 该示例演示如何指定用户可以在自定义期间拉伸按钮，指定在用户单击按钮时显示按钮的边框，在文本框控件中设置文本，指定应用程序中编辑框按钮的平面样式外观，以及指定工具栏编辑框控件的样式。

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>要求

**标题：** afxtoolbar编辑盒按钮.h

## <a name="cmfctoolbareditboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolbar编辑盒按钮：：可以拉伸

指定用户是否可以在自定义期间拉伸按钮。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>返回值

此方法返回 TRUE。

### <a name="remarks"></a>备注

默认情况下，框架不允许用户在自定义期间拉伸工具栏按钮。 此方法通过允许用户在自定义期间拉伸编辑框工具栏按钮来扩展基类实现[（CMFCToolBarButton：：：CanBe拉伸](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)）。

## <a name="cmfctoolbareditboxbuttoncmfctoolbareditboxbutton"></a><a name="cmfctoolbareditboxbutton"></a>CMFCToolbar编辑盒按钮：CMFC工具栏编辑箱按钮

构造[CMFCToolBar 编辑BoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)对象。

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[在]指定控件 ID。

*i图像*<br/>
[在]指定工具栏图像的零基索引。 图像位于[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)维护的[CMFCToolBar 图像类](../../mfc/reference/cmfctoolbarimages-class.md)对象中。

*dwStyle*<br/>
[在]指定编辑控件样式。

*iWidth*<br/>
[在]指定编辑控件的宽度（以像素为单位）。

### <a name="remarks"></a>备注

默认构造函数将编辑控件样式设置为以下组合：

WS_CHILD |WS_VISIBLE |ES_AUTOHSCROLL

控件的默认宽度为 150 像素。

## <a name="cmfctoolbareditboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolbar编辑盒按钮：：抄袭

将另一个工具栏按钮的属性复制到当前按钮。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[在]对要从中复制的源按钮的引用。

### <a name="remarks"></a>备注

调用此方法以将另一个工具栏按钮复制到此工具栏按钮。 *src*必须是 类型的`CMFCToolBarEditBoxButton`。

## <a name="cmfctoolbareditboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolbar编辑盒按钮：：创建编辑

在按钮中创建新的编辑控件。

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指定编辑控件的父窗口。 值不得为 NULL。

*矩形*<br/>
[在]指定编辑控件的大小和位置。

### <a name="return-value"></a>返回值

指向新创建的编辑控件的指针;如果控件的创建和附件失败，则为 NULL。

### <a name="remarks"></a>备注

分两步`CMFCToolBarEditBoxButton`构造对象。 首先调用构造函数，然后调用`CreateEdit`，这将创建 Windows 编辑控件并将其附加到`CMFCToolBarEditBoxButton`对象。

## <a name="cmfctoolbareditboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolbar编辑盒按钮：：获取

检索应用程序中具有指定`CMFCToolBarEditBoxButton`命令 ID 的第一个对象。

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]要检索的按钮的命令 ID。

### <a name="return-value"></a>返回值

应用程序中的第`CMFCToolBarEditBoxButton`一个对象具有指定的命令 ID，如果不存在此类对象，则为 NULL。

### <a name="remarks"></a>备注

此共享实用程序方法由以下方法使用，例如[CMFCToolBarEditBoxButton：SetContentsAll](#setcontentsall)和[CMFCToolBarEditBoxButton：获取内容所有](#getcontentsall)来设置或获取具有指定命令 ID 的第一个编辑框工具栏控件的文本。

## <a name="cmfctoolbareditboxbuttongetcontentsall"></a><a name="getcontentsall"></a>CMFCToolbar编辑盒按钮：：获取内容所有

检索具有指定命令 ID 的第一个编辑框工具栏控件的文本。

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]要从中检索内容的按钮的命令 ID。

### <a name="return-value"></a>返回值

包含`CString`具有指定命令 ID 的第一个编辑框工具栏控件的文本的对象。

### <a name="remarks"></a>备注

如果没有`CMFCToolBarEditBoxButton`对象具有指定的命令 ID，此方法将返回空字符串。

## <a name="cmfctoolbareditboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolbar编辑盒按钮：：获取上下文菜单ID

检索与按钮关联的快捷菜单的资源 ID。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>返回值

与按钮关联的快捷菜单的资源 ID;如果按钮没有关联的快捷菜单，则为 0。

### <a name="remarks"></a>备注

当用户右键单击按钮时，框架使用资源 ID 创建快捷菜单。

## <a name="cmfctoolbareditboxbuttongeteditborder"></a><a name="geteditborder"></a>CMFCToolbar编辑盒按钮：：获取编辑边框

检索编辑框按钮编辑部分的边界矩形。

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>参数

*rectBorder*<br/>
[出]对接收边界矩形`CRect`的对象的引用。

### <a name="remarks"></a>备注

此方法检索客户端坐标中编辑控件的边界矩形。 它将每个方向上的矩形大小扩展一个像素。

`CMFCToolBarEditBoxButton` [CMFCVisualManager：在绘制对象周围的边框时，OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder)方法调用此方法。

## <a name="cmfctoolbareditboxbuttongeteditbox"></a><a name="geteditbox"></a>CMFCToolbar编辑盒按钮：：获取编辑框

返回指向嵌入在按钮中的[CEdit 类](../../mfc/reference/cedit-class.md)控件的指针。

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>返回值

指向按钮包含[的 CEdit 类](../../mfc/reference/cedit-class.md)控件的指针。 如果尚未创建控件，`CEdit`则为 NULL。

### <a name="remarks"></a>备注

您可以通过调用`CEdit`[CMFCToolBar 编辑BoxButton来创建控件：创建编辑](#createedit)。

## <a name="cmfctoolbareditboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBar编辑盒按钮：：获取Hwnd

检索与工具栏按钮关联的窗口句柄。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>返回值

与按钮关联的窗口句柄。

### <a name="remarks"></a>备注

此方法通过返回编辑框按钮的编辑控件部分的窗口句柄来覆盖[CMFCToolBarButton：：GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。

## <a name="cmfctoolbareditboxbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a>CMFCToolbar编辑盒按钮：：获得验证

检索必须重绘的按钮的工作区区域。

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>返回值

指定`CRect`必须重绘的区域的对象。

### <a name="remarks"></a>备注

此方法通过在区域中包括文本标签的区域来扩展基类实现[CMFCToolBarButton：：获取验证Rect。](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)

## <a name="cmfctoolbareditboxbuttonhavehotborder"></a><a name="havehotborder"></a>CMFCToolbar编辑盒按钮：：有热边框

确定当用户单击该按钮时是否显示按钮的边框。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>返回值

如果按钮在选定时显示其边框，则非零;否则 0。

### <a name="remarks"></a>备注

此方法通过在控件可见时返回非零值来扩展基类实现[CMFCToolBarButton：：HaveHotBorder。](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)

## <a name="cmfctoolbareditboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolbar编辑盒按钮：：是平模式

确定编辑框按钮是否具有平面样式。

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>返回值

如果按钮具有平面样式，则非零;否则，0。

### <a name="remarks"></a>备注

默认情况下，编辑框按钮具有平面样式。 使用[CMFCToolBar 编辑BoxButton：SetFlatMode](#setflatmode)方法来更改应用程序的平面样式外观。

## <a name="cmfctoolbareditboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolbar编辑盒按钮：：通知命令

指定按钮是否处理[WM_COMMAND](/windows/win32/menurc/wm-command)消息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>参数

*iNotify代码*<br/>
[在]与命令关联的通知消息。

### <a name="return-value"></a>返回值

如果按钮处理WM_COMMAND消息，则为 TRUE，或 FALSE 指示该消息必须由父工具栏处理。

### <a name="remarks"></a>备注

当此方法要向父窗口发送[WM_COMMAND](/windows/win32/menurc/wm-command)消息时，框架将调用此方法。

此方法通过处理[EN_UPDATE](/windows/win32/Controls/en-update)通知来扩展基类实现 （ [CMFCToolBarButton：：通知命令](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)）。 对于每个具有相同对象命令 ID 的编辑框，它将其文本标签设置为此对象的文本标签。

## <a name="cmfctoolbareditboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolbar编辑盒按钮：：在"添加"上自定义页面

将按钮添加到 **"自定义"** 对话框时由框架调用。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>备注

此方法通过从具有与此对象具有相同命令 ID 的任何工具栏中的编辑框控件中的属性复制来扩展基类实现 （ [CMFCToolBarButton：：：onAddTo自定义页](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)）。 如果没有工具栏具有与此对象具有相同命令 ID 的编辑框控件，则此方法不执行任何操作。

有关 **"自定义"** 对话框的详细信息，请参阅[CMFCToolBars 自定义对话框类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

## <a name="cmfctoolbareditboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolbar编辑盒按钮：：打开更改家长

将按钮插入到新工具栏时由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向新父窗口的指针。

### <a name="remarks"></a>备注

此方法通过重新创建内部`CEdit`对象来重写基类实现 （ [CMFCToolBarButton：：onChangeParentwnd）。](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)

## <a name="cmfctoolbareditboxbuttononclick"></a><a name="onclick"></a>CMFCToolbar编辑盒按钮：：点击

当用户单击鼠标按钮时由框架调用。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]闲置。

*bDelay*<br/>
[在]闲置。

### <a name="return-value"></a>返回值

如果按钮处理单击消息，则非零;否则 0。

### <a name="remarks"></a>备注

此方法通过在内部`CEdit`对象可见时返回非零值来覆盖基类实现[（CMFCToolBarButton：：OnClick）。](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)

## <a name="cmfctoolbareditboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolbar编辑盒按钮：：在CtlColor上

当父工具栏处理WM_CTLCOLOR消息时，框架调用。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]显示按钮的设备上下文。

*nCtlColor*<br/>
[在]闲置。

### <a name="return-value"></a>返回值

全局窗口画笔的句柄。

### <a name="remarks"></a>备注

此方法通过分别将所提供的设备上下文的文本和背景颜色分别设置为全局文本和背景颜色来覆盖基类实现[（CMFCToolBarButton：：onCtlColor）。](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)

有关应用程序可用的全局选项的详细信息，请参阅[AFX_GLOBAL_DATA结构](../../mfc/reference/afx-global-data-structure.md)。

## <a name="cmfctoolbareditboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolbar编辑盒按钮：：在全局字体上更改

当全局字体已更改时由框架调用。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>备注

此方法通过将控件的字体更改为全局字体来扩展基类实现 （ [CMFCToolBarButton：：onGlobalFonts 已更改](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)）。

有关应用程序可用的全局选项的详细信息，请参阅[AFX_GLOBAL_DATA结构](../../mfc/reference/afx-global-data-structure.md)。

## <a name="cmfctoolbareditboxbuttononmove"></a><a name="onmove"></a>CMFCToolbar编辑盒按钮：：移动

当父工具栏移动时由框架调用。

```
virtual void OnMove();
```

### <a name="remarks"></a>备注

此方法通过更新内部`CEdit`对象的位置来覆盖默认类实现 （ [CMFCToolBarButton：：onMove）](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)

## <a name="cmfctoolbareditboxbuttononshow"></a><a name="onshow"></a>CMFCToolbar编辑盒按钮：：上展

当按钮变得可见或不可见时，由框架调用。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
[在]指定按钮是否可见。 如果此参数为 TRUE，则按钮为可见。 否则，该按钮不可见。

### <a name="remarks"></a>备注

此方法通过显示按钮（如果*bShow*为 TRUE）来扩展基类实现 （ [CMFCToolBarButton：：onShow）。](../../mfc/reference/cmfctoolbarbutton-class.md#onshow) 否则，此方法将隐藏该按钮。

## <a name="cmfctoolbareditboxbuttononsize"></a><a name="onsize"></a>CMFCToolbar编辑盒按钮：：打开尺寸

当父工具栏更改其大小或位置且此更改导致按钮更改大小时，框架调用该按钮。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>参数

*iSize*<br/>
[在]按钮的新宽度（以像素为单位）。

### <a name="remarks"></a>备注

此方法通过更新内部`CEdit`对象的大小和位置来覆盖默认类实现[CMFCToolBarButton：：onSize。](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)

## <a name="cmfctoolbareditboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolbar编辑盒按钮：：更新工具提示

当父工具栏更新其工具提示文本时，由框架调用。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]闲置。

*iButtonIndex*<br/>
[在]闲置。

*wndToolTip*<br/>
[在]显示工具提示文本的控件。

*Str*<br/>
[出]接收`CString`更新的工具提示文本的对象。

### <a name="return-value"></a>返回值

如果方法更新工具提示文本，则非零;否则 0。

### <a name="remarks"></a>备注

此方法通过显示与按钮的编辑部分关联的工具提示文本来扩展基类实现[（CMFCToolBarButton：：onUpdateToolTip）。](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip) 如果内部`CEdit`对象为 NULL 或`CEdit`对象的窗口句柄未标识现有窗口，则此方法不执行任何操作并返回 FALSE。

## <a name="cmfctoolbareditboxbuttonsetcontents"></a><a name="setcontents"></a>CMFCToolbar编辑盒按钮：：设置内容

设置文本框控件中的文本。

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>参数

*内容*<br/>
[在]指定要设置的新文本。

## <a name="cmfctoolbareditboxbuttonsetcontentsall"></a><a name="setcontentsall"></a>CMFCToolbar编辑盒按钮：：设置内容所有

查找具有指定命令 ID 并在其文本框中设置指定文本的[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)对象。

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]指定要为其更改文本的控件的命令 ID。

*斯特里特*<br/>
[在]指定要设置的新文本。

### <a name="return-value"></a>返回值

设置文本时非零;如果具有指定`CMFCToolBarEditBoxButton`命令 ID 的控件不存在，则为 0。

## <a name="cmfctoolbareditboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolbar编辑盒按钮：：设置上下文菜单ID

指定与按钮关联的快捷菜单的资源 ID。

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]快捷菜单的资源 ID。

### <a name="remarks"></a>备注

当用户右键单击工具栏按钮时，框架使用资源 ID 创建快捷菜单。

## <a name="cmfctoolbareditboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolbar编辑盒按钮：：设置平压模式

指定应用程序中编辑框按钮的平面样式外观。

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>参数

*bFlat*<br/>
[在]编辑框按钮的平面样式。 如果此参数为 TRUE，则启用平面样式外观;如果此参数为 TRUE，则启用平面样式外观。否则，平面样式外观将禁用。

### <a name="remarks"></a>备注

编辑框按钮的默认平面样式为 TRUE。 使用[CMFCToolBar 编辑BoxButton：isFlatMode](#isflatmode)方法检索应用程序的平面样式外观。

## <a name="cmfctoolbareditboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolbar编辑盒按钮：：设置样式

指定工具栏编辑框控件的样式。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>参数

*nStyle*<br/>
[在]要设置的新样式。

### <a name="remarks"></a>备注

此方法将[CMFCToolBarButton：：m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)设置为*nStyle*当应用程序处于自定义模式时，它还禁用文本框，并在应用程序未处于自定义模式时启用它（请参阅[CMFCToolBar：set自定义模式](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode)和[CMFCToolBar：：是自定义模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)）。 有关有效样式标志的列表，请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC工具栏按钮类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CMFC工具栏：更换按钮](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
