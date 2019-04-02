---
title: 消息映射范围的处理程序
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
ms.openlocfilehash: d2bc961486d9bc686e1ca0d5feb0fe01d65f9512
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773991"
---
# <a name="handlers-for-message-map-ranges"></a>消息映射范围的处理程序

本文介绍如何将一系列消息映射到单个消息处理程序函数 （而不是将一条消息映射到一个功能）。

有些的时候需要在完全相同的方式处理多个消息或控件通知。 在这种情况下，你可能想要将所有的消息映射到单个处理程序函数。 消息映射范围允许你为连续范围的消息执行此操作：

- 可以映射到的命令 Id 的范围：

  - 命令处理程序函数。

  - 一个命令更新处理程序函数。

- 可以将一系列控件 Id 的控件通知消息映射到消息处理程序函数。

在本文中涵盖的主题包括：

- [编写消息映射条目](#_core_writing_the_message.2d.map_entry)

- [声明处理程序函数](#_core_declaring_the_handler_function)

- [范围内的命令 Id 的示例](#_core_example_for_a_range_of_command_ids)

- [范围的控件 Id 的示例](#_core_example_for_a_range_of_control_ids)

##  <a name="_core_writing_the_message.2d.map_entry"></a> 编写消息映射条目

在。CPP 文件中，添加你的消息映射条目，如下面的示例中所示：

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

消息映射条目包括以下各项：

- 消息映射范围宏：

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- 在宏参数：

  前两个宏采用三个参数：

  - 范围的起始命令 ID

  - 命令 ID 范围的结束

  - 消息处理程序函数的名称

  命令 Id 的范围必须是连续的。

  第三个宏`ON_CONTROL_RANGE`，采用附加第一个参数： 控件通知消息，如**EN_CHANGE**。

##  <a name="_core_declaring_the_handler_function"></a> 声明处理程序函数

添加处理程序函数声明中的。H 文件。 下面的代码演示如何这看起来，如下所示：

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

单个命令的处理程序函数通常不带任何参数。 更新处理程序函数，但消息映射范围的处理程序函数需要一个额外的参数， *nID*，类型的**UINT**。 此参数是第一个参数。 额外的参数提供额外的命令 ID，用于指定用户实际选择哪个命令。

有关更新处理程序函数的参数要求的详细信息，请参阅[示例的范围内的命令 Id 的](#_core_example_for_a_range_of_command_ids)。

##  <a name="_core_example_for_a_range_of_command_ids"></a> 范围的命令 Id 的示例

何时可以使用一个示例是在处理命令，例如 MFC 示例中的缩放命令的范围[HIERSVR](../overview/visual-cpp-samples.md)。 此命令会放大的视图中，缩放 25%到其正常尺寸的 300%之间。 HIERSVR 的视图类使用范围来处理与类似于这样的消息映射条目的缩放命令：

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

当您编写的消息映射条目，则指定：

- 两个命令 Id，开始和结束连续范围。

   它们就在这里**ID_VIEW_ZOOM25**并**ID_VIEW_ZOOM300**。

- 命令处理程序函数的名称。

   此处它具有`OnZoom`。

函数声明将类似于以下：

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

更新处理程序函数的情况是类似，并可能具有更广泛的用途。 它是很常见，编写`ON_UPDATE_COMMAND_UI`的处理程序的命令数，将发现自己编写，或复制，相同的代码反复。 解决方法是映射到一个 Id 更新处理程序函数使用的命令范围`ON_UPDATE_COMMAND_UI_RANGE`宏。 命令 Id 必须形成连续的范围。 有关示例，请参阅`OnUpdateZoom`处理程序并将其`ON_UPDATE_COMMAND_UI_RANGE`HIERSVR 示例视图类中的消息映射条目。

更新处理程序函数的单个命令通常采用一个参数， *pCmdUI*，类型的`CCmdUI*`。 与处理程序函数，不同的消息映射范围的更新处理程序函数不需要一个额外的参数， *nID*，类型的**UINT**。 在中找到的命令 ID，需要指定该命令在用户实际选择`CCmdUI`对象。

##  <a name="_core_example_for_a_range_of_control_ids"></a> 范围的控件 Id 的示例

另一个有趣的情况范围的控件 Id 的控件通知消息映射到单个处理程序。 假设用户可以单击任何 10 个按钮。 若要将所有 10 个按钮映射到一个处理程序，您的消息映射条目将类似如下：

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

当你编写`ON_CONTROL_RANGE`消息映射中的宏，则指定：

- 特定的控件通知消息。

   此处却**BN_CLICKED**。

- 与连续范围的控件关联的控件 ID 值。

   这些如下**IDC_BUTTON1**并**IDC_BUTTON10**。

- 消息处理程序函数的名称。

   此处它具有`OnButtonClicked`。

当您编写处理程序函数时，指定额外**UINT**参数，如以下所示：

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

`OnButtonClicked`处理程序的单个**BN_CLICKED**消息不需要任何参数。 为一系列按钮相同的处理程序将其中一个**UINT**。 额外的参数，用于标识特定的控件负责生成**BN_CLICKED**消息。

在示例中所示的代码是典型： 将值传递给转换`int`消息范围内定义这种情况下断言。 然后，您可能需要一些不同的操作，具体取决于所单击的按钮。

## <a name="see-also"></a>请参阅

[声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
