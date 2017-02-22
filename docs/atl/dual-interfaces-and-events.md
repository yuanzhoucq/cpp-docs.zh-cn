---
title: "Dual Interfaces and Events | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "双重接口, 事件"
  - "事件 [C++], 双重接口"
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Dual Interfaces and Events
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当设计事件接口为双时是可能的，有多种虚拟设计原因不这样做。  根本原因是事件的源只会激发此事件传递vtable或通过 `Invoke`，而不是两个。  如果事件源激发事件，当一个直接vtable调用方法，将不使用 `IDispatch` 方法，并清楚接口都应是纯vtable接口。  如果事件源激发该事件作为调用 `Invoke`，将不使用vtable方法，并清楚接口都应是调度接口。  如果定义了自己的事件接口双倍，您需要客户端实现不使用的接口。  
  
> [!NOTE]
>  此参数不适用于双重接口，通常。  从实现方面，双倍是实现到所有类型的客户端访问的接口一个express，方便支持的方式。  
  
 有进一步的原因避免双事件接口;Visual Basic和Internet Explorer不支持它们。  
  
## 请参阅  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)