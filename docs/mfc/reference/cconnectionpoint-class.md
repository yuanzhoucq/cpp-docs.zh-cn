---
title: "CConnectionPoint Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CConnectionPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CConnectionPoint class"
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CConnectionPoint Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义用于接口的特定类型与其他OLE对象进行通信，称为“连接点”。  
  
## 语法  
  
```  
class CConnectionPoint : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CConnectionPoint::CConnectionPoint](../Topic/CConnectionPoint::CConnectionPoint.md)|构造 `CConnectionPoint` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CConnectionPoint::GetConnections](../Topic/CConnectionPoint::GetConnections.md)|在连接映射检索所有连接点。|  
|[CConnectionPoint::GetContainer](../Topic/CConnectionPoint::GetContainer.md)|检索拥有连接映射到控件的容器。|  
|[CConnectionPoint::GetIID](../Topic/CConnectionPoint::GetIID.md)|检索接口ID连接点。|  
|[CConnectionPoint::GetMaxConnections](../Topic/CConnectionPoint::GetMaxConnections.md)|检索最大连接数。点支持由控件。|  
|[CConnectionPoint::GetNextConnection](../Topic/CConnectionPoint::GetNextConnection.md)|检索指向连接组件在 `pos`。|  
|[CConnectionPoint::GetStartPosition](../Topic/CConnectionPoint::GetStartPosition.md)|通过返回传递到 `GetNextConnection` 调用的 **POSITION** 值开头映射迭代。|  
|[CConnectionPoint::OnAdvise](../Topic/CConnectionPoint::OnAdvise.md)|调用由结构，在生成或中断连接时。|  
|[CConnectionPoint::QuerySinkInterface](../Topic/CConnectionPoint::QuerySinkInterface.md)|检索指向请求的接收接口。|  
  
## 备注  
 不同于常规的OLE接口，用于实现和显示OLE控件的功能，连接点实现可以启动对其他对象的事件，如激发事件和更改通知的一个输出接口。  
  
 连接由两部分组成:调用接口的对象，称为“源”，以及实现接口的对象，称为“接收器”。通过显示连接点，源允许接收器生成与自身的连接。  通过连接点机制，源对象获取指向接收器的实现一组成员函数。  例如，通过调用接收器实现的事件，源可以调用接收器的实现的相应方法。  
  
 默认情况下，`COleControl`派生类实现两个连接点:事件的和属性更改通知的。  这些连接使用，分别，为事件激发以及通知接收器\(例如，控件的容器\)，当属性值更改时。  support用于OLE控件还提供其他的连接点的实现。  对于每个附加的连接点实现在控件选件类，则您必须声明“连接部件”该连接点的实现。  如果实现一个或多个连接点，还需要声明单一“连接映射”在控件选件类。  
  
 下面的示例演示简单的连接映射，然后对 `Sample` OLE控件连接点，包括代码的两个片段:第一部分声明连接映射点;第二个实现此映射点。  第一个片段插入到控件选件类的声明，如 `protected` 部分:  
  
 [!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/CPP/cconnectionpoint-class_1.h)]  
  
 `BEGIN_CONNECTION_PART` 和 `END_CONNECTION_PART` 宏声明嵌入选件类，`XSampleConnPt` \(从派生\) `CConnectionPoint`此特定连接点的实现。  如果要重写任何 `CConnectionPoint` 成员函数或添加自己的成员函数中，声明它们在这两个宏之间。  例如，`CONNECTION_IID` 宏重写 `CConnectionPoint::GetIID` 成员函数，放置在这两个宏之间。  
  
 第二个代码段插入到实现文件\(.CPP\)您的控件选件类。  此代码实现连接映射，包括附加的连接点，`SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/CPP/cconnectionpoint-class_2.cpp)]  
  
 对于插入了这些代码片段，示例OLE控件将显示 **ISampleSink** 接口的连接点。  
  
 通常，连接点支持“多路广播”，是指广播到多个接收器连接到同一接口。  下面的代码片段演示如何通过重复完成多路广播通过中的每个接收器连接点:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/CPP/cconnectionpoint-class_3.cpp)]  
  
 此示例检索当前设置在 `SampleConnPt` 的连接连接点用于对 `CConnectionPoint::GetConnections`。  它通过连接然后重复并对每个活动连接的 `ISampleSink::SinkFunc`。  
  
 有关使用 `CConnectionPoint`的更多信息，请参见文章 [连接点](../../mfc/connection-points.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CConnectionPoint`  
  
## 要求  
 **Header:** afxdisp.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)