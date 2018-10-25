---
title: MFC ActiveX 控件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC ActiveX Controls (MFC)
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33c79dc8c83f40d0b553a2c44cf22fa107f5ef34
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065585"
---
# <a name="mfc-activex-controls"></a>MFC ActiveX 控件

ActiveX 控件是基于组件对象模型 (COM) 的可重用软件组件，支持各种 OLE 功能，并且可以进行自定义来满足多种软件所需。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关详细信息，请参阅[ActiveX 控件](activex-controls.md)。

ActiveX 控件专供在普通的 ActiveX 控件容器和 World Wide Web 页面中在 Internet 上。 您可以创建 ActiveX 控件使用 MFC，在这里，或使用描述[活动模板库 (ATL)](../atl/active-template-library-atl-concepts.md)。

ActiveX 控件可以自我绘制在其自己的窗口中，响应事件 （如鼠标单击），并通过包括属性和方法中的自动化对象类似的界面进行管理。

这些控件可开发出许多用途，如数据库访问、 监视或绘图的数据。 除了其可移植性，ActiveX 控件支持功能以前不可用的 ActiveX 控件，例如与现有的 OLE 容器的兼容性以及为其菜单与 OLE 容器菜单的功能。 此外，ActiveX 控件完全支持自动化，它允许控件公开读/写属性和一组控件，用户可以调用的方法。

您可以创建仅当它们变为活动状态时创建窗口的控件以及无窗口 ActiveX 控件。 无窗口控件的应用程序的显示的速度，并使其可以有透明和非矩形控件。 此外可以以异步方式加载 ActiveX 控件属性。

ActiveX 控件被实现为进程内服务器 （通常是一个小的对象），可在任何 OLE 容器中。 请注意，ActiveX 控件的完整功能仅在设计需要注意的 ActiveX 控件的 OLE 容器内使用时才可用。 请参阅[端口为其他应用程序的 ActiveX 控件](../mfc/containers-for-activex-controls.md)支持 ActiveX 控件的容器的列表。 这种容器类型，以下称为"控件容器"，可以使用控件的属性和方法，运行 ActiveX 控件，并接收来自事件的形式中的 ActiveX 控件的通知。 下图演示了这种交互。

![ActiveX 控件容器与控件的交互作用](../mfc/media/vc37221.gif "vc37221")之间 ActiveX 控件容器的交互与有窗口的 ActiveX 控件

某些优化 ActiveX 控件的最新信息，请参阅[MFC ActiveX 控件： 优化](../mfc/mfc-activex-controls-optimization.md)。

若要创建 MFC ActiveX 控件，请参阅[创建 ActiveX 控件项目](../mfc/reference/mfc-activex-control-wizard.md)。

有关详细信息，请参见:

- [ActiveX 控件容器](../mfc/activex-control-containers.md)

- [活动文档](../mfc/active-documents.md)

- [了解 ActiveX 控件](/windows/desktop/com/activex-controls)

