---
title: CMonthCalCtrl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f8dd962a06d6c7edadcdd029bd83d44b251aec8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377734"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl 类
封装月历控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CMonthCalCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|构造 `CMonthCalCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMonthCalCtrl::Create](#create)|创建月历控件并将其附加到`CMonthCalCtrl`对象。|  
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|检索当前月历控件的边框的宽度。|  
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|检索当前月历控件中显示的日历的数目。|  
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|检索当前月历控件有关的信息。|  
|[CMonthCalCtrl::GetCalID](#getcalid)|检索当前月历控件的日历标识符。|  
|[CMonthCalCtrl::GetColor](#getcolor)|获取月历控件的指定区域的颜色。|  
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|检索当前显示通过当前月历控件的视图。|  
|[CMonthCalCtrl::GetCurSel](#getcursel)|检索系统时间，按当前所选日期所示。|  
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|获取日历的最左侧列中显示在一周的第一天。|  
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|检索当前的最大数量的月历控件中可选择的天数。|  
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|检索当前月历控件的"今天"字符串的最大宽度。|  
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|检索月历控件中显示一整月所需的最小大小。|  
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|检索月历控件的滚动率。|  
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|检索日期表示月历控件的显示的高和低限制的信息。|  
|[CMonthCalCtrl::GetRange](#getrange)|检索在月历控件中设置的当前最小和最大日期。|  
|[CMonthCalCtrl::GetSelRange](#getselrange)|检索表示当前由用户选择的日期范围的上限和下限限制的日期信息。|  
|[CMonthCalCtrl::GetToday](#gettoday)|检索指定为"今天"的月历控件的日期的日期信息。|  
|[CMonthCalCtrl::HitTest](#hittest)|确定在屏幕上给定时刻处于月历控件的哪个节。|  
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|指示当前月历控件的当前视图是否世纪视图。|  
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|指示当前月历控件的当前视图是否为十年视图。|  
|[CMonthCalCtrl::IsMonthView](#ismonthview)|指示当前月历控件的当前视图是否为月视图。|  
|[CMonthCalCtrl::IsYearView](#isyearview)|指示当前月历控件的当前视图是否年视图。|  
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|设置当前月历控件的边框的宽度。|  
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|设置当前月历控件的边框的默认宽度。|  
|[CMonthCalCtrl::SetCalID](#setcalid)|设置当前月历控件的日历标识符。|  
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|设置当前月历控件以显示世纪视图。|  
|[CMonthCalCtrl::SetColor](#setcolor)|设置月历控件的指定区域的颜色。|  
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|设置当前月历控件以显示指定的视图。|  
|[CMonthCalCtrl::SetCurSel](#setcursel)|设置月历控件的当前所选的日期。|  
|[Cmonthcalctrl:: Setdaystate](#setdaystate)|设置月历控件中的天的显示。|  
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|当前的月历控件设置为十年视图。|  
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|设置要在最左边的日历列中显示星期几。|  
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|设置月历控件中可选择最大天数。|  
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|设置月历控件的滚动率。|  
|[CMonthCalCtrl::SetMonthView](#setmonthview)|设置当前月历控件以显示月视图。|  
|[CMonthCalCtrl::SetRange](#setrange)|设置最小值和最大允许月历控件的日期。|  
|[CMonthCalCtrl::SetSelRange](#setselrange)|所选择的月历控件设置为给定的日期范围。|  
|[CMonthCalCtrl::SetToday](#settoday)|设置当前日期的日历控件。|  
|[CMonthCalCtrl::SetYearView](#setyearview)|当前的月历控件设置为年视图。|  
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|重绘月历控制转移到其最小值、 一个月的大小。|  
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|对于当前月历控件，将计算最小的矩形可以包含指定的矩形中容纳不下的所有日历。|  
  
## <a name="remarks"></a>备注  
 月历控件提供了简单的日历界面，用户可以从中选择日期的用户。 用户可以更改通过显示：  
  
-   向后和向前移动，滚动到月份的月份。  
  
-   单击要显示当天的当前文本 (如果**MCS_NOTODAY**不使用样式)。  
  
-   选取一个月或每年从弹出菜单。  
  
 你可以自定义每月通过将各种样式应用于对象，当你创建月历控件。 这些样式中所述[月日历控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760919)Windows SDK 中。  
  
 月历控件可以显示超过一个月，并且它可以通过粗指示 （例如节假日） 的特殊天的日期。  
  
 使用月历控件的详细信息，请参阅[使用 CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CMonthCalCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdtctl.h  
  
##  <a name="cmonthcalctrl"></a>  CMonthCalCtrl::CMonthCalCtrl  
 构造 `CMonthCalCtrl` 对象。  
  
```  
CMonthCalCtrl();
```  
  
### <a name="remarks"></a>备注  
 必须调用**创建**构造对象之后。  
  
##  <a name="create"></a>  CMonthCalCtrl::Create  
 创建月历控件并将其附加到`CMonthCalCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);

 
