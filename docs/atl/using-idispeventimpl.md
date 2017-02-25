---
title: "Using IDispEventImpl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDispEventImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventImpl class, using"
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Using IDispEventImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在使用 `IDispEventImpl` 处理事件时，您需要:  
  
-   从 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)派生您的选件类。  
  
-   添加 [事件接收器映射](../Topic/BEGIN_SINK_MAP.md) 到您的选件类。  
  
-   使用 [SINK\_ENTRY](../Topic/SINK_ENTRY.md) 或 [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY_EX.md) 宏，将项添加到事件接收器映射。  
  
-   执行方法您对处理感兴趣。  
  
-   建议和unadvise事件源。  
  
## 示例  
 在下面的示例显示了处理 **DocumentChange** 事件如何通过运行的 **Application** 对象激发的。  此事件定义为 **ApplicationEvents** 调度接口的方法。  
  
 此示例是从 [ATLEventHandling示例](../top/visual-cpp-samples.md)。  
  
 `[`  
  
 `uuid(000209F7-0000-0000-C000-000000000046),`  
  
 `hidden`  
  
 `]`  
  
 `dispinterface ApplicationEvents {`  
  
 `properties:`  
  
 `methods:`  
  
 `[id(0x00000001), restricted, hidden]`  
  
 `void Startup();`  
  
 `[id(0x00000002)]`  
  
 `void Quit();`  
  
 `[id(0x00000003)]`  
  
 `void DocumentChange();`  
  
 `};`  
  
 该示例使用 `#import` 从生成的类型库所需的标头文件。  如果要使用Word的其他版本的此示例，必须指定正确的mso dll文件。  例如，Office 2000提供mso9.dll，而Office XP提供mso.dll。  此代码从stdafx.h简化:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/CPP/using-idispeventimpl_1.h)]  
  
 下面的代码显示NotSoSimple.h。  相关代码按注释说明:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/CPP/using-idispeventimpl_2.h)]  
  
## 请参阅  
 [事件处理](../atl/event-handling-and-atl.md)   
 [ATLEventHandling示例](../top/visual-cpp-samples.md)