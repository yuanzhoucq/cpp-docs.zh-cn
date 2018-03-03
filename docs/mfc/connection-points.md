---
title: "连接点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- IConnectionPoint interface
- connections, connection points
- OLE COM connection points
- MFC COM, connection points
- COM, connection points
- interfaces, IConnectionPoint
- MFC, COM support
- connection points [MFC]
- CCmdTarget class [MFC], and connection points
- sinks, connection points
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d8bbb131aa5d4ce1b12cba84c3928b80a8b2a7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="connection-points"></a>连接点
此文章介绍了如何实现连接点 （以前称为 OLE 连接点） 使用的 MFC 类`CCmdTarget`和`CConnectionPoint`。  
  
 在过去，组件对象模型 (COM) 定义一种机制 (**iunknown:: Queryinterface**) 允许对象来实现和公开接口中的功能。 但是，未定义允许对象来公开其功能，若要调用的特定接口的相应机制。 COM，即对对象定义如何传入的指针 （指向该对象的接口） 的处理，但它不具有用于输出接口 （对象保存到其他对象的接口的指针） 的显式模型。 COM 现在具有一个模型，称为连接点支持此功能。  
  
 连接由两部分组成： 调用调用源，并实现该接口的对象的接口的对象调用了接收器。 连接点是由源公开的接口。 通过公开连接点，源允许建立到自身 （源） 连接的接收器。 通过连接点机制 ( **IConnectionPoint**接口)，指向接收器接口的指针传递到源对象。 此指针提供源有权访问的一组的成员函数的接收器的实现。 例如，若要激发事件接收器实现的源可以调用接收器的实现的适当方法。 下图演示了连接刚刚介绍的点。  
  
 ![实现连接点](../mfc/media/vc37lh1.gif "vc37lh1")  
已实现的连接点  
  
 MFC 实现在此模型[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)和[CCmdTarget](../mfc/reference/ccmdtarget-class.md)类。 类派生自**CConnectionPoint**实现**IConnectionPoint**用来公开对其他对象的连接点的接口。 类派生自`CCmdTarget`实现**IConnectionPointContainer**接口，可以枚举的所有对象的可用连接点或查找特定的连接点。  
  
 在你的类中实现每个连接点，您必须声明实现连接点的连接部分。 如果你实现一个或多个连接点，还必须在类中声明一个单一连接映射。 连接映射是 ActiveX 控件支持的连接点的表。  
  
 下面的示例演示一个简单的连接映射和一个连接点。 第一个示例声明了连接映射和点;第二个示例实现的映射和点。 请注意，`CMyClass`必须`CCmdTarget`-派生类。 在第一个示例中，插入代码在类声明中下,**保护**部分：  
  
 [!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]  
  
 `BEGIN_CONNECTION_PART`和**END_CONNECTION_PART**宏声明一个嵌入的类、 `XSampleConnPt` (派生自`CConnectionPoint`)，实现此特定连接点。 如果你想要重写任何`CConnectionPoint`成员函数或添加你自己的成员函数，将它们声明这些两个宏之间。 例如，`CONNECTION_IID`宏重写`CConnectionPoint::GetIID`成员函数时置于这些两个宏之间。  
  
 在第二个示例中，在控件实现文件 （.cpp 文件） 中插入代码。 此代码实现连接映射，其中包括连接点， `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]  
  
 如果你的类具有多个连接点，插入其他`CONNECTION_PART`宏之间`BEGIN_CONNECTION_MAP`和`END_CONNECTION_MAP`宏。  
  
 最后，添加对的调用`EnableConnections`类的构造函数中。 例如:  
  
 [!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]  
  
 一旦已插入此代码，你`CCmdTarget`-派生的类公开的连接点**ISampleSink**接口。 下图说明了此示例。  
  
 ![通过使用 MFC 实现连接点](../mfc/media/vc37lh2.gif "vc37lh2")  
使用 MFC 实现连接点  
  
 通常情况下，连接点支持"多播"-广播到多个接收器能够连接到相同的接口。 下面的示例片段演示了如何通过迭代浏览每个接收器连接点上的多播：  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]  
  
 此示例检索当前的一组连接上`SampleConnPt`连接点通过调用`CConnectionPoint::GetConnections`。 然后，循环访问的连接和调用**ISampleSink::SinkFunc**上每个活动连接。  
  
## <a name="see-also"></a>请参阅  
 [MFC COM](../mfc/mfc-com.md)

