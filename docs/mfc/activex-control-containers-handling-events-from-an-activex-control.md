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
ms.openlocfilehash: ae623ee0973e78db3b542646dd6bdec58cc2dfc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367954"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX 控件容器：处理 ActiveX 控件中的事件

本文讨论使用**属性**窗口（**类视图**中）在 ActiveX 控件容器中为 ActiveX 控件安装事件处理程序。 事件处理程序用于接收某些事件的通知（来自控件），并在响应中执行某些操作。 此通知称为"触发"事件。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

> [!NOTE]
> 本文使用一个名为 Container、基于对话框的 ActiveX 控件容器项目和一个名为 Circ 的嵌入控件分别作为过程和代码中的示例。

使用 **"属性**"窗口中的事件按钮（**在类视图中**），可以创建 ActiveX 控件容器应用程序中可能发生的事件映射。 此映射称为"事件接收器映射"，由 Visual C++在将事件处理程序添加到控件容器类时创建和维护。 每个事件处理程序（使用事件映射条目实现）将特定事件映射到容器事件处理程序成员函数。 当 ActiveX 控件对象触发指定事件时，将调用此事件处理程序函数。

有关事件接收器映射的详细信息，请参阅*类库参考*中的[事件接收器映射](../mfc/reference/event-sink-maps.md)。

## <a name="event-handler-modifications-to-the-project"></a><a name="_core_event_handler_modifications_to_the_project"></a>事件处理程序对项目的修改

使用 **"属性"** 窗口添加事件处理程序时，将声明和在项目中定义事件接收器映射。 以下语句将添加到控件 中。首次添加事件处理程序时，CPP 文件。 此代码声明对话框类的事件接收器映射（在本例中`CContainerDlg`为 ）：

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

当您使用 **"属性"** 窗口添加事件时，事件映射条目 （`ON_EVENT`） 将添加到事件接收器映射中，并将事件处理程序函数添加到容器的实现 （）。CPP）文件。

以下示例声明 Circ 控件`OnClickInCircCtrl``ClickIn`事件的事件处理程序，称为 ，该处理程序：

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

此外，以下模板将添加到`CContainerDlg`类实现 （。事件处理程序成员函数的 CPP） 文件：

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

有关事件接收器宏的详细信息，请参阅*类库参考*中的[事件接收器映射](../mfc/reference/event-sink-maps.md)。

#### <a name="to-create-an-event-handler-function"></a>创建事件处理程序函数

1. 从类视图中，选择包含 ActiveX 控件的对话框类。 在此示例中，请使用`CContainerDlg`。

1. 在 **“属性”** 窗口中，单击 **“事件”** 按钮。

1. 在 **"属性"** 窗口中，选择嵌入的 ActiveX 控件的控制 ID。 在此示例中，请使用`IDC_CIRCCTRL1`。

   "**属性"** 窗口显示可由嵌入的 ActiveX 控件触发的事件列表。 以粗体显示的任何成员函数都已为其分配了处理程序函数。

1. 选择要处理对话框类的事件。 在此示例中，选择**单击**。

1. 从右侧的下拉列表框中，选择"**\<添加> ClickCircctrl1**。

1. 双击类视图的新处理程序函数以跳转到实现中的事件处理程序代码 （。的 CPP）`CContainerDlg`文件。

## <a name="see-also"></a>另请参阅

[ActiveX 控制容器](../mfc/activex-control-containers.md)
