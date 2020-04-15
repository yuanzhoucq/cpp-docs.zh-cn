---
title: MFC ActiveX 控件
ms.date: 11/19/2018
f1_keywords:
- MFC ActiveX Controls (MFC)
helpviewer_keywords:
- COleControl class [MFC], MFC ActiveX controls
- ActiveX controls [MFC], MFC
- containers [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], serializing
- MFC ActiveX controls [MFC], containers
- serialization [MFC], MFC ActiveX controls
- dispatch maps [MFC], for MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- events [MFC], ActiveX controls
- MFC ActiveX controls [MFC]
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
ms.openlocfilehash: e9cc38eebed0b1f8e0932e89ef1452261aefd7dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365443"
---
# <a name="mfc-activex-controls"></a>MFC ActiveX 控件

ActiveX 控件是基于组件对象模型 (COM) 的可重用软件组件，支持各种 OLE 功能，并且可以进行自定义来满足多种软件所需。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关详细信息，请参阅[ActiveX 控件](activex-controls.md)。

ActiveX 控件设计用于普通 ActiveX 控制容器和 Internet、万维网页面。 您可以使用此处描述的 MFC 或[使用活动模板库 （ATL）](../atl/active-template-library-atl-concepts.md)创建 ActiveX 控件。

ActiveX 控件可以在自己的窗口中绘制自身，响应事件（如鼠标单击），并通过包含类似于自动化对象的属性和方法的接口进行管理。

这些控件可以开发用于多种用途，例如数据库访问、数据监视或图形绘制。 除了可移植性外，ActiveX 控制支持以前对 ActiveX 控件不可用的功能，例如与现有 OLE 容器的兼容性以及将其菜单与 OLE 容器菜单集成的能力。 此外，ActiveX 控件完全支持自动化，它允许控件公开读取\write 属性和一组控件用户可以调用的方法。

您可以创建无窗口的 ActiveX 控件和控件，这些控件和控件仅在窗口变为活动时创建窗口。 无窗口控件可加快应用程序的显示速度，并可以具有透明和非矩形控件。 您还可以异步加载 ActiveX 控件属性。

ActiveX 控件作为可在任何 OLE 容器中使用的进程内服务器（通常是小对象）实现。 请注意，ActiveX 控件的全部功能仅在旨在了解 ActiveX 控件的 OLE 容器中使用时才可用。 有关支持 ActiveX 控件的容器列表，请参阅[将 ActiveX 控件移植到其他应用程序](../mfc/containers-for-activex-controls.md)。 此容器类型（以下简称"控制容器"）可以使用控件的属性和方法操作 ActiveX 控件，并接收来自 ActiveX 控件的通知（事件形式）。 下图演示了此交互。

![ActiveX 控件容器与控件之间的相互作用](../mfc/media/vc37221.gif "ActiveX 控件容器与控件之间的相互作用") <br/>
ActiveX 控件容器与有窗口的 ActiveX 控件之间的交互

有关优化 ActiveX 控件的一些最新信息，请参阅[MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)。

要创建 MFC ActiveX 控件，请参阅[创建 ActiveX 控件项目](../mfc/reference/mfc-activex-control-wizard.md)。

有关详细信息，请参阅：

- [ActiveX 控制容器](../mfc/activex-control-containers.md)

- [活动文档](../mfc/active-documents.md)

- [了解 ActiveX 控件](/windows/win32/com/activex-controls)

- [升级要在 Internet 上使用的现有 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)

## <a name="basic-components-of-an-activex-control"></a><a name="_core_basic_components_of_an_activex_control"></a>ActiveX 控件的基本组件

ActiveX 控件使用多个编程元素与控件容器和用户进行有效交互。 这些是[COleControl](../mfc/reference/colecontrol-class.md)类、一组事件触发函数和调度映射。

您开发的每个 ActiveX 控件对象都继承其 MFC 基类中`COleControl`一组强大的功能。 这些功能包括就地激活和自动化逻辑。 `COleControl`可以为控件对象提供与 MFC 窗口对象相同的功能，以及触发事件的能力。 `COleControl`也可以提供[无窗口控件](../mfc/providing-windowless-activation.md)，这些控件依赖于其容器来帮助窗口提供的一些功能（鼠标捕获、键盘焦点、滚动），但显示速度要快得多。

由于控件类派生自`COleControl`，因此它继承了在满足某些条件时向控件容器发送或"fire"消息（称为事件）的功能。 当控件中发生重要情况时，这些事件用于通知控件容器。 通过将参数附加到事件，可以将有关事件的其他信息发送到控件容器。 有关 ActiveX 控制事件的详细信息，请参阅文章[MFC ActiveX 控件：事件](../mfc/mfc-activex-controls-events.md)。

