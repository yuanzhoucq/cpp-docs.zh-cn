---
title: MFC ActiveX 控件：事件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
ms.openlocfilehash: 129b805379fa68cb4f50ee1f8e3ac7d1b725d9ec
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622328"
---
# <a name="mfc-activex-controls-events"></a>MFC ActiveX 控件：事件

ActiveX 控件使用事件来通知容器控件发生了某个事件。 事件的常见示例包括单击控件、使用键盘输入的数据，以及控件状态的更改。 当执行这些操作时，控件将引发一个事件以提醒容器。

事件也称为消息。

MFC 支持两种类型的事件： stock 和 custom。 Stock 事件是类[COleControl](reference/colecontrol-class.md)自动处理的事件。 有关常用事件的完整列表，请参阅[MFC ActiveX 控件：添加常用事件](mfc-activex-controls-adding-stock-events-to-an-activex-control.md)一文。 自定义事件允许控件在特定于该控件的操作发生时通知容器。 某些示例是控件内部状态或特定窗口消息的接收状态的更改。

为了使控件正确地引发事件，控件类必须将控件的每个事件映射到在发生相关事件时应调用的成员函数。 这种映射机制（称为事件映射）集中了有关事件的信息，并允许 Visual Studio 轻松访问和操作控件的事件。 此事件映射由以下宏声明，该宏位于标头（。H）文件：

[!code-cpp[NVC_MFC_AxUI#2](codesnippet/cpp/mfc-activex-controls-events_1.h)]

声明事件映射后，必须在控件的实现中定义（。CPP）文件。 下面几行代码定义事件映射，使控件能够触发特定事件：

[!code-cpp[NVC_MFC_AxUI#3](codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

如果使用 MFC ActiveX 控件向导创建项目，则会自动添加这些行。 如果不使用 MFC ActiveX 控件向导，则必须手动添加这些行。

使用类视图，你可以添加由类 `COleControl` 或你定义的自定义事件支持的常用事件。 对于每个新事件，类视图自动将适当的条目添加到控件的事件映射和控件的。IDL 文件。

其他两篇文章详细讨论了事件：

- [MFC ActiveX 控件：添加常用事件](mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [MFC ActiveX 控件：添加自定义事件](mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 类](reference/colecontrol-class.md)
