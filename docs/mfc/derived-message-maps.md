---
title: 派生消息映射
ms.date: 11/19/2018
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: 2ae536a53a43472a4fb81d30e685fbc3faaa603f
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175595"
---
# <a name="derived-message-maps"></a>派生消息映射

消息处理期间，检查类自己的消息映射是否是消息映射描述的结尾。 会发生什么情况类`CMyView`(派生自`CView`) 具有一条消息没有匹配项

记住，`CView`（`CMyView` 的基类）是依次从 `CWnd` 派生的。 从而`CMyView`*是*`CView`并*是* `CWnd`。 这些类都有其自己的消息映射。 下图“视图层次结构”显示了类的层次关系，但记住，`CMyView` 对象是具有所有树类的特征的单个对象。

![视图层次结构](../mfc/media/vc38621.gif "视图层次结构") <br/>
视图层次结构

因此，如果消息无法在类 `CMyView` 的消息映射中匹配，则框架还将在其即时基类中搜索消息映射。 位于消息映射开头的 `BEGIN_MESSAGE_MAP` 宏将指定两个类名称作为其自变量：

[!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]

第一个自变量命名消息映射所属的类。 第二个参数提供与即时基类 `CView` 的关系，以便框架也可搜索其消息映射。

基类中提供的消息处理程序将由派生类集成。 这非常类似于标准虚拟成员函数，无需使所有处理程序成员函数成为虚拟。

如果在任何基类消息映射中都未找到处理程序，则将对消息执行默认处理。 如果消息是命令，则框架会将其路由至下一命令目标。 如果消息是标准 Windows 消息，则消息将传递给适当的默认窗口程序。

为了加快消息映射匹配，框架将根据再次收到相同的消息的可能性缓存最近的匹配项。 这样做的一个结果就是框架将非常高效地处理未处理的消息。 消息映射还比使用虚函数的实现更省空间。

## <a name="see-also"></a>请参阅

[框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)

