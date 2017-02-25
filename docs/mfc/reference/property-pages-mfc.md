---
title: "属性页 (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 中的属性页数据传输函数"
  - "属性页, 全局 MFC 函数"
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 属性页 (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

属性页通过支持基于对话框的数据配置机制显示当前值在自定义图形接口，OLE 控件的特定属性显示和编辑数据交换 \(DDX\)。  
  
 此数据分析机制映射属性页控件对 OLE 控件的各个属性。  控件属性的值以反映属性页的状态控件或内容。  属性页控件和属性之间的映射。**DDP\_** 函数调用指定在属性页的 `DoDataExchange` 成员函数。  以下是列表 **DDP\_** 函数使用控件的属性页数据交换，输入：  
  
### 属性页传输数据  
  
|||  
|-|-|  
|[DDP\_CBIndex](../Topic/DDP_CBIndex.md)|链接组合框中控件属性的选定字符串索引。|  
|[DDP\_CBString](../Topic/DDP_CBString.md)|连接组合框中控件属性的选定字符串属性。  选中的字符串可以以相同的字母开头，如属性值，但不需要完全匹配它。|  
|[DDP\_CBStringExact](../Topic/DDP_CBStringExact.md)|连接组合框中控件属性的选定字符串属性。  选定的字符串和属性字符串值必须完全匹配。|  
|[DDP\_Check](../Topic/DDP_Check.md)|链接控件中属性页上的复选框的控件的属性。|  
|[DDP\_LBIndex](../Topic/DDP_LBIndex.md)|使用控件的属性来链接列表框的选定字符串索引。|  
|[DDP\_LBString](../Topic/DDP_LBString.md)|链接列表框中控件属性的选定字符串。  选中的字符串可以以相同的字母开头，如属性值，但不需要完全匹配它。|  
|[DDP\_LBStringExact](../Topic/DDP_LBStringExact.md)|链接列表框中控件属性的选定字符串。  选定的字符串和属性字符串值必须完全匹配。|  
|[DDP\_PostProcessing](../Topic/DDP_PostProcessing.md)|完成属性值将从控件的。|  
|[DDP\_Radio](../Topic/DDP_Radio.md)|链接控件中的属性页的单选按钮组的控件的属性。|  
|[DDP\_Text](../Topic/DDP_Text.md)|链接控件中属性页上的控件的属性。  此函数处理属性的几种不同的类型，例如 **double**、**short**、`BSTR`和 **long**。|  
  
 有关 `DoDataExchange` 和属性页的更多信息，请参见知识库文章 [ActiveX 控件：属性页](../../mfc/mfc-activex-controls-property-pages.md)。  
  
 以下是宏的列表创建和管理一个 OLE 控件的属性页：  
  
### 属性页  
  
|||  
|-|-|  
|[BEGIN\_PROPPAGEIDS](../Topic/BEGIN_PROPPAGEIDS.md)|启动属性页 ID 列表。|  
|[END\_PROPPAGEIDS](../Topic/END_PROPPAGEIDS.md)|结束属性页 ID 列表。|  
|[PROPPAGEID](../Topic/PROPPAGEID.md)|声明控件类的属性页。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)