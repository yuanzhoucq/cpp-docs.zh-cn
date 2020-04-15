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
ms.openlocfilehash: 79cd4fc572e55c67cc5a2cfe3a00e04f2a4a7850
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364689"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX 控件：向 ActiveX 控件添加常用事件

股票事件与自定义事件不同，因为它们由[COleControl](../mfc/reference/colecontrol-class.md)类自动触发。 `COleControl`包含预定义的成员函数，这些函数触发由常见操作引起的事件。 通过实现`COleControl`的某些常见操作包括对控件的单次单击和双击、键盘事件以及更改鼠标按钮的状态。 股票事件的事件映射条目始终前面有EVENT_STOCK前缀。

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>添加事件向导支持的股票事件

该`COleControl`类提供十个股票事件，列在下表中。 您可以使用["添加事件向导](../ide/add-event-wizard.md)"在控件中指定所需的事件。

### <a name="stock-events"></a>股票事件

|事件|点火功能|注释|
|-----------|---------------------|--------------|
|单击|**空火点击（ ）**|当控件捕获鼠标时触发，收到任何**BUTTONUP（** 左、中或右）消息，并在控件上释放按钮。 库存鼠标向下和鼠标Up事件在此事件之前发生。<br /><br /> 事件地图条目： **EVENT_STOCK_CLICK（ ）**|
|DblClick|**空火点点击（ ）**|类似于单击，但在收到**BUTTONDBLCLK**消息时触发。<br /><br /> 事件地图条目： **EVENT_STOCK_DBLCLICK（ ）**|
|错误|**空火错误（SCODE***码***， LPCSTR，** `lpszDescription` **UINT**`nHelpID`= 0 **）**        |当在方法调用或属性访问范围之外的 ActiveX 控件中发生错误时触发。<br /><br /> 事件地图条目： **EVENT_STOCK_ERROREVENT（ ）**|
|KeyDown|**空火键下（短**`nChar`**， 短**`nShiftState`**）**      |收到`WM_SYSKEYDOWN`或`WM_KEYDOWN`消息时触发。<br /><br /> 事件地图条目： **EVENT_STOCK_KEYDOWN（ ）**|
|键新闻|**空火键新闻（短**<strong>\*</strong>`pnChar`**）**    |收到`WM_CHAR`消息时触发。<br /><br /> 事件地图条目： **EVENT_STOCK_KEYPRESS（ ）**|
|KeyUp|**空火钥匙（短**`nChar`**，短**`nShiftState`**）**      |收到`WM_SYSKEYUP`或`WM_KEYUP`消息时触发。<br /><br /> 事件地图条目： **EVENT_STOCK_KEYUP（ ）**|
|鼠标向下|**空火鼠标向下（短**`nButton`**， 短**`nShiftState`**， 浮点***x，* **浮点***y）***)**          |如果收到任何**BUTTONDOWN（** 左、中或右），则触发。 在触发此事件之前，将立即捕获鼠标。<br /><br /> 事件地图条目： **EVENT_STOCK_MOUSEDOWN（ ）**|
|鼠标移动|**空火鼠标移动（短**`nButton`**，短**`nShiftState`**，浮点***x，***浮点***y）***)**          |收到WM_MOUSEMOVE消息时触发。<br /><br /> 事件地图条目： **EVENT_STOCK_MOUSEMOVE （ ）**|
|鼠标向上|**空火鼠标（短**`nButton`**，短**`nShiftState`**，浮点***x，***浮点***y）***)**          |如果收到任何**BUTTONUP（** 左、中或右），则触发。 在触发此事件之前释放鼠标捕获。<br /><br /> 事件地图条目： **EVENT_STOCK_MOUSEUP（ ）**|
|就绪状态更改|**空火准备状态转换（ ）**|当控件由于接收的数据量而转换到下一个就绪状态时触发。<br /><br /> 事件地图条目： **EVENT_STOCK_READYSTATECHANGE（ ）**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>使用添加事件向导添加股票事件

添加股票事件所需的工作比添加自定义事件少，因为实际事件的触发由基类自动处理`COleControl`。 以下过程将库存事件添加到使用[MFC ActiveX 控制向导](../mfc/reference/mfc-activex-control-wizard.md)开发的控件。 当按下键且控件处于活动状态时，该事件称为 KeyPress。 此过程还可用于添加其他库存事件。 将所选股票事件名称替换为 KeyPress。

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>使用"添加事件向导"添加 KeyPress 股票事件

1. 加载控件的项目。

1. 在类视图中，右键单击 ActiveX 控件类以打开快捷菜单。

1. 在快捷菜单中，单击"**添加"，** 然后单击"**添加事件**"。

   这将打开"添加事件向导"。

1. 在 **"事件名称**"下拉列表中，选择`KeyPress`。

1. 单击“完成”  。

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>添加股票事件的事件向导更改

由于股票事件由控件的基类处理，因此添加事件向导不会以任何方式更改类声明。 它将事件添加到控件的事件映射，并在 其 中进行条目。IDL 文件。 下一行将添加到位于控件类实现 （的控件的事件映射中。CPP） 文件：

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

当收到WM_CHAR消息且控件处于活动状态时，添加此代码将触发 KeyPress 事件。 KeyPress 事件可以通过在控制代码中调用其触发函数（例如），`FireKeyPress`在其他时间触发。

添加事件向导将以下代码行添加到控件的 。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

此行将 KeyPress 事件与其标准调度 ID 关联，并允许容器预测 KeyPress 事件。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