virtual BOOL Create(
    DWORD dwStyle,  
    const POINT& pt,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定应用于月历控件的窗口样式的组合。 请参阅[月日历控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760919)样式有关的详细信息的 Windows SDK 中。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。 包含的位置和月历控件的大小。  
  
 `pt`  
 对引用[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)标识月历控件的位置的结构。  
  
 `pParentWnd`  
 指向的指针[CWnd](../../mfc/reference/cwnd-class.md)是月历控件的父窗口的对象。 它不能**NULL**。  
  
 `nID`  
 指定月历控件的控件 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 创建一个月月历控件中两个步骤：  
  
1.  调用[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)构造`CMonthCalCtrl`对象。  
  
2.  调用此成员函数，它创建月历控件并将其附加到`CMonthCalCtrl`对象。  
  
 当调用**创建**，常见的控件进行初始化。 版本**创建**你调用确定如何将其大小调整：  
  
-   要使 MFC 自动调整大小对一个月的控制，请调用使用的替代`pt`参数。  
  
-   若要调整控件的大小自己，调用使用此函数的重写`rect`参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]  
  
##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder  
 检索当前月历控件的边框的宽度。  
  
```  
int GetCalendarBorder() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件边框宽度，以像素为单位。  
  
### <a name="remarks"></a>备注  
 此方法可发送[MCM_GETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760945)消息，Windows SDK 中介绍。  
  
##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount  
 检索当前月历控件中显示的日历的数目。  
  
```  
int GetCalendarCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 日历月历控件中当前显示的数。 最大允许的数目日历为 12。  
  
### <a name="remarks"></a>备注  
 此方法可发送[MCM_GETCALENDARCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760947)消息，Windows SDK 中介绍。  
  
##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo  
 检索当前月历控件有关的信息。  
  
```  
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `pmcGridInfo`|指向[MCGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760925)接收当前月历控件的相关信息的结构。 调用方负责分配和初始化此结构。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[MCM_GETCALENDARGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760949)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例使用`GetCalendarGridInfo`方法来检索当前月历控件显示的日历日期。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]  
  
##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID  
 检索当前月历控件的日历标识符。  
  
```  
CALID GetCalID() const;  
```  
  
### <a name="return-value"></a>返回值  
 之一[日历标识符](http://msdn.microsoft.com/library/windows/desktop/dd317732)常量。  
  
### <a name="remarks"></a>备注  
 日历标识符表示特定区域的日历，如公历 （本地化）、 日语或回历日历。 你的应用程序可以使用具有各种语言支持功能的日历标识符。  
  
 此方法可发送[MCM_GETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760951)消息，Windows SDK 中介绍。  
  
##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor  
 检索每月的区域的颜色月历控件指定`nRegion`。  
  
```  
COLORREF GetColor(int nRegion) const;  
```  
  
### <a name="parameters"></a>参数  
 `nRegion`  
 从中检索颜色月历控件的区域。 值的列表，请参阅`nRegion`参数[SetColor](#setcolor)。  
  
### <a name="return-value"></a>返回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值指定与月历控件，部分关联的颜色，如果成功。 否则，此成员函数返回-1。  
  
##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView  
 检索当前显示通过当前月历控件的视图。  
  
```  
DWORD GetCurrentView() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前视图，这将由以下值之一：  
  
|值|含义|  
|-----------|-------------|  
|`MCMV_MONTH`|每月的视图|  
|`MCMV_YEAR`|每年的视图|  
|`MCMV_DECADE`|十年视图|  
|`MCMV_CENTURY`|世纪视图|  
  
