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
ms.openlocfilehash: fc33df6957beab6e4e8de3093dfc00cf2651780e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370512"
---
# <a name="handlers-for-message-map-ranges"></a>消息映射范围的处理程序

本文介绍如何将一系列消息映射到单个消息处理程序函数（而不是将一条消息映射到只有一个函数）。

有时，您需要以完全相同的方式处理多条消息或控制通知。 在这种情况下，您可能希望将所有消息映射到单个处理程序函数。 消息映射范围允许您对连续的消息范围执行此操作：

- 您可以将命令 ID 的范围映射到：

  - 命令处理程序函数。

  - 命令更新处理程序函数。

- 您可以将一系列控件的 I 将控件通知消息映射到消息处理程序函数。

本文涵盖的主题包括：

- [编写消息映射条目](#_core_writing_the_message.2d.map_entry)

- [声明处理程序函数](#_core_declaring_the_handler_function)

- [命令 I 系列的示例](#_core_example_for_a_range_of_command_ids)

- [控件一系列指示器的示例](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>编写消息映射条目

在。CPP 文件，添加消息映射条目，如以下示例所示：

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

消息映射条目由以下项组成：

- 消息映射范围宏：

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- 宏的参数：

  前两个宏采用三个参数：

  - 启动范围的命令 ID

  - 结束范围的命令 ID

  - 消息处理程序函数的名称

  命令指示的范围从连续的。

  第三个宏`ON_CONTROL_RANGE`，获取额外的第一个参数：控制通知消息，如**EN_CHANGE**。

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>声明处理程序函数

在 中添加处理程序函数声明。H 文件。 以下代码显示了可能如下所示，如下所示：

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

单个命令的处理程序函数通常不采用任何参数。 除了更新处理程序函数外，消息映射范围的处理程序函数需要**UINT**类型的额外参数*nID*。 此参数是第一个参数。 额外参数容纳指定用户实际选择的命令所需的额外命令 ID。

有关更新处理程序函数的参数要求的详细信息，请参阅命令[I 范围示例](#_core_example_for_a_range_of_command_ids)。

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>命令指示范围的示例

何时可以使用范围 一个示例是处理 MFC 示例[HIERSVR](../overview/visual-cpp-samples.md)中的缩放命令等命令。 此命令可缩放视图，将其缩放在正常大小的 25% 到 300% 之间。 HIERSVR 的视图类使用范围来处理缩放命令，其消息映射条目类似于：

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

编写消息映射条目时，指定：

- 两个命令指示，开始和结束连续范围。

   在这里，他们是**ID_VIEW_ZOOM25**和**ID_VIEW_ZOOM300。**

- 命令的处理程序函数的名称。

   这里是`OnZoom`。

函数声明类似于：

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

更新处理程序函数的情况类似，并且可能更有用。 为许多命令编写`ON_UPDATE_COMMAND_UI`处理程序，并发现自己一遍又一遍地编写或复制相同的代码是很常见的。 解决方案是使用`ON_UPDATE_COMMAND_UI_RANGE`宏将命令指示数范围映射到一个更新处理程序函数。 命令指示必须形成连续范围。 例如，请参阅 HIERSVR 示例的视图类中的`OnUpdateZoom`处理程序及其`ON_UPDATE_COMMAND_UI_RANGE`消息映射条目。

单个命令的更新处理程序函数通常采用类型`CCmdUI*`为 的单个参数*pCmdUI。* 与处理程序函数不同，消息映射范围的更新处理程序函数不需要**UINT**类型的额外参数*nID*。 命令 ID（用于指定用户实际选择的命令）在`CCmdUI`对象中找到。

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>控制指示范围的示例

另一个有趣的情况是，将一系列控件的 I 将控制通知消息映射到单个处理程序。 假设用户可以单击 10 个按钮中的任何一个。 要将所有 10 个按钮映射到一个处理程序，消息映射条目如下所示：

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

在消息映射中`ON_CONTROL_RANGE`写入宏时，请指定：

- 特定的控制通知消息。

   这是**BN_CLICKED。**

- 与控件的连续范围关联的控件 ID 值。

   这里是**IDC_BUTTON1**和**IDC_BUTTON10。**

- 消息处理程序函数的名称。

   这里是`OnButtonClicked`。

编写处理程序函数时，请指定额外的**UINT**参数，如下所示：

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

单个`OnButtonClicked`**BN_CLICKED**消息的处理程序不采用任何参数。 一系列按钮的同一处理程序需要一个**UINT**。 额外的参数允许识别负责生成**BN_CLICKED**消息的特定控件。

示例中显示的代码是典型的：将传递`int`的值转换为消息范围内的值，并断言情况确实如此。 然后，您可以根据单击的按钮执行一些不同的操作。

## <a name="see-also"></a>另请参阅

[声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
