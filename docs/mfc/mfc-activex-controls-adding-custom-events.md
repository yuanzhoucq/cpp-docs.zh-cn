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
ms.openlocfilehash: 8d464e5d7c9731e158e44d66d569fd1555401e17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364720"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX 控件：添加自定义事件

自定义事件与股票事件不同，因为它们不会由类`COleControl`自动触发。 自定义事件将由控件开发人员确定的特定操作识别为事件。 自定义事件的事件映射条目由EVENT_CUSTOM宏表示。 以下部分为使用 ActiveX 控制向导创建的 ActiveX 控件项目实现自定义事件。

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a>使用添加事件向导添加自定义事件

以下过程添加了特定的自定义事件 ClickIn。 可以使用此过程添加其他自定义事件。 将自定义事件名称及其参数替换为 ClickIn 事件名称和参数。

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>使用"添加事件向导"添加"点击"自定义事件

1. 加载控件的项目。

1. 在**类视图中**，右键单击 ActiveX 控件类以打开快捷菜单。

1. 在快捷菜单中，单击"**添加"，** 然后单击"**添加事件**"。

   这将打开"添加事件向导"。

1. 在 **"事件名称**"框中，首先选择任何现有事件，然后单击 **"自定义**单选"按钮，然后键入*ClickIn*。

1. 在 **"内部名称**"框中，键入事件触发函数的名称。 在此示例中，请使用添加事件向导 （ ）`FireClickIn`提供的默认值。

1. 使用**参数名称**和**参数类型**控件添加一个参数，称为*xCoord（* 类型*OLE_XPOS_PIXELS*）。

1. 添加第二个参数，称为*yCoord（**类型OLE_YPOS_PIXELS*）。

1. 单击 **"完成"** 以创建事件。

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a>为自定义事件添加事件向导更改

添加自定义事件时，"添加事件向导"会更改控件类 。H。CPP 和 。IDL 文件。 以下代码示例特定于 ClickIn 事件。

以下行将添加到标头 （。H） 控制类的文件：

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

此代码声明一个内联函数，`FireClickIn`称为[COleControl：：FireEvent，](../mfc/reference/colecontrol-class.md#fireevent)包含使用添加事件向导定义的 ClickIn 事件和参数。

此外，下一行将添加到位于实现 （的控件的事件映射中。控制类的 CPP） 文件：

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

此代码将事件 ClickIn 映射到内联函数`FireClickIn`，传递使用添加事件向导定义的参数。

最后，将以下行添加到控件的 。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

此行为 ClickIn 事件分配一个特定的 ID 号，该 ID 号取自事件在"添加事件向导"事件列表中的位置。 事件列表中的条目允许容器预测事件。 例如，它可能提供触发事件时要执行的处理程序代码。

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a>调用火点击

现在，您已经使用"添加事件向导"添加了 ClickIn 自定义事件，您必须决定何时触发此事件。 执行此操作时调用`FireClickIn`相应的操作。 对于此讨论，当用户单击圆形`InCircle`或椭圆`WM_LBUTTONDOWN`区域时，控件使用消息处理程序内的函数触发 ClickIn 事件。 以下过程添加`WM_LBUTTONDOWN`处理程序。

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>使用"添加事件向导"添加消息处理程序

1. 加载控件的项目。

1. 在**类视图中**，选择 ActiveX 控件类。

1. 在 **"属性"** 窗口中，您将看到一个由 ActiveX 控件可以处理的消息列表。 以粗体显示的任何消息都已为其分配了处理程序函数。

1. 选择要处理的消息。 在此示例中，选择`WM_LBUTTONDOWN`。

1. 从右侧的下拉列表框中，选择**\<"添加> OnLButtonDown**。

1. 双击**类视图中**的新处理程序函数以跳转到实现中的消息处理程序代码 （。ActiveX 控件的 CPP）文件。

每次在控制窗口中单击鼠标`InCircle`左键时，以下代码示例都会调用该函数。 此示例可以在`WM_LBUTTONDOWN`处理程序函数 中找到，`OnLButtonDown`在 Circ[示例](../overview/visual-cpp-samples.md)摘要中找到。

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> 当添加事件向导为鼠标按钮操作创建消息处理程序时，将自动添加对基类的同一消息处理程序的调用。 不要删除此呼叫。 如果控件使用任何库存鼠标消息，则必须调用基类中的消息处理程序以确保正确处理鼠标捕获。

在下面的示例中，仅当单击发生在控件内的圆形或椭圆区域中时，事件才会触发。 要实现此行为，可以将`InCircle`函数放在控件的实现中 （。CPP） 文件：

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

您还需要将`InCircle`函数的以下声明添加到控件的标头 （。H） 文件：

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a>具有股票名称的自定义事件

您可以创建与股票事件同名的自定义事件，但不能在同一控件中实现这两个事件。 例如，您可能希望创建名为 Click 的自定义事件，该自定义事件在股票事件 Click 通常会触发时不会触发。 然后，您可以随时通过调用其触发函数触发 Click 事件。

以下过程添加自定义 Click 事件。

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>添加使用股票事件名称的自定义事件

1. 加载控件的项目。

1. 在**类视图中**，右键单击 ActiveX 控件类以打开快捷菜单。

1. 在快捷菜单中，单击"**添加"，** 然后单击"**添加事件**"。

   这将打开"添加事件向导"。

1. 在**事件名称**下拉列表中，选择股票事件名称。 在此示例中，选择**单击**。

1. 对于**事件类型**，选择 **"自定义**"。

1. 单击 **"完成"** 以创建事件。

1. 在`FireClick`代码的适当位置呼叫。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
