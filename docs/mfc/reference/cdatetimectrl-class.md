---
title: "CDateTimeCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDateTimeCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl class"
  - "date-picking functionality"
  - "DateTimePicker control [MFC]"
  - "DateTimePicker control [MFC], CDateTimeCtrl class"
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDateTimeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装日期和时间选择器控件的功能。  
  
## 语法  
  
```  
class CDateTimeCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDateTimeCtrl::CDateTimeCtrl](../Topic/CDateTimeCtrl::CDateTimeCtrl.md)|构造 `CDateTimeCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDateTimeCtrl::CloseMonthCal](../Topic/CDateTimeCtrl::CloseMonthCal.md)|关闭当前日期和时间选择器控件。|  
|[CDateTimeCtrl::Create](../Topic/CDateTimeCtrl::Create.md)|创建日期和时间选择器控件并将它附加到 `CDateTimeCtrl` 对象。|  
|[CDateTimeCtrl::GetDateTimePickerInfo](../Topic/CDateTimeCtrl::GetDateTimePickerInfo.md)|检索有关当前日期和时间选择器控件的信息。|  
|[CDateTimeCtrl::GetIdealSize](../Topic/CDateTimeCtrl::GetIdealSize.md)|返回需要显示当前日期或时间日期和时间选择器控件的理想的大小。|  
|[CDateTimeCtrl::GetMonthCalColor](../Topic/CDateTimeCtrl::GetMonthCalColor.md)|检索月历的特定部分中的颜色为日期和时间选择器控件中。|  
|[CDateTimeCtrl::GetMonthCalCtrl](../Topic/CDateTimeCtrl::GetMonthCalCtrl.md)|检索 `CMonthCalCtrl` 对象与日期和时间选择器控件。|  
|[CDateTimeCtrl::GetMonthCalFont](../Topic/CDateTimeCtrl::GetMonthCalFont.md)|检索日期和时间选择器控件的子month calendar控件当前使用的字体。|  
|[CDateTimeCtrl::GetMonthCalStyle](../Topic/CDateTimeCtrl::GetMonthCalStyle.md)|获取当前日期和时间选择器控件的样式。|  
|[CDateTimeCtrl::GetRange](../Topic/CDateTimeCtrl::GetRange.md)|检索当前最小值和最大值允许的系统时间的日期和时间选择器控件。|  
|[CDateTimeCtrl::GetTime](../Topic/CDateTimeCtrl::GetTime.md)|从日期和时间选择器控件在指定的 `SYSTEMTIME` 结构检索当前所选时间并将其放在|  
|[CDateTimeCtrl::SetFormat](../Topic/CDateTimeCtrl::SetFormat.md)|设置日期和时间选择器控件的显示与特定格式字符串匹配。|  
|[CDateTimeCtrl::SetMonthCalColor](../Topic/CDateTimeCtrl::SetMonthCalColor.md)|设置月历的特定部分中的颜色为日期和时间选择器控件中。|  
|[CDateTimeCtrl::SetMonthCalFont](../Topic/CDateTimeCtrl::SetMonthCalFont.md)|设置日期和时间选择器控件的子month calendar控件将使用的字体。|  
|[CDateTimeCtrl::SetMonthCalStyle](../Topic/CDateTimeCtrl::SetMonthCalStyle.md)|设置当前日期和时间选择器控件的样式。|  
|[CDateTimeCtrl::SetRange](../Topic/CDateTimeCtrl::SetRange.md)|设置最小值和最大值允许的系统时间的日期和时间选择器控件。|  
|[CDateTimeCtrl::SetTime](../Topic/CDateTimeCtrl::SetTime.md)|将日期和时间选择器控件的时间。|  
  
## 备注  
 日期和时间选择器控件\(DTP控件\)提供简单的接口交换日期和时间信息与用户。  此接口包含字段，每个显示该控件存储的日期和时间信息的部分。  用户可以更改在控件中存储的信息通过更改字符串的内容在特定字段。  使用鼠标或键盘，用户可以从域移动到域。  
  
 通过应用各种样式自定义日期和时间选择器控件应用于对象，在创建它。  在参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 的 [日期和时间选择器控件样式](http://msdn.microsoft.com/library/windows/desktop/bb761728) 有关样式的更多信息特定于日期和时间选择器控件。  使用布局样式，可以将DTP控件的显示格式。  这些格式样式。[!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 主题 [日期和时间选择器控件样式](http://msdn.microsoft.com/library/windows/desktop/bb761728)介绍在“格式下样式”。  
  
 日期和时间选择器控件还使用通知和回调，在 [使用CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)所述。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDateTimeCtrl`  
  
## 要求  
 **Header:** afxdtctl.h  
  
## 请参阅  
 [MFC示例CMNCTRL1](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMonthCalCtrl Class](../../mfc/reference/cmonthcalctrl-class.md)