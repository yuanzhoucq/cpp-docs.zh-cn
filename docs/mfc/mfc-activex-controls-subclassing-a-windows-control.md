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
ms.openlocfilehash: ccebbad22be92b84fa2fd84434f788484d332cce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375996"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC ActiveX 控件：创建 Windows 控件的子类

本文介绍了通过将常用的 Windows 控件子类化来创建 ActiveX 控件的过程。 将现有的 Windows 控件子类化是一种开发 ActiveX 控件的快速方法。 新的控件将具有已被子类化的 Windows 控件的能力，如绘制和响应鼠标单击。 MFC ActiveX 控件示例[BUTTON](../overview/visual-cpp-samples.md)是对 Windows 控件进行子类化的示例。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

若要将 Windows 控件子类化，请完成以下任务：

- [重写 COleControl 的 IsSubclassedControl 和 PreCreateWindow 成员函数](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [修改 OnDraw 成员函数](#_core_modifying_the_ondraw_member_function)

- [处理反射给控件的所有 ActiveX 控件消息 (OCM)](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > 如果选择控件使用 **"控件设置"** 页上**的"选择父窗口类**"下拉列表进行子分类，则大部分工作由 ActiveX 控件向导完成。

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>重写是子类控制和预创建窗口

要重写`PreCreateWindow``IsSubclassedControl`和，请向控件类声明的**受保护**部分添加以下行代码：

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

在控件实现文件 (.cpp) 中，添加以下代码行以实现两个重写的函数：

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

请注意，在此示例中，将在 `PreCreateWindow` 中指定 Windows 按钮控件。 但是，任何标准 Windows 控件都可以子类化。 有关标准 Windows 控件的详细信息，请参阅[控件](../mfc/controls-mfc.md)。

在子类化 Windows 控件时，您可能需要指定在创建控件的窗口时要使用的特定窗口样式 (WS_) 或扩展窗口样式 (WS_EX_) 标志。 您可以通过修改 和`PreCreateWindow``cs.style``cs.dwExStyle`结构字段在成员函数中设置这些参数的值。 应使用**OR**操作对这些字段进行修改，以保留由 类`COleControl`设置的默认标志。 例如，如果控件将对 BUTTON 控件进行子类化，而你希望控件显示为复选框，则应在 `CSampleCtrl::PreCreateWindow` 的实现中，在返回语句之前插入以下代码行：

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

此操作将添加BS_CHECKBOX样式标志，同时保留类`COleControl`的默认样式标志（WS_CHILD）。

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>修改 OnDraw 成员函数

如果您希望子类化控件与相应的 Windows 控件保持同样的外观，则该控件的 `OnDraw` 成员函数只应包含对 `DoSuperclassPaint` 成员函数的调用，如以下示例中所示：

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

由 `DoSuperclassPaint` 实现的 `COleControl` 成员函数使用 Windows 控件的窗口过程，在指定的设备上下文中的边框内绘制控件。 这将使控件即使处于不活动状态时也可见。

> [!NOTE]
> 成员`DoSuperclassPaint`函数将仅适用于那些允许将设备上下文作为WM_PAINT消息的*wParam*传递的控件类型。 这包含某些标准的 Windows 控件，例如 SCROLLBAR 和 BUTTON 以及所有常用控件。 对于不支持此行为的控件，必须提供你自己的代码来正确地显示不活动的控件。

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>处理反射窗口消息

Windows 控件通常将特定窗口信息发送到其父窗口。 其中一些消息（如WM_COMMAND）提供用户操作的通知。 其他（如WM_CTLCOLOR）用于从父窗口获取信息。 ActiveX 控件与父窗口的通信通常采用其他方式完成。 将通过激发事件（发送事件通知）来传递通知，并通过访问容器的环境属性来获取有关控件容器的信息。 由于存在这些通信方法，因此 ActiveX 控件容器不应处理由控件发送的任何窗口信息。

若要阻止容器接收由子类化 Windows 控件发送的窗口消息，`COleControl` 将创建一个额外的窗口来充当控件的父级。 此额外窗口称为“反射器”，仅针对子类化 Windows 控件且与控件窗口具有相同大小和位置的 ActiveX 控件创建。 反射器窗口截获某些窗口消息并将其发送回控件。 控件（在其窗口过程中）可以通过对 ActiveX 控件采取适当操作（例如，激发事件）来处理这些反射的消息。 有关截获的窗口消息及其相应的反射消息的列表，请参阅[反射窗口消息文档。](../mfc/reflected-window-message-ids.md)

ActiveX 控件容器可以设计为自行执行消息反射，从而不必使用 `COleControl` 来创建反射器窗口，减少了子类化 Windows 控件的运行时开销。 `COleControl`通过检查值为**TRUE**的 MessageReflect 环境属性，检测容器是否支持此功能。

若要处理一个反射窗口消息，请在控件消息映射中添加一个条目，并实现处理程序函数。 由于反射的消息不是由 Windows 定义的标准消息集的一部分，因此类视图不支持添加此类消息处理程序。 然而，手动添加处理程序并不困难。

要添加反射窗口消息的消息处理程序，需要手动执行以下操作：

- 在控件类 .H 文件中，声明一个处理程序函数。 该函数应具有**LRESULT**的返回类型和两个参数，分别具有**WPARAM**和**LPARAM**类型。 例如：

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- 在控制类中。CPP 文件，向消息映射添加ON_MESSAGE条目。 此条目的参数应该是消息标识符和处理程序函数的名称。 例如：

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- 也在 。CPP 文件，`OnOcmCommand`实现成员函数来处理反射的消息。 *wParam*和*lParam*参数与原始窗口消息的参数相同。

有关如何处理反射消息的示例，请参阅 MFC ActiveX 控件示例[BUTTON](../overview/visual-cpp-samples.md)。 它演示了`OnOcmCommand`一个处理程序，该处理程序检测BN_CLICKED通知代码并通过触发（发送）`Click`事件进行响应。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)
