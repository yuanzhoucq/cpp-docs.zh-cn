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
ms.openlocfilehash: c14d8247be2abdf828b88e728bd930691ec6571f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214147"
---
# <a name="connection-points"></a>连接点

本文说明如何使用 MFC 类和实现连接点（以前称为 OLE 连接点） `CCmdTarget` `CConnectionPoint` 。

过去，组件对象模型（COM）定义了一个 `IUnknown::QueryInterface` 允许对象实现并公开接口中的功能的常规机制（*）。 但是，如果未定义允许对象公开其调用特定接口功能的相应机制，则为。 也就是说，COM 定义了如何处理指向对象的传入指针（指向该对象的接口的指针），但它没有用于传出接口的显式模型（对象保存到其他对象接口的指针）。 COM 现在具有一个名为 "连接点" 的模型，该模型支持此功能。

连接具有两部分：调用接口的对象（称为 "源"）和一个实现接口的对象（称为接收器）。 连接点是由源公开的接口。 通过公开连接点，源允许接收器建立与自身（源）的连接。 通过连接点机制（ `IConnectionPoint` 接口），指向接收器接口的指针传递到源对象。 此指针提供源，可以访问接收器对一组成员函数的实现。 例如，若要激发由接收器实现的事件，源可以调用接收器实现的适当方法。 下图显示了刚刚介绍的连接点。

![已实现的连接点](../mfc/media/vc37lh1.gif "已实现的连接点") <br/>
已实现的连接点

MFC 在[CConnectionPoint](reference/cconnectionpoint-class.md)和[CCmdTarget](reference/ccmdtarget-class.md)类中实现此模型。 派生自 `CConnectionPoint` 的类实现 `IConnectionPoint` 接口，用于向其他对象公开连接点。 派生自的类 `CCmdTarget` 实现 `IConnectionPointContainer` 接口，该接口可枚举对象的所有可用连接点或查找特定连接点。

对于在类中实现的每个连接点，必须声明实现连接点的连接部分。 如果实现一个或多个连接点，则还必须在类中声明一个连接映射。 连接映射是 ActiveX 控件支持的连接点表。

下面的示例演示了一个简单的连接映射和一个连接点。 第一个示例声明连接映射和点;第二个示例实现了地图和点。 请注意， `CMyClass` 必须是 `CCmdTarget` 派生类。 在第一个示例中，代码将插入到类声明中的 **`protected`** 以下部分：

[!code-cpp[NVC_MFCConnectionPoints#1](codesnippet/cpp/connection-points_1.h)]

**BEGIN_CONNECTION_PART**和**END_CONNECTION_PART**宏声明 `XSampleConnPt` `CConnectionPoint` 实现此特定连接点的嵌入类（派生自）。 如果要重写任何 `CConnectionPoint` 成员函数或添加自己的成员函数，请在这两个宏之间进行声明。 例如，当在 `CONNECTION_IID` `CConnectionPoint::GetIID` 两个宏之间放置成员函数时，宏会重写该函数。

在第二个示例中，代码插入到控件的实现文件（.cpp 文件）中。 此代码实现连接映射，其中包括连接点 `SampleConnPt` ：

[!code-cpp[NVC_MFCConnectionPoints#2](codesnippet/cpp/connection-points_2.cpp)]

如果类具有多个连接点，请在**BEGIN_CONNECTION_MAP**和**END_CONNECTION_MAP**宏之间插入其他**CONNECTION_PART**宏。

最后， `EnableConnections` 在类的构造函数中添加对的调用。 例如：

[!code-cpp[NVC_MFCConnectionPoints#3](codesnippet/cpp/connection-points_3.cpp)]

插入此代码后， `CCmdTarget` 派生类将公开接口的连接点 `ISampleSink` 。 下图说明了此示例。

![使用 MFC 实现的连接点](../mfc/media/vc37lh2.gif "使用 MFC 实现的连接点") <br/>
使用 MFC 实现的连接点

通常，连接点支持 "多播"-广播到连接到同一接口的多个接收器。 以下示例段演示了如何通过循环访问连接点上的每个接收器来进行多播：

[!code-cpp[NVC_MFCConnectionPoints#4](codesnippet/cpp/connection-points_4.cpp)]

此示例 `SampleConnPt` 通过调用来检索连接点上的当前连接集 `CConnectionPoint::GetConnections` 。 然后，它会遍历连接，并对 `ISampleSink::SinkFunc` 每个活动的连接调用。

## <a name="see-also"></a>另请参阅

[MFC COM](mfc-com.md)
