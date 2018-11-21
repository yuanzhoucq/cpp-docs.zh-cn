---
title: 连接点
ms.date: 11/19/2018
f1_keywords:
- IConnectionPoint
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
ms.openlocfilehash: bf21e7bf591a5b1977784db1542053817a73e6cd
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175478"
---
# <a name="connection-points"></a>连接点

此文章介绍了如何实现连接点 （以前称为 OLE 连接点） 使用 MFC 类`CCmdTarget`和`CConnectionPoint`。

在过去，组件对象模型 (COM) 定义的通用机制 (`IUnknown::QueryInterface`*) 允许对象实现和公开接口中的功能。 但是，未定义相应的机制，允许对象来公开其功能来调用特定的接口。 它是 COM 对象定义如何传入指针 （指向该对象的接口的指针） 进行处理，但它不具有输出接口 （该对象保存到其他对象的接口的指针） 的显式模型。 COM 现在具有一个模型，称为连接点支持此功能。

一个连接的两个部分： 调用调用源，并实现接口，该对象的接口的对象调用了接收器。 连接点是由源公开的接口。 通过公开连接点，源允许接收器来建立连接到其自身 （源）。 通过连接点机制 (`IConnectionPoint`接口)，到接收器接口的指针传递到源对象。 此指针提供有权访问接收器的实现的一组的成员函数的源。 例如，若要激发事件接收器实现的源可以调用的接收器的实现适当的方法。 下图演示了连接刚刚介绍的点。

![实现连接点](../mfc/media/vc37lh1.gif "实现连接点") <br/>
已实现的连接点

MFC 实现在此模型[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)并[CCmdTarget](../mfc/reference/ccmdtarget-class.md)类。 类派生自`CConnectionPoint`实现`IConnectionPoint`接口，用于公开与其他对象的连接点。 类派生自`CCmdTarget`实现`IConnectionPointContainer`接口，它可以枚举的所有对象的可用连接点或查找特定的连接点。

在您的类中实现每个连接点，您必须声明实现连接点的连接部分。 如果你实现一个或多个连接点，还必须在类中声明一个单一连接映射。 连接映射是 ActiveX 控件支持的连接点的表。

以下示例演示一个简单的连接映射和一个连接点。 第一个示例声明连接映射和点;第二个示例实现地图和点。 请注意，`CMyClass`必须是`CCmdTarget`-派生的类。 在第一个示例中，代码中插入类声明中下,**保护**部分：

[!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]

**BEGIN_CONNECTION_PART**并**END_CONNECTION_PART**宏声明嵌入的类， `XSampleConnPt` (派生自`CConnectionPoint`)，使实现此特定连接点。 如果你想要重写任何`CConnectionPoint`成员函数或添加您自己的成员函数，将它们声明两个两个宏之间。 例如，`CONNECTION_IID`宏重写`CConnectionPoint::GetIID`成员函数时放置在以下两个宏之间。

在第二个示例中，代码插入控件的实现文件 （.cpp 文件） 中。 该代码将实现连接映射，其中包括连接点， `SampleConnPt`:

[!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]

如果您的类具有多个连接点，插入其他**CONNECTION_PART**宏之间**BEGIN_CONNECTION_MAP**并**END_CONNECTION_MAP**宏。

最后，添加对的调用`EnableConnections`类的构造函数中。 例如：

[!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]

一旦已插入此代码，你`CCmdTarget`的派生的类公开的连接点`ISampleSink`接口。 下图演示了此示例。

![使用 MFC 实现的连接点](../mfc/media/vc37lh2.gif "使用 MFC 实现的连接点") <br/>
使用 MFC 实现连接点

通常情况下，连接点支持"多播"— 能够广播到多个接收器连接到相同的接口。 下面的示例片段演示如何通过迭代浏览每个接收器连接点上的多播：

[!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]

此示例检索当前的连接集上`SampleConnPt`连接点通过调用`CConnectionPoint::GetConnections`。 然后循环访问连接和调用`ISampleSink::SinkFunc`上每个活动连接。

## <a name="see-also"></a>请参阅

[MFC COM](../mfc/mfc-com.md)

