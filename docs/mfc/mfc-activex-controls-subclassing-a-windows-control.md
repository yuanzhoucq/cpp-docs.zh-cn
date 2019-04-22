---
title: MFC ActiveX 控件：子类化 Windows 控件
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: 7042df6e7b7dc2c9a608470ba7cfc5a9e9f6127a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773250"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC ActiveX 控件：子类化 Windows 控件

本文介绍了通过将常用的 Windows 控件子类化来创建 ActiveX 控件的过程。 将现有的 Windows 控件子类化是一种开发 ActiveX 控件的快速方法。 新的控件将具有已被子类化的 Windows 控件的能力，如绘制和响应鼠标单击。 MFC ActiveX 控件示例[按钮](../overview/visual-cpp-samples.md)是子类化 Windows 控件的一个示例。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

若要将 Windows 控件子类化，请完成以下任务：

- [重写 COleControl 的 IsSubclassedControl 和 PreCreateWindow 成员函数](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [修改 OnDraw 成员函数](#_core_modifying_the_ondraw_member_function)

- [处理反射给控件所有 ActiveX 控件消息 (OCM)](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > 其中的大部分工作为您完成 ActiveX 控件向导如果您选择要使用子类化控件**选择父窗口类**上的下拉列表**控制设置**页。

##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> 重写 IsSubclassedControl 和 PreCreateWindow

若要重写`PreCreateWindow`并`IsSubclassedControl`，添加以下代码行**受保护的**控件类声明的部分：

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

在控件实现文件 (.cpp) 中，添加以下代码行以实现两个重写的函数：

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

请注意，在此示例中，将在 `PreCreateWindow` 中指定 Windows 按钮控件。 但是，任何标准 Windows 控件都可以子类化。 有关标准 Windows 控件的详细信息，请参阅[控件](../mfc/controls-mfc.md)。

当子类化 Windows 控件，您可能想要指定特定窗口样式 (WS_) 或要在创建控件的窗口中使用的扩展的窗口样式 (WS_EX_) 标志。 可以设置这些参数中的值`PreCreateWindow`成员函数通过修改`cs.style`和`cs.dwExStyle`结构字段。 应使用进行到这些字段的修改**或者**操作，用于保留由类设置的默认标志`COleControl`。 例如，如果控件将对 BUTTON 控件进行子类化，而你希望控件显示为复选框，则应在 `CSampleCtrl::PreCreateWindow` 的实现中，在返回语句之前插入以下代码行：

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

此操作而使类的默认样式标志 (WS_CHILD) 添加 BS_CHECKBOX 样式标志，`COleControl`保持不变。

##  <a name="_core_modifying_the_ondraw_member_function"></a> 修改 OnDraw 成员函数

如果您希望子类化控件与相应的 Windows 控件保持同样的外观，则该控件的 `OnDraw` 成员函数只应包含对 `DoSuperclassPaint` 成员函数的调用，如以下示例中所示：

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

由 `DoSuperclassPaint` 实现的 `COleControl` 成员函数使用 Windows 控件的窗口过程，在指定的设备上下文中的边框内绘制控件。 这将使控件即使处于不活动状态时也可见。

> [!NOTE]
>  `DoSuperclassPaint`成员函数仅使用允许设备上下文以作为传递这些控件类型*wParam*的 WM_PAINT 消息。 这包括一些标准 Windows 控件，如滚动条和按钮，以及所有常用控件。 对于不支持此行为的控件，必须提供你自己的代码来正确地显示不活动的控件。

##  <a name="_core_handling_reflected_window_messages"></a> 处理反射窗口消息

Windows 控件通常将特定窗口信息发送到其父窗口。 其中某些消息，如 WM_COMMAND，提供由用户操作的通知。 其他人，例如 WM_CTLCOLOR，用于从父窗口中获取信息。 ActiveX 控件与父窗口的通信通常采用其他方式完成。 将通过激发事件（发送事件通知）来传递通知，并通过访问容器的环境属性来获取有关控件容器的信息。 由于存在这些通信方法，因此 ActiveX 控件容器不应处理由控件发送的任何窗口信息。

若要阻止容器接收由子类化 Windows 控件发送的窗口消息，`COleControl` 将创建一个额外的窗口来充当控件的父级。 此额外窗口称为“反射器”，仅针对子类化 Windows 控件且与控件窗口具有相同大小和位置的 ActiveX 控件创建。 反射器窗口截获某些窗口消息并将其发送回控件。 控件（在其窗口过程中）可以通过对 ActiveX 控件采取适当操作（例如，激发事件）来处理这些反射的消息。 请参阅[反映窗口消息 Id](../mfc/reflected-window-message-ids.md)有关被截取的窗口的列表的消息和及其相应的反射消息。

ActiveX 控件容器可以设计为自行执行消息反射，从而不必使用 `COleControl` 来创建反射器窗口，减少了子类化 Windows 控件的运行时开销。 `COleControl` 检测容器是否支持此功能通过检查 MessageReflect 环境属性值为 **，则返回 TRUE**。

若要处理一个反射窗口消息，请在控件消息映射中添加一个条目，并实现处理程序函数。 由于反射的消息不是由 Windows 定义的标准消息集的一部分，因此类视图不支持添加此类消息处理程序。 然而，手动添加处理程序并不困难。

要添加反射窗口消息的消息处理程序，需要手动执行以下操作：

- 在控件类 .H 文件中，声明一个处理程序函数。 该函数应具有的返回类型**LRESULT**和类型的两个参数**WPARAM**并**LPARAM**分别。 例如：

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- 在控件类中。CPP 文件中，将一个 ON_MESSAGE 条目添加到消息映射。 此条目的参数应该是消息标识符和处理程序函数的名称。 例如：

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- 另外，请在。CPP 文件实现`OnOcmCommand`成员函数处理反射的消息。 *WParam*并*lParam*参数是不同于原始窗口消息。

有关举例说明如何反映在处理消息，请参阅 MFC ActiveX 控件示例[按钮](../overview/visual-cpp-samples.md)。 它演示了`OnOcmCommand`处理程序，它检测 BN_CLICKED 通知代码，并通过激发 （发送） 响应`Click`事件。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)