- [升级现有 ActiveX 控件在 Internet 上使用](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a> ActiveX 控件的基本组件

ActiveX 控件使用多个编程元素与控件容器和用户高效地交互。 这些是类[COleControl](../mfc/reference/colecontrol-class.md)，一个组的事件触发函数的和调度映射。

您开发的每个 ActiveX 控件对象从其 MFC 基类继承一组强大的功能`COleControl`。 这些功能包括就地激活，以及自动化逻辑。 `COleControl` 可以向控件对象提供与 MFC 窗口对象，并且能够激发事件相同的功能。 `COleControl` 此外可以提供[无窗口控件](../mfc/providing-windowless-activation.md)，这依赖于其容器有关的某些功能的帮助窗口提供 (鼠标捕获、 键盘焦点时，滚动)，但提供要快得多的显示。

由于控件类派生`COleControl`，它将继承的功能，若要发送，或"fire，"消息，名为事件，向控件容器满足某些条件时。 这些事件用于通知控件容器一些重要的活动时，会在控件中发生情况。 通过将参数附加到该事件，可以将有关事件的其他信息发送到控件容器。 有关 ActiveX 控件事件的详细信息，请参阅文章[MFC ActiveX 控件： 事件](../mfc/mfc-activex-controls-events.md)。

最后一个元素是调度映射，用于公开一组函数 （称为方法） 和控制用户属性 （称为属性）。 属性允许控制容器或控制用户用来处理各种方法中的控件。 用户可以更改控件的外观、 更改该控件的某些值或发出请求的控件，例如访问一个特定的控件保持的数据。 此接口由控件开发人员，并且使用定义**类视图**。 ActiveX 控件方法和属性的详细信息，请参阅文章[MFC ActiveX 控件： 方法](../mfc/mfc-activex-controls-methods.md)并[属性](../mfc/mfc-activex-controls-properties.md)。

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> 使用 Windows 控件和 ActiveX 控件容器之间的交互

当控件容器中使用控件时，它使用两种机制来进行通信： 它公开属性和方法，并激发的事件。 下图演示了如何实现这两种机制。

![ActiveX 控件与其容器通信](../mfc/media/vc37222.gif "vc37222")之间 ActiveX 控件容器的通信和 ActiveX 控件

上图还说明了如何由控件处理其他 OLE 接口 （除了自动化和事件）。

执行所有与此容器的控件的通信是`COleControl`。 若要处理某些容器的请求，`COleControl`将调用成员函数在控件类中实现。 以这种方式处理所有方法和某些属性。 控件的类还可通过调用成员函数的启动与容器通信`COleControl`。 以这种方式触发事件。

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> 活动和非活动状态的 ActiveX 控件

控件有两种基本状态： 活动和非活动。 传统上，控件是否有一个窗口来区分这些状态。 活动控件有窗口;不支持的非活动状态的控件。 无窗口激活的引入，这一区别不再是通用的但仍适用于许多控件。

当[无窗口控件](../mfc/providing-windowless-activation.md)变为活动状态，它将调用鼠标捕获、 键盘焦点、 滚动和其他窗口服务从其容器。 此外可以[提供对非活动状态的控件的鼠标交互](../mfc/providing-mouse-interaction-while-inactive.md)，以及创建控件[等待，直到激活创建窗口](../mfc/turning-off-the-activate-when-visible-option.md)。

当与窗口控件变为活动状态时，是能够完全与控件容器、 用户和 Windows 进行交互。 下图演示 ActiveX 控件，控件容器与操作系统之间的通信的路径。

![活动窗口的 ActiveX 控件中的消息处理](../mfc/media/vc37223.gif "vc37223") （时活动） 有窗口 ActiveX 控件中的 Windows 消息处理

##  <a name="_core_serializing_activex_elements"></a> 序列化

序列化数据，有时称为持久性的能力使控件可以将其属性的值写入到持久存储。 从存储读取对象的状态可以重新创建的控件。

请注意，控件不负责获取到存储介质的访问权限。 相反，控件的容器负责为控件提供存储介质中以使用在适当的时间。 序列化的详细信息，请参阅文章[MFC ActiveX 控件： 序列化](../mfc/mfc-activex-controls-serializing.md)。 有关优化序列化的信息，请参阅[优化持久性和初始化](../mfc/optimizing-persistence-and-initialization.md)在 ActiveX 控件： 优化。

##  <a name="_core_installing_activex_control_classes_and_tools"></a> 安装 ActiveX 控件类和工具

在安装 Visual c + + 时，MFC ActiveX 控件类和零售和调试运行时 Dll 将自动安装，如果在安装程序 （它们通过默认选中） 中选择了 ActiveX 控件的 ActiveX 控件。

默认情况下下 \Program Files\Microsoft Visual Studio.NET 中的以下子目录中安装的 ActiveX 控件类和工具：

- **\Common7\Tools**

   包含测试容器文件 （TstCon32.exe，以及其帮助文件）。

- **\Vc7\atlmfc\include**

   包含用于开发 mfc ActiveX 控件包含文件

- **\Vc7\atlmfc\src\mfc**

   包含在 MFC 中的特定 ActiveX 控件类的源代码

- **\Vc7\atlmfc\lib**

   包含开发与 MFC 的 ActiveX 控件所需的库

也有适用于 MFC ActiveX 控件示例。 有关这些示例的详细信息，请参阅[控件示例： MFC-Based ActiveX 控件](../visual-cpp-samples.md)

## <a name="see-also"></a>请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)
