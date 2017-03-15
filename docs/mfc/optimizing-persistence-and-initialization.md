---
title: "优化持久性和初始化 | Microsoft Docs"
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
  - "MFC ActiveX 控件, 优化"
  - "优化, ActiveX 控件"
  - "优化性能, ActiveX 控件"
  - "性能, ActiveX 控件"
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 优化持久性和初始化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，保持和初始化该控件由 `DoPropExchange` 成员函数处理。  在一个典型的控件，该函数包含对多种 **PX\_** 函数 \(`PX_Color`，`PX_Font`，依此类推\)，每个属性。  
  
 此方法有一些优点一个 `DoPropExchange` 实现可以用于初始化，用于保持以二进制格式为持久性和在某些使用容器的所谓的“属性”包格式。  这一功能在合适的位置提供有关属性及其默认值的所有信息。  
  
 但是，这是一般性牺牲效率。  **PX\_** 函数通过比直接的更多本质上效率低多层的实现获取灵活性，但是，更不灵活，方法。  此外，如果控制传递，默认值设置 **PX\_** 函数，即使在以下情况下必须每当提供该默认值，那么，当绑定时可以不使用默认值。  如果生成默认值是一项重要任务 \(例如，环境属性，则值从一获取\)，则额外，不必要的工作已完成，在不使用的情况下默认值。  
  
 您可以通过重写控件的 `Serialize` 功能提高控件的二进制的性能。  该成员函数的默认实现调用 `DoPropExchange` 函数。  通过重写，它可用于二进制持久性提供更简单的实现。  例如，请考虑此 `DoPropExchange` 函数：  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_1.cpp)]  
  
 为了改进此控件的二进制的性能，您可以重写 `Serialize` 函数类似：  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_2.cpp)]  
  
 局部 `dwVersion` 变量可用于检测控件的持久状态的版本加载或保存。  可以使用此变量 \(而非调用 [CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md)。  
  
 若要节省中持久格式的 ACE 空间 **BOOL** 属性 \(和保存其与 `PX_Bool`生成的格式兼容\)，也可以将属性视为 **BYTE**，如下所示：  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_3.cpp)]  
  
 注意，在负载情况，临时变量使用其值然后分配，而不是引用 `m_boolProp` 转换为 **BYTE**。  铸造路由只会修改的字节 `m_boolProp`，同时保持其余的字节中移除该初始化。  
  
 对于同一控件中，也可以通过重写控件 [COleControl::OnResetState](../Topic/COleControl::OnResetState.md) 优化的按如下方式初始化：  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_4.cpp)]  
  
 尽管 `Serialize` 和 `OnResetState` 重写，应保持完整 `DoPropExchange` 函数，因为为仍然使用持久性。属性包格式。  维护所有三这些函数必须确保控件的一致地管理其属性，保持机制容器使用。  
  
## 请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)