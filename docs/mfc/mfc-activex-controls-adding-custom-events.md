---
title: "MFC ActiveX 控件： 添加自定义事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], events [MFC]
- EVENT_CUSTOM prefix [MFC]
- custom events [MFC], adding to ActiveX controls
- EVENT_CUSTOM macro [MFC]
- InCircle method [MFC]
- ClickIn event
- FireClickIn event
- COleControl class [MFC], custom events [MFC]
- Click event, custom events [MFC]
- events [MFC], ActiveX controls
- custom events [MFC]
- FireEvent method, adding custom events
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a93f0354395dee3110749a942e1800581f146fdf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX 控件：添加自定义事件
自定义事件不同于常用事件，因为类自动不激发`COleControl`。 自定义事件识别的某些操作，由控件开发人员，为事件。 自定义事件的事件映射条目由`EVENT_CUSTOM`宏。 以下部分实现使用 ActiveX 控件向导创建 ActiveX 控件项目的自定义事件。  
  
##  <a name="_core_adding_a_custom_event_with_classwizard"></a>添加具有自定义事件添加事件向导  
 下面的过程添加特定的自定义事件，ClickIn。 此过程可用于添加其他自定义事件。 替换你自定义事件的名称和有关 ClickIn 事件名称和参数其参数。  
  
#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>若要添加使用添加事件向导 ClickIn 自定义事件  
  
1.  加载控件的项目。  
  
2.  在类视图中，右键单击你的 ActiveX 控件类，以打开快捷菜单。  
  
3.  从快捷菜单中，单击**添加**，然后单击**添加事件**。  
  
     这将打开添加事件向导。  
  
4.  在**事件名称**框中，首先选择现有的任何事件，然后单击**自定义**单选按钮，然后键入`ClickIn`。  
  
5.  在**内部名称**框中，键入的事件触发函数的名称。 对于此示例中，使用添加事件向导提供的默认值 (`FireClickIn`)。  
  
6.  添加名为的参数`xCoord`(类型`OLE_XPOS_PIXELS`)，并使用**参数名称**和**参数类型**控件。  
  
7.  添加第二个参数，调用`yCoord`(类型`OLE_YPOS_PIXELS`)。  
  
8.  单击**完成**创建事件。  
  
##  <a name="_core_classwizard_changes_for_custom_events"></a>对于自定义事件添加事件向导更改  
 当你添加自定义事件时，添加事件向导对控件类进行更改。H、。CPP，和。IDL 文件。 以下代码示例是特定于 ClickIn 事件。  
  
 将以下行添加到标头 (。H） 文件的控件类：  
  
 [!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]  
  
 此代码声明了内联函数调用`FireClickIn`调用[COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent)具有 ClickIn 事件和参数定义使用添加事件向导。  
  
 此外，将以下行添加到位于中实现的控件事件映射 (。控件类的 CPP) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]  
  
 此代码映射到的内联函数的事件 ClickIn `FireClickIn`，传递使用添加事件向导定义的参数。  
  
 最后，以下行添加到你的控件。IDL 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]  
  
 此行将 ClickIn 事件分配一个特定的 ID 号，取自添加事件向导事件列表中的事件的位置。 事件列表中的条目允许容器以应对预期的事件。 例如，它可以提供激发事件时要执行的处理程序代码。  
  
##  <a name="_core_calling_fireclickin"></a>调用 FireClickIn  
 现在，你已添加使用添加事件向导 ClickIn 自定义事件，你必须决定要激发此事件时。 执行此操作通过调用`FireClickIn`相应的操作发生的时间。 有关此讨论，该控件使用`InCircle`函数内`WM_LBUTTONDOWN`激发 ClickIn 事件，当用户单击圆形或椭圆形区域内的消息处理程序。 下面的过程添加`WM_LBUTTONDOWN`处理程序。  
  
#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>若要使用添加事件向导添加消息处理程序  
  
1.  加载控件的项目。  
  
2.  在类视图中，选择 ActiveX 控件类。  
  
3.  在属性窗口中，单击**消息**按钮。  
  
     属性窗口显示的消息可以由 ActiveX 控件的列表。 已以粗体显示的任何消息有为其分配一个处理程序函数。  
  
4.  从属性窗口中，选择你想要处理的消息。 对于此示例中，选择`WM_LBUTTONDOWN`。  
  
5.  从右侧的下拉列表框中，选择**\<添加 > OnLButtonDown**。  
  
6.  双击跳转到消息处理程序代码中实现的类视图中的新处理程序函数 (。ActiveX 控件的 CPP) 文件。  
  
 下面的代码示例调用**InCircle**函数每次在控制窗口内单击鼠标左键。 此示例可在`WM_LBUTTONDOWN`处理程序函数，`OnLButtonDown`中[Circ 示例](../visual-cpp-samples.md)抽象。  
  
 [!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]  
  
> [!NOTE]
>  当添加事件向导创建鼠标按钮操作的消息处理程序时，将自动添加到相同的消息处理程序的基类的调用。 不要删除此调用。 如果你的控件使用任何常用鼠标的消息，则必须调用基类中的消息处理程序以确保正确处理鼠标捕获。  
  
 在下面的示例中，事件将激发单击发生在控件内的圆形或椭圆形区域内的仅时。 若要实现此行为，可以将放`InCircle`控件的实现中的函数 (。CPP) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]  
  
 你还需要添加的以下声明`InCircle`到控件的标头的函数 (。H） 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]  
  
##  <a name="_core_custom_events_with_stock_names"></a>使用常用的名称的自定义事件  
 但是不可以实现不管是在同一个控件，可以使用同名的常用事件中创建自定义事件。 例如，你可能想要创建自定义称为常用事件通常将激发单击时，不会不会激发的 Click 事件。 然后，你无法通过调用其触发函数在任何时间触发 Click 事件。  
  
 下面的过程添加自定义的 Click 事件。  
  
#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>若要添加自定义事件，使用一个常用事件名称  
  
1.  加载控件的项目。  
  
2.  在类视图中，右键单击你的 ActiveX 控件类，以打开快捷菜单。  
  
3.  从快捷菜单中，单击**添加**，然后单击**添加事件**。  
  
     这将打开添加事件向导。  
  
4.  在**事件名称**下拉列表中，选择常用事件名称。 对于此示例中，选择**单击**。  
  
5.  有关**事件类型**，选择**自定义**。  
  
6.  单击**完成**创建事件。  
  
7.  调用`FireClick`在代码中的相应位置。  
  
## <a name="see-also"></a>另请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 类](../mfc/reference/colecontrol-class.md)
