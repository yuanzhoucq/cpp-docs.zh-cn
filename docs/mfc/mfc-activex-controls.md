---
title: "MFC ActiveX 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MFC ActiveX Controls (MFC)"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], MFC"
  - "COleControl 类, MFC ActiveX 控件"
  - "容器 [C++], MFC ActiveX 控件"
  - "调度映射, 用于 MFC ActiveX 控件"
  - "事件 [C++], ActiveX 控件"
  - "MFC ActiveX 控件 [C++]"
  - "MFC ActiveX 控件 [C++], 活动/非活动状态"
  - "MFC ActiveX 控件 [C++], 容器"
  - "MFC ActiveX 控件 [C++], 序列化"
  - "序列化 [C++], MFC ActiveX 控件"
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控件是基于组件对象模型 \(COM\) 的可重用软件组件，它支持广泛的 OLE 功能并可自定义以满足多种软件的需要。  ActiveX 控件旨在用于普通的 ActiveX 控件容器和 Internet 上的万维网页。  你可以使用MFC直接描述或是使用 [Active模块类 \(ATL\)](../atl/active-template-library-atl-concepts.md) 创建ActiveX控件。  
  
 ActiveX 控件可以在其自己的窗口的绘制，响应事件 \(例如鼠标单击\) 并通过包含类似于自动化对象属性和方法的接口管理。  
  
 这些控件开发用于许多使用，例如数据库访问，数据监视或关系图。  除了可移植性外，ActiveX 控件之前支持的功能对于 ActiveX 控件不可用，如使用现有的 OLE 容器的兼容性和能够整合其与 OLE 容器菜单的菜单。  此外，ActiveX 控件完全支持自动化，允许控件显示读取\\编写属性和 set 方法可以通过控件用户调用。  
  
 可以创建无窗口的 ActiveX 控件和仅当被激活时才创建窗口的控件。  无窗口控件加快应用程序显示并可以具有透明和非矩形控件。  您也可以异步加载 ActiveX 控件的属性。  
  
 ActiveX 控件实现为可以用于任何 OLE 容器的进程内服务器 \(通常是小对象\)。  请注意 ActiveX 控件的全部功能可用，只有当使用中设计的一个 OLE 容器中了解 ActiveX 控件。  请参阅 [端口 ActiveX 控件](../mfc/containers-for-activex-controls.md) 为支持ActiveX控件的容器的列表。  此容器类型，此后称为“控件容器，通过使用控件的属性和方法，并用事件的形式接收来自 ActiveX 控件的通知，可以运行 ActiveX 控件。  下面的图形演示此交互。  
  
 ![ActiveX 控件容器与控件之间的相互作用](../mfc/media/vc37221.png "vc37221")  
ActiveX 控件容器与有窗口的 ActiveX 控件之间的交互  
  
 有关优化的ActiveX控件的一些最新信息，请参阅[MFC ActiveX Controls: Optimization](../mfc/mfc-activex-controls-optimization.md)。  
  
 想创建一个 MFC ActiveX 控件，请参阅 [新建 ActiveX 控件项目](../mfc/reference/mfc-activex-control-wizard.md)。  
  
 有关详细信息，请参阅：  
  
-   [ActiveX 控件容器](../mfc/activex-control-containers.md)  
  
-   [活动文档](../mfc/active-documents.md)  
  
-   [使用 ActiveX 控件](../data/ado-rdo/using-activex-controls.md)  
  
-   [\<caps:sentence id\="tgt23" sentenceid\="e07c7a1ebdac21120a91f75018670c81" class\="tgtSentence"\>了解 ActiveX 控件\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms693753)  
  
-   [升级在 Internet 使用的现有的 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)  
  
##  <a name="_core_basic_components_of_an_activex_control"></a> ActiveX 控件的基本组件  
 ActiveX 控件使用多种编程元素有效地与控件容器和与用户进行交互。  这些类[COleControl](../mfc/reference/colecontrol-class.md), 一组事件触发功能，以及一个调度映射。  
  
 开发的每个ActiveX控件对象继承了来自其MFC基类的一套强大的功能，`COleControl`。  这些功能包括就地激活和自动化逻辑。  `COleControl` 可以提供具有与MFC窗口对象相同功能的控制对象，再加上触发事件的能力。  `COleControl` 可以提供 [windowless controls](../mfc/providing-windowless-activation.md), 它依靠自己的容器用于帮助窗口提供一些功能（鼠标捕获，键盘焦点，滚动），但提供更快的显示。  
  
 因为控件类从`COleControl`派生，它继承了其功能，当满足一定的条件时，发送或是“射发”消息，称为事件，到控制容器。  当在控件发生一些重要事情时，这些事件用于通知控件容器。  可以通过将参数传递给事件发送有关事件的其他信息给控件容器。  有关 ActiveX 控件事件的更多信息，请参阅文章 [MFC ActiveX 控件：事件](../mfc/mfc-activex-controls-events.md)。  
  
 最后一个元素为调度映射，用于在用户控件显示函数集 \(调用方法\) 和属性 \(称为特性\) 。  属性允许控件容器或控件用户以多种方式操作控件。  用户可以更改控件的外观，改变控件的某些值或发出控件请求，如访问控件维护的数据特定部分。  该接口是由控件开发人员确定和使用  “类视图”定义。  有关 ActiveX 控件方法和属性的详细信息，请参阅文章 [MFC ActiveX 控件: 方法](../mfc/mfc-activex-controls-methods.md) 和 [属性](../mfc/mfc-activex-controls-properties.md)。  
  
