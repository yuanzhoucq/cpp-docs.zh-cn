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
ms.openlocfilehash: 0ff9178679792929bbd6eb92bb6148cfa008dcad
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621696"
---
# <a name="handlers-for-message-map-ranges"></a>消息映射范围的处理程序

本文介绍如何将一系列消息映射到单个消息处理程序函数（而不是仅将一条消息映射到一个函数）。

有时，您需要以完全相同的方式处理多个消息或控件通知。 在这种情况下，你可能希望将所有消息映射到一个处理程序函数。 消息映射范围允许您为一系列连续的消息执行此操作：

- 可以将命令 Id 的范围映射到：

  - 命令处理程序函数。

  - 命令更新处理程序函数。

- 您可以将一系列控件 Id 的控制通知消息映射到消息处理程序函数。

本文中涵盖的主题包括：

- [写入消息映射项](#_core_writing_the_message.2d.map_entry)

- [声明处理函数](#_core_declaring_the_handler_function)

- [命令 Id 范围的示例](#_core_example_for_a_range_of_command_ids)

- [控制 Id 范围的示例](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>写入消息映射项

在。CPP 文件中，添加消息映射条目，如以下示例中所示：

[!code-cpp[NVC_MFCMessageHandling#6](codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

消息映射项由以下项组成：

- 消息映射范围宏：

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- 宏的参数：

  前两个宏采用三个参数：

  - 启动范围的命令 ID

  - 结束范围的命令 ID

  - 消息处理程序函数的名称

  命令 Id 的范围必须是连续的。

  第三个宏 `ON_CONTROL_RANGE` 使用额外的第一个参数：控件通知消息，如**EN_CHANGE**。

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>声明处理函数

在中添加处理函数声明。H 文件。 下面的代码演示了这种情况的外观，如下所示：

[!code-cpp[NVC_MFCMessageHandling#7](codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

用于单个命令的处理程序函数通常不采用任何参数。 除了更新处理程序函数之外，消息映射范围的处理程序函数需要**UINT**类型的额外参数*nID*。 此参数是第一个参数。 额外参数可容纳指定用户实际选择的命令所需的额外命令 ID。

有关更新处理程序函数的参数要求的详细信息，请参阅[有关一系列命令 id 的示例](#_core_example_for_a_range_of_command_ids)。

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>命令 Id 范围的示例

使用范围时，一个示例就是处理类似于 MFC 示例[HIERSVR](../overview/visual-cpp-samples.md)中的 Zoom 命令的命令。 此命令会缩放视图，并在其正常大小的25% 到300% 之间进行缩放。 HIERSVR 的视图类使用范围来处理包含类似于以下内容的消息映射项的缩放命令：

[!code-cpp[NVC_MFCMessageHandling#8](codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

写入消息映射项时，指定：

- 开始和结束连续范围的两个命令 Id。

   此处**ID_VIEW_ZOOM25**和**ID_VIEW_ZOOM300**。

- 命令的处理程序函数的名称。

   这就是 `OnZoom` 。

函数声明如下所示：

[!code-cpp[NVC_MFCMessageHandling#9](codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

更新处理程序函数的情况与此类似，并且可能更广泛地发挥作用。 为 `ON_UPDATE_COMMAND_UI` 多个命令编写处理程序很常见，并发现您自己编写或复制了相同的代码。 解决方案是使用宏将一系列命令 Id 映射到一个更新处理程序函数 `ON_UPDATE_COMMAND_UI_RANGE` 。 命令 Id 必须构成一个连续的范围。 有关示例，请参阅 `OnUpdateZoom` `ON_UPDATE_COMMAND_UI_RANGE` HIERSVR 示例的视图类中的处理程序及其消息映射项。

用于单个命令的更新处理程序函数通常采用类型为*pCmdUI*的单个参数 pCmdUI `CCmdUI*` 。 与处理程序函数不同，消息映射范围的更新处理程序函数不需要**UINT**类型的额外参数*nID*。 在对象中找到指定用户实际选择的命令所需的命令 ID `CCmdUI` 。

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>控制 Id 范围的示例

另一个有趣的情况是将一系列控件 Id 的控件通知消息映射到单个处理程序。 假设用户可以单击10个按钮中的任意一个。 若要将所有10个按钮映射到一个处理程序，消息映射条目应如下所示：

[!code-cpp[NVC_MFCMessageHandling#10](codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

当您在 `ON_CONTROL_RANGE` 消息映射中编写宏时，您指定：

- 特定的控件通知消息。

   这里**BN_CLICKED**。

- 与控件的连续范围关联的控件 ID 值。

   此处**IDC_BUTTON1**和**IDC_BUTTON10**。

- 消息处理程序函数的名称。

   这就是 `OnButtonClicked` 。

编写处理程序函数时，请指定额外的**UINT**参数，如下所示：

[!code-cpp[NVC_MFCMessageHandling#11](codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

`OnButtonClicked`单个**BN_CLICKED**消息的处理程序不采用任何参数。 一系列按钮的相同处理程序采用一个**UINT**。 额外参数允许标识负责生成**BN_CLICKED**消息的特定控件。

示例中所示的代码是典型的：将传递给的值转换为 `int` 消息范围内的，并断言这种情况。 然后，你可能需要执行一些不同的操作，具体取决于所单击的按钮。

## <a name="see-also"></a>另请参阅

[声明消息处理程序函数](declaring-message-handler-functions.md)
