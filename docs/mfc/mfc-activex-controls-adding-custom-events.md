---
title: "MFC ActiveX 控件：添加自定义事件 | Microsoft Docs"
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
  - "Click 事件, 自定义事件"
  - "ClickIn 事件"
  - "COleControl 类, 自定义事件"
  - "自定义事件"
  - "自定义事件, 添加到 ActiveX 控件"
  - "EVENT_CUSTOM 宏"
  - "EVENT_CUSTOM 前缀"
  - "事件 [C++], ActiveX 控件"
  - "FireClickIn 事件"
  - "FireEvent 方法, 添加自定义事件"
  - "InCircle 方法"
  - "MFC ActiveX 控件, 事件"
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：添加自定义事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自定义事件不同于常用事件不同它们不会被 `COleControl`类自动触发。  自定义识别某些操作事件，依赖控件的开发人员，为事件。  自定义事件映射项由 `EVENT_CUSTOM` 宏表示。  下面部分实现使用 ActiveX 控件向导，创建的 ActiveX 控件项目的自定义事件。  
  
##  <a name="_core_adding_a_custom_event_with_classwizard"></a> 添加与添加事件向导中自定义事件  
 下面过程添加特定的自定义事件，ClickIn。  您可以使用此过程来添加其他自定义事件。  替换 ClickIn 事件名称和参数重写自定义事件名称及其参数。  
  
#### 使用"添加事件向导，将 ClickIn 自定义事件  
  
1.  加载控件的项目。  
  
2.  在"类视图"中，右击该 ActiveX 控件类打开快捷菜单。  
  
3.  从快捷菜单中单击 **添加**，然后单击 **添加事件**。  
  
     这将打开"添加事件向导"  
  
4.  在 **事件名称** 框，请先选择任何现有事件，然后单击 **自定义** 单选按钮，然后键入 `ClickIn`。  
  
5.  在 **内部名称** 框中，键入事件触发的函数的名称。  对于此例，请使用添加事件向导提供的默认值 \(`FireClickIn`\)。  
  
6.  参数添加，调用 `xCoord` \( `OLE_XPOS_PIXELS`类型\)，使用 **参数名称** 并 **参数类型** 控件。  
  
7.  将第二个参数，则调用 `yCoord` \( `OLE_YPOS_PIXELS`类型\)。  
  
8.  单击以创建事件的 **完成**。  
  
##  <a name="_core_classwizard_changes_for_custom_events"></a> 添加事件向导为自定义事件更改  
 在添加自定义事件时，添加事件向导对更改控件的类。H 和 .cpp、.idl 文件。  下面的代码示例是特定于 ClickIn 事件。  
  
 以下行添加到标头 \(。H\) 控件类的文件：  
  
 [!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_1.h)]  
  
 此代码声明使用"添加事件向导，使用的调用 ClickIn 事件和参数的 [COleControl::FireEvent](../Topic/COleControl::FireEvent.md) 您定义的内联函数调用 `FireClickIn`。  
  
 此外，下列代码行添加到控件的事件映射，位于控件类的实现 \(.cpp\) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_2.cpp)]  
  
 此代码将事件 ClickIn 对内联函数 `FireClickIn`，后者传递使用"添加事件向导，您定义的参数。  
  
 最后，代码行添加到控件的 .idl 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_3.idl)]  
  
 此行将 ClickIn 事件特定 ID 号，来自"添加事件向导事件列表事件的位置。  在事件列表的输入允许容器所需的事件。  例如，在中，该事件触发时，可能要提供实现的处理程序代码。  
  
##  <a name="_core_calling_fireclickin"></a> 调用 FireClickIn  
 使用"添加事件向导，现在已添加了 ClickIn 自定义事件，您必须决定此事件时将触发。  通过调用 `FireClickIn` 完成此操作，在适当时发生。  对于本讨论中，当用户在此单击一个圆形或椭圆区域内部时，控件将在 `WM_LBUTTONDOWN` 消息处理程序内的 `InCircle` 函数 ClickIn 激发事件。  以下过程向 `WM_LBUTTONDOWN` 处理程序。  
  
#### 将添加事件向导"的消息处理程序  
  
1.  加载控件的项目。  
  
2.  在"类视图，选择 ActiveX 控件类。  
  
3.  在“属性”窗口中，单击“消息”按钮。  
  
     属性窗口显示可由 ActiveX 控件处理消息的列表。  在粗体的所有消息添加已经有处理程序函数分配给它。  
  
4.  在属性窗口中，选择您希望处理的消息。  对于此示例，选择 `WM_LBUTTONDOWN`。  
  
5.  从右边的下拉列表框中，选择 **\<Add OnLButtonDown\>** 。  
  
6.  双击新处理程序函数在"类视图"跳转到在 ActiveX 控件的实现 \(.cpp\) 文件的消息处理程序代码。  
  
 在鼠标左键在控件窗口内单击时，以下代码示例调用 **InCircle** 函数。  此示例可以在 `WM_LBUTTONDOWN` 处理函数，`OnLButtonDown`查找，在 [Circ 示例](../top/visual-cpp-samples.md) 抽象。  
  
 [!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_4.cpp)]  
  
> [!NOTE]
>  当添加事件向导"创建操作鼠标按钮时的消息处理程序，对基类相同的消息处理程序的调用自动添加。  请勿删除此调用。  如果控件使用任何常用鼠标消息，基类的调用捕获鼠标消息处理程序必须确保正确处理。  
  
 在下面的示例中，事件激发时，才单击出现在控件内的循环或省略区域内。  要实现此行为，可以在控件的实现 \(.cpp\) 文件中的 `InCircle` 函数：  
  
 [!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_5.cpp)]  
  
 您还需要添加 `InCircle` 函数中的下列声明到控件标头 \(。H\) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_6.h)]  
  
##  <a name="_core_custom_events_with_stock_names"></a> 与产品名称的自定义事件  
 您可以创建一个名为的自定义事件和库存事件相同，但是，您无法实现都在同一控件。  例如，您可能想创建不调用触发单击的自定义事件、事件何时单击通常都将激发。  您可以通过调用其触发函数然后触发随时单击事件。  
  
 下面过程添加自定义。单击事件  
  
#### 添加使用常用事件名称的自定义事件  
  
1.  加载控件的项目。  
  
2.  在"类视图"中，右击该 ActiveX 控件类打开快捷菜单。  
  
3.  从快捷菜单中单击 **添加**，然后单击 **添加事件**。  
  
     这将打开"添加事件向导"  
  
4.  在 **事件名称** 下拉列表中，选择一个常用事件名称。  对于此示例，选择 **单击**。  
  
5.  对于 **事件类型**，选择 **自定义**。  
  
6.  单击以创建事件的 **完成**。  
  
7.  在代码中适当位置调用 `FireClick`。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)