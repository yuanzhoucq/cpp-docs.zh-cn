---
title: "消息映射范围的处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令处理, 命令更新处理程序"
  - "命令 ID, 消息映射"
  - "命令传送, 命令更新处理程序"
  - "命令更新处理程序"
  - "控件通知消息"
  - "控件 [MFC], 通知"
  - "处理函数"
  - "处理函数, 声明"
  - "处理函数, 消息映射范围"
  - "处理程序"
  - "处理程序, 消息映射范围"
  - "映射, 消息范围"
  - "消息处理程序"
  - "消息处理, 消息处理程序函数"
  - "消息映射, 消息处理程序函数"
  - "消息映射, 范围"
  - "消息范围"
  - "消息范围, 映射"
  - "消息映射范围"
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 消息映射范围的处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明映射范围消息添加到一条消息处理程序 \(函数代替为仅一的函数映射。消息\)。  
  
 当需要相同时，处理多个消息或控件通知有时间。  在此时间，您可能希望映射任何消息到单个处理程序函数。  消息映射范围允许这样做一连续范围的消息：  
  
-   可以映射范围命令 ID:  
  
    -   命令处理程序函数。  
  
    -   命令更新处理程序函数。  
  
-   可以映射范围的控件通知消息控件 ID 到消息处理函数。  
  
 本文涵盖的主题包括：  
  
-   [编写消息映射项](#_core_writing_the_message.2d.map_entry)  
  
-   [声明处理程序函数](#_core_declaring_the_handler_function)  
  
-   [范围的示例命令 ID](#_core_example_for_a_range_of_command_ids)  
  
-   [范围的示例控件 ID](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a> 编写消息映射项  
 如下面的示例所示在 .cpp 文件，添加消息映射项，例如：  
  
 [!CODE [NVC_MFCMessageHandling#6](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#6)]  
  
 消息映射项包括以下项：  
  
-   消息映射范围宏：  
  
    -   [ON\_COMMAND\_RANGE](../Topic/ON_COMMAND_RANGE.md)  
  
    -   [ON\_UPDATE\_COMMAND\_UI\_RANGE](../Topic/ON_UPDATE_COMMAND_UI_RANGE.md)  
  
    -   [ON\_CONTROL\_RANGE](../Topic/ON_CONTROL_RANGE.md)  
  
-   至宏的参数：  
  
     前两宏采用三个参数：  
  
    -   开始范围的命令 ID  
  
    -   结束范围的命令 ID  
  
    -   消息处理程序函数的名称  
  
     范围命令 ID 必须连续的。  
  
     第三，宏 `ON_CONTROL_RANGE`，它采用一个第一个参数：一控件通知消息，例如 **EN\_CHANGE**。  
  
##  <a name="_core_declaring_the_handler_function"></a> 声明处理程序函数  
 将处理程序的函数声明。H 文件。  下面的代码演示这可能如何查找，如下所示：  
  
 [!CODE [NVC_MFCMessageHandling#7](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#7)]  
  
 单个命令的处理程序函数通常不采用参数。  除了更新处理程序函数以外，消息映射范围的处理程序函数需要一个额外的参数，即 `nID`，**UINT**类型。  此参数是第一个参数。  额外的参数满足需要额外的命令 ID 指定命令用户实际上并选择。  
  
 有关更新处理程序函数的参数要求的更多信息，请参见 [范围的示例命令 ID](#_core_example_for_a_range_of_command_ids)。  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a> 范围的示例命令 ID  
 何时可以使用范围？  一个示例在类似的命令处理缩放在 MFC 示例 [HIERSVR](../top/visual-cpp-samples.md)。  此命令缩放视图时，缩放将在 25% 和 300% 之间。为其正常大小  HIERSVR 的视图类使用值域处理类似的消息映射项的缩放命令：  
  
 [!CODE [NVC_MFCMessageHandling#8](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#8)]  
  
 当您写入消息映射项时，指定：  
  
-   两个命令 ID、开始和结束连续的范围。  
  
     下面是这些 `ID_VIEW_ZOOM25` 和 `ID_VIEW_ZOOM300`。  
  
-   命令的处理程序函数的名称。  
  
     下面是其 `OnZoom`。  
  
 函数声明将类似于：  
  
 [!CODE [NVC_MFCMessageHandling#9](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#9)]  
  
 用例更新处理程序函数的 flavor 和可能很有用。  相当常见的写许多命令的 `ON_UPDATE_COMMAND_UI` 处理程序并发现自己文本，或者复制，反复相同的代码。  解决方案会映射范围命令 ID 对更新处理程序函数使用 `ON_UPDATE_COMMAND_UI_RANGE` 宏。  命令 ID 必须构成一连续的范围。  有关示例，请参见 **OnUpdateZoom** 处理程序及其 `ON_UPDATE_COMMAND_UI_RANGE` 消息映射项在 HIERSVR 示例中视图类。  
  
 更新单个命令的处理程序函数通常采用单个参数，`pCmdUI`，**CCmdUI\***类型。  与不同处理程序函数，更新消息映射范围的处理程序函数不需要一个额外的参数，即 `nID`，**UINT**类型。  命令 ID，需要的指定命令用户实际上并选择，在 `CCmdUI` 对象中。  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a> 示例控件 ID的例子  
 另一个有趣大小写映射范围的控件通知消息控件 ID。一个处理程序。  假设用户可单击按钮 10 中的\)。  所有映射到 10 个按钮一个处理程序，如下所示：消息映射项：  
  
 [!CODE [NVC_MFCMessageHandling#10](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#10)]  
  
 在中编写消息映射中，`ON_CONTROL_RANGE` 宏指定：  
  
-   特定控件通知消息。  
  
     此处的为 **BN\_CLICKED**。  
  
-   控件 ID 值与相邻范围的控件。  
  
     它们是 `IDC_BUTTON1` 和 `IDC_BUTTON10`。  
  
-   消息处理程序函数的名称。  
  
     下面是其 `OnButtonClicked`。  
  
 当您编写处理程序函数，如下面的所示，请指定附加的 **UINT** 参数，例如：  
  
 [!CODE [NVC_MFCMessageHandling#11](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#11)]  
  
 单个 **BN\_CLICKED** 消息的 `OnButtonClicked` 处理程序未采用任何参数。  范围内的同一按钮处理程序接受一个 **UINT**。  额外的参数允许标识特定控件负责生成 **BN\_CLICKED** 消息。  
  
 示例中显示的代码是典型的：转换值传递给。消息大小和断言内的 `int` 是这样。  然后可以采取按钮单击的一些附加操作。  
  
## 请参阅  
 [声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)