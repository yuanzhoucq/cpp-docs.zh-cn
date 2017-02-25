---
title: "调度映射 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调度映射宏"
  - "调度映射"
  - "调度映射宏"
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 调度映射
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE 自动化提供了调用方法和访问跨越应用程序的属性。  调度的这些请求 Microsoft 基础类 \(MFC\) 库提供的机制是将函数对象和属性为内部和外部名称的映射计划“，”，以及属性的数据类型和函数参数。  
  
### 计划映射  
  
|||  
|-|-|  
|[DECLARE\_DISPATCH\_MAP](../Topic/DECLARE_DISPATCH_MAP.md)|声明将计划映射用于公开类的方法和属性 \(必须在类中声明\)。|  
|[BEGIN\_DISPATCH\_MAP](../Topic/BEGIN_DISPATCH_MAP.md)|开始计划映射中定义。|  
|[END\_DISPATCH\_MAP](../Topic/END_DISPATCH_MAP.md)|结束计划映射中定义。|  
|[DISP\_FUNCTION](../Topic/DISP_FUNCTION.md)|用于在调度映射定义的 OLE 自动化的函数。|  
|[DISP\_PROPERTY](../Topic/DISP_PROPERTY.md)|定义了 OLE 自动化属性。|  
|[DISP\_PROPERTY\_EX](../Topic/DISP_PROPERTY_EX.md)|定义了 OLE 自动化属性命名为 Get 和 Set 函数。|  
|[DISP\_PROPERTY\_NOTIFY](../Topic/DISP_PROPERTY_NOTIFY.md)|定义一通知的 OLE 自动化属性。|  
|[DISP\_PROPERTY\_PARAM](../Topic/DISP_PROPERTY_PARAM.md)|定义参数并命名 get 和 set 函数的 OLE 自动化属性。|  
|[DISP\_DEFVALUE](../Topic/DISP_DEFVALUE.md)|使现有属性默认值的对象。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)