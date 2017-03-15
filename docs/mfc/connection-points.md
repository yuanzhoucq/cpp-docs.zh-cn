---
title: "连接点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IConnectionPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCmdTarget 类, 和连接点"
  - "COM, 连接点"
  - "连接点 [C++]"
  - "连接, 连接点"
  - "IConnectionPoint 接口"
  - "接口, IConnectionPoint"
  - "MFC [C++], COM 支持"
  - "MFC COM, 连接点"
  - "OLE COM 连接点"
  - "接收器, 连接点"
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 连接点
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何实现连接点 \(原来称作 OLE 连接点\) 使用 MFC 类，`CCmdTarget` 和 `CConnectionPoint`。  
  
 以前，组件对象模型 \(COM\) 允许 \(COM\) 定义对象实现和接口公开了功能的常规机制 \(**IUnknown::QueryInterface**\)。  不过，允许对象公开其功能调用特定接口对应的机制未定义。  也就是说 COM 定义为对象 \(该对象的接口指针的传入的指针\) 如何处理了，但没有输出接口显式的模型 \(指向对象持有对其他对象的接口\)。  COM 具有模型现在调用，连接点，则支持此功能。  
  
 连接由两部分组成：调用接口的对象，称作源和实现接口的对象，调用接收器。  连接点为源公开的接口。  通过公开连接点，源接收生成允许自身的连接 \(源\)。  通过连接点机制 \(即 **IConnectionPoint** 接口\)，到接收接口的指针传递到源对象。  该指针的源提供对一组的接收器实现的成员函数访问。  例如，接收器实现激发的事件调用的接收器，源可以实现相应的方法。  下图演示中描述的连接点。  
  
 ![已实现的连接点](../mfc/media/vc37lh1.png "vc37LH1")  
已实现的连接点  
  
 MFC 实现并在 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)[CCmdTarget](../mfc/reference/ccmdtarget-class.md) 此类模型。  从 **CConnectionPoint** 派生的类实现 **IConnectionPoint** 接口，用于向其他对象的连接点。  从 `CCmdTarget` 派生的类实现 **IConnectionPointContainer** 接口，则可以枚举所有对象的可用或连接点查找特定连接点。  
  
 为类实现的每个连接点，必须"声明"实现连接点的连接部分。  如果实现一个或多个连接点，必须还在类中声明单个串联映射。  连接映射是 ActiveX 控件支持连接点的表。  
  
 下面的示例演示简单的连接映射和使用连接点。  第一个示例声明连接映射和点；第二个示例实现映射和点。  注意 `CMyClass` 必须是 `CCmdTarget`派生类。  在第一个示例中，插入代码位于类声明，在 **protected** 部分下：  
  
 [!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/CPP/connection-points_1.h)]  
  
 `BEGIN_CONNECTION_PART` 和 **END\_CONNECTION\_PART** 宏声明嵌入的类中，`XSampleConnPt` \(从 `CConnectionPoint`派生\) 中实现，此特定连接点。  如果要重写任何 `CConnectionPoint` 成员函数或添加成员函数的声明，它们在这个宏。  例如，`CONNECTION_IID` 宏重写 `CConnectionPoint::GetIID` 成员函数，则将在这个宏。  
  
 在第二个示例中，代码在控件的实现文件 \(.cpp 文件\) 插入。  此代码实现一连接映射，包括，连接点 `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/CPP/connection-points_2.cpp)]  
  
 如果类具有多个连接点，请插入到 `BEGIN_CONNECTION_MAP` 和 `END_CONNECTION_MAP` 宏之间的附加 `CONNECTION_PART` 宏。  
  
 最后，添加一个调用到类的构造函数的 `EnableConnections`。  例如：  
  
 [!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/CPP/connection-points_3.cpp)]  
  
 在此代码粘贴，`CCmdTarget`派生类公开 **ISampleSink** 接口的连接点。  下图演示此示例。  
  
 ![使用 MFC 实现的连接点](../mfc/media/vc37lh2.png "vc37LH2")  
连接点实现使用 MFC  
  
 通常，支持连接点“多点发送”\- 功能广播到多个接收器连接到相同的接口。  下面的示例演示如何循环段通过访问多路广播在连接点的每接收：  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/CPP/connection-points_4.cpp)]  
  
 此示例检索当前设置 `SampleConnPt` 连接点的连接通过调用 `CConnectionPoint::GetConnections`。  它通过连接然后循环访问的并调用每个有效连接上的 **ISampleSink::SinkFunc**。  
  
## 请参阅  
 [MFC COM](../mfc/mfc-com.md)