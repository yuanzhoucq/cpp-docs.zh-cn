---
title: "标准对话框数据交换例程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "标准对话框, 数据交换例程"
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
caps.latest.revision: 13
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 标准对话框数据交换例程
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此主题列出了常见的 MFC 对话框控件的标准对话框数据交换 \(DDX\) 例程。  
  
> [!NOTE]
>  标准对话框数据交换的例程在头文件 afxdd\_.h. 定义。  但是，您的应用程序应该包括 afxwin.h。  
  
### DDX 函数  
  
|||  
|-|-|  
|[DDX\_CBIndex](../Topic/DDX_CBIndex.md)|初始化组合框或检索控件中的当前选定内容的索引。|  
|[DDX\_CBString](../Topic/DDX_CBString.md)|初始化或检索组合框控件的编辑字段的当前内容。|  
|[DDX\_CBStringExact](../Topic/DDX_CBStringExact.md)|初始化或检索组合框控件的编辑字段的当前内容。|  
|[DDX\_Check](../Topic/DDX_Check.md)|初始化或检索复选框控件的当前状态。|  
|[DDX\_Control](../Topic/DDX_Control.md)|子类对话框内的特定控件。|  
|[DDX\_DateTimeCtrl](../Topic/DDX_DateTimeCtrl.md)|初始化或检索日期时间选择器控件日期和时间的数据。|  
|[DDX\_IPAddress](../Topic/DDX_IPAddress.md)|初始化或检索 IP 地址控件的当前值。|  
|[DDX\_LBIndex](../Topic/DDX_LBIndex.md)|初始化或检索列表框控件中当前选择的索引。|  
|[DDX\_LBString](../Topic/DDX_LBString.md)|初始化或检索在列表框控件中的当前选择。|  
|[DDX\_LBStringExact](../Topic/DDX_LBStringExact.md)|初始化或检索在列表框控件中的当前选择。|  
|[DDX\_MonthCalCtrl](../Topic/DDX_MonthCalCtrl.md)|初始化或检索月历控件的当前值。|  
|[DDX\_Radio](../Topic/DDX_Radio.md)|初始化或检索在单选控件组中当前检查无线控制的从 0 开始的索引。|  
|[DDX\_Scroll](../Topic/DDX_Scroll.md)|初始化或检索滚动控件的缩略图的当前位置。|  
|[DDX\_Slider](../Topic/DDX_Slider.md)|初始化或检索滑块控件的缩略图的当前位置。|  
|[DDX\_Text](../Topic/DDX_Text.md)|初始化或检索编辑控件的当前值。|  
  
## 请参阅  
 [标准对话框数据验证例程](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)