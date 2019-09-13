---
title: ActiveX 控件容器：处理 ActiveX 控件中的事件
ms.date: 09/12/2018
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
ms.openlocfilehash: 7487792fbc9fe6775640f40755a7f725543fb9f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907761"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX 控件容器：处理 ActiveX 控件中的事件

本文介绍如何使用 "**属性**" 窗口（在**类视图**中）为 activex 控件容器中的 activex 控件安装事件处理程序。 事件处理程序用于接收某些事件的通知（来自控件）并执行某些操作以响应。 此通知称为 "激发" 事件。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

> [!NOTE]
>  本文使用一个名为 Container、基于对话框的 ActiveX 控件容器项目和一个名为 Circ 的嵌入控件分别作为过程和代码中的示例。

使用 "**属性**" 窗口中的 "事件" 按钮（在**类视图**中），可以创建可在 ActiveX 控件容器应用程序中发生的事件的映射。 在将事件处理程序添加到控件容器类C++时，此映射称为 "事件接收器映射"。 使用事件映射项实现的每个事件处理程序将一个特定事件映射到一个容器事件处理程序成员函数。 当 ActiveX 控件对象激发指定的事件时，将调用此事件处理程序函数。

有关事件接收器映射的详细信息，请参阅类库*参考*中的[事件接收器映射](../mfc/reference/event-sink-maps.md)。

##  <a name="_core_event_handler_modifications_to_the_project"></a>对项目的事件处理程序修改

使用 "**属性**" 窗口添加事件处理程序时，会在项目中声明和定义事件接收器映射。 以下语句将添加到控件中。在第一次添加事件处理程序时的 CPP 文件。 此代码为对话框类（在本例中`CContainerDlg`为）声明一个事件接收器映射：

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

使用 "**属性**" 窗口添加事件时，会将事件映射项（`ON_EVENT`）添加到事件接收器映射，并将事件处理程序函数添加到容器的实现（。CPP）文件。

下面的示例为 Circ 控件的`OnClickInCircCtrl` `ClickIn`事件声明一个名为的事件处理程序：

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

此外，以下模板将添加到`CContainerDlg`类实现（。CPP）文件：

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

有关事件接收器宏的详细信息，请参阅类库*参考*中的[事件接收器映射](../mfc/reference/event-sink-maps.md)。

#### <a name="to-create-an-event-handler-function"></a>创建事件处理程序函数

1. 在类视图中，选择包含 ActiveX 控件的对话框类。 对于本示例，请`CContainerDlg`使用。

1. 在 **“属性”** 窗口中，单击 **“事件”** 按钮。

1. 在 "**属性**" 窗口中，选择嵌入的 ActiveX 控件的控件 ID。 对于本示例，请`IDC_CIRCCTRL1`使用。

   "**属性**" 窗口显示可由嵌入 ActiveX 控件触发的事件的列表。 以粗体显示的任何成员函数都已分配有处理程序函数。

1. 选择希望对话框类处理的事件。 对于本示例，请选择 **"单击"** 。

1. 从右侧的下拉列表框中，选择 **\<"添加 > ClickCircctrl1**"。

1. 双击类视图的新处理程序函数，跳转到实现中的事件处理程序代码（。CPP）文件`CContainerDlg`。

## <a name="see-also"></a>请参阅

[ActiveX 控件容器](../mfc/activex-control-containers.md)