### <a name="remarks"></a>备注  
 此方法可发送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>示例  
 当前，以下代码示例报表来查看月历控件显示。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]  
  
##  <a name="getcursel"></a>  CMonthCalCtrl::GetCurSel  
 检索系统时间，按当前所选日期所示。  
  
```  
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;  
   
BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>参数  
 `refDateTime`  
 对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。 接收的当前时间。  
  
 `pDateTime`  
 指向的指针[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)将接收的当前所选日期信息的结构。 此参数必须是有效的地址，不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零otherwize 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_GETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb760957)，如 Windows SDK 中所述。  
  
> [!NOTE]
>  如果此成员函数将失败样式**MCS_MULTISELECT**设置。  
  
 MFC 的实现中`GetCurSel`，你可以指定`COleDateTime`使用情况，`CTime`用法，或`SYSTEMTIME`结构使用情况。  
  
##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek  
 获取日历的最左侧列中显示在一周的第一天。  
  
```  
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 *pbLocal*  
 指向的指针**BOOL**值。 如果值为非零，则控件的设置不匹配控制面板中的设置。  
  
### <a name="return-value"></a>返回值  
 一个整数值，表示一周的第一天。 请参阅**备注**有关这些整数所表示的含义的详细信息。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_GETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb760958)，如 Windows SDK 中所述。 每周天数，如下所示为整数，表示。  
  
|值|日期是星期几|  
|-----------|---------------------|  
|0|星期一|  
|1|星期二|  
|2|星期三|  
|3|星期四|  
|4|星期五|  
|5|星期六|  
|6|星期日|  
  
### <a name="example"></a>示例  
  请参阅示例[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)。  
  
##  <a name="getmaxselcount"></a>  CMonthCalCtrl::GetMaxSelCount  
 检索当前的最大数量的月历控件中可选择的天数。  
  
```  
int GetMaxSelCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个整数值，表示控件可选择天的总数。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_GETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760960)，如 Windows SDK 中所述。 此成员函数可用于与控件**MCS_MULTISELECT**样式集。  
  
### <a name="example"></a>示例  
  请参阅示例[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)。  
  
##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth  
 检索当前月历控件的"今天"字符串的最大宽度。  
  
```  
DWORD GetMaxTodayWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 字符串的宽度"今天"，以像素为单位。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例演示`GetMaxTodayWidth`方法。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]  
  
### <a name="remarks"></a>备注  
 用户可以通过单击"今天"字符串，其中月历控件底部会显示为当前日期，返回。 "今天"字符串包括标签文本和日期文本。  
  
 此方法可发送[MCM_GETMAXTODAYWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760962)消息，Windows SDK 中介绍。  
  
##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect  
 检索月历控件中显示一整月所需的最小大小。  
  
```  
BOOL GetMinReqRect(RECT* pRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `pRect`  
 指向的指针[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)将接收边界矩形信息的结构。 此参数必须是有效的地址，不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果设置成功，，此成员函数将返回非零和`lpRect`接收合适的边界信息。 如果不成功，则该成员函数将返回 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_GETMINREQRECT](http://msdn.microsoft.com/library/windows/desktop/bb760978)，如 Windows SDK 中所述。  
  
##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta  
 检索月历控件的滚动率。  
  
```  
int GetMonthDelta() const;  
```  
  
### <a name="return-value"></a>返回值  
 月历控件滚动率。 滚动率是控件，当用户单击滚动按钮一次会移动其显示的月数。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_GETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb760980)，如 Windows SDK 中所述。  
  
##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange  
 检索日期表示月历控件的显示的高和低限制的信息。  
  
```  
int GetMonthRange(
    COleDateTime& refMinRange,  
    COleDateTime& refMaxRange,  
    DWORD dwFlags) const;  
  
int GetMonthRange(
    CTime& refMinRange,  
    CTime& refMaxRange,  
    DWORD dwFlags) const;  
  
int GetMonthRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange,  
    DWORD dwFlags) const;  
