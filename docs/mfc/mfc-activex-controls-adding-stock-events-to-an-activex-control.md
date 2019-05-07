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
ms.openlocfilehash: 9f6f3c63f0436296791df428c704bce96eca3ec0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392721"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX 控件：向 ActiveX 控件添加常用事件

常用事件不同于自定义事件，它们会自动触发由类[COleControl](../mfc/reference/colecontrol-class.md)。 `COleControl` 包含引发事件导致的常见操作的预定义的成员函数。 由实现的一些常见操作`COleControl`包括单-和当时的 clicks 控件、 键盘事件和更改鼠标按钮的状态。 事件映射条目股票 EVENT_STOCK 前缀始终前面带有事件。

##  <a name="_core_stock_events_supported_by_classwizard"></a> 常用支持的事件添加事件向导

`COleControl`类提供了十个股票的事件下, 表中列出。 可以指定你想使用控件中的事件[添加事件向导](../ide/add-event-wizard.md)。

### <a name="stock-events"></a>常用事件

|Event|触发函数|注释|
|-----------|---------------------|--------------|
|单击|**void FireClick( )**|触发时控制捕获鼠标，任何**BUTTONUP**接收 （左侧、 中间或右侧） 消息，并在控件上释放该按钮。 此事件之前发生的股票鼠标按下和 MouseUp 事件。<br /><br /> 事件映射条目：**EVENT_STOCK_CLICK( )**|
|DblClick|**void FireDblClick( )**|单击与类似但时引发的**BUTTONDBLCLK**接收消息。<br /><br /> 事件映射条目：**EVENT_STOCK_DBLCLICK( )**|
|Error|**void FireError( SCODE**  *scode* **, LPCSTR**  `lpszDescription` **, UINT**  `nHelpID`  **= 0 )**|当将范围之外的方法调用或属性访问 ActiveX 控件中发生错误时引发。<br /><br /> 事件映射条目：**EVENT_STOCK_ERROREVENT( )**|
|KeyDown|**void FireKeyDown( short**  `nChar` **, short**  `nShiftState`  **)**|时引发的`WM_SYSKEYDOWN`或`WM_KEYDOWN`接收消息。<br /><br /> 事件映射条目：**EVENT_STOCK_KEYDOWN( )**|
|KeyPress|**void FireKeyPress( short** <strong>\*</strong>  `pnChar`  **)**|时引发的`WM_CHAR`接收消息。<br /><br /> 事件映射条目：**EVENT_STOCK_KEYPRESS( )**|
|KeyUp|**void FireKeyUp (短**`nChar` **，short**`nShiftState`**)**|时引发的`WM_SYSKEYUP`或`WM_KEYUP`接收消息。<br /><br /> 事件映射条目：**EVENT_STOCK_KEYUP( )**|
|MouseDown|**void FireMouseDown (短**`nButton` **，short** `nShiftState` **，float** *x* **，float** *y*  **)**|如果任何激发**BUTTONDOWN**收到 （左侧、 中间或右侧）。 将鼠标捕获前激发此事件。<br /><br /> 事件映射条目：**EVENT_STOCK_MOUSEDOWN( )**|
|MouseMove|**void FireMouseMove (短**`nButton` **，short** `nShiftState` **，float**  *x* **，float** *y*  **)**|当收到 WM_MOUSEMOVE 消息时触发。<br /><br /> 事件映射条目：**EVENT_STOCK_MOUSEMOVE( )**|
|MouseUp|**void FireMouseUp (短**`nButton` **，short** `nShiftState` **，float**  *x*   **，float** *y*  **)**|如果任何激发**BUTTONUP**收到 （左侧、 中间或右侧）。 激发此事件之前释放鼠标捕获。<br /><br /> 事件映射条目：**EVENT_STOCK_MOUSEUP( )**|
|ReadyStateChange|**void FireReadyStateChange( )**|当控件转换为收到的数据量由于下一步的就绪状态时引发。<br /><br /> 事件映射条目：**EVENT_STOCK_READYSTATECHANGE( )**|

##  <a name="_core_adding_a_stock_event_using_classwizard"></a> 添加常用事件使用添加事件向导

添加常用事件的工作量较比添加自定义事件，因为基类，由自动处理实际事件的激发`COleControl`。 以下过程使用开发的控件添加常用事件[MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)。 调用 KeyPress 事件时触发，按下某个键并在控件处于活动状态。 此过程还用于添加其他常用事件。 替换 KeyPress 的所选的常用事件名称。

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>若要添加按键股票事件使用添加事件向导

1. 加载控件的项目。

1. 在类视图中，右键单击你的 ActiveX 控件类以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加事件**。

   这将打开添加事件向导。

1. 在中**事件名称**下拉列表中，选择`KeyPress`。

1. 单击 **“完成”**。

##  <a name="_core_classwizard_changes_for_stock_events"></a> 为常用事件添加事件向导更改

因为常用事件处理由控件的基类，添加事件向导不会更改以任何方式在类声明。 它将事件添加到控件的事件映射，并使将项记入它。IDL 文件。 将以下行添加到控件的事件映射，位于控件类实现 (。CPP) 文件：

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

添加此代码会触发 KeyPress 事件时接收到 WM_CHAR 消息和控件处于活动状态。 通过调用其触发函数，可以在其他时间触发 KeyPress 事件 (例如， `FireKeyPress`) 从在控件代码内。

添加事件向导将以下代码行添加到控件的。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

此行将按键事件与标准的调度 ID 相关联，并允许以应对预期的 KeyPress 事件的容器。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
