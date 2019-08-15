---
title: CMFCToolBarDateTimeCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
ms.openlocfilehash: 7ab6a240a403e70446ebc1860474f6cb9e1d71e3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504761"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl 类

包含日期和时间选取器控件的工具栏按钮。

## <a name="syntax"></a>语法

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|构造 `CMFCToolBarDateTimeCtrl` 对象。|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|指定用户是否可以在自定义过程中拉伸该按钮。 (重写[CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)。)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。 (重写[CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|留待将来使用。|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|将文本从工具栏按钮复制到菜单。|
|`CMFCToolBarDateTimeCtrl::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|检索应用程序`CMFCToolBarDateTimeCtrl`中具有指定命令 ID 的第一个对象。|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|返回指向日期和时间选取器控件的指针。|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|检索与工具栏按钮关联的窗口句柄。 (重写[CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)。)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|从日期和时间选取器控件获取所选时间, 并将其放在指定的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构中。|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|从具有指定命令 ID 的时间选取器控件按钮返回所选时间。|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|确定当用户选择按钮时是否显示按钮的边框。 (重写[CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|指定按钮是否处理[WM_COMMAND](/windows/win32/menurc/wm-command)消息。 (重写[CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)。)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|在将按钮添加到 "**自定义**" 对话框时由框架调用。 (重写[CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|由框架调用, 用于计算指定设备上下文和停靠状态的按钮大小。 (重写[CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|在将按钮插入新工具栏时由框架调用。 (重写[CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|当用户单击控件时由框架调用。 (重写[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|当父工具栏处理 WM_CTLCOLOR 消息时由框架调用。 (重写[CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|由框架调用, 用于通过使用指定的样式和选项绘制按钮。 (重写[CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|由框架调用, 用于绘制 "**自定义**" 对话框的 "**命令**" 窗格中的按钮。 (重写[CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|当全局字体已更改时由框架调用。 (重写[CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)。)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|当父工具栏移动时由框架调用。 (重写[CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)。)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|当按钮变为可见或不可见时由框架调用。 (重写[CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)。)|
|`CMFCToolBarDateTimeCtrl::OnSize`|当父工具栏更改其大小或位置并且此更改导致按钮更改大小时, 由框架调用。 (重写[CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|当父工具栏更新其工具提示文本时由框架调用。 (重写[CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)。)|
|`CMFCToolBarDateTimeCtrl::Serialize`|从存档中读取此对象或将其写入存档, (重写[CMFCToolBarButton:: 串行化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|设置工具栏按钮的样式。 (重写[CMFCToolBarButton:: system.windows.forms.control.setstyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|设置时间选取器控件中的时间和日期。|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|设置具有指定命令 ID 的时间选取器控件的所有实例中的时间和日期。|

## <a name="remarks"></a>备注

有关如何使用日期和时间选取器控件的示例, 请参阅 ToolbarDateTimePicker 示例项目。 有关如何向工具栏添加控件按钮的详细信息, 请[参阅演练:将控件放置在](../../mfc/walkthrough-putting-controls-on-toolbars.md)工具栏上。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>要求

**标头:** afxtoolbardatetimectrl

##  <a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched

指定用户是否可以在自定义过程中拉伸该按钮。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>返回值

此方法返回 TRUE。

### <a name="remarks"></a>备注

默认情况下, 框架不允许用户在自定义过程中拉伸工具栏按钮。 此方法通过允许用户在自定义过程中拉伸日期和时间工具栏按钮来扩展基类实现 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched))。

##  <a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

创建并初始化[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)对象。

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>参数

*uiID*<br/>
中控件 ID。

*iImage*<br/>
中工具栏的`CMFCToolBarImages`对象中的图像的索引。

*dwStyle*<br/>
中用户单击按钮时`CMFCToolBarDateTimeCtrlImpl`创建的窗口的样式。

*iWidth*<br/>
中控件的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

此对象将初始化为系统日期和时间。 内部`CMFCToolBarDateTimeCtrlImpl`对象的窗口样式包括*dwStyle*参数和 WS_CHILD 和 WS_VISIBLE 样式。 不能使用`CMFCToolBarDateTimeCtrl::SetStyle`更改这些样式。 用于`SetStyle`更改`CMFCToolBarDateTimeCtrl`控件的样式。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCToolBarDateTimeCtrl`类的对象。 此代码片段是[工具栏日期时间选取器示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCToolBarDateTimeCtrl:: CopyFrom

将另一个工具栏按钮的属性复制到当前按钮。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
中对要从中进行复制的源按钮的引用。

### <a name="remarks"></a>备注

调用此方法可将另一个工具栏按钮复制到此工具栏按钮。 *src*的类型`CMFCToolBarDateTimeCtrl`必须为。

##  <a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton

将文本从工具栏按钮复制到菜单。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>参数

*menuButton*<br/>
中对 "目标" 菜单按钮的引用。

### <a name="return-value"></a>返回值

此方法返回 TRUE。

### <a name="remarks"></a>备注

此方法通过加载与控件的命令 ID 相关联的字符串资源来重写基类实现 ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton))。 有关字符串资源的详细信息, 请参阅[CStringT:: LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)。

##  <a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd

检索应用程序`CMFCToolBarDateTimeCtrl`中具有指定命令 ID 的第一个对象。

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中要检索的按钮的命令 ID。

### <a name="return-value"></a>返回值

应用程序`CMFCToolBarDateTimeCtrl`中具有指定命令 id 的第一个对象, 如果没有`CMFCToolBarDateTimeCtrl`指定的命令 id, 则为 NULL。

### <a name="remarks"></a>备注

此共享实用工具方法由[CMFCToolBarDateTimeCtrl:: SetTimeAll](#settimeall)和[CMFCToolBarDateTimeCtrl:: GetTimeAll](#gettimeall)等方法用来设置或获取具有指定命令 ID 的时间选取器控件的所有实例的时间和日期。

##  <a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

返回指向日期和时间选取器控件的指针。

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>返回值

指向 date 和 time 选取器控件的指针;如果该控件不存在, 则为 NULL。

### <a name="remarks"></a>备注

向`CMFCToolBarDateTimeCtrl`工具栏中插入`m_pWndDateTime` `CMFCToolBarDateTimeCtrl`对象时, 类将初始化数据成员。

##  <a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd

检索与工具栏按钮关联的窗口句柄。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>返回值

与 "日期和时间" 工具栏按钮关联的窗口句柄。

### <a name="remarks"></a>备注

此方法重写[CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。

##  <a name="gettime"></a>CMFCToolBarDateTimeCtrl:: GetTime

从关联的日期和时间选取器控件获取所选时间, 并将其放在指定的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构中

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>参数

*timeDest*<br/>
弄在第一个重载中, 是将接收系统时间信息的[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象。 在第二个重载中, 将接收系统时间信息的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。

*pTimeDest*<br/>
弄指向用于接收系统时间信息的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针。 不得为 NULL。

### <a name="return-value"></a>返回值

在第一个重载中, 如果成功将时间写入[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象, 则为非零值;否则为0。 在第二个和第三个重载中, 返回值是等于在[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)结构中设置的 dwFlag 成员的 DWORD。

### <a name="remarks"></a>备注

方法设置[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)结构成员 dwFlags, 以指示日期和时间选取器是否设置为日期和时间。 如果该值等于 GDT_NONE, 则将控件设置为`no date` status, 并使用 DTS_SHOWNONE 样式。 如果返回的值等于 GDT_VALID, 则系统时间已成功存储在目标位置。

##  <a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll

返回用户从具有指定命令 ID 的时间选取器控件按钮中选择的时间。

```
static BOOL GetTimeAll(
    UINT uiCmd,
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeDest);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中指定工具栏按钮的命令 ID。

*timeDest*<br/>
弄在第一个重载中, 是将接收系统时间信息的[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象。 在第二个重载中, 将接收系统时间信息的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。

*pTimeDest*<br/>
弄指向用于接收系统时间信息的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针。 不得为 NULL。

### <a name="return-value"></a>返回值

如果框架找不到与命令 ID *uiCmd*匹配的工具栏按钮, 则在第一个重载中返回值为零, 在其他重载中为 GDT_NONE。 如果找到工具栏按钮, 则返回值与该按钮上对[CMFCToolBarDateTimeCtrl:: GetTime](#gettime)的调用中的返回值相同。 如果找到了按钮, 则返回值为零或 GDT_NONE, 这表示对的调用`GetTime`未返回有效日期, 原因可能是某个其他原因。

### <a name="remarks"></a>备注

此方法查找具有指定命令 ID 的工具栏按钮, 并对该按钮调用[CMFCToolBarDateTimeCtrl:: GetTime](#gettime)方法。

##  <a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder

确定当用户选择按钮时是否显示按钮的边框。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>返回值

如果按钮在选中时显示其边框, 则为非零;否则为0。

### <a name="remarks"></a>备注

如果该控件可见, 此方法将返回一个非零值。

##  <a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand

指定按钮是否处理[WM_COMMAND](/windows/win32/menurc/wm-command)消息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>参数

*iNotifyCode*<br/>
中与命令关联的通知消息。

### <a name="return-value"></a>返回值

如果该按钮处理 WM_COMMAND 消息, 则为 TRUE; 如果为 FALSE, 则指示应由父工具栏处理该消息。

### <a name="remarks"></a>备注

当框架即将向父窗口发送[WM_COMMAND](/windows/win32/menurc/wm-command)消息时, 框架会调用此方法。

此方法通过处理[DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange)通知扩展基类实现 ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand))。 它更新内部时间状态, 并更新具有相同命令 ID 的`CMFCToolBarDateTimeCtrl`所有对象的时间属性。

##  <a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

在将按钮添加到 "**自定义**" 对话框时由框架调用。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>备注

此方法通过从与此对象具有相同命令 ID 的任何工具栏中的第一个 "日期和时间" 控件中复制属性, 来扩展基类实现[CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。 如果没有具有与此对象相同的命令 ID 的 "日期和时间" 控件, 则此方法不执行任何操作。

有关 "**自定义**" 对话框的详细信息, 请参阅[CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

##  <a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

在将按钮插入新工具栏时由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中新的父窗口。

### <a name="remarks"></a>备注

此方法通过重新创建内部`CMFCToolBarDateTimeCtrlImpl`对象来重写基类实现 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd))。

##  <a name="onclick"></a>CMFCToolBarDateTimeCtrl:: OnClick

当用户单击控件时由框架调用。

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

此方法通过返回非零值 (如果内部`CMFCToolBarDateTimeCtrlImpl`对象可见) 来重写基类实现[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。

##  <a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor

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

框架用于绘制按钮背景的全局画笔的句柄。

### <a name="remarks"></a>备注

此方法重写基类实现[CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), 方法是将所提供的设备上下文的文本和背景色分别设置为全局文本和背景色。

有关可用于应用程序的全局选项的详细信息, 请参阅[AFX_GLOBAL_DATA 结构](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

当全局字体已更改时由框架调用。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>备注

此方法通过将控件的字体更改为全局字体的字体来扩展基类实现 ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged))。

有关可用于应用程序的全局选项的详细信息, 请参阅[AFX_GLOBAL_DATA 结构](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove

当父工具栏移动时由框架调用。

```
virtual void OnMove();
```

### <a name="remarks"></a>备注

此方法通过更新内部`CMFCToolBarDateTimeCtrlImpl`对象的位置来重写默认类实现 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove))。

##  <a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow

当按钮变为可见或不可见时由框架调用。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
中指定按钮是否可见。 如果此参数为 TRUE, 则该按钮可见。 否则, 该按钮将不可见。

### <a name="remarks"></a>备注

如果*bShow*为 TRUE, 则此方法将通过显示该按钮来扩展基类实现 ( [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow))。 否则, 此方法将隐藏按钮。

##  <a name="onsize"></a>CMFCToolBarDateTimeCtrl:: OnSize

当父工具栏更改其大小或位置并且此更改导致按钮更改大小时, 由框架调用。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>参数

*iSize*<br/>
中按钮的新宽度 (以像素为单位)。

### <a name="remarks"></a>备注

此方法通过更新内部`CMFCToolBarDateTimeCtrlImpl`对象的大小和位置来重写默认类实现 ( [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize))。

##  <a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip

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
中父窗口。

*iButtonIndex*<br/>
中父按钮集合中的按钮的从零开始的索引。

*wndToolTip*<br/>
中用于显示工具提示文本的控件。

*str*<br/>
弄一个`CString`对象, 它接收更新的工具提示文本。

### <a name="return-value"></a>返回值

如果方法更新工具提示文本, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此方法通过显示与按钮关联的工具提示文本来扩展基类实现 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip))。 如果该按钮未水平停靠, 则此方法不执行任何操作并返回 FALSE。

##  <a name="settime"></a>CMFCToolBarDateTimeCtrl:: SetTime

设置时间选取器控件中的时间和日期。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>参数

*timeNew*<br/>
中在第一个版本中, 是对[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用, 该对象包含将设置控件的时间。 在第二个版本中, 是指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针, 该对象包含将设置控件的时间。

*pTimeNew*<br/>
中指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该结构包含将设置控件的时间。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

通过调用[CDateTimeCtrl:: SetTime](../../mfc/reference/cdatetimectrl-class.md#settime)设置日期和时间选取器控件中的时间。

##  <a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll

设置具有指定命令 ID 的时间选取器控件的所有实例中的时间和日期。

```
static BOOL SetTimeAll(
    UINT uiCmd,
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中指定工具栏按钮的命令 ID。

*timeNew*<br/>
中在第一个版本中, 是一个[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象, 它包含将设置控件的时间。 在第二个版本中, 是指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针, 该对象包含将设置控件的时间。

*pTimeNew*<br/>
中指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该结构包含将设置控件的时间。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

查找具有指定命令 ID 的工具栏按钮, 并通过调用[CMFCToolBarDateTimeCtrl:: SetTime](#settime)在日期和时间选取器控件中设置时间。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[演练：将控件添加到工具栏](../../mfc/walkthrough-putting-controls-on-toolbars.md)