```  
  
### <a name="parameters"></a>参数  
 `refMinRange`  
 对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含允许的最小日期。  
  
 `refMaxRange`  
 对引用`COleDateTime`或`CTime`对象，其中包含允许的最大日期。  
  
 `pMinRange`  
 指向的指针[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，它包含范围的最低末尾处的日期。  
  
 `pMaxRange`  
 指向的指针`SYSTEMTIME`结构，它包含在最高范围末尾的日期。  
  
 `dwFlags`  
 值，该值指定要检索的范围限制的作用域。 此值必须是下列其中一项。  
  
|值|含义|  
|-----------|-------------|  
|GMR_DAYSTATE|包括的前导和尾随的可见区域仅部分显示的月。|  
|GMR_VISIBLE|包括完全显示这些个月。|  
  
### <a name="return-value"></a>返回值  
 一个整数，表示范围，以月为单位，跨两个限制由`refMinRange`和`refMaxRange`在第一个和第二个版本中，或`pMinRange`和`pMaxRange`在三个版本。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_GETMONTHRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760981)，如 Windows SDK 中所述。 MFC 的实现中`GetMonthRange`，你可以指定`COleDateTime`使用情况，`CTime`用法，或`SYSTEMTIME`结构使用情况。  
  
### <a name="example"></a>示例  
  请参阅示例[cmonthcalctrl:: Setdaystate](#setdaystate)。  
  
##  <a name="getrange"></a>  CMonthCalCtrl::GetRange  
 检索在月历控件中设置的当前最小和最大日期。  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
  
DWORD GetRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange) const;  
```  
  
### <a name="parameters"></a>参数  
 `pMinRange`  
 指向的指针`COleDateTime`对象，`CTime`对象，或[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，它包含范围的最低末尾处的日期。  
  
 `pMaxRange`  
 指向的指针`COleDateTime`对象，`CTime`对象，或[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，它包含在最高范围末尾的日期。  
  
### <a name="return-value"></a>返回值  
 A`DWORD`可能为零 （设置不受限制） 或指定限制信息的以下值的组合。  
  
|值|含义|  
|-----------|-------------|  
|GDTR_MAX|用于控制，设置最大限制`pMaxRange`有效，并且包含适用日期信息。|  
|GDTR_MIN|最小限制设置用于控制，`pMinRange`有效，并且包含适用日期信息。|  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760983)，如 Windows SDK 中所述。 MFC 的实现中`GetRange`，你可以指定`COleDateTime`使用情况，`CTime`用法，或`SYSTEMTIME`结构使用情况。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]  
  
##  <a name="getselrange"></a>  CMonthCalCtrl::GetSelRange  
 检索表示当前由用户选择的日期范围的上限和下限限制的日期信息。  
  
```  
BOOL GetSelRange(
    COleDateTime& refMinRange,  
    COleDateTime& refMaxRange) const;  
  
BOOL GetSelRange(
    CTime& refMinRange,  
    CTime& refMaxRange) const;  
  
BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange) const;  
```  
  
### <a name="parameters"></a>参数  
 `refMinRange`  
 对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含允许的最小日期。  
  
 `refMaxRange`  
 对引用`COleDateTime`或`CTime`对象，其中包含允许的最大日期。  
  
 `pMinRange`  
 指向的指针[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，它包含范围的最低末尾处的日期。  
  
 `pMaxRange`  
 指向的指针`SYSTEMTIME`结构，它包含在最高范围末尾的日期。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_GETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760985)，如 Windows SDK 中所述。 `GetSelRange` 如果应用于不使用月历控件将会失败**MCS_MULTISELECT**样式。  
  
 MFC 的实现中`GetSelRange`，你可以指定`COleDateTime`使用情况，`CTime`用法，或`SYSTEMTIME`结构使用情况。  
  
##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday  
 检索指定为"今天"的月历控件的日期的日期信息。  
  