##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> 控件与窗口和 ActiveX 控件容器之间的交互  
 当控件在控件容器中使用时，它使用两中机制通信：它显示属性和方法，并且激发事件。  下图演示了这两种机制如何实现。  
  
 ![ActiveX 控件与其容器通信](../Image/vc37222.gif "vc37222")  
ActiveX 控件容器与 ActiveX 控件之间的通信  
  
 上图还阐释其他 OLE 接口 \(除了自动和事件外\) 如何通过控件处理。  
  
 所有控件与容器的通信都是通过 `COleControl`进行的。  为了处理一些容器请求，**COleControl**  将调用在控制类中实现的成员函数。  所有方法和一些属性是这样处理的。  您的控件类也可以通过调用`COleControl`的成员函数初始化与容器通信。  事件以此方式触发。  
  
##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> ActiveX 控件的活动和非活动状态。  
 控件有两种基本状态：活动和非活动。  传统上，这些状态通过控件是否具有窗口来区分。  一个活动控件具有一个窗口；非活动控件没有。  通过引入无窗口激活，这种区别不再通用，但仍适用于许多控件。  
  
 当[无窗口控件](../mfc/providing-windowless-activation.md) 激活时，它调用鼠标捕获，键盘焦点，滚动，和从它的容器的其他窗口服务。  你也可以 [提供鼠标交互来控制不活跃控件](../mfc/providing-mouse-interaction-while-inactive.md)，以及创建控件 [等到激活创建一个窗口](../mfc/turning-off-the-activate-when-visible-option.md)。  
  
 在具有窗口的控件变为活动状态时，可以使用控件容器、用户和窗口完全交互。  下面的图演示 Activex 控件、控件容器和操作系统之间的通信路径。  
  
 ![有窗口的活动 ActiveX 控件中的消息处理](../mfc/media/vc37223.png "vc37223")  
有窗口的 ActiveX 控件中的 Windows 消息处理（活动时）  
  
##  <a name="_core_serializing_activex_elements"></a> 序列化  
 能够序列化数据，有时称为持久性，提供控件将其属性的值写入并永久存储。  控件通过读取存储的对象状态然后再次创建。  
  
 请注意控件为获取对存储媒介的访问是不负责的。  相反，控件的容器对提供控件在适当的时间以存储媒介使用是负责的。  有关序列化的详细信息，请参阅文章 [MFC ActiveX 控件：序列化](../mfc/mfc-activex-controls-serializing.md)。  有关优化序列化的详细信息，请参阅ActiveX 控件：优化中的 [优化的持久性和初始化](../mfc/optimizing-persistence-and-initialization.md)  
  
##  <a name="_core_installing_activex_control_classes_and_tools"></a> 安装 ActiveX 控件类和工具  
 当安装 Visual C\+\+ 时，MFC ActiveX 控件类和发布、调试 ActiveX 控件运行时 DLL 会自动安装，如果ActiveX控件在设置中选择（它们被默认选中）。  
  
 默认情况下，ActiveX 控件类和工具在下面的子目录中安装在\\program files\\Microsoft Visual Studio .NET:  
  
-   **\\Common7\\tools**  
  
     包含测试容器文件 \(TstCon32.exe，以及帮助文件\)。  
  
-   **\\Vc7\\atlmfc\\include**  
  
     包含了包括用MFC 开发 ActiveX控件所需的文件  
  
-   **\\Vc7\\atlmfc\\src\\mfc**  
  
     在 MFC 包含特定 ActiveX 控件类的源代码  
  
-   **\\Vc7\\atlmfc\\lib**  
  
     包含了用 MFC 开发 ActiveX 控件所要求的库  
  
 还具有 MFC ActiveX 控件的示例。  有关这些示例的详细信息，请参阅 [控件示例: 基于MFC的ActiveX控件](../top/visual-cpp-samples.md)  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)