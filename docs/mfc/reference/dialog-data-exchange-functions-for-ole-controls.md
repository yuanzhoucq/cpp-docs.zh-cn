---
title: "OLE 控件的对话框数据交换函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "对话框数据交换 (DDX), OLE 支持"
  - "OLE 控件, DDX 函数"
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# OLE 控件的对话框数据交换函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题列出 DDX\_OC 函数用于在一个 OLE 控件的属性之间交换数据，视图在对话框窗体或控件视图和对话框对象、窗体、视图或控件视图对象的数据成员。  
  
### DDX\_OC函数  
  
|||  
|-|-|  
|[DDX\_OCBool](../Topic/DDX_OCBool.md)|**BOOL** 管理数据传输。一个 OLE 控件的属性和数据成员 **BOOL** 之间的。|  
|[DDX\_OCBoolRO](../Topic/DDX_OCBoolRO.md)|**BOOL** 管理数据传输。一个 OLE 控件的只读属性和数据成员 **BOOL** 之间的。|  
|[DDX\_OCColor](../Topic/DDX_OCColor.md)|**OLE\_COLOR** 管理数据传输。一个 OLE 控件的属性和数据成员 **OLE\_COLOR** 之间的。|  
|[DDX\_OCColorRO](../Topic/DDX_OCColorRO.md)|**OLE\_COLOR** 管理数据传输。一个 OLE 控件的只读属性和数据成员 **OLE\_COLOR** 之间的。|  
|[DDX\_OCFloat](../Topic/DDX_OCFloat.md)|管理 **浮动** \(或 **double**\) 的数据传输。一个 OLE 控件的属性和 **浮动** \(或 **double**\) 数据成员之间的。|  
|[DDX\_OCFloatRO](../Topic/DDX_OCFloatRO.md)|管理 **浮动** \(或 **double**\) 的数据传输。一个 OLE 控件的只读属性和 **浮动** \(或 **double**\) 数据成员之间的。|  
|[DDX\_OCInt](../Topic/DDX_OCInt.md)|管理 `int` \(或 **long**\) 的数据传输。一个 OLE 控件的属性和 `int` \(或 **long**\) 数据成员之间的。|  
|[DDX\_OCIntRO](../Topic/DDX_OCIntRO.md)|管理 `int` \(或 **long**\) 的数据传输。一个 OLE 控件的只读属性和 `int` \(或 **long**\) 数据成员之间的。|  
|[DDX\_OCShort](../Topic/DDX_OCShort.md)|**short** 管理数据传输。一个 OLE 控件的属性和数据成员 **short** 之间的。|  
|[DDX\_OCShortRO](../Topic/DDX_OCShortRO.md)|**short** 管理数据传输。一个 OLE 控件的只读属性和数据成员 **short** 之间的。|  
|[DDX\_OCText](../Topic/DDX_OCText.md)|**CString** 管理数据传输。一个 OLE 控件的属性和数据成员 **CString** 之间的。|  
|[DDX\_OCTextRO](../Topic/DDX_OCTextRO.md)|**CString** 管理数据传输。一个 OLE 控件的只读属性和数据成员 **CString** 之间的。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)