```  
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;  
   
BOOL GetToday(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>参数  
 `refDateTime`  
 对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，该值指示当前的日期。  
  
 `pDateTime`  
 指向的指针[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)将收到的日期信息的结构。 此参数必须是有效的地址，不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_GETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb760987)，如 Windows SDK 中所述。 MFC 的实现中`GetToday`，你可以指定`COleDateTime`使用情况，`CTime`用法，或`SYSTEMTIME`结构使用情况。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]  
  
##  <a name="hittest"></a>  CMonthCalCtrl::HitTest  
 确定哪些月历控件，如果任何，位于指定位置。  
  
```  
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```  
  
### <a name="parameters"></a>参数  
 *pMCHitTest*  
 指向的指针[MCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760927)月历控件的点的结构，它包含的命中测试。  
  
### <a name="return-value"></a>返回值  
 一个 `DWORD` 值。 等于**uHit**的成员**MCHITTESTINFO**结构。  
  
### <a name="remarks"></a>备注  
 `HitTest` 使用**MCHITTESTINFO**结构，其中包含有关命中测试信息。  
  
##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView  
 指示当前月历控件的当前视图是否世纪视图。  
  
```  
BOOL IsCenturyView() const;  
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果当前视图是世纪视图中;否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)消息，Windows SDK 中介绍。 如果该消息返回`MCMV_CENTURY`，此方法返回`true`。  
  
##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView  
 指示当前月历控件的当前视图是否为十年视图。  
  
```  
BOOL IsDecadeView() const;  
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果当前视图是十年视图中;否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)消息，Windows SDK 中介绍。 如果该消息返回`MCMV_DECADE`，此方法返回`true`。  
  
##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView  
 指示当前月历控件的当前视图是否为月视图。  
  
```  
BOOL IsMonthView() const;  
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果当前视图是月视图中;否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)消息，Windows SDK 中介绍。 如果该消息返回`MCMV_MONTH`，此方法返回`true`。  
  
##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView  
 指示当前月历控件的当前视图是否年视图。  
  
```  
BOOL IsYearView() const;  
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果当前视图是年视图中;否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955)消息，Windows SDK 中介绍。 如果该消息返回`MCMV_YEAR`，此方法返回`true`。  
  
##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder  
 设置当前月历控件的边框的宽度。  
  
```  
void SetCalendarBorder(int cxyBorder);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `cxyBorder`|边框宽度，以像素为单位。|  
  
### <a name="remarks"></a>备注  
 如果此方法成功，边框宽度设置为`cxyBorder`参数。 否则，边框宽度将重置指定由当前的默认值为[主题](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx)，或如果不使用主题为零。  
  
 此方法可发送[MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置月历的边框宽度控制为八个像素。 使用[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)方法来确定此方法是否成功。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]  
  
##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault  
 设置当前月历控件的边框的默认宽度。  
  
```  
void SetCalendarBorderDefault();
```  
  
### <a name="remarks"></a>备注  
 边框宽度设置为指定由当前的默认值[主题](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx)，或如果不使用主题为零。  
  
 此方法可发送[MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993)消息，Windows SDK 中介绍。  
  
##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID  
 设置当前月历控件的日历标识符。  
  
```  
BOOL SetCalID(CALID calid);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `calid`|之一[日历标识符](http://msdn.microsoft.com/library/windows/desktop/dd317732)常量。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 日历标识符指定特定于区域的日历，如公历 （本地化）、 日语或回历日历。 使用`SetCalID`方法以显示指定的日历`calid`参数，如果在计算机上安装包含日历的区域设置。  
  
 此方法可发送[MCM_SETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760995)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置月历控件以显示日语和历日历。 `SetCalID`方法时在计算机上安装该日历的情况下，才会成功。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]  
  
##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView  
 设置当前月历控件以显示世纪视图。  
  
```  
BOOL SetCenturyView();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法将视图设置为`MCMV_CENTURY`，它表示世纪视图。  
  
##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor  
 设置月历控件的指定区域的颜色。  
  
```  
COLORREF SetColor(
    int nRegion,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>参数  
 `nRegion`  
 指定要设置哪些月日历颜色的整数值。 此值可以是下列其中一项。  
  
|值|含义|  
|-----------|-------------|  
|MCSC_BACKGROUND|显示不同的月份的背景色。|  
|MCSC_MONTHBK|在月份中显示的背景色。|  
|MCSC_TEXT|用来在一个月内显示文本的颜色。|  
|MCSC_TITLEBK|日历的标题中显示的背景色。|  
|MCSC_TITLETEXT|用于显示日历的标题中的文本的颜色。|  
|MCSC_TRAILINGTEXT|用来显示标头和尾随日文本的颜色。 标头和后续日期是从上一个和下一个月的当前日历上显示的日期。|  
  
 `ref`  
 A **COLORREF**月历控件的指定部分的新颜色设置的值。  
  
### <a name="return-value"></a>返回值  
 A **COLORREF**如果成功，则表示的指定部分的月历控件，以前的颜色设置的值。 否则，此消息返回-1。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_SETCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760997)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]  
  
##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView  
 设置当前月历控件以显示指定的视图。  
  
```  
BOOL SetCurrentView(DWORD dwNewView);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `dwNewView`|指定每月，年度、 十年中或世纪视图的以下值之一。<br /><br /> MCMV_MONTH： 每月视图<br /><br /> MCMV_YEAR： 年度视图<br /><br /> MCMV_DECADE： 十年视图<br /><br /> MCMV_CENTURY： 世纪视图|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[MCM_SETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760998)消息，Windows SDK 中介绍。  
  