最后一个元素是调度映射，用于向控件用户公开一组函数（称为方法）和属性（称为属性）。 属性允许控件容器或控件用户以各种方式操作控件。 用户可以更改控件的外观、更改控件的某些值或发出控件的请求，例如访问控件维护的特定数据段。 此接口由控件开发人员确定，并使用**类视图**定义。 有关 ActiveX 控件方法和属性的详细信息，请参阅文章[MFC ActiveX 控件：方法和](../mfc/mfc-activex-controls-methods.md)[属性](../mfc/mfc-activex-controls-properties.md)。

## <a name="interaction-between-controls-with-windows-and-activex-control-containers"></a><a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>控件与 Windows 和 ActiveX 控制容器之间的交互

当在控件容器中使用控件时，它使用两种机制进行通信：它公开属性和方法，并触发事件。 下图演示了如何实现这两个机制。

![ActiveX 控件与其容器通信](../mfc/media/vc37222.gif "ActiveX 控件与其容器通信") <br/>
ActiveX 控件容器与 ActiveX 控件之间的通信

上图还说明了控件如何处理其他 OLE 接口（除了自动化和事件）。

控件与容器的所有通信都由 执行`COleControl`。 要处理容器的某些请求，`COleControl`将调用在控件类中实现的成员函数。 所有方法和某些属性都以这种方式处理。 控件的类还可以通过调用 的成员函数启动与容器的通信`COleControl`。 事件以这种方式触发。

## <a name="active-and-inactive-states-of-an-activex-control"></a><a name="_core_active_and_inactive_states_of_an_activex_control"></a>活动X控件的活跃和非活动状态

控件有两个基本状态：活动状态和非活动状态。 传统上，这些状态以控件是否具有窗口来区分。 活动控件有一个窗口;非活动控件没有。 引入无窗口激活后，这种区别不再普遍，但仍适用于许多控件。

当[无窗口控件](../mfc/providing-windowless-activation.md)处于活动状态时，它将从容器调用鼠标捕获、键盘焦点、滚动和其他窗口服务。 您还可以[为非活动控件提供鼠标交互](../mfc/providing-mouse-interaction-while-inactive.md)，以及创建[等待激活以创建窗口的](../mfc/turning-off-the-activate-when-visible-option.md)控件。

当具有窗口的控件变为活动时，它能够与控件容器、用户和 Windows 完全交互。 下图演示了 ActiveX 控件、控制容器和操作系统之间的通信路径。

![有窗口的活动 ActiveX 控件中的消息处理](../mfc/media/vc37223.gif "有窗口的活动 ActiveX 控件中的消息处理") <br/>
有窗口的 ActiveX 控件中的 Windows 消息处理（活动时）

## <a name="serialization"></a><a name="_core_serializing_activex_elements"></a>序列 化

序列化数据（有时称为持久性）的能力允许控件将其属性的值写入持久存储。 然后，可以通过从存储中读取对象的状态来重新创建控件。

请注意，控件不负责获取对存储介质的访问。 相反，控件的容器负责为控件提供在适当时间使用的存储介质。 有关序列化的详细信息，请参阅文章[MFC ActiveX 控件：序列化](../mfc/mfc-activex-controls-serializing.md)。 有关优化序列化的信息，请参阅 ActiveX 控件[中的优化持久性和初始化](../mfc/optimizing-persistence-and-initialization.md)：优化。

## <a name="installing-activex-control-classes-and-tools"></a><a name="_core_installing_activex_control_classes_and_tools"></a>安装 ActiveX 控制类和工具

安装 Visual C++ 时，如果在安装程序中选择 ActiveX 控件（默认情况下选择它们），则会自动安装 MFC ActiveX 控件类以及零售和调试 ActiveX 控件运行时 DLL。

默认情况下，ActiveX 控件类和工具安装在 [程序文件]Microsoft Visual Studio .NET 下的以下子目录中：

- **[公共7]工具**

   包含测试容器文件（TstCon32.exe 及其帮助文件）。

- **[Vc7]atlmfc_包括**

   包含使用 MFC 开发 ActiveX 控件所需的包含文件

- **[Vc7]atlmfc\src\mfc**

   包含 MFC 中特定 ActiveX 控制类的源代码

- **[Vc7]atlmfc_lib**

   包含使用 MFC 开发 ActiveX 控件所需的库

还有 MFC ActiveX 控件的示例。 有关这些示例的详细信息，请参阅[控件示例：基于 MFC 的 ActiveX 控件](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>另请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)
