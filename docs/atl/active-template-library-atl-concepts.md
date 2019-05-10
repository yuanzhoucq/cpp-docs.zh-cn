---
title: 活动模板库 (ATL) 概念
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: 785b929e935962f6461ffbc3722f573a61cb8749
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221297"
---
# <a name="active-template-library-atl-concepts"></a>活动模板库 (ATL) 概念

活动模板库 (ATL) 是一套基于模板的C++类，可快速创建小型，组件对象模型 (COM) 对象。 它具有对密钥的 COM 功能，包括常用实现、 双重接口、 标准 COM 枚举器接口，连接点、 分离式接口和 ActiveX 控件的特殊支持。

如果做了大量 ATL 编程时，将想要详细了解 COM 和.NET 属性，用于简化 COM 编程。 有关详细信息，请参阅[特性化编程](../windows/attributed-programming-concepts.md)。 (COM 和.NET 属性将不会与混淆\[\[属性]] 中的功能C++标准。)

## <a name="in-this-section"></a>本节内容

[ATL 教程](../atl/active-template-library-atl-tutorial.md)<br/>
将引导你完成创建控件，并演示过程中的某些 ATL 基础知识。

[COM 和 ATL 介绍](../atl/introduction-to-com-and-atl.md)<br/>
介绍主要概念背后组件对象模型 (COM)。 本文还简要介绍什么是 ATL 以及何时应使用它。

[ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)<br/>
讨论各种 ATL 类和如何实现这些类之间的关系。

[双重接口和 ATL](../atl/dual-interfaces-and-atl.md)<br/>
介绍了双重接口从 ATL 的角度。

[ATL 集合和枚举数](../atl/atl-collections-and-enumerators.md)<br/>
介绍了实现和创建集合和枚举器在 atl。

[复合控件基础知识](../atl/atl-composite-control-fundamentals.md)<br/>
提供用于创建复合控件的分步说明。 复合控件是一种可以包含其他 ActiveX 控件或 Windows 控件的 ActiveX 控件。

[ATL 控件包含常见问题解答](../atl/atl-control-containment-faq.md)<br/>
介绍了与托管 atl。 与控件相关的基本问题。

[ATL COM 属性页](../atl/atl-com-property-pages.md)<br/>
演示如何指定和实现 COM 属性页。

[ATL 支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)<br/>
提供用于创建 DHTML 控件的分步说明。

[ATL 连接点](../atl/atl-connection-points.md)<br/>
介绍连接点是什么以及如何 ATL 实现它们。

[事件处理和 ATL](../atl/event-handling-and-atl.md)<br/>
介绍需要执行来处理使用 ATL 的 COM 事件的步骤[IDispEventImpl](../atl/reference/idispeventimpl-class.md)并[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)类。

[ATL 和自由线程封送拆收器](../atl/atl-and-the-free-threaded-marshaler.md)<br/>
提供允许您的类聚合自由线程封送处理程序 (FTM) 的 ATL 简单对象向导的选项的详细信息。

[指定项目的线程模型](../atl/specifying-the-threading-model-for-a-project-atl.md)<br/>
介绍可用于控制运行时性能与您的项目中的线程处理相关的宏。

[ATL Module 类](../atl/atl-module-classes.md)<br/>
ATL 7.0 讨论新的模块类。 Module 类实现的基本功能所需的 atl。

[ATL 服务](../atl/atl-services.md)<br/>
介绍如何实现服务时所发生事件的序列。 此外讨论一些与开发服务相关的概念。

[ATL 窗口类](../atl/atl-window-classes.md)<br/>
介绍如何创建、 超类，子类中和窗口 atl。 ATL 窗口类不是 COM 类。

[ATL 集合类](../atl/atl-collection-classes.md)<br/>
介绍如何使用数组和映射在 atl。

[ATL 注册表组件 （注册器）](../atl/atl-registry-component-registrar.md)<br/>
讨论 ATL 脚本语法和可替换参数。 它还介绍了如何设置到注册机构的静态链接。

[使用 ATL 和 C 运行时代码进行编程](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
讨论将静态或动态链接到 C 运行时库 (CRT) 的优势。

[使用 ccombstr 进行编程](../atl/programming-with-ccombstr-atl.md)<br/>
讨论当使用编程时，需要注意的几种情况下`CComBSTR`。

[编码引用](../atl/atl-encoding-reference.md)<br/>
提供函数和支持编码和中的一系列常见的 Internet 标准，如 uuencode，十六进制，UTF8 中保留的宏。

[实用程序引用](../atl/atl-utilities-reference.md)<br/>
提供有关操作的窗体中的路径和 Url 的代码[CPathT](../atl/reference/cpatht-class.md)并[CUrl](../atl/reference/curl-class.md)。 线程池[CThreadPool](../atl/reference/cthreadpool-class.md)，可以在自己的应用程序中使用。 可以在 atlpath.h 和 atlutil.h 中找到此代码。

## <a name="related-sections"></a>相关章节

[ATL 示例](../overview/visual-cpp-samples.md)<br/>
提供的说明以及指向 ATL 示例程序。

[创建 ATL 项目](../atl/reference/creating-an-atl-project.md)<br/>
包含 ATL 项目向导的信息。

[ATL 控件向导](../atl/reference/atl-control-wizard.md)<br/>
讨论如何添加类。

[特性化的编程](../windows/attributed-programming-concepts.md)<br/>
提供使用属性来简化 COM 编程加上的其他详细主题的链接列表上的概述。

[ATL 类概述](../atl/atl-class-overview.md)<br/>
提供的参考信息以及指向 ATL 类。
