---
title: MFC ActiveX 控件：创建 Windows 控件的子类
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
ms.openlocfilehash: 354cd1cac5db775ea56cb5215a8528bdfe9ac5ab
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225002"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC ActiveX 控件：创建 Windows 控件的子类

本文介绍了通过将常用的 Windows 控件子类化来创建 ActiveX 控件的过程。 将现有的 Windows 控件子类化是一种开发 ActiveX 控件的快速方法。 新的控件将具有已被子类化的 Windows 控件的能力，如绘制和响应鼠标单击。 MFC ActiveX 控件示例[按钮](../overview/visual-cpp-samples.md)是对 Windows 控件进行子类化的示例。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

若要将 Windows 控件子类化，请完成以下任务：

- [重写 COleControl 的 IsSubclassedControl 和 PreCreateWindow 成员函数](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [修改 OnDraw 成员函数](#_core_modifying_the_ondraw_member_function)

- [处理反射给控件的所有 ActiveX 控件消息 (OCM)](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > 如果使用 "**控件设置**" 页上的 "**选择父窗口类**" 下拉列表选择要划分为子类的控件，则 ActiveX 控件向导会为您完成大部分工作。

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>重写 IsSubclassedControl 和 PreCreateWindow

若要重写 `PreCreateWindow` 和 `IsSubclassedControl` ，请将以下代码行添加到 **`protected`** 控件类声明的部分中：

[!code-cpp[NVC_MFC_AxSub#1](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

在控件实现文件 (.cpp) 中，添加以下代码行以实现两个重写的函数：

[!code-cpp[NVC_MFC_AxSub#2](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

请注意，在此示例中，将在 `PreCreateWindow` 中指定 Windows 按钮控件。 但是，任何标准 Windows 控件都可以子类化。 有关标准 Windows 控件的详细信息，请参阅[控件](controls-mfc.md)。

在子类化 Windows 控件时，您可能需要指定在创建控件的窗口时要使用的特定窗口样式 (WS_) 或扩展窗口样式 (WS_EX_) 标志。 `PreCreateWindow`通过修改 `cs.style` 和结构字段，可以在成员函数中设置这些参数的值 `cs.dwExStyle` 。 应使用**或**操作对这些字段进行修改，以便保留由类设置的默认标志 `COleControl` 。 例如，如果控件将对 BUTTON 控件进行子类化，而你希望控件显示为复选框，则应在 `CSampleCtrl::PreCreateWindow` 的实现中，在返回语句之前插入以下代码行：

[!code-cpp[NVC_MFC_AxSub#3](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

此操作会添加 BS_CHECKBOX 样式标志，同时保留类的默认样式标志（WS_CHILD）不 `COleControl` 变。

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>修改 OnDraw 成员函数

如果您希望子类化控件与相应的 Windows 控件保持同样的外观，则该控件的 `OnDraw` 成员函数只应包含对 `DoSuperclassPaint` 成员函数的调用，如以下示例中所示：

[!code-cpp[NVC_MFC_AxSub#4](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

由 `DoSuperclassPaint` 实现的 `COleControl` 成员函数使用 Windows 控件的窗口过程，在指定的设备上下文中的边框内绘制控件。 这将使控件即使处于不活动状态时也可见。

> [!NOTE]
> `DoSuperclassPaint`成员函数将仅适用于那些允许将设备上下文作为 WM_PAINT 消息的*wParam*传递的控件类型。 这包含某些标准的 Windows 控件，例如 SCROLLBAR 和 BUTTON 以及所有常用控件。 对于不支持此行为的控件，必须提供你自己的代码来正确地显示不活动的控件。

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>处理反射的窗口消息

Windows 控件通常将特定窗口信息发送到其父窗口。 其中一些消息（如WM_COMMAND）提供用户操作的通知。 其他一些信息（如 WM_CTLCOLOR）用于从父窗口中获取信息。 ActiveX 控件与父窗口的通信通常采用其他方式完成。 将通过激发事件（发送事件通知）来传递通知，并通过访问容器的环境属性来获取有关控件容器的信息。 由于存在这些通信方法，因此 ActiveX 控件容器不应处理由控件发送的任何窗口信息。

若要阻止容器接收由子类化 Windows 控件发送的窗口消息，`COleControl` 将创建一个额外的窗口来充当控件的父级。 此额外窗口称为“反射器”，仅针对子类化 Windows 控件且与控件窗口具有相同大小和位置的 ActiveX 控件创建。 反射器窗口截获某些窗口消息并将其发送回控件。 控件（在其窗口过程中）可以通过对 ActiveX 控件采取适当操作（例如，激发事件）来处理这些反射的消息。 有关被截获的 windows 消息及其相应的反射消息的列表，请参阅[反射窗口消息 id](reflected-window-message-ids.md) 。

ActiveX 控件容器可以设计为自行执行消息反射，从而不必使用 `COleControl` 来创建反射器窗口，减少了子类化 Windows 控件的运行时开销。 `COleControl`通过检查值为**TRUE**的 MessageReflect 环境属性，检测容器是否支持此功能。

若要处理一个反射窗口消息，请在控件消息映射中添加一个条目，并实现处理程序函数。 由于反射的消息不是由 Windows 定义的标准消息集的一部分，因此类视图不支持添加此类消息处理程序。 然而，手动添加处理程序并不困难。

要添加反射窗口消息的消息处理程序，需要手动执行以下操作：

- 在控件类 .H 文件中，声明一个处理程序函数。 函数的返回类型应为**LRESULT**和两个参数，分别为类型**WPARAM**和**LPARAM**。 例如：

   [!code-cpp[NVC_MFC_AxSub#5](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- 在控件类中。CPP 文件中，将 ON_MESSAGE 条目添加到消息映射。 此条目的参数应该是消息标识符和处理程序函数的名称。 例如：

   [!code-cpp[NVC_MFC_AxSub#7](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- 还在中。CPP 文件中，实现 `OnOcmCommand` 成员函数来处理反射的消息。 *WParam*和*lParam*参数与原始窗口消息的参数相同。

有关如何处理反射消息的示例，请参阅 MFC ActiveX 控件示例[按钮](../overview/visual-cpp-samples.md)。 它演示了一个 `OnOcmCommand` 处理程序，该处理程序通过触发（发送）事件来检测 BN_CLICKED 通知代码并做出响应 `Click` 。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
