---
title: MFC ActiveX 控件：向 ActiveX 控件添加常用事件
ms.date: 11/04/2016
f1_keywords:
- EVENT__STOCK_ERROR
- EVENT__STOCK_READYSTATECHANGE
- ReadyStateChange
- EVENT__STOCK_MOUSEMOVE
- EVENT__STOCK_MOUSEUP
- EVENT__STOCK_DBLCLICK
- KeyPress
- EVENT__STOCK_KEYDOWN
- EVENT__STOCK
- EVENT__STOCK_MOUSEDOWN
- EVENT__STOCK_KEYPRESS
- EVENT__STOCK_CLICK
- EVENT__STOCK_KEYUP
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- KeyPress event
- FireDblClick event
- FireMouseDown event
- events [MFC], stock
- FireKeyPress event
- EVENT_STOCK_MOUSEMOVE event
- EVENT_STOCK_CLICK event
- FireClick event
- FireKeyUp event
- FireMouseUp event
- EVENT_STOCK_ERROREVENT event
- EVENT_STOCK_KEYDOWN event
- EVENT_STOCK_MOUSEDOWN event
- EVENT_STOCK_KEYPRESS macro [MFC]
- EVENT_STOCK_KEYUP event
- EVENT_STOCK_DBLCLICK event
- FireError event
- FireKeyDown event
- ReadyStateChange event
- EVENT_STOCK_MOUSEUP event
- FireMouseMove event
- EVENT_STOCK prefix
- EVENT_STOCK_READYSTATECHANGE event
- EVENT_STOCK_KEYPRESS event
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
ms.openlocfilehash: a97c08baaf3c11b0436e52bb4fd4ac380999d69a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615594"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX 控件：向 ActiveX 控件添加常用事件

Stock 事件与自定义事件的不同之处在于，它们由类[COleControl](reference/colecontrol-class.md)自动触发。 `COleControl`包含一些预定义的成员函数，这些函数可触发常见操作生成的事件。 实现的一些常见操作 `COleControl` 包括单双击控件、键盘事件以及鼠标按钮状态的更改。 常用事件的事件映射条目始终以 EVENT_STOCK 前缀开头。

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>添加事件向导支持的常用事件

`COleControl`类提供了10个常用事件，如下表所示。 您可以使用 "[添加事件向导](../ide/add-event-wizard.md)" 指定控件中所需的事件。

### <a name="stock-events"></a>股票事件

|事件|触发函数|注释|
|-----------|---------------------|--------------|
|单击|**void FireClick （）**|当控件捕获鼠标、接收到任何**BUTTONUP** （左、中或右）消息并在控件上释放按钮时激发。 股票 MouseDown 和 MouseUp 事件发生在此事件之前。<br /><br /> 事件映射项： **EVENT_STOCK_CLICK （）**|
|DblClick|**void FireDblClick （）**|类似于单击，但在收到**BUTTONDBLCLK**消息时触发。<br /><br /> 事件映射项： **EVENT_STOCK_DBLCLICK （）**|
|错误|**void FireError （SCODE***SCODE* **，LPCSTR** `lpszDescription` **，UINT** `nHelpID` **= 0）**        |当 ActiveX 控件中的错误发生在方法调用或属性访问范围之外时引发。<br /><br /> 事件映射项： **EVENT_STOCK_ERROREVENT （）**|
|KeyDown|**void FireKeyDown （short** `nChar` **，short** `nShiftState` **）**      |`WM_SYSKEYDOWN`接收或消息时触发 `WM_KEYDOWN` 。<br /><br /> 事件映射项： **EVENT_STOCK_KEYDOWN （）**|
|KeyPress|**Void FireKeyPress （short** <strong>\*</strong> `pnChar`**)**    |接收到消息时触发 `WM_CHAR` 。<br /><br /> 事件映射项： **EVENT_STOCK_KEYPRESS （）**|
|KeyUp|**void FireKeyUp （short** `nChar` **，short** `nShiftState` **）**      |`WM_SYSKEYUP`接收或消息时触发 `WM_KEYUP` 。<br /><br /> 事件映射项： **EVENT_STOCK_KEYUP （）**|
|MouseDown|**void FireMouseDown （short** `nButton` **、short** `nShiftState` **、float***x* **、float***y***）**          |接收到任何**BUTTONDOWN** （左、中或右）时触发。 此事件触发前，会立即捕获鼠标。<br /><br /> 事件映射项： **EVENT_STOCK_MOUSEDOWN （）**|
|MouseMove|**void FireMouseMove （short** `nButton` **、short** `nShiftState` **、float***x* **、float***y***）**          |接收到 WM_MOUSEMOVE 消息时触发。<br /><br /> 事件映射项： **EVENT_STOCK_MOUSEMOVE （）**|
|MouseUp|**void FireMouseUp （short** `nButton` **、short** `nShiftState` **、float***x* **、float***y***）**          |接收到任何**BUTTONUP** （左、中或右）时触发。 在激发此事件之前释放鼠标捕获。<br /><br /> 事件映射项： **EVENT_STOCK_MOUSEUP （）**|
|ReadyStateChange|**void FireReadyStateChange （）**|当控件由于收到的数据量而转换到下一个就绪状态时触发。<br /><br /> 事件映射项： **EVENT_STOCK_READYSTATECHANGE （）**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>使用添加事件向导添加股票事件

添加常用事件比添加自定义事件需要更少的工作，因为实际事件的激发由基类自动处理 `COleControl` 。 以下过程将常用事件添加到使用[MFC ActiveX 控件向导](reference/mfc-activex-control-wizard.md)开发的控件中。 当按下某个键且该控件处于活动状态时，将触发称为按键的事件。 此过程也可用于添加其他股票事件。 将所选的常用事件名称替换为按键。

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>使用添加事件向导添加按键常用事件

1. 加载控件的项目。

1. 在类视图中，右键单击 ActiveX 控件类以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加事件**"。

   这将打开 "添加事件向导"。

1. 在 "**事件名称**" 下拉列表中，选择 `KeyPress` 。

1. 单击“完成”。

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>添加股票事件的事件向导更改

由于常用事件由控件的基类处理，因此添加事件向导不会以任何方式更改类声明。 它会将事件添加到控件的事件映射，并在其中输入一个条目。IDL 文件。 将以下行添加到控件的事件映射，该映射位于控件类实现（）中。CPP）文件：

[!code-cpp[NVC_MFC_AxUI#5](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

当接收到 WM_CHAR 消息并且控件处于活动状态时，添加此代码将触发按键事件。 按键事件可以在其他时间通过 `FireKeyPress` 从控制代码中调用其触发函数（例如）来激发。

添加事件向导将以下代码行添加到控件的。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#6](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

该行将按键事件与其标准调度 ID 相关联，并允许容器预测按键事件。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 类](reference/colecontrol-class.md)
