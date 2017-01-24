---
title: "事件映射 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "事件映射"
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 事件映射
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

每当控件需要通知其容器某些操作 \(由控件开发\) 发生 \(如鼠标单击或按键、更改控制到状态\) 将调用事件触发函数。  该函数通知控件容器某些重要操作通过激发相关事件发生。  
  
 Microsoft 基础类 \(MFC\) 库提供优化激发的事件的编程模型。  在此模型中，在特定函数“控件的事件的事件映射”使用选定。  事件映射包含每个事件的宏。  例如，如下所示：激发一个库存单击事件的事件映射：  
  
 [!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/CPP/event-maps_1.cpp)]  
  
 **EVENT\_STOCK\_CLICK** 宏表示控件将激发它每次检测到鼠标单击的常用单击事件。  有关其他常用事件更详细的列表，请参见 [ActiveX 控件：事件](../../mfc/mfc-activex-controls-events.md)文章。  宏还可用一个自定义事件。  
  
 尽管事件映射宏是重要的，您并不直接通常插入它们。  这是因为当你使用消息关联消息处理函数时，属性窗口在源文件自动创建消息映射项。  任何时候你需要编辑或添加消息映射项，可以使用属性窗口。  
  
 若要支持事件映射，MFC 提供下面的宏：  
  
### 映射将声明和事件  
  
|||  
|-|-|  
|[DECLARE\_EVENT\_MAP](../Topic/DECLARE_EVENT_MAP.md)|声明事件映射在类映射事件向事件触发函数 \(必须在类中声明\)。|  
|[BEGIN\_EVENT\_MAP](../Topic/BEGIN_EVENT_MAP.md)|启动消息映射的定义 \(必须在类中实现。\)|  
|[END\_EVENT\_MAP](../Topic/END_EVENT_MAP.md)|启动消息映射的定义 \(必须在类中实现。\)|  
  
### 事件映射宏  
  
|||  
|-|-|  
|[EVENT\_CUSTOM](../Topic/EVENT_CUSTOM.md)|指示事件触发函数将触发指定的事件。|  
|[EVENT\_CUSTOM\_ID](../Topic/EVENT_CUSTOM_ID.md)|指示事件触发函数将触发指定的事件，并指定的调度 ID.|  
  
### 消息映射宏  
  
|||  
|-|-|  
|[ON\_OLEVERB](../Topic/ON_OLEVERB.md)|将 OLE 控件处理的自定义谓词。|  
|[ON\_STDOLEVERB](../Topic/ON_STDOLEVERB.md)|OLE 重写控件的标准谓词映射。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)