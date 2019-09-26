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
ms.openlocfilehash: a1c7bb070a75f4406556817163931f0707706c40
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2019
ms.locfileid: "69508117"
---
# <a name="mfc-activex-controls"></a>MFC ActiveX 控件

ActiveX 控件是基于组件对象模型 (COM) 的可重用软件组件，支持各种 OLE 功能，并且可以进行自定义来满足多种软件所需。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关详细信息，请参阅[ActiveX 控件](activex-controls.md)。

ActiveX 控件设计为在普通 ActiveX 控件容器和 Internet 上的万维网上使用。 您可以用 MFC （在此处介绍）或[活动模板库（ATL）](../atl/active-template-library-atl-concepts.md)创建 ActiveX 控件。

ActiveX 控件可以在其自己的窗口中进行绘制，响应事件（例如鼠标单击），并通过包含类似于自动化对象中的属性和方法的界面进行管理。

这些控件可用于多种用途，例如数据库访问、数据监视或图形。 除可移植性外，ActiveX 控件还支持以前不适用于 ActiveX 控件的功能，如与现有 OLE 容器的兼容性，以及将其菜单与 OLE 容器菜单集成的功能。 此外，ActiveX 控件完全支持自动化，这允许控件公开读 \ 写属性以及可由控件用户调用的一组方法。

你可以创建无窗口 ActiveX 控件和控件，这些控件和控件在处于活动状态时仅创建窗口。 无窗口控件可以加快应用程序的显示速度，并使其具有透明和非矩形控件。 还可以异步加载 ActiveX 控件属性。

ActiveX 控件以进程内服务器（通常是小对象）的形式实现，可用于任何 OLE 容器。 请注意，ActiveX 控件的全部功能只有在旨在识别 ActiveX 控件的 OLE 容器中使用时才可用。 有关支持 ActiveX 控件的容器的列表，请参阅[将 Activex 控件移植到其他应用程序](../mfc/containers-for-activex-controls.md)。 此容器类型（以后称为 "控制容器"）可以通过使用控件的属性和方法来操作 ActiveX 控件，并以事件的形式从 ActiveX 控件接收通知。 下图演示了这种交互。

![ActiveX 控件容器和控件的相互作用](../mfc/media/vc37221.gif "ActiveX 控件容器和控件的相互作用") <br/>
ActiveX 控件容器与有窗口的 ActiveX 控件之间的交互

有关优化 ActiveX 控件的一些最新信息，请[参阅 MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)。

若要创建 MFC ActiveX 控件，请参阅[创建 ActiveX 控件项目](../mfc/reference/mfc-activex-control-wizard.md)。

有关详细信息，请参见:

- [ActiveX 控件容器](../mfc/activex-control-containers.md)

- [活动文档](../mfc/active-documents.md)

- [了解 ActiveX 控件](/windows/win32/com/activex-controls)

