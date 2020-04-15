---
title: CMFCToolBarDatetimeCtrl 类
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
ms.openlocfilehash: 9aebd55f19a6687554d8d8378ef84ed5932025a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372179"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDatetimeCtrl 类

包含日期和时间选取器控件的工具栏按钮。

## <a name="syntax"></a>语法

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCToolBarDatetimeCtrl：：CMFCToolBarDatetimeCtrl](#cmfctoolbardatetimectrl)|构造 `CMFCToolBarDateTimeCtrl` 对象。|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCToolBarDatetimeCtrl：：可以拉伸](#canbestretched)|指定用户是否可以在自定义期间拉伸按钮。 （覆盖[CMFC 工具栏按钮：：可以拉伸](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).）|
|[CMFCToolBarDatetimectrl：：从](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。 （覆盖[CMFCToolBar 按钮：：从](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)复制。）|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|保留供将来使用。|
|[CMFC工具栏按钮：：导出到菜单按钮](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|将工具栏按钮中的文本复制到菜单。|
|`CMFCToolBarDateTimeCtrl::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCToolBarDatetimectrl：：GetByCmd](#getbycmd)|检索应用程序中具有指定`CMFCToolBarDateTimeCtrl`命令 ID 的第一个对象。|
|[CMFCToolBarDatetimeCtrl：：获取DatetimeCtrl](#getdatetimectrl)|返回指向日期和时间选取器控件的指针。|
|[CMFCToolBarDatetimeCtrl：：GetHwnd](#gethwnd)|检索与工具栏按钮关联的窗口句柄。 （覆盖[CMFCToolBarButton：获取 Hwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).）|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCToolBarDatetimeCtrl：：获取时间](#gettime)|从日期和时间选取器控件获取所选时间，并将其放入指定的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构中。|
|[CMFCToolBarDatetimeCtrl：获取时间所有](#gettimeall)|从具有指定命令 ID 的时间选取器控制按钮返回所选时间。|
|[CMFCToolBarDatetimeCtrl：：有热边界](#havehotborder)|确定当用户选择该按钮时是否显示按钮的边框。 （覆盖[CMFCToolBar 按钮：：有 Hot 边框](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).）|
|[CMFCToolBarDatetimeCtrl：：通知命令](#notifycommand)|指定按钮是否处理[WM_COMMAND](/windows/win32/menurc/wm-command)消息。 （覆盖[CMFCToolBar 按钮：通知命令](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).）|
|[CMFCToolbardatetimectrl：：在Addto自定义页面上](#onaddtocustomizepage)|将按钮添加到 **"自定义"** 对话框时由框架调用。 （覆盖[CMFC 工具栏按钮：：在 Addto 自定义页](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).）|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|由框架调用，以计算指定设备上下文和停靠状态的按钮大小。 （覆盖[CMFC 工具栏按钮："正在计算大小](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)"）|
|[CMFCToolBarDatetimectrl：：在更改家长](#onchangeparentwnd)|将按钮插入到新工具栏时由框架调用。 （覆盖[CMFC 工具栏按钮：打开更改父项](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).）|
|[CMFCToolBarDatetimectrl：：点击](#onclick)|当用户单击控件时由框架调用。 （覆盖[CMFC 工具栏按钮：：单击](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).）|
|[CMFCToolBarDatetimectrl：onCtlColor](#onctlcolor)|当父工具栏处理WM_CTLCOLOR消息时，框架调用。 （覆盖[CMFCToolBar 按钮：OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).）|
|`CMFCToolBarDateTimeCtrl::OnDraw`|框架调用使用指定的样式和选项绘制按钮。 （覆盖[CMFC 工具栏按钮：：OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).）|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|由框架调用以在 **"自定义"** 对话框的 **"命令"** 窗格中绘制按钮。 （覆盖[CMFC 工具栏按钮：在"绘制"自定义列表](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).）|
|[CMFCToolBarDatetimectrl：：在全局字体上更改](#onglobalfontschanged)|当全局字体已更改时由框架调用。 （覆盖[CMFC 工具栏按钮：：在全局字体更改](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).）|
|[CMFCToolBarDatetimectrl：：移动](#onmove)|当父工具栏移动时由框架调用。 （覆盖[CMFC 工具栏按钮：：打开](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)移动 .）|
|[CMFCToolBarDatetimectrl：：上展](#onshow)|当按钮变得可见或不可见时，由框架调用。 （覆盖[CMFCToolBar 按钮：：在显示](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).）|
|`CMFCToolBarDateTimeCtrl::OnSize`|当父工具栏更改其大小或位置且此更改导致按钮更改大小时，框架调用该按钮。 （覆盖[CMFC 工具栏按钮：：打开大小](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).）|
|[CMFCToolBarDatetimectrl：：打开更新工具提示](#onupdatetooltip)|当父工具栏更新其工具提示文本时，由框架调用。 （覆盖[CMFC 工具栏按钮：打开更新工具提示](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).）|
|`CMFCToolBarDateTimeCtrl::Serialize`|从存档中读取此对象或将其写入存档（覆盖[CMFCToolBarButton：：序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。|
|`CMFCToolBarDateTimeCtrl::SetStyle`|设置工具栏按钮的样式。 （覆盖[CMFC 工具栏按钮：：设置样式](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).）|
|[CMFCToolBarDatetimeCtrl：：设置时间](#settime)|设置时间选取器控件中的时间和日期。|
|[CMFCToolBarDatetimeCtrl：：设置时间所有](#settimeall)|设置具有指定命令 ID 的时间选取器控件的所有实例中的时间和日期。|

## <a name="remarks"></a>备注

有关如何使用日期和时间选取器控件的示例，请参阅工具栏DateTimePicker示例项目。 有关如何向工具栏添加控制按钮的信息，请参阅[演练：将控件放在工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDatetimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>要求

**标题：** afxtoolbardatetimectrl.h

## <a name="cmfctoolbardatetimectrlcanbestretched"></a><a name="canbestretched"></a>CMFCToolBarDatetimeCtrl：：可以拉伸

指定用户是否可以在自定义期间拉伸按钮。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>返回值

此方法返回 TRUE。

### <a name="remarks"></a>备注

默认情况下，框架不允许用户在自定义期间拉伸工具栏按钮。 此方法通过允许用户在自定义期间拉伸日期和时间工具栏按钮来扩展基类实现[（CMFCToolBarButton：：：CanBe拉伸](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)）。

## <a name="cmfctoolbardatetimectrlcmfctoolbardatetimectrl"></a><a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDatetimeCtrl：：CMFCToolBarDatetimeCtrl

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
[在]控件 ID。

*i图像*<br/>
[在]工具栏对象中图像的`CMFCToolBarImages`索引。

*dwStyle*<br/>
[在]当用户单击按钮时`CMFCToolBarDateTimeCtrlImpl`创建的窗口样式。

*iWidth*<br/>
[在]控件的宽度（以像素为单位）。

### <a name="remarks"></a>备注

此对象将初始化到系统日期和时间。 内部`CMFCToolBarDateTimeCtrlImpl`对象的窗口样式包括*dwStyle*参数以及WS_CHILD和WS_VISIBLE样式。 不能通过使用`CMFCToolBarDateTimeCtrl::SetStyle`来更改这些样式。 用于`SetStyle`更改控件的`CMFCToolBarDateTimeCtrl`样式。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCToolBarDateTimeCtrl`类的对象。 此代码段是[工具栏日期时间选取器示例的一](../../overview/visual-cpp-samples.md)部分。

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

## <a name="cmfctoolbardatetimectrlcopyfrom"></a><a name="copyfrom"></a>CMFCToolBarDatetimectrl：：从

将另一个工具栏按钮的属性复制到当前按钮。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[在]对要从中复制的源按钮的引用。

### <a name="remarks"></a>备注

调用此方法以将另一个工具栏按钮复制到此工具栏按钮。 *src*必须是 类型的`CMFCToolBarDateTimeCtrl`。

## <a name="cmfctoolbardatetimectrlexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolbardatetimectrl：：导出到菜单按钮

将工具栏按钮中的文本复制到菜单。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>参数

*菜单按钮*<br/>
[在]对目标菜单按钮的引用。

### <a name="return-value"></a>返回值

此方法返回 TRUE。

### <a name="remarks"></a>备注

此方法通过加载与控件的命令 ID 关联的字符串资源来覆盖基类实现[（CMFCToolBarButton：：exportToMenuButton）。](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton) 有关字符串资源的详细信息，请参阅[CStringT：：LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)。

## <a name="cmfctoolbardatetimectrlgetbycmd"></a><a name="getbycmd"></a>CMFCToolBarDatetimectrl：：GetByCmd

检索应用程序中具有指定`CMFCToolBarDateTimeCtrl`命令 ID 的第一个对象。

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]要检索的按钮的命令 ID。

### <a name="return-value"></a>返回值

应用程序中具有`CMFCToolBarDateTimeCtrl`指定命令 ID 的第一个对象，如果没有`CMFCToolBarDateTimeCtrl`对象具有指定的命令 ID，则为 NULL。

### <a name="remarks"></a>备注

此共享实用程序方法由以下方法使用，例如[CMFCToolBarDateTimeCtrl：SetTimeAll](#settimeall)和[CMFCToolBarDateTimeCtrl：GetTimeAll](#gettimeall)用于设置或获取具有指定命令 ID 的时间选取器控件的所有实例的时间和日期。

## <a name="cmfctoolbardatetimectrlgetdatetimectrl"></a><a name="getdatetimectrl"></a>CMFCToolBarDatetimeCtrl：：获取DatetimeCtrl

返回指向日期和时间选取器控件的指针。

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>返回值

指向日期和时间选取器控件的指针;或 NULL，如果控件不存在。

### <a name="remarks"></a>备注

当您`CMFCToolBarDateTimeCtrl`将对象插入工具栏时`m_pWndDateTime`，`CMFCToolBarDateTimeCtrl`类将初始化数据成员。

## <a name="cmfctoolbardatetimectrlgethwnd"></a><a name="gethwnd"></a>CMFCToolBarDatetimeCtrl：：GetHwnd

检索与工具栏按钮关联的窗口句柄。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>返回值

与日期和时间工具栏按钮关联的窗口句柄。

### <a name="remarks"></a>备注

此方法重写[CMFCToolBarButton：getHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。

## <a name="cmfctoolbardatetimectrlgettime"></a><a name="gettime"></a>CMFCToolBarDatetimeCtrl：：获取时间

从关联的日期和时间选取器控件获取所选时间，并将其置于指定的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构中

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>参数

*时间时间*<br/>
[出]在第一个重载中，将接收系统时间信息的[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象。 在第二个重载中，将收到系统时间信息的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。

*pTimeD最*<br/>
[出]指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，用于接收系统时间信息。 不能为 NULL。

### <a name="return-value"></a>返回值

在第一个重载中，如果时间成功写入[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象，则非零;否则 0。 在第二个和第三个重载中，返回值是 DWORD，它等于[在 NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)结构中设置的 dwFlag 成员。

### <a name="remarks"></a>备注

该方法设置[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)结构成员 dwFlags 以指示日期和时间选取器是否设置为日期和时间。 如果值等于GDT_NONE，则控件将设置为`no date`状态，并使用DTS_SHOWNONE样式。 如果返回的值等于GDT_VALID，则系统时间将成功存储在目标位置。

## <a name="cmfctoolbardatetimectrlgettimeall"></a><a name="gettimeall"></a>CMFCToolBarDatetimeCtrl：获取时间所有

从具有指定命令 ID 的时间选取器控件按钮返回用户选择的时间。

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

*乌伊Cmd*<br/>
[在]指定工具栏按钮的命令 ID。

*时间时间*<br/>
[出]在第一个重载中，将接收系统时间信息的[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象。 在第二个重载中，将收到系统时间信息的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。

*pTimeD最*<br/>
[出]指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，用于接收系统时间信息。 不能为 NULL。

### <a name="return-value"></a>返回值

如果框架找不到与命令 ID *uiCmd*匹配的工具栏按钮，则返回值在第一次重载中为零，并在其他重载中GDT_NONE。 如果找到工具栏按钮，则返回值与从调用[CMFCToolBarDateTimeCtrl](#gettime)返回值相同：获取该按钮上的返回时间。 找到按钮时，可能会出现零或GDT_NONE的返回值，该按钮指示对的`GetTime`调用由于某种其他原因未返回有效日期。

### <a name="remarks"></a>备注

此方法查找具有指定命令 ID 并调用该按钮上的[CMFCToolBarDateTimeCtrl：getTime](#gettime)方法的工具栏按钮。

## <a name="cmfctoolbardatetimectrlhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarDatetimeCtrl：：有热边界

确定当用户选择该按钮时是否显示按钮的边框。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>返回值

如果按钮在选定时显示其边框，则非零;否则 0。

### <a name="remarks"></a>备注

如果控件可见，此方法将返回非零值。

## <a name="cmfctoolbardatetimectrlnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarDatetimeCtrl：：通知命令

指定按钮是否处理[WM_COMMAND](/windows/win32/menurc/wm-command)消息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>参数

*iNotify代码*<br/>
[在]与命令关联的通知消息。

### <a name="return-value"></a>返回值

如果按钮处理WM_COMMAND消息，则为 TRUE，或 FALSE 指示该消息应由父工具栏处理。

### <a name="remarks"></a>备注

当此方法要向父窗口发送[WM_COMMAND](/windows/win32/menurc/wm-command)消息时，框架将调用此方法。

此方法通过处理[DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange)通知扩展基类实现 （ [CMFCToolBarButton：：通知命令](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)）。 它更新内部时间状态，并更新具有相同命令 ID`CMFCToolBarDateTimeCtrl`的所有对象的时间属性。

## <a name="cmfctoolbardatetimectrlonaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolbardatetimectrl：：在Addto自定义页面上

将按钮添加到 **"自定义"** 对话框时由框架调用。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>备注

此方法通过复制具有相同对象的命令 ID的任何工具栏中的第一个日期和时间控件的属性来扩展基类实现[CMFCToolBarButton：：onAddTo自定义页](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。 如果没有工具栏具有与此对象具有相同命令 ID 的日期和时间控件，则此方法不执行任何操作。

有关 **"自定义"** 对话框的详细信息，请参阅[CMFCToolBars 自定义对话框类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

## <a name="cmfctoolbardatetimectrlonchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarDatetimectrl：：在更改家长

将按钮插入到新工具栏时由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]新的父窗口。

### <a name="remarks"></a>备注

此方法通过重新创建内部`CMFCToolBarDateTimeCtrlImpl`对象来重写基类实现 （ [CMFCToolBarButton：：onChangeParentwnd）。](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)

## <a name="cmfctoolbardatetimectrlonclick"></a><a name="onclick"></a>CMFCToolBarDatetimectrl：：点击

当用户单击控件时由框架调用。

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

此方法重写基类实现[CMFCToolBarButton：：onClick，](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)通过在内部`CMFCToolBarDateTimeCtrlImpl`对象可见时返回非零值。

## <a name="cmfctoolbardatetimectrlonctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarDatetimectrl：onCtlColor

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

框架用于绘制按钮背景的全局画笔的句柄。

### <a name="remarks"></a>备注

此方法通过分别将所提供的设备上下文的文本和背景颜色分别设置为全局文本和背景颜色来覆盖基类实现[CMFCToolBarButton：onCtlColor。](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)

有关应用程序可用的全局选项的详细信息，请参阅[AFX_GLOBAL_DATA结构](../../mfc/reference/afx-global-data-structure.md)。

## <a name="cmfctoolbardatetimectrlonglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarDatetimectrl：：在全局字体上更改

当全局字体已更改时由框架调用。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>备注

此方法通过将控件的字体更改为全局字体来扩展基类实现 （ [CMFCToolBarButton：：onGlobalFonts 已更改](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)）。

有关应用程序可用的全局选项的详细信息，请参阅[AFX_GLOBAL_DATA结构](../../mfc/reference/afx-global-data-structure.md)。

## <a name="cmfctoolbardatetimectrlonmove"></a><a name="onmove"></a>CMFCToolBarDatetimectrl：：移动

当父工具栏移动时由框架调用。

```
virtual void OnMove();
```

### <a name="remarks"></a>备注

此方法通过更新内部`CMFCToolBarDateTimeCtrlImpl`对象的位置来重写默认类实现 （ [CMFCToolBarButton：：onMove）。](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)

## <a name="cmfctoolbardatetimectrlonshow"></a><a name="onshow"></a>CMFCToolBarDatetimectrl：：上展

当按钮变得可见或不可见时，由框架调用。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
[在]指定按钮是否可见。 如果此参数为 TRUE，则按钮为可见。 否则，该按钮不可见。

### <a name="remarks"></a>备注

此方法通过显示按钮（如果*bShow*为 TRUE）来扩展基类实现 （ [CMFCToolBarButton：：onShow）。](../../mfc/reference/cmfctoolbarbutton-class.md#onshow) 否则，此方法将隐藏该按钮。

## <a name="cmfctoolbardatetimectrlonsize"></a><a name="onsize"></a>CMFCToolBarDatetimectrl：：打开尺寸

当父工具栏更改其大小或位置且此更改导致按钮更改大小时，框架调用该按钮。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>参数

*iSize*<br/>
[在]按钮的新宽度（以像素为单位）。

### <a name="remarks"></a>备注

此方法通过更新内部`CMFCToolBarDateTimeCtrlImpl`对象的大小和位置来覆盖默认类实现 （ [CMFCToolBarButton：：onSize）。](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)

## <a name="cmfctoolbardatetimectrlonupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarDatetimectrl：：打开更新工具提示

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
[在]父窗口。

*iButtonIndex*<br/>
[在]父按钮集合中按钮的零基索引。

*wndToolTip*<br/>
[在]显示工具提示文本的控件。

*Str*<br/>
[出]接收`CString`更新的工具提示文本的对象。

### <a name="return-value"></a>返回值

如果方法更新工具提示文本，则非零;否则 0。

### <a name="remarks"></a>备注

此方法通过显示与按钮关联的工具提示文本来扩展基类实现[（CMFCToolBarButton：：onUpdateToolTip）。](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip) 如果按钮未水平停靠，则此方法不执行任何操作并返回 FALSE。

## <a name="cmfctoolbardatetimectrlsettime"></a><a name="settime"></a>CMFCToolBarDatetimeCtrl：：设置时间

设置时间选取器控件中的时间和日期。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>参数

*时间新*<br/>
[在]在第一个版本中，对包含将控件设置为的时间的[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用。 在第二个版本中，指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针，该对象包含将控件设置为的时间。

*pTimeNew*<br/>
[在]指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，其中包含将控件设置为的时间。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

通过调用[CDateTimeCtrl：：setTime，](../../mfc/reference/cdatetimectrl-class.md#settime)设置日期和时间选取器控件中的时间。

## <a name="cmfctoolbardatetimectrlsettimeall"></a><a name="settimeall"></a>CMFCToolBarDatetimeCtrl：：设置时间所有

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

*乌伊Cmd*<br/>
[在]指定工具栏按钮的命令 ID。

*时间新*<br/>
[在]在第一版本中，包含将控件设置为的时间的[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象。 在第二个版本中，指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针，该对象包含将控件设置为的时间。

*pTimeNew*<br/>
[在]指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，其中包含将控件设置为的时间。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

查找具有指定命令 ID 的工具栏按钮，并通过调用[CMFCToolBarDateTimeCtrl：：SetTime](#settime)来设置日期和时间选取器控件中的时间。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC工具栏按钮类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
