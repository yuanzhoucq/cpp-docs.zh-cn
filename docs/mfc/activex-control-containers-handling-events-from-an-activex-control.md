---
title: "ActiveX 控件容器：处理 ActiveX 控件中的事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件容器 [C++], 事件接收器"
  - "ActiveX 控件 [C++], 事件"
  - "BEGIN_EVENTSINK_MAP 宏"
  - "END_EVENTSINK_MAP 宏, using"
  - "事件处理程序 [C++], ActiveX 控件"
  - "事件处理 [C++], ActiveX 控件"
  - "事件 [C++], ActiveX 控件"
  - "ON_EVENT 宏"
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ActiveX 控件容器：处理 ActiveX 控件中的事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文讨论使用属性窗口安装 ActiveX 控件的事件处理程序中的 ActiveX 控件容器。  事件处理程序中响应用于接收通知 \(来自控件\) 某些事件并执行一些操作。  此通知调用“激发”事件。  
  
> [!NOTE]
>  本文中的过程和代码使用一个基于对话框的 ActiveX 控件容器项目命名的容器和作为示例中名为的 Circ 嵌入的控件。  
  
 使用事件按在"属性"窗口中，可以在 ActiveX 控件容器应用程序中发生事件的映射。  此映射，名为“事件接收器”映射，通过 Visual C\+\+ 创建和维护，将事件处理程序连接到的控件容器类时。  每个事件处理程序实现，与事件映射项，映射给定事件对容器事件处理程序成员函数。  指定的事件。ActiveX 控件对象激发时，此事件处理函数调用。  
  
 有关事件接收器的更多信息，请参见位于 *类库参考中*[事件接收器会映射](../mfc/reference/event-sink-maps.md)。  
  
##  <a name="_core_event_handler_modifications_to_the_project"></a> 对项目的事件处理程序中修改  
 当您正在使用"属性"窗口添加事件处理程序时，将事件接收在映射项目声明和定义。  第一个事件处理程序中，添加下列语句添加至控件 .cpp 文件。  此代码声明对话框类的 \(在这种情况下，`CContainerDlg`\) 的事件接收器映射：  
  
 [!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]  
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]  
  
 因为您正在使用"属性"窗口添加事件，事件映射项 \(`ON_EVENT`\) 添加到事件接收器和函数映射添加到容器实现的事件处理程序 \(.cpp\) 文件。  
  
 下面的示例声明事件处理程序中，调用 `OnClickInCircCtrl`，Circ 控件的 **ClickIn** 事件中：  
  
 [!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]  
  
 此外，以下模板会添加到事件处理程序 `CContainerDlg` 类成员函数的实现 \(.cpp\) 文件：  
  
 [!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]  
  
 有关宏事件接收器的更多信息，请参见位于 *类库参考中*[事件接收器会映射](../mfc/reference/event-sink-maps.md)。  
  
#### 创建事件处理函数  
  
1.  从"类视图"中，选择包含 ActiveX 控件的对话框类。  对于此例，请使用 `CContainerDlg`。  
  
2.  在“属性”窗口中单击**“事件”**按钮。  
  
3.  在属性窗口中，选择的 ActiveX 控件嵌入的控件 ID。  对于此例，请使用 `IDC_CIRCCTRL1`。  
  
     属性窗口显示可由嵌入一个 ActiveX 控件激发事件的列表。  以粗体显示的所有成员函数已经有处理程序函数分配给它。  
  
4.  选择希望对话框类处理事件。  对于此示例，选择 **单击**。  
  
5.  从右边的下拉列表框中，选择 **\<Add ClickCircctrl1\>** 。  
  
6.  双击类从视图的新处理程序函数跳转到 `CContainerDlg`实现 \(.cpp\) 文件中的事件处理程序代码。  
  
## 请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)