##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel  
 设置月历控件的当前所选的日期。  
  
```  
BOOL SetCurSel(const COleDateTime& refDateTime);  
BOOL SetCurSel(const CTime& refDateTime);  
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>参数  
 `refDateTime`  
 对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md) ，该值指示当前所选月历控件的对象。  
  
 `pDateTime`  
 指向[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，其中包含要设置为当前所选内容的日期。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_SETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb761002)，如 Windows SDK 中所述。 MFC 的实现中`SetCurSel`，你可以指定`COleDateTime`使用情况，`CTime`用法，或`SYSTEMTIME`结构使用情况。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]  
  
##  <a name="setdaystate"></a>  Cmonthcalctrl:: Setdaystate  
 设置月历控件中的天的显示。  
  
```  
BOOL SetDayState(
    int nMonths,  
    LPMONTHDAYSTATE pStates);
```  
  
### <a name="parameters"></a>参数  
 *nMonths*  
 值，该值指示数组中的元素数量的`pStates`指向。  
  
 `pStates`  
 指向的指针[MONTHDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760915)定义如何月历控件将其显示在绘制每一天的值的数组。 **MONTHDAYSTATE**数据类型是一个位字段，其中每一位 (1 到 31) 表示一个月中的一天的状态。 如果某个位处于打开状态，则以粗体显示对应的那一天，否则将不会突出显示。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_SETDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb761004)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]  
  
##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView  
 当前的月历控件设置为十年视图。  
  
```  
BOOL SetDecadeView();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法将视图设置为`MCMV_DECADE`，它表示十年视图。  
  
##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek  
 设置要在最左边的日历列中显示星期几。  
  
```  
BOOL SetFirstDayOfWeek(
    int iDay,  
    int* lpnOld = NULL);
```  
  
### <a name="parameters"></a>参数  
 *iDay*  
 表示哪一天的整数值是要设置为一周的第一天。 此值必须是一个日期编号。 请参阅[GetFirstDayOfWeek](#getfirstdayofweek)有关日期编号的说明。  
  
 *lpnOld*  
 指向一个整数，表示一周以前的第一天的设置。  
  
### <a name="return-value"></a>返回值  
 如果以前的第一个日期是星期几设置以外的值为非零**LOCALE_IFIRSTDAYOFWEEK**，即指示在控件面板设置中的天。 否则，此函数返回 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_SETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb761006)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]  
  
##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount  
 设置月历控件中可选择最大天数。  
  
```  
BOOL SetMaxSelCount(int nMax);
```  
  
### <a name="parameters"></a>参数  
 `nMax`  
 将设置来表示最大天数可选择的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_SETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761008)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]  
  
##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta  
 设置月历控件的滚动率。  
  
```  
int SetMonthDelta(int iDelta);
```  
  
### <a name="parameters"></a>参数  
 *iDelta*  
 要设置为控件的滚动率的月数。 如果此值为零，则会将月增量重置为默认情况下，在控件中显示的月份数。  
  
### <a name="return-value"></a>返回值  
 以前的滚动率。 如果以前尚未设置的滚动率，返回值为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_SETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb761010)，如 Windows SDK 中所述。  
  
##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView  
 设置当前月历控件以显示月视图。  
  
```  
BOOL SetMonthView();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法将视图设置为`MCMV_MONTH`，它表示月视图。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置月历控件显示月份、 年、 十年中，和世纪视图。  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]  
  
##  <a name="setrange"></a>  CMonthCalCtrl::SetRange  
 设置月历控件的最小和最大允许日期。  
  
```  
BOOL SetRange(
    const COleDateTime* pMinRange,  
    const COleDateTime* pMaxRange);

 
BOOL SetRange(
    const CTime* pMinRange,  
    const CTime* pMaxRange);

 
BOOL SetRange(
    const LPSYSTEMTIME pMinRange,  
    const LPSYSTEMTIME pMaxRange);
```  
  
### <a name="parameters"></a>参数  
 `pMinRange`  
 指向的指针`COleDateTime`对象，`CTime`对象，或[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，它包含范围的最低末尾处的日期。  
  
 `pMaxRange`  
 指向的指针`COleDateTime`对象，`CTime`对象，或`SYSTEMTIME`结构，它包含在最高范围末尾的日期。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761012)，如 Windows SDK 中所述。 MFC 的实现中`SetRange`，你可以指定`COleDateTime`使用情况，`CTime`用法，或`SYSTEMTIME`结构使用情况。  
  
### <a name="example"></a>示例  
  请参阅示例[CMonthCalCtrl::GetRange](#getrange)。  
  
##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange  
 所选择的月历控件设置为给定的日期范围。  
  
```  
BOOL SetSelRange(
    const COleDateTime& pMinRange,  
    const COleDateTime& pMaxRange);

 
BOOL SetSelRange(
    const CTime& pMinRange,  
    const CTime& pMaxRange);

 
BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,  
    const LPSYSTEMTIME pMaxRange);
```  
  
### <a name="parameters"></a>参数  
 `pMinRange`  
 指向的指针`COleDateTime`对象，`CTime`对象，或[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，它包含范围的最低末尾处的日期。  
  
 `pMaxRange`  
 指向的指针`COleDateTime`对象，`CTime`对象，或`SYSTEMTIME`结构，它包含在最高范围末尾的日期。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_SETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761014)，如 Windows SDK 中所述。 MFC 的实现中`SetSelRange`，你可以指定`COleDateTime`使用情况，`CTime`用法，或`SYSTEMTIME`结构使用情况。  
  
##  <a name="settoday"></a>  CMonthCalCtrl::SetToday  
 设置当前日期的日历控件。  
  
```  
void SetToday(const COleDateTime& refDateTime);  
void SetToday(const CTime* pDateTime);  
  void SetToday(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>参数  
 `refDateTime`  
 对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含当前日期。  
  
 `pDateTime`  
 在第二个版本中，指向的指针[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含当前日期信息。 在第三个版本中，指向的指针[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)包含当前日期信息的结构。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[MCM_SETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb761016)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
  请参阅示例[CMonthCalCtrl::GetToday](#gettoday)。  
  
##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView  
 当前的月历控件设置为年视图。  
  
```  
BOOL SetYearView();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法将视图设置为`MCMV_YEAR`，它表示每年的视图。  
  
##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq  
 显示每月执行最小程度的月历控件大小，显示一个月。  
  
```  
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bRepaint`  
 指定控件是否进行重新绘制。 默认情况下， **TRUE**。 如果**FALSE**，没有重新绘制时发生。  
  
### <a name="return-value"></a>返回值  
 如果月历控件的大小为最小化; 大小则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 调用`SizeMinReq`已成功为一个月的日历显示整个月历控件。  
  
##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin  
 对于当前月历控件，将计算最小的矩形可以包含指定的矩形中容纳不下的所有日历。  
  
```  
LPRECT SizeRectToMin(LPRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `lpRect`|指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它定义一个包含所需的日历数的矩形。|  
  
### <a name="return-value"></a>返回值  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)定义其大小小于或等于矩形的矩形的结构由来定义`lpRect`参数。  
  
### <a name="remarks"></a>备注  
 此方法计算中由指定的矩形可以容纳该值多少日历`lpRect`参数，然后返回最小的矩形可以包含该数量的日历。 实际上，此方法将缩小以完全适合所需的日历数的指定的矩形。  
  
 此方法可发送[MCM_SIZERECTTOMIN](http://msdn.microsoft.com/library/windows/desktop/bb761020)消息，Windows SDK 中介绍。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CMNCTRL1](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDateTimeCtrl 类](../../mfc/reference/cdatetimectrl-class.md)
