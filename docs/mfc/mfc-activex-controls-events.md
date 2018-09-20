---
title: MFC ActiveX 控件： 事件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4c60c949832f03df6b7bb0e69cfdd95dfafc137
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422865"
---
# <a name="mfc-activex-controls-events"></a>MFC ActiveX 控件：事件

ActiveX 控件使用事件来通知发生到控件的容器。 事件的常见示例包括单击在控件上，输入在控件的状态中使用键盘和更改的数据。 这些操作发生时，该控件触发事件以提醒容器。

事件也称为消息。

MFC 支持两种类型的事件： 常用和自定义。 常用事件是事件的类[COleControl](../mfc/reference/colecontrol-class.md)会自动处理。 常用事件的完整列表，请参阅文章[MFC ActiveX 控件： 添加常用事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)。 自定义事件使控件能够在特定于该控件的操作发生时通知该容器。 一些示例是一个控件的内部状态或在某些窗口消息接收更改。

为您正确地引发事件的控制，你的控件类必须映射到相关的事件发生时，应调用的成员函数的控件的每个事件。 此映射机制 （称为事件映射） 集中了有关事件的信息，并允许 Visual Studio 轻松访问和操作该控件的事件。 下面的宏，位于标头中声明此事件映射 (。H） 文件的控件类声明：

[!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]

声明事件映射后，它必须在定义控件的实现 (。CPP) 文件。 以下代码行定义事件映射，从而允许您控制触发特定事件：

[!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

如果您使用 MFC ActiveX 控件向导创建项目，它会自动添加这些行。 如果不使用 MFC ActiveX 控件向导，则必须手动添加这些行。

类视图，则你可以添加类支持的常用事件`COleControl`或你定义的自定义事件。 对于每个新的事件，类视图会自动将相应的条目添加到控件的事件映射和控件的。IDL 文件。

下面两篇文章讨论了事件的详细信息：

- [MFC ActiveX 控件： 添加常用事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [MFC ActiveX 控件：添加自定义事件](../mfc/mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
