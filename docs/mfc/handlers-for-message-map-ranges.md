---
title: 消息映射范围的处理程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be596ea38a8d0a3919ed43d9c5478bb0127032d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="handlers-for-message-map-ranges"></a>消息映射范围的处理程序
此文章介绍了如何将一系列消息映射到单个消息处理程序函数 （而不是将一条消息映射到一个功能）。  
  
 有何时需要在完全相同的方式处理多个消息或控件通知的时间。 在这种情况下，你可能想要将所有消息映射到单个处理程序函数。 消息映射范围允许你执行此操作的消息的连续范围：  
  
-   可以映射到的命令 Id 的范围：  
  
    -   命令处理程序函数。  
  
    -   一个命令更新处理程序函数。  
  
-   可以将控件 Id 的范围的控件通知消息映射到消息处理程序函数。  
  
 本文中涵盖的主题包括：  
  
-   [写入消息映射条目](#_core_writing_the_message.2d.map_entry)  
  
-   [声明处理程序函数](#_core_declaring_the_handler_function)  
  
-   [对一系列的命令 Id 的示例](#_core_example_for_a_range_of_command_ids)  
  
-   [范围的控件 Id 的示例](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a> 写入消息映射条目  
 在。CPP 文件中，添加你的消息映射条目，如下面的示例中所示：  
  
 [!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]  
  
 消息映射条目包括以下各项：  
  
-   消息映射范围宏：  
  
    -   [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)  
  
    -   [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)  
  
    -   [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)  
  
-   在宏参数：  
  
     前两个宏采用三个参数：  
  
    -   命令 ID 范围的起始  
  
    -   命令 ID 范围的结束  
  
    -   消息处理程序函数的名称  
  
     命令 Id 的范围必须是连续的。  
  
     第三个宏， `ON_CONTROL_RANGE`，采用附加第一个参数： 控件通知消息，如**EN_CHANGE**。  
  
##  <a name="_core_declaring_the_handler_function"></a> 声明处理程序函数  
 添加处理程序函数声明中的。H 文件。 下面的代码演示如何它可能看起来，如下所示：  
  
 [!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]  
  
 单个命令的处理程序函数通常不带任何参数。 除了更新处理程序函数，消息映射范围的处理程序函数需要一个额外的参数， `nID`，类型的**UINT**。 此参数是第一个参数。 额外的参数提供额外的命令 ID，用于指定用户实际选择哪个命令。  
  
 有关更新处理程序函数的参数要求的详细信息，请参阅[示例的范围的命令 Id 的](#_core_example_for_a_range_of_command_ids)。  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a> 范围的命令 Id 的示例  
 何时可以使用一个例子就是在处理如 MFC 示例中的缩放命令的命令的范围[HIERSVR](../visual-cpp-samples.md)。 此命令将视图中，缩放 25%和其正常大小的 300%之间。 HIERSVR 的视图类使用一系列处理并类似于这一个消息映射条目的缩放命令：  
  
 [!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]  
  
 当你编写的消息映射条目，您指定：  
  
-   这两个命令 Id，开始和结束时间连续范围。  
  
     以下是方法`ID_VIEW_ZOOM25`和`ID_VIEW_ZOOM300`。  
  
-   命令处理程序函数的名称。  
  
     它具有此处`OnZoom`。  
  
 函数声明将类似于以下：  
  
 [!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]  
  
 更新处理程序函数的大小写是类似，并可能具有更广泛的用途。 这是十分常见编写`ON_UPDATE_COMMAND_UI`处理程序的命令数，将发现自己编写，或复制，相同的代码反复。 该解决方案旨在的命令 Id 传递给其中一个更新处理程序函数使用范围映射`ON_UPDATE_COMMAND_UI_RANGE`宏。 命令 Id 必须形成连续范围。 有关示例，请参阅**OnUpdateZoom**处理程序并将其`ON_UPDATE_COMMAND_UI_RANGE`HIERSVR 示例的 view 类中的消息映射条目。  
  
 更新处理程序函数的单个命令通常需要一个参数`pCmdUI`，类型的**CCmdUI\***。 与处理程序函数，不同的消息映射范围的更新处理程序函数不需要额外的参数， `nID`，类型的**UINT**。 命令 ID，将需要指定用户实际选择的命令，该文件位于`CCmdUI`对象。  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a> 范围的控件 Id 的示例  
 另一个有趣的用例将控件 Id 的范围的控件通知消息映射到单个处理程序。 假设用户可以单击任何 10 个按钮。 若要映射到一个处理程序的所有 10 个按钮，你的消息映射条目将如下所示：  
  
 [!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]  
  
 当你编写`ON_CONTROL_RANGE`消息映射中的宏，你指定：  
  
-   特定的控件通知消息。  
  
     它具有此处**BN_CLICKED**。  
  
-   关联控件的连续范围内的控件 ID 值。  
  
     这些是此处`IDC_BUTTON1`和`IDC_BUTTON10`。  
  
-   消息处理程序函数的名称。  
  
     它具有此处`OnButtonClicked`。  
  
 当你编写的处理程序函数时，指定额外**UINT**参数，如如下所示：  
  
 [!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]  
  
 `OnButtonClicked`处理程序单个**BN_CLICKED**消息不采用任何参数。 一个范围的按钮的同一处理程序接收一个**UINT**。 额外的参数允许进行标识特定的控件负责生成**BN_CLICKED**消息。  
  
 在示例中所示的代码是典型： 将值传递到转换`int`内的消息范围和声明这种情况。 然后，你可能需要一些不同的操作，具体取决于单击按钮。  
  
## <a name="see-also"></a>请参阅  
 [声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
