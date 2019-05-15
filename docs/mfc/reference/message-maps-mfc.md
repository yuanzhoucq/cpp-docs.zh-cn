---
title: 消息映射 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 14c08a008456160fe817f066e5b22b06b9f9fa14
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611815"
---
# <a name="message-maps-mfc"></a>消息映射 (MFC)

引用的此部分列出了所有[消息映射宏](../../mfc/reference/message-map-macros-mfc.md)和全部[CWnd](../../mfc/reference/cwnd-class.md)消息映射条目以及相应的成员函数原型：

|类别|描述|
|--------------|-----------------|
|ON\_命令消息处理程序|处理`WM_COMMAND`用户菜单选项或菜单访问键生成的消息。|
|[子窗口通知消息处理程序](../../mfc/reference/child-window-notification-message-handlers.md)|处理来自子窗口通知消息。|
|[WM_ 消息处理程序](../../mfc/reference/handlers-for-wm-messages.md)|处理`WM_`消息，如`WM_PAINT`。|
|[用户定义消息处理程序](../../mfc/reference/user-defined-handlers.md)|处理用户定义的消息。|

(有关术语和本参考中使用的约定的说明，请参阅[如何使用消息映射交叉引用](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)。)

由于 Windows 是一个面向消息的操作系统，对 Windows 环境进行编程有很大一部分涉及到消息处理。 每次单击击键或鼠标等事件发生时，消息发送到应用程序，然后必须处理该事件。

Microsoft 基础类库提供了优化的基于消息的编程的编程模型。 在此模型中，"消息映射"用于指定哪些函数将处理特定类的各种消息。 消息映射包含指定的消息将由哪些函数处理的一个或多个宏。 例如，一个消息映射，其中包含`ON_COMMAND`宏可能如下所示：

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

`ON_COMMAND`宏用于处理生成的菜单、 按钮和快捷键的命令消息。 [宏](../../mfc/reference/message-map-macros-mfc.md)包含可映射以下：

## <a name="windows-messages"></a>Windows 消息

- 控件通知

- 用户定义的消息

## <a name="command-messages"></a>命令消息

- 已注册的用户定义的消息

- 用户界面更新消息

## <a name="ranges-of-messages"></a>范围的消息

- 命令

- 更新处理程序的消息

- 控件通知

尽管消息映射宏很重要，但你通常不必直接使用它们。 这是因为属性窗口时自动创建消息映射条目在源文件中使用它来将消息处理函数与消息相关联。 无论的何时想要编辑或添加一个消息映射条目，可以使用属性窗口。

> [!NOTE]
>  属性窗口不支持消息映射范围。 您必须自己编写这些消息映射条目。

但是，消息映射是 Microsoft 基础类库的一个重要部分。 您应了解它们的功能，并为其提供文档。

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
