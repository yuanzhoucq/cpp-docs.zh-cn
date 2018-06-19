---
title: ActiveX 控件容器： 处理 ActiveX 控件中的事件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [MFC], ActiveX controls
- ActiveX control containers [MFC], event sinks
- event handling [MFC], ActiveX controls
- ON_EVENT macro [MFC]
- ActiveX controls [MFC], events [MFC]
- END_EVENTSINK_MAP macro, using
- events [MFC], ActiveX controls
- BEGIN_EVENTSINK_MAP macro
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f142fc49d2759c4edd7cdb8701b300d435e67f54
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333825"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX 控件容器：处理 ActiveX 控件中的事件
本文讨论如何使用属性窗口在 ActiveX 控件容器中安装 ActiveX 控件的事件处理程序。 使用事件处理程序接收通知 （从控件） 的某些事件，并在响应中执行某些操作。 此通知称为"触发"事件。  
  
> [!NOTE]
>  本文使用一个名为 Container、基于对话框的 ActiveX 控件容器项目和一个名为 Circ 的嵌入控件分别作为过程和代码中的示例。  
  
 在属性窗口中使用事件按钮，可以创建 ActiveX 控件容器应用程序中可能会发生事件的映射。 此映射，称为"事件接收器映射 '，是由创建和维护 Visual c + + 事件处理程序添加到的控件容器类时。 每个事件处理程序，实现与事件映射项，将特定事件映射到容器事件处理程序成员函数。 指定的事件激发通过 ActiveX 控件对象时调用此事件处理程序函数。  
  
 有关事件接收器映射的详细信息，请参阅[事件接收器映射](../mfc/reference/event-sink-maps.md)中*类库参考*。  
  
##  <a name="_core_event_handler_modifications_to_the_project"></a> 项目的修改的事件处理程序  
 当使用属性窗口来添加事件处理程序时，事件接收器映射是声明和定义项目中。 以下语句添加到控件。CPP 文件添加事件处理程序的第一个时间。 此代码声明事件接收器映射对话框类 (在这种情况下， `CContainerDlg`):  
  
 [!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]  
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]  
  
 因为你可以使用属性窗口来添加事件，事件映射条目 (`ON_EVENT`) 添加到事件接收器映射和事件处理程序函数添加到容器的实现 (。CPP) 文件。  
  
 下面的示例声明一个事件处理程序，调用`OnClickInCircCtrl`，Circ 控件**ClickIn**事件：  
  
 [!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]  
  
 此外，以下模板添加到`CContainerDlg`类实现 (。事件处理程序成员函数的 CPP) 文件：  
  
 [!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]  
  
 有关事件接收器宏的详细信息，请参阅[事件接收器映射](../mfc/reference/event-sink-maps.md)中*类库参考*。  
  
#### <a name="to-create-an-event-handler-function"></a>若要创建事件处理程序函数  
  
1.  从类视图中，选择包含 ActiveX 控件的对话框类。 对于此示例中，使用`CContainerDlg`。  
  
2.  在属性窗口中，单击**事件**按钮。  
  
3.  在属性窗口中，选择嵌入 ActiveX 控件的控件 ID。 对于此示例中，使用`IDC_CIRCCTRL1`。  
  
     属性窗口显示可以由嵌入 ActiveX 控件触发的事件的列表。 已以粗体显示的任何成员函数具有分配给它的处理程序函数。  
  
4.  选择要在对话框类来处理的事件。 对于此示例中，选择**单击**。  
  
5.  从右侧的下拉列表框中，选择**\<添加 > ClickCircctrl1**。  
  
6.  双击从类视图跳转到事件处理程序代码中实现的新处理程序函数 (。CPP） 文件中的`CContainerDlg`。  
  
## <a name="see-also"></a>请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)

