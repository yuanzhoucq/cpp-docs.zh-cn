---
title: "CMonthCalCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMonthCalCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonthCalCtrl class"
  - "公共控件, Internet Explorer 4.0"
  - "Internet Explorer 4.0 common controls"
  - "month calendar controls"
  - "month calendar controls, CMonthCalCtrl class"
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMonthCalCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装month calendar控件的功能。  
  
## 语法  
  
```  
class CMonthCalCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMonthCalCtrl::CMonthCalCtrl](../Topic/CMonthCalCtrl::CMonthCalCtrl.md)|构造 `CMonthCalCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMonthCalCtrl::Create](../Topic/CMonthCalCtrl::Create.md)|创建一个month calendar控件并将它附加到 `CMonthCalCtrl` 对象。|  
|[CMonthCalCtrl::GetCalendarBorder](../Topic/CMonthCalCtrl::GetCalendarBorder.md)|检索当前month calendar控件的边框的宽度。|  
|[CMonthCalCtrl::GetCalendarCount](../Topic/CMonthCalCtrl::GetCalendarCount.md)|检索在当前月份日历控件显示日历的数量。|  
|[CMonthCalCtrl::GetCalendarGridInfo](../Topic/CMonthCalCtrl::GetCalendarGridInfo.md)|检索有关当前month calendar控件的信息。|  
|[CMonthCalCtrl::GetCalID](../Topic/CMonthCalCtrl::GetCalID.md)|检索当前month calendar控件的日历标识符。|  
|[CMonthCalCtrl::GetColor](../Topic/CMonthCalCtrl::GetColor.md)|获取month calendar控件的指定范围的颜色。|  
|[CMonthCalCtrl::GetCurrentView](../Topic/CMonthCalCtrl::GetCurrentView.md)|检索由当前month calendar控件当前显示的视图。|  
|[CMonthCalCtrl::GetCurSel](../Topic/CMonthCalCtrl::GetCurSel.md)|检索系统时间表示的由当前选定的日期。|  
|[CMonthCalCtrl::GetFirstDayOfWeek](../Topic/CMonthCalCtrl::GetFirstDayOfWeek.md)|在日历中最左侧的列获取第一周中显示。|  
|[CMonthCalCtrl::GetMaxSelCount](../Topic/CMonthCalCtrl::GetMaxSelCount.md)|检索在月历控件可以选择日的当前最大数目。|  
|[CMonthCalCtrl::GetMaxTodayWidth](../Topic/CMonthCalCtrl::GetMaxTodayWidth.md)|检索最大的宽度“today”为当前month calendar控件的字符串。|  
|[CMonthCalCtrl::GetMinReqRect](../Topic/CMonthCalCtrl::GetMinReqRect.md)|在月历控件检索所需的最小大小显示完整的月份。|  
|[CMonthCalCtrl::GetMonthDelta](../Topic/CMonthCalCtrl::GetMonthDelta.md)|检索month calendar控件的滚动速度。|  
|[CMonthCalCtrl::GetMonthRange](../Topic/CMonthCalCtrl::GetMonthRange.md)|检索表示month calendar控件的公开高和少的日期信息。|  
|[CMonthCalCtrl::GetRange](../Topic/CMonthCalCtrl::GetRange.md)|检索在月历控件和最大日期设置的当前最小值。|  
|[CMonthCalCtrl::GetSelRange](../Topic/CMonthCalCtrl::GetSelRange.md)|检索表示日期范围的上限和下限的日期信息当前选定内容由用户。|  
|[CMonthCalCtrl::GetToday](../Topic/CMonthCalCtrl::GetToday.md)|为“today”指定的日期中检索日期信息。month calendar控件。|  
|[CMonthCalCtrl::HitTest](../Topic/CMonthCalCtrl::HitTest.md)|确定month calendar控件的哪个部分中给出的点在屏幕上。|  
|[CMonthCalCtrl::IsCenturyView](../Topic/CMonthCalCtrl::IsCenturyView.md)|指示当前month calendar控件的当前视图是世纪视图。|  
|[CMonthCalCtrl::IsDecadeView](../Topic/CMonthCalCtrl::IsDecadeView.md)|指示当前month calendar控件的当前视图是十年视图。|  
|[CMonthCalCtrl::IsMonthView](../Topic/CMonthCalCtrl::IsMonthView.md)|指示当前month calendar控件的当前视图是月份视图。|  
|[CMonthCalCtrl::IsYearView](../Topic/CMonthCalCtrl::IsYearView.md)|指示当前month calendar控件的当前视图是年视图。|  
|[CMonthCalCtrl::SetCalendarBorder](../Topic/CMonthCalCtrl::SetCalendarBorder.md)|设置当前month calendar控件的边框的宽度。|  
|[CMonthCalCtrl::SetCalendarBorderDefault](../Topic/CMonthCalCtrl::SetCalendarBorderDefault.md)|设置当前month calendar控件的边框的默认宽度。|  
|[CMonthCalCtrl::SetCalID](../Topic/CMonthCalCtrl::SetCalID.md)|设置当前month calendar控件的日历标识符。|  
|[CMonthCalCtrl::SetCenturyView](../Topic/CMonthCalCtrl::SetCenturyView.md)|设置当前month calendar控件显示世纪视图。|  
|[CMonthCalCtrl::SetColor](../Topic/CMonthCalCtrl::SetColor.md)|设置month calendar控件的指定范围的颜色。|  
|[CMonthCalCtrl::SetCurrentView](../Topic/CMonthCalCtrl::SetCurrentView.md)|设置当前month calendar控件显示指定的视图。|  
|[CMonthCalCtrl::SetCurSel](../Topic/CMonthCalCtrl::SetCurSel.md)|设置month calendar控件的当前选定的日期。|  
|[CMonthCalCtrl::SetDayState](../Topic/CMonthCalCtrl::SetDayState.md)|将显示在月历控件的日。|  
|[CMonthCalCtrl::SetDecadeView](../Topic/CMonthCalCtrl::SetDecadeView.md)|设置当前month calendar控件为十年视图。|  
|[CMonthCalCtrl::SetFirstDayOfWeek](../Topic/CMonthCalCtrl::SetFirstDayOfWeek.md)|设置在日历中最左侧的列中显示的每周日期。|  
|[CMonthCalCtrl::SetMaxSelCount](../Topic/CMonthCalCtrl::SetMaxSelCount.md)|设置在月历控件可以选择天的最大数目。|  
|[CMonthCalCtrl::SetMonthDelta](../Topic/CMonthCalCtrl::SetMonthDelta.md)|设置month calendar控件的滚动速度。|  
|[CMonthCalCtrl::SetMonthView](../Topic/CMonthCalCtrl::SetMonthView.md)|设置当前month calendar控件显示月份视图。|  
|[CMonthCalCtrl::SetRange](../Topic/CMonthCalCtrl::SetRange.md)|将最小值，并允许的最大值为month calendar控件日期。|  
|[CMonthCalCtrl::SetSelRange](../Topic/CMonthCalCtrl::SetSelRange.md)|设置month calendar控件的选择到特定日期范围。|  
|[CMonthCalCtrl::SetToday](../Topic/CMonthCalCtrl::SetToday.md)|为当前日期设置日历控件。|  
|[CMonthCalCtrl::SetYearView](../Topic/CMonthCalCtrl::SetYearView.md)|设置当前month calendar控件绑定到视图中。|  
|[CMonthCalCtrl::SizeMinReq](../Topic/CMonthCalCtrl::SizeMinReq.md)|重新绘制month calendar控件绑定到其最小，一个月的大小。|  
|[CMonthCalCtrl::SizeRectToMin](../Topic/CMonthCalCtrl::SizeRectToMin.md)|对当前月份日历控件，计算可能包含所有日历适合一个指定矩形的最小矩形。|  
  
## 备注  
 month calendar控件提供用户以简单的日历接口，用户可以选择日期。  用户可以将该示:  
  
-   向前或向后移动，在不同。  
  
-   单击当前文本显示当前日期\(如果未使用 **MCS\_NOTODAY** 样式）。  
  
-   选择一个月或年从弹出菜单。  
  
 通过应用各种样式自定义月历控件应用于对象，在创建它。  这些样式在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [Month calendar控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760919) 所述。  
  
 month calendar控件可以显示多个月份，并且，既可以由字号指示特定日期\(如假日\)该日期。  
  
 有关使用month calendar控件的更多信息，请参见 [使用CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CMonthCalCtrl`  
  
## 要求  
 **Header:** afxdtctl.h  
  
## 请参阅  
 [MFC示例CMNCTRL1](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDateTimeCtrl Class](../../mfc/reference/cdatetimectrl-class.md)