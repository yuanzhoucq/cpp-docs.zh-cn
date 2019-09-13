---
title: MFC ActiveX 控件：添加自定义事件
ms.date: 11/04/2016
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
ms.openlocfilehash: d22eb6016635c509d6b8bb2068f00125d0227ca2
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907313"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX 控件：添加自定义事件

自定义事件不同于 stock 事件，因为它们不是由类`COleControl`自动触发的。 自定义事件识别由控件开发人员确定为事件的特定操作。 自定义事件的事件映射项由 EVENT_CUSTOM 宏表示。 以下部分实现了使用 ActiveX 控件向导创建的 ActiveX 控件项目的自定义事件。

##  <a name="_core_adding_a_custom_event_with_classwizard"></a>使用 "添加事件向导" 添加自定义事件

以下过程将添加特定的自定义事件 ClickIn。 您可以使用此过程添加其他自定义事件。 将自定义事件名称和参数替换为 ClickIn 事件名称和参数。

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>使用添加事件向导添加 ClickIn 自定义事件

1. 加载控件的项目。

1. 在**类视图**中，右键单击 ActiveX 控件类以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加事件**"。

   这将打开 "添加事件向导"。

1. 在 "**事件名称**" 框中，首先选择任何现有事件，单击 "**自定义**" 单选按钮，然后键入 " *ClickIn*"。

1. 在 "**内部名称**" 框中，键入事件的触发函数的名称。 对于本示例，请使用添加事件向导提供的默认值（`FireClickIn`）。

1. 使用**参数名称**和**参数类型**控件，添加一个名为*xCoord* （类型为*OLE_XPOS_PIXELS*）的参数。

1. 添加名为*yCoord*的第二个参数（类型为*OLE_YPOS_PIXELS*）。

1. 单击 "**完成**" 创建事件。

##  <a name="_core_classwizard_changes_for_custom_events"></a>添加自定义事件的事件向导更改

添加自定义事件时，"添加事件向导" 会对控件类进行更改。H，。CPP 和。IDL 文件。 下面的代码示例特定于 ClickIn 事件。

将以下行添加到标头（。H）文件：

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

此代码声明一个名`FireClickIn`为的内联函数，该函数使用 "添加事件向导" 定义的 ClickIn 事件和参数调用[COleControl：： FireEvent](../mfc/reference/colecontrol-class.md#fireevent) 。

此外，还会将以下行添加到控件的事件映射中（位于实现中）（）。CPP）文件：

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

此代码将事件 ClickIn 映射到内联函数`FireClickIn`，同时传递使用 "添加事件向导" 定义的参数。

最后，将以下行添加到控件的。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

此行将 ClickIn 事件指定为在添加事件向导事件列表中事件的位置获取的特定 ID 号。 事件列表中的条目允许容器预测事件。 例如，它可能提供在激发事件时要执行的处理程序代码。

##  <a name="_core_calling_fireclickin"></a>调用 FireClickIn

现在，您已使用 "添加事件向导" 添加了 ClickIn 自定义事件，您必须确定何时激发此事件。 为此，可在`FireClickIn`发生适当操作时调用。 对于此讨论，控件在`InCircle` `WM_LBUTTONDOWN`消息处理程序中使用函数，以便在用户单击圆形或椭圆区域内时触发 ClickIn 事件。 下面的过程添加`WM_LBUTTONDOWN`处理程序。

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>使用添加事件向导添加消息处理程序

1. 加载控件的项目。

1. 在**类视图**中，选择 ActiveX 控件类。

1. 在 "**属性**" 窗口中，可以看到 ActiveX 控件可以处理的消息列表。 以粗体显示的所有消息都已分配有处理程序函数。

1. 选择要处理的消息。 对于本示例，请`WM_LBUTTONDOWN`选择。

1. 从右侧的下拉列表框中，选择 **\<"添加 > OnLButtonDown**"。

1. 在**类视图**中双击新处理程序函数，跳转到实现中的消息处理程序代码（。CPP）文件。

下面的代码示例在控件`InCircle`窗口中每次单击鼠标左键时调用函数。 可以在`WM_LBUTTONDOWN` [Circ 示例](../overview/visual-cpp-samples.md)抽象的处理程序`OnLButtonDown`函数中找到此示例。

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  当 "添加事件向导" 为鼠标按钮操作创建消息处理程序时，将自动添加对基类的同一消息处理程序的调用。 请勿删除此调用。 如果控件使用任何常用鼠标消息，则必须调用基类中的消息处理程序，以确保正确处理鼠标捕获。

在下面的示例中，仅当在控件内的圆或椭圆区域内发生单击时，事件才会激发。 若要实现此行为，可以将`InCircle`函数置于控件的实现（。CPP）文件：

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

还需要将`InCircle`函数的以下声明添加到控件的标头（。H）文件：

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a>带有股票名称的自定义事件

您可以创建与 stock 事件同名的自定义事件，但是不能在同一控件中同时实现两者。 例如，你可能想要创建一个名为 Click 的自定义事件，该事件在常用事件单击通常会触发时不会激发。 然后，你可以通过调用其触发函数随时触发 Click 事件。

以下过程将添加一个自定义 Click 事件。

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>添加使用常用事件名称的自定义事件

1. 加载控件的项目。

1. 在**类视图**中，右键单击 ActiveX 控件类以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加事件**"。

   这将打开 "添加事件向导"。

1. 在 "**事件名称**" 下拉列表中，选择 "股票" 事件名称。 对于本示例，请选择 **"单击"** 。

1. 对于 "**事件类型**"，选择 "**自定义**"。

1. 单击 "**完成**" 创建事件。

1. 在`FireClick`代码中的适当位置调用。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
