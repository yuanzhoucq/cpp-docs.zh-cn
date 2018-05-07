---
title: MFC ActiveX 控件： 向 ActiveX 控件添加常用事件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 210749906391ccdba2e488b75be98264bcba39cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX 控件：向 ActiveX 控件添加常用事件
常用事件不同于自定义事件，因为它们自动触发由类[COleControl](../mfc/reference/colecontrol-class.md)。 `COleControl` 包含激发事件导致常见操作的预定义的成员函数。 实现的一些常见操作`COleControl`纳入单-和当时-clicks 上的控件、 键盘事件和更改鼠标按钮的状态。 常用事件的事件映射条目始终前面带有**EVENT_STOCK**前缀。  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a> 常用支持的事件添加事件向导  
 `COleControl`类提供了十个常用的事件下, 表中列出。 你可以指定希望你使用在控件中的事件[添加事件向导](../ide/add-event-wizard.md)。  
  
### <a name="stock-events"></a>常用事件  
  
|事件|触发函数|注释|  
|-----------|---------------------|--------------|  
|单击|**void FireClick （)**|当控件捕获鼠标，任何激发**BUTTONUP**接收 （左、 中间，或向右） 的消息，并且在控件上释放按钮。 在此事件之前发生的 stock MouseDown 和 MouseUp 事件。<br /><br /> 事件映射条目： **EVENT_STOCK_CLICK （)**|  
|DblClick|**void FireDblClick （)**|时，单击与类似但激发**BUTTONDBLCLK**接收消息。<br /><br /> 事件映射条目： **EVENT_STOCK_DBLCLICK （)**|  
|Error|**void FireError (SCODE***scode* **，LPCSTR** `lpszDescription` **，UINT**`nHelpID`**= 0)** |在范围之外的方法调用或属性访问 ActiveX 控件内发生错误时激发。<br /><br /> 事件映射条目： **EVENT_STOCK_ERROREVENT （)**|  
|KeyDown|**void FireKeyDown (短**`nChar` **，short**`nShiftState`**)** |时激发`WM_SYSKEYDOWN`或`WM_KEYDOWN`接收消息。<br /><br /> 事件映射条目： **EVENT_STOCK_KEYDOWN （)**|  
|KeyPress|**void FireKeyPress (短\***`pnChar`**)** |时激发`WM_CHAR`接收消息。<br /><br /> 事件映射条目： **EVENT_STOCK_KEYPRESS （)**|  
|KeyUp|**void FireKeyUp (短**`nChar` **，short**`nShiftState`**)** |时激发`WM_SYSKEYUP`或`WM_KEYUP`接收消息。<br /><br /> 事件映射条目： **EVENT_STOCK_KEYUP （)**|  
|MouseDown|**void FireMouseDown (短**`nButton` **，short** `nShiftState` **，float***x* **，float** *y***)** |如果任何激发**BUTTONDOWN**收到 （左、 中间或向右）。 激发此事件之前，捕获了鼠标。<br /><br /> 事件映射条目： **EVENT_STOCK_MOUSEDOWN （)**|  
|MouseMove|**void FireMouseMove (短**`nButton` **，short** `nShiftState` **，float***x* **，float** *y***)** |时激发`WM_MOUSEMOVE`接收消息。<br /><br /> 事件映射条目： **EVENT_STOCK_MOUSEMOVE （)**|  
|MouseUp|**void FireMouseUp (短**`nButton` **，short** `nShiftState` **，float***x* **，float** *y***)** |如果任何激发**BUTTONUP**收到 （左、 中间或向右）。 激发此事件之前，释放鼠标捕获。<br /><br /> 事件映射条目： **EVENT_STOCK_MOUSEUP （)**|  
|ReadyStateChange|**void FireReadyStateChange （)**|在控件转换到下一步收到的数据量由于就绪状态时激发。<br /><br /> 事件映射条目： **EVENT_STOCK_READYSTATECHANGE （)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a> 添加常用事件使用添加事件向导  
 添加常用事件需要比实际事件的激发会自动处理由基类，因为添加自定义事件的工作较少`COleControl`。 下面的过程开发使用的控件添加常用事件[MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)。 当按下某个键且该控件处于活动状态，将引发该事件，调用 KeyPress。 此过程还可用来添加其他常用事件。 KeyPress 的所选的常用事件名称替换。  
  
#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>若要添加使用添加事件向导 KeyPress 常用事件  
  
1.  加载控件的项目。  
  
2.  在类视图中，右键单击你的 ActiveX 控件类，以打开快捷菜单。  
  
3.  从快捷菜单中，单击**添加**，然后单击**添加事件**。  
  
     这将打开添加事件向导。  
  
4.  在**事件名称**下拉列表中，选择`KeyPress`。  
  
5.  单击 **“完成”**。  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a> 有关常用事件添加事件向导更改  
 因为常用事件处理由控件的基类，添加事件向导不会更改类声明中的以任何方式。 它将事件添加到控件的事件映射，并使将项记入其。IDL 文件。 以下行添加到控件的事件映射，位于控件类实现 (。CPP) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 添加此代码将触发 KeyPress 事件时`WM_CHAR`接收消息并且该控件处于活动状态。 通过调用其触发函数，可以在其他时间激发 KeyPress 事件 (例如， `FireKeyPress`) 从该控件代码中。  
  
 添加事件向导将以下代码行添加到控件的。IDL 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 此行将 KeyPress 事件与其标准的调度 ID 相关联，并允许容器后，可以预计的 KeyPress 事件。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 类](../mfc/reference/colecontrol-class.md)