- [升级要在 Internet 上使用的现有 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a>ActiveX 控件的基本组件

ActiveX 控件使用几个编程元素与控件容器和用户有效地交互。 这些是类[COleControl](../mfc/reference/colecontrol-class.md)、一组事件触发函数和一个调度映射。

开发的每个 ActiveX 控件对象从其 MFC 基类`COleControl`继承一组功能强大的功能。 这些功能包括就地激活和自动化逻辑。 `COleControl`可以为控件对象提供与 MFC 窗口对象相同的功能，并提供激发事件的能力。 `COleControl`还可以提供[无窗口控件](../mfc/providing-windowless-activation.md)，这些控件依赖于其容器来帮助提供窗口提供的某些功能（鼠标捕获、键盘焦点、滚动），但提供的显示速度更快。

由于此控件类派生自`COleControl`，因此在满足某些条件时，它将继承向控件容器发送消息或 "激发" 消息（称为事件）的功能。 当控件中发生重要的问题时，这些事件用于通知控件容器。 可以通过将参数附加到事件来向控件容器发送有关事件的其他信息。 有关 ActiveX 控件事件的详细信息，请参阅[MFC ActiveX 控件：事件](../mfc/mfc-activex-controls-events.md)。

最后一个元素是一个调度映射，用于向控件用户公开一组函数（称为方法）和特性（称为 "属性"）。 属性允许控件容器或控制用户以各种方式操作控件。 用户可以更改控件的外观、更改控件的某些值或发出控件请求，如访问控件所维护的特定数据片段。 此接口由控件开发人员确定，并使用**类视图**定义。 有关 ActiveX 控件方法和属性的详细信息，请参阅文章[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)和[属性](../mfc/mfc-activex-controls-properties.md)。

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>具有 Windows 和 ActiveX 控件容器的控件之间的交互

控件容器中使用控件时，会使用两种机制进行通信：公开属性和方法，并激发事件。 下图演示了如何实现这两种机制。

![ActiveX 控件与其容器通信](../mfc/media/vc37222.gif "ActiveX 控件与其容器通信") <br/>
ActiveX 控件容器与 ActiveX 控件之间的通信

上图还说明了控件如何处理其他 OLE 接口（自动化和事件除外）。

控件与容器的所有通信都由`COleControl`执行。 若要处理容器的某些请求， `COleControl`将调用在控件类中实现的成员函数。 所有方法和某些属性都是以这种方式处理的。 控件的类还可以通过调用的`COleControl`成员函数来启动与容器的通信。 事件以这种方式激发。

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a>ActiveX 控件的活动和非活动状态

控件具有两种基本状态：活动和非活动。 传统上，这些状态是由控件是否有窗口来区分。 活动控件具有窗口;不活动的控件没有。 引入无窗口激活后，这种区别不再是通用的，但仍适用于许多控件。

[无窗口控件](../mfc/providing-windowless-activation.md)进入活动状态时，它将从其容器调用鼠标捕获、键盘焦点、滚动以及其他窗口服务。 你还可以向[非活动控件提供鼠标交互](../mfc/providing-mouse-interaction-while-inactive.md)，以及创建[等待到激活状态以创建窗口](../mfc/turning-off-the-activate-when-visible-option.md)的控件。

当具有窗口的控件变为活动状态时，它可以与控件容器、用户和窗口完全交互。 下图演示了 ActiveX 控件、控件容器和操作系统之间的通信路径。

![处于活动状态的 ActiveX 控件中的消息处理](../mfc/media/vc37223.gif "处于活动状态的 ActiveX 控件中的消息处理") <br/>
有窗口的 ActiveX 控件中的 Windows 消息处理（活动时）

##  <a name="_core_serializing_activex_elements"></a>化为

序列化数据的能力（有时称为持久性）允许控件将其属性的值写入持久性存储。 然后，可以通过从存储中读取对象的状态来重新创建控件。

请注意，控件不负责获取对存储媒体的访问权限。 相反，控件的容器负责为控件提供在适当时间使用的存储介质。 有关序列化的详细信息，请参阅[MFC ActiveX 控件：序列](../mfc/mfc-activex-controls-serializing.md)化。 有关优化序列化的信息，请参阅在 ActiveX 控件中[优化持久性和初始化](../mfc/optimizing-persistence-and-initialization.md)：搜索引擎优化.

##  <a name="_core_installing_activex_control_classes_and_tools"></a>安装 ActiveX 控件类和工具

安装视觉对象C++时，如果在安装程序中选择了 activex 控件，则将自动安装 MFC ActiveX 控件类和零售和调试 activex 控件运行时 dll （默认情况下处于选中状态）。

默认情况下，ActiveX 控件类和工具安装在 \Program Files\Microsoft Visual Studio .NET 下的以下子目录中：

- **\Common7\Tools**

   包含测试容器文件（TstCon32）以及其帮助文件。

- **\Vc7\atlmfc\include**

   包含用 MFC 开发 ActiveX 控件所需的包含文件

- **\Vc7\atlmfc\src\mfc**

   包含 MFC 中特定 ActiveX 控件类的源代码

- **\Vc7\atlmfc\lib**

   包含用 MFC 开发 ActiveX 控件所需的库

MFC ActiveX 控件也有一些示例。 有关这些示例的详细信息，请[参阅控件示例：基于 MFC 的 ActiveX 控件](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)
