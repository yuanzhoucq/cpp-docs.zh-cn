---
title: "MFC ActiveX 控件：向 ActiveX 控件添加常用事件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENT__STOCK_ERROR"
  - "EVENT__STOCK_READYSTATECHANGE"
  - "ReadyStateChange"
  - "EVENT__STOCK_MOUSEMOVE"
  - "EVENT__STOCK_MOUSEUP"
  - "EVENT__STOCK_DBLCLICK"
  - "KeyPress"
  - "EVENT__STOCK_KEYDOWN"
  - "EVENT__STOCK"
  - "EVENT__STOCK_MOUSEDOWN"
  - "EVENT__STOCK_KEYPRESS"
  - "EVENT__STOCK_CLICK"
  - "EVENT__STOCK_KEYUP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EVENT_STOCK 前缀"
  - "EVENT_STOCK_CLICK 事件"
  - "EVENT_STOCK_DBLCLICK 事件"
  - "EVENT_STOCK_ERROREVENT 事件"
  - "EVENT_STOCK_KEYDOWN 事件"
  - "EVENT_STOCK_KEYPRESS 事件"
  - "EVENT_STOCK_KEYPRESS 宏"
  - "EVENT_STOCK_KEYUP 事件"
  - "EVENT_STOCK_MOUSEDOWN 事件"
  - "EVENT_STOCK_MOUSEMOVE 事件"
  - "EVENT_STOCK_MOUSEUP 事件"
  - "EVENT_STOCK_READYSTATECHANGE 事件"
  - "事件 [C++], 常用"
  - "FireClick 事件"
  - "FireDblClick 事件"
  - "FireError 事件"
  - "FireKeyDown 事件"
  - "FireKeyPress 事件"
  - "FireKeyUp 事件"
  - "FireMouseDown 事件"
  - "FireMouseMove 事件"
  - "FireMouseUp 事件"
  - "KeyPress 事件"
  - "MFC ActiveX 控件, 事件"
  - "ReadyStateChange 事件"
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：向 ActiveX 控件添加常用事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

常用事件与自定义事件不同它们由类 [COleControl](../mfc/reference/colecontrol-class.md)自动触发。  `COleControl` 包含预定义的成员函数将事件激发由常见操作。  在控件、和键盘事件更改的 `COleControl` 包含单和双击实现的一些常见操作。鼠标按钮的状态。  事件从事件的映射项始终由 **EVENT\_STOCK** 前缀开头。  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a> 添加事件向导支持常用的事件  
 `COleControl` 类提供了十常用事件，列出了在下表中。  指定可以使用 [添加事件向导](../ide/add-event-wizard.md)中，控件所需的事件。  
  
### 常用事件  
  
|Event|Firing函数|注释|  
|-----------|--------------|--------|  
|单击|**void FireClick \(\)**|激发，当控件捕获鼠标后，所有 **BUTTONUP** \(退出，中间或右对齐\) 接收消息，而按钮释放位于控件上方。  股票 MouseDown 事件和 MouseUp 此事件之前发生。<br /><br /> 事件映射项：**EVENT\_STOCK\_CLICK\( \)**|  
|DblClick|**void FireDblClick \(\)**|类似于，但引发单击 **BUTTONDBLCLK** 消息时接收。<br /><br /> 事件映射项：**EVENT\_STOCK\_DBLCLICK\( \)**|  
|错误|**void FireError\( SCODE  , LPCSTR  , UINT**  *scode* `lpszDescription` `nHelpID`  **\= 0 \)**|激发发生错误，在 ActiveX 控件中生成该方法调用或属性访问的范围之外。<br /><br /> 事件映射项：**EVENT\_STOCK\_ERROREVENT\( \)**|  
|KeyDown|**void FireKeyDown\( short**  `nChar` **, short**  `nShiftState`  **\)**|激发，当 `WM_SYSKEYDOWN` 或 `WM_KEYDOWN` 接收消息。<br /><br /> 事件映射项：**EVENT\_STOCK\_KEYDOWN\( \)**|  
|KeyPress|**void FireKeyPress\( short\***  `pnChar`  **\)**|当 `WM_CHAR` 收消息时激发。<br /><br /> 事件映射项：**EVENT\_STOCK\_KEYPRESS\( \)**|  
|KeyUp|**void FireKeyUp\( short**  `nChar` **, short**  `nShiftState`  **\)**|当 `WM_SYSKEYUP` 或 `WM_KEYUP` 接收消息激发。<br /><br /> 事件映射项：**EVENT\_STOCK\_KEYUP\( \)**|  
|MouseDown|**void FireMouseDown\( short**  `nButton` **, short**  `nShiftState` *x* *y*  **\) , float  , float**|如果任何 **BUTTONDOWN** \(中间或右对齐\) 接收激发。  此事件在引发之前，鼠标捕获。<br /><br /> 事件映射项：**EVENT\_STOCK\_MOUSEDOWN\( \)**|  
|MouseMove|**void FireMouseMove\( short**  `nButton` **, short**  `nShiftState` *x* *y*  **\) , float  , float**|当 `WM_MOUSEMOVE` 收消息时激发。<br /><br /> 事件映射项：**EVENT\_STOCK\_MOUSEMOVE\( \)**|  
|MouseUp|**void FireMouseUp\( short**  `nButton` **, short**  `nShiftState` *x* *y*  **\) , float  , float**|如果任何 **BUTTONUP** \(中间或右对齐\) 接收激发。  此事件在引发之前，释放鼠标捕获。<br /><br /> 事件映射项： **EVENT\_STOCK\_MOUSEUP\( \)**|  
|ReadyStateChange|**void FireReadyStateChange \(\)**|当为就绪状态的下一个控件切换由于数据量来接收激发。<br /><br /> 事件映射项：**EVENT\_STOCK\_READYSTATECHANGE\( \)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a> 添加使用"添加事件向导的一个常用事件  
 添加股票事件比添加自定义事件，因此实际事件激发由基类自动处理，`COleControl`少工作。  下面过程添加常用事件。使用 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)，可能已刻意的控件。  当按下了键时和控件是活动的时，KeyPress 事件，调用，触发。  此过程还使用添加其他常用事件。  KeyPress 选择替换重写常用的事件名称。  
  
#### 使用"添加事件向导，将库存中 KeyPress 事件  
  
1.  加载控件项目。  
  
2.  在"类视图"中，右击该 ActiveX 控件类打开快捷菜单。  
  
3.  从快捷菜单中单击“添加”，然后单击“添加事件”。  
  
     这将打开"添加事件向导"。  
  
4.  在 **Event Name** 拉列表中选择 `KeyPress`。  
  
5.  单击**“完成”**。  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a> 添加事件向导"提供常用事件更改  
 因为股票事件由控件的基类处理，添加事件向导既不更改类声明。  它向控件添加事件的事件映射并在其 .idl 的输入文件。  下列代码行添加到控件的事件映射，位于控件类实现 \(.cpp\) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 添加此代码激发 KeyPress 事件，当 `WM_CHAR` 接收消息时，控件处于活动状态。  KeyPress 事件可以通过调用函数触发在其他时间调用 \(例如，`FireKeyPress`\) 从控件代码内。  
  
 添加事件向导向控件添加以下代码行的 .idl 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 此行将 KeyPress 事件与其标准调度 ID 并允许容器预期 KeyPress 事件。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)