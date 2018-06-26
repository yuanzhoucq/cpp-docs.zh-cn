---
title: MFC ActiveX 控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 1209353f10e52b13202a91ae120057ba85dfa805
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930092"
---
# <a name="mfc-activex-controls"></a>MFC ActiveX 控件
ActiveX 控件是基于组件对象模型 (COM) 的可重用软件组件，支持各种 OLE 功能，并且可以进行自定义来满足多种软件所需。 ActiveX 控件被设计用于在普通的 ActiveX 控件容器和在 Internet 上，在全球通用 Web 页。 你可以创建 ActiveX 控件使用 MFC，所述在这里，或与[活动模板库 (ATL)](../atl/active-template-library-atl-concepts.md)。  
  
 ActiveX 控件可以对自身进行绘制在其自己的窗口中，响应事件 （如鼠标单击），并管理通过包括属性和方法类似于自动化对象的接口。  
  
 这些控件可以监视或绘图的数据开发的许多用途，例如数据库访问。 除了其可移植性，ActiveX 控件支持 ActiveX 控件，例如与现有 OLE 容器的兼容性以及与 OLE 容器菜单集成其菜单的功能以前未提供的功能。 此外，ActiveX 控件完全支持自动化，使控件可以公开读/写属性和一组控件，用户可以调用的方法。  
  
 你可以创建无窗口的 ActiveX 控件和它们变为活动状态时才创建窗口的控件。 无窗口控件加快你的应用程序的显示，并使其可以使透明和非矩形控件。 你也可以以异步方式加载 ActiveX 控件属性。  
  
 ActiveX 控件实现为可以在任何 OLE 容器中使用的进程内服务器 （通常是一个小的对象）。 请注意，ActiveX 控件的完整功能仅当在设计要注意的 ActiveX 控件的 OLE 容器内使用时才可用。 请参阅[到其他应用程序的端口 ActiveX 控件](../mfc/containers-for-activex-controls.md)有关支持 ActiveX 控件的容器的列表。 此容器类型，以后调用"控制容器"，可以通过使用控件的属性和方法，运行 ActiveX 控件，并从事件表单中的 ActiveX 控件接收通知。 下图演示了这种交互。  
  
 ![ActiveX 控件容器与控件交互作用](../mfc/media/vc37221.gif "vc37221")  
ActiveX 控件容器与有窗口的 ActiveX 控件之间的交互  
  
 有关优化你的 ActiveX 控件一些新信息，请参阅[MFC ActiveX 控件： 优化](../mfc/mfc-activex-controls-optimization.md)。  
  
 若要创建 MFC ActiveX 控件，请参阅[创建 ActiveX 控件项目](../mfc/reference/mfc-activex-control-wizard.md)。  
  
 有关详细信息，请参见:  
  
-   [ActiveX 控件容器](../mfc/activex-control-containers.md)  
  
-   [活动文档](../mfc/active-documents.md)  
  
-   [了解 ActiveX 控件](http://msdn.microsoft.com/library/windows/desktop/ms693753)  
  
-   [升级现有 ActiveX 控件在 Internet 上使用](../mfc/upgrading-an-existing-activex-control.md)  
  
##  <a name="_core_basic_components_of_an_activex_control"></a> ActiveX 控件的基本组件  
 ActiveX 控件使用几个编程元素的控件容器和用户有效地交互。 这些是类[COleControl](../mfc/reference/colecontrol-class.md)、 一组事件触发函数，以及一调度映射。  
  
 你开发的每个 ActiveX 控件对象继承一套强大的功能其 MFC 基类的类， `COleControl`。 这些功能包括在就地激活和自动化逻辑。 `COleControl` 可以将控件对象提供 MFC 窗口对象，并加上激发事件的功能相同的功能。 `COleControl` 此外可以提供[无窗口控件](../mfc/providing-windowless-activation.md)，其中依赖于其容器中的部分功能的帮助窗口提供 (鼠标捕获、 键盘焦点时，滚动)，但提供快得多的显示。  
  
 由于控件类派生自`COleControl`、 它继承的功能，若要发送，或"激发，"消息，调用事件，向控件容器满足某些条件时。 这些事件用于通知控件容器一些重要时，会发生情况控件中。 通过将参数附加到事件，可以将有关的事件的其他信息发送到控件容器。 有关 ActiveX 控件事件的详细信息，请参阅文章[MFC ActiveX 控件： 事件](../mfc/mfc-activex-controls-events.md)。  
  
 最后一个元素是调度映射，用于公开的函数 （称为方法） 和属性 （称为属性），到控制用户组。 属性允许控制容器或控制用户用来处理各种方法中的控件。 用户可以更改控件的外观、 更改的控件，某些值或发出请求的控件，如访问一个特定的控件保持的数据。 此接口由控件开发人员，使用定义**类视图**。 ActiveX 控件方法和属性的详细信息，请参阅文章[MFC ActiveX 控件： 方法](../mfc/mfc-activex-controls-methods.md)和[属性](../mfc/mfc-activex-controls-properties.md)。  
  
##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> 有窗口控件和 ActiveX 控件容器之间的交互  
 在控件容器内使用控件时，它使用两种机制来进行通信： 它公开属性和方法，并激发事件。 下图演示了如何实现这两种机制。  
  
 ![ActiveX 控件与其容器通信](../mfc/media/vc37222.gif "vc37222")  
ActiveX 控件容器与 ActiveX 控件之间的通信  
  
 上图还说明了如何由控件处理其他 OLE 接口 （除了自动化和事件）。  
  
 通过执行的所有与容器的控件的通信`COleControl`。 若要处理的容器的请求，某些`COleControl`将调用成员函数可在控件类中实现。 采用这种方式来处理所有方法，并且某些属性。 控件的类还可以通过调用的成员函数来启动与容器的通信`COleControl`。 在这种方式中触发事件。  
  
##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> 活动和非活动状态的 ActiveX 控件  
 控件有两种基本状态： 活动和非活动。 传统上，控件是否有一个窗口来区分这些状态。 活动控件有窗口;不支持非活动控件。 随着无窗口激活的推出，这一区别不再通用的但仍然适用于很多控件。  
  
 当[无窗口控件](../mfc/providing-windowless-activation.md)变为活动状态，它调用鼠标捕获、 键盘焦点、 滚动和从其容器其他窗口服务。 你还可以[提供到非活动控件的鼠标交互](../mfc/providing-mouse-interaction-while-inactive.md)，也可以创建控件[等待，直到激活创建窗口](../mfc/turning-off-the-activate-when-visible-option.md)。  
  
 当与窗口控件变为活动状态时，就能够与控件容器、 用户和 Windows 完全交互。 下图演示 ActiveX 控件，控件容器与操作系统之间的通信的路径。  
  
 ![活动窗口的 ActiveX 控件中的消息处理](../mfc/media/vc37223.gif "vc37223")  
有窗口的 ActiveX 控件中的 Windows 消息处理（活动时）  
  
##  <a name="_core_serializing_activex_elements"></a> 序列化  
 序列化数据，有时称为持久性的能力使控件可以将其属性的值写入到持久存储。 从存储中读取对象的状态可以重新创建的控件。  
  
 请注意，控件不负责获取访问权限的存储介质。 相反，控件的容器将负责为控件提供存储媒体，以便使用在合适的时间。 在序列化的详细信息，请参阅文章[MFC ActiveX 控件： 序列化](../mfc/mfc-activex-controls-serializing.md)。 有关优化序列化的信息，请参阅[优化持久性和初始化](../mfc/optimizing-persistence-and-initialization.md)在 ActiveX 控件： 优化。  
  
##  <a name="_core_installing_activex_control_classes_and_tools"></a> 安装 ActiveX 控件类和工具  
 在安装 Visual c + + 时，MFC ActiveX 控件类和零售和调试运行时 Dll 将自动安装，如果选择安装程序 （它们默认情况下选中） 中的 ActiveX 控件的 ActiveX 控件。  
  
 默认情况下 files\microsoft Visual Studio.NET 的以下子目录中安装的 ActiveX 控件类和工具：  
  
-   **\Common7\Tools**  
  
     包含测试容器文件 （TstCon32.exe，以及其帮助文件）。  
  
-   **\Vc7\atlmfc\include**  
  
     包含用它们来开发使用 MFC ActiveX 控件包含文件  
  
-   **\Vc7\atlmfc\src\mfc**  
  
     包含在 MFC 中的特定 ActiveX 控件类的源代码  
  
-   **\Vc7\atlmfc\lib**  
  
     包含开发使用 MFC ActiveX 控件所需的库  
  
 此外，还存在用于 MFC ActiveX 控件的示例。 有关这些示例的详细信息，请参阅[控件示例： MFC-Based ActiveX 控件](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)
