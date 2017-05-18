---
title: "CMFCToolBarDateTimeCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- SetStyle method
- OnCalculateSize method
- OnDraw method
- OnDrawOnCustomizeList method
- CMFCToolBarDateTimeCtrl class
- Serialize method
- OnSize method
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
caps.latest.revision: 30
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9558d62710c7be571d6aefab2c44fe504ca56d60
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl 类
包含日期和时间选取器控件的工具栏按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|构造 `CMFCToolBarDateTimeCtrl` 对象。|  
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|指定用户是否可以自定义期间拉伸按钮。 (重写[CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)。)|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。 (重写[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|留待将来使用。|  
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|复制从工具栏按钮的文本复制到菜单。|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|检索第一个`CMFCToolBarDateTimeCtrl`对象中的应用程序都有指定的命令 id。|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|返回一个指向日期和时间选取器控件。|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|检索与工具栏按钮关联的窗口句柄。 (重写[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)。)|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|从日期和时间选取器控件获取所选的时间，并将其放入指定[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构。|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|从具有指定的命令 ID 的时间选取器控件按钮返回所选的时间|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|确定当用户选择该按钮是否显示按钮的边框。 (重写[CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|指定是否处理按钮[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息。 (重写[CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)。)|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|当该按钮添加到由框架调用**自定义**对话框。 (重写[CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。)|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|调用由框架来计算指定的设备上下文和插接状态的按钮的大小。 (重写[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|在按钮插入到一个新的工具栏时由框架调用。 (重写[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|  
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|在用户单击控件时由框架调用。 (重写[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|当在父级工具栏处理由框架调用`WM_CTLCOLOR`消息。 (重写[CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。)|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|由框架通过使用指定的样式和选项绘制按钮调用。 (重写[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|由框架调用以将按钮画入**命令**窗格**自定义**对话框。 (重写[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|当全局字体发生更改时由框架调用。 (重写[CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)。)|  
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|当在父级工具栏将由框架调用。 (重写[CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)。)|  
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|由框架调用时该按钮即变为可见或不可见。 (重写[CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)。)|  
|`CMFCToolBarDateTimeCtrl::OnSize`|在父级工具栏更改其大小或位置和此更改将导致该按钮来更改大小时由框架调用。 (重写[CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。)|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|当在父级工具栏更新其工具提示文本由框架调用。 (重写[CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)。)|  
|`CMFCToolBarDateTimeCtrl::Serialize`|从存档读取此对象或将其写入存档，(重写[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|将工具栏按钮样式设置。 (重写[CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。)|  
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|设置的时间和日期时间选取器控件中。|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|将时间和日期设置在所有时间选取器控件的实例具有指定的命令 id。|  
  
## <a name="remarks"></a>备注  
 有关如何使用日期和时间选取器控件的示例，请参阅 ToolbarDateTimePicker 示例项目。 有关如何将控制按钮添加到工具栏的信息，请参阅[演练︰ 将控件在工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbardatetimectrl.h  
  
##  <a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched  
 指定用户是否可以自定义期间拉伸按钮。  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>返回值  
 此方法返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，框架不允许用户自定义期间拉伸工具栏按钮。 此方法会扩展的基类实现 ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) 通过允许用户自定义期间拉伸日期和时间的工具栏按钮。  
  
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
 [in] `uiID`  
 控件 id。  
  
 [in] `iImage`  
 在工具栏中的图像的索引`CMFCToolBarImages`对象。  
  
 [in] `dwStyle`  
 样式`CMFCToolBarDateTimeCtrlImpl`时用户单击按钮时，将创建的窗口。  
  
 [in] `iWidth`  
 控件的宽度（以像素为单位）。  
  
### <a name="remarks"></a>备注  
 此对象将初始化为系统日期和时间。 内部的窗口样式`CMFCToolBarDateTimeCtrlImpl`对象包括`dwStyle`参数和`WS_CHILD`和`WS_VISIBLE`样式。 不能通过更改这些样式`CMFCToolBarDateTimeCtrl::SetStyle`。 使用`SetStyle`若要更改的样式`CMFCToolBarDateTimeCtrl`控件。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCToolBarDateTimeCtrl`类。 此代码段属于[工具栏日期时间选取器示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_ToolbarDateTimePicker #&1;](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyFrom  
 将另一个工具栏按钮的属性复制到当前按钮。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 源按钮对从中进行复制的引用。  
  
### <a name="remarks"></a>备注  
 调用此方法以将另一个工具栏按钮复制到此工具栏按钮。 `src`类型必须为`CMFCToolBarDateTimeCtrl`。  
  
##  <a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton  
 复制从工具栏按钮的文本复制到菜单。  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `menuButton`  
 对目标菜单按钮的引用。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 此方法重写基类实现 ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) 通过加载与该控件的命令 ID 相关联的字符串资源。 有关字符串资源的详细信息，请参阅[CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)。  
  
##  <a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd  
 检索第一个`CMFCToolBarDateTimeCtrl`对象中的应用程序都有指定的命令 id。  
  
```  
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 要检索按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 第一个`CMFCToolBarDateTimeCtrl`中具有指定的命令 ID 的应用程序对象或`NULL`如果不是`CMFCToolBarDateTimeCtrl`对象具有指定的命令 id。  
  
### <a name="remarks"></a>备注  
 此共享的实用程序方法如由方法[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)和[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)来设置或获取的时间和日期时间选取器控件的所有实例，具有指定的命令 id。  
  
##  <a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl  
 返回一个指向日期和时间选取器控件。  
  
```  
CDateTimeCtrl* GetDateTimeCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 日期和时间选取器控件，则指向的指针或`NULL`如果控件不存在。  
  
### <a name="remarks"></a>备注  
 `CMFCToolBarDateTimeCtrl`类初始化`m_pWndDateTime`数据成员插入时`CMFCToolBarDateTimeCtrl`为工具栏对象。  
  
##  <a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd  
 检索与工具栏按钮关联的窗口句柄。  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>返回值  
 与日期和时间工具栏按钮关联窗口句柄。  
  
### <a name="remarks"></a>备注  
 此方法重写[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。  
  
##  <a name="gettime"></a>CMFCToolBarDateTimeCtrl::GetTime  
 从关联的日期和时间选取器控件获取所选的时间，并将其放入指定[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>参数  
 `[out] timeDest`  
 在第一个重载中， [COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)将收到系统时间信息的对象。 在第二个重载中， [CTime](../../atl-mfc-shared/reference/ctime-class.md)将收到系统时间信息的对象。  
  
 `[out] pTimeDest`  
 一个指向[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)接收系统时间信息的结构。 不得为 `NULL`。  
  
### <a name="return-value"></a>返回值  
 在第一个重载中，如果已成功写入时间，则为非[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象; 否则为 0。 在第二个和第三个重载，则返回值是`DWORD`等于在中设置的 dwFlag 成员[NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730)结构。  
  
### <a name="remarks"></a>备注  
 方法设置[NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730)结构成员 dwFlags 以指示是否为日期和时间设置日期和时间选取器。 如果值等于 GDT_NONE，控件设置成`no date`状态，而且使用 DTS_SHOWNONE 样式。 如果返回的值等于 GDT_VALID，系统时间已成功存储在目标位置。  
  
##  <a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll  
 返回具有指定的命令 ID 的时间选取器控件按钮从用户所选的时间  
  
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
 `[in] uiCmd`  
 指定工具栏按钮的命令 id。  
  
 `[out] timeDest`  
 在第一个重载中， [COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)将收到系统时间信息的对象。 在第二个重载中， [CTime](../../atl-mfc-shared/reference/ctime-class.md)将收到系统时间信息的对象。  
  
 `[out] pTimeDest`  
 一个指向[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)接收系统时间信息的结构。 不得为 `NULL`。  
  
### <a name="return-value"></a>返回值  
 如果框架找不到匹配的命令 ID 的工具栏按钮`uiCmd`，则返回值为零在第一个重载中，并且在其他重载 GDT_NONE。 如果找到工具栏按钮，则返回值是通过调用的返回值相同[CMFCToolBarDateTimeCtrl::GetTime](#gettime)对该按钮。 返回值零或 GDT_NONE 可能找到按钮后，该值指示调用`GetTime`未返回有效的日期，由于其他原因。  
  
### <a name="remarks"></a>备注  
 此方法查找具有指定的命令 ID 和调用的工具栏按钮[CMFCToolBarDateTimeCtrl::GetTime](#gettime)该按钮上的方法。  
  
##  <a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder  
 确定当用户选择该按钮是否显示按钮的边框。  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零值时的按钮显示选择; 时其边框否则为 0。  
  
### <a name="remarks"></a>备注  
 如果控件可见，则此方法返回一个非零值。  
  
##  <a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand  
 指定是否处理按钮[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息。  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>参数  
 [in] `iNotifyCode`  
 与命令关联通知消息。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该按钮处理`WM_COMMAND`消息，或`FALSE`以指示消息应由在父级工具栏。  
  
### <a name="remarks"></a>备注  
 框架将调用此方法时将要发送[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息发送到父窗口。  
  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) 通过处理[DTN_DATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761737)通知。 它将内部时间的状态更新，并更新时属性的所有`CMFCToolBarDateTimeCtrl`对象具有相同命令 id。  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage  
 当该按钮添加到由框架调用**自定义**对话框。  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现， [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)、 通过将属性复制从第一个日期和时间在任何具有相同的命令 ID 与此对象的工具栏中的控件。 如果没有工具栏具有具有相同的命令 ID 与此对象的日期和时间控件，则此方法执行任何操作。  
  
 有关详细信息**自定义**对话框中，请参阅[CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd  
 在按钮插入到一个新的工具栏时由框架调用。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 新的父窗口。  
  
### <a name="remarks"></a>备注  
 此方法重写基类实现 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 通过重新创建内部`CMFCToolBarDateTimeCtrlImpl`对象。  
  
##  <a name="onclick"></a>CMFCToolBarDateTimeCtrl::OnClick  
 在用户单击控件时由框架调用。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 未使用。  
  
 [in] `bDelay`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 如果该按钮处理单击消息时为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法重写基类实现[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)，通过返回一个非零值，如果内部`CMFCToolBarDateTimeCtrlImpl`对象是可见的。  
  
##  <a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor  
 当在父级工具栏处理由框架调用`WM_CTLCOLOR`消息。  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 所显示的按钮的设备上下文。  
  
 [in] `nCtlColor`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 指向全局框架用来绘制按钮背景的画笔的句柄。  
  
### <a name="remarks"></a>备注  
 此方法重写基类实现[CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)、 通过设置的文本和分别后台提供的设备上下文为全局文本的颜色和背景色。  
  
 有关可供您的应用程序的全局选项的详细信息，请参阅[AFX_GLOBAL_DATA 结构](../../mfc/reference/afx-global-data-structure.md)。  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged  
 当全局字体发生更改时由框架调用。  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) 通过与全局字体更改控件的字体。  
  
 有关可供您的应用程序的全局选项的详细信息，请参阅[AFX_GLOBAL_DATA 结构](../../mfc/reference/afx-global-data-structure.md)。  
  
##  <a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove  
 当在父级工具栏将由框架调用。  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>备注  
 此方法重写默认类实现 ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) 通过更新内部位置`CMFCToolBarDateTimeCtrlImpl`对象。  
  
##  <a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow  
 由框架调用时该按钮即变为可见或不可见。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 指定的按钮是否可见。 如果此参数为`TRUE`，按钮是否可见。 否则，该按钮不可见。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) 通过显示按钮，如果`bShow`是`TRUE`。 否则，此方法会隐藏按钮。  
  
##  <a name="onsize"></a>CMFCToolBarDateTimeCtrl::OnSize  
 在父级工具栏更改其大小或位置和此更改将导致该按钮来更改大小时由框架调用。  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>参数  
 [in] `iSize`  
 按钮，以像素为单位的新宽度。  
  
### <a name="remarks"></a>备注  
 此方法重写默认类实现 ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) 通过更新的大小和位置的内部`CMFCToolBarDateTimeCtrlImpl`对象。  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip  
 当在父级工具栏更新其工具提示文本由框架调用。  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 父窗口中。  
  
 [in] `iButtonIndex`  
 父按钮集合中按钮的从零开始索引。  
  
 [in] `wndToolTip`  
 显示的工具提示文本的控件。  
  
 [out] `str`  
 一个`CString`对象，它接收的已更新的工具提示文本。  
  
### <a name="return-value"></a>返回值  
 非零，如果此方法将更新的工具提示文本。否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) 通过显示与按钮关联的工具提示文本。 如果未水平停靠按钮，此方法不执行任何操作，并返回`FALSE`。  
  
##  <a name="settime"></a>CMFCToolBarDateTimeCtrl::SetTime  
 设置的时间和日期时间选取器控件中。  
  
```  
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>参数  
 `[in] timeNew`  
 在第一个版本中，对引用[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含将控件设置的时间。 在第二个版本中，指向的指针[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含将控件设置的时间。  
  
 `[in] pTimeNew`  
 一个指向[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，其中包含将控件设置的时间。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 通过调用日期和时间选取器控件中设置的时间[CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime)。  
  
##  <a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll  
 将时间和日期设置在所有时间选取器控件的实例具有指定的命令 id。  
  
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
 `[in] uiCmd`  
 指定工具栏按钮的命令 id。  
  
 `[in] timeNew`  
 在第一个版本中， [COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含将控件设置的时间。 在第二个版本中，指向的指针[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含将控件设置的时间。  
  
 `[in] pTimeNew`  
 一个指向[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，其中包含将控件设置的时间。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 查找与指定的命令 ID 的工具栏按钮，并通过调用日期和时间选取器控件中设置的时间[CMFCToolBarDateTimeCtrl::SetTime](#settime)。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [演练︰ 将置于工具栏上的控件](../../mfc/walkthrough-putting-controls-on-toolbars.md)




