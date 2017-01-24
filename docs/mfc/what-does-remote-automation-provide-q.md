---
title: "远程自动化提供什么？ | Microsoft Docs"
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
  - "远程自动化, DCOM"
ms.assetid: 269ad218-e164-40ef-9b87-25fcc8ba21de
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 远程自动化提供什么？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

远程的自动化允许程序调用 `IDispatch` 实现从一台机器到另一台。  它还支持自动化需要的其他接口，特别是支持集合的 **IEnumVARIANT** 。  它不能提供分布其他 COM 接口 \( **IUnknown**，\)的能力，并且，像常规自动化，它包含封送仅支持自动化支持的那些数据类型。  
  
 此组功能允许程序访问方法和属性，包括在一个可访问的网络节点上运行的对象的返回集合或进一步自动化对象。  如果客户端也运行相应的软件，服务器可能会响应客户端，再次使用自动化功能 \(这仅为 32 位和 64 位客户端工作，是概念上类似于事件，尽管它不使用相同的机制\)。  
  
 对于应用程序作为远程的自动化服务器是可操作的，必须实现为可执行的 \(也就是说为“本地服务器”而不是“inproc 服务器”\)。  
  
## 请参阅  
 [远程自动化的适用条件](../mfc/where-does-remote-automation-fit-in-q.md)   
 [DCOM 历史记录](../mfc/history-of-dcom.md)