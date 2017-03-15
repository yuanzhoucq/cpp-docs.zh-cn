---
title: "Using IDispEventSimpleImpl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDispEventSimpleImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventSimpleImpl class, using"
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Using IDispEventSimpleImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在使用 `IDispEventSimpleImpl` 处理事件时，您需要:  
  
-   从 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)派生您的选件类。  
  
-   添加 [事件接收器映射](../Topic/BEGIN_SINK_MAP.md) 到您的选件类。  
  
-   定义描述操作的 [\_ATL\_FUNC\_INFO](../atl/reference/atl-func-info-structure.md) 结构。  
  
-   使用 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md) 宏，将项添加到事件接收器映射。  
  
-   执行方法您对处理感兴趣。  
  
-   建议和unadvise事件源。  
  
## 示例  
 在下面的示例显示了您处理 **DocumentChange** 事件如何通过运行的 **Application** 对象激发的。  此事件定义为 **ApplicationEvents** 调度接口的方法。  
  
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
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/CPP/using-idispeventsimpleimpl_1.h)]  
  
 从类型用于此示例实际的库的所有信息是Word **Application** 对象和 **ApplicationEvents** 接口的IID的CLSID。  此信息只使用在编译时。  
  
 下面的代码显示Simple.h。  相关代码按注释说明:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/CPP/using-idispeventsimpleimpl_2.h)]  
  
 下面的代码是从Simple.cpp:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/CPP/using-idispeventsimpleimpl_3.cpp)]  
  
## 请参阅  
 [事件处理](../atl/event-handling-and-atl.md)   
 [ATLEventHandling示例](../top/visual-cpp-samples.md)