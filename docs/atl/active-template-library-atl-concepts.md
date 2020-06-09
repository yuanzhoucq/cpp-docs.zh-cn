---
title: 活动模板库 (ATL) 概念
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: cc96b5ed931713ca64a0582ca1cc18a8526ea8af
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616685"
---
# <a name="active-template-library-atl-concepts"></a>活动模板库 (ATL) 概念

活动模板库 (ATL) 是一组基于模板的 C++ 类，可用于创建小型、便捷的组件对象模型 (COM) 对象。 它对关键 COM 功能提供特殊支持，包括常用实现、双重接口、标准 COM 枚举器接口、连接点、分离式接口和 ActiveX 控件。

如果进行大量 ATL 编程，你将希望了解关于 COM 和 .NET 属性的详细信息，这些属性可以简化 COM 编程。 有关详细信息，请参阅[属性化编程](../windows/attributed-programming-concepts.md)。 （请勿将 COM 和 .NET 属性与 C++ 标准版中的 \[\[attribute]] 功能混淆。）

## <a name="in-this-section"></a>本节内容

[COM 和 ATL 简介](introduction-to-com-and-atl.md)<br/>
介绍组件对象模型 (COM) 背后的主要概念。 本文还简要介绍了 ATL 是什么以及何时应该使用它。

[ATL COM 对象的基本知识](fundamentals-of-atl-com-objects.md)<br/>
讨论各种 ATL 类之间的关系以及这些类的实现方式。

[双重接口和 ATL](dual-interfaces-and-atl.md)<br/>
从 ATL 角度介绍双重接口。

[ATL 集合和枚举数](atl-collections-and-enumerators.md)<br/>
介绍 ATL 中集合和枚举器的实现与创建。

[复合控件基础知识](atl-composite-control-fundamentals.md)<br/>
提供创建复合控件的分步说明。 复合控件是一种 ActiveX 控件，可以包含其他 ActiveX 控件或 Windows 控件。

[ATL 控件包含常见问题](atl-control-containment-faq.md)<br/>
涵盖与 ATL 承载控件相关的基本问题。

[ATL COM 属性页](atl-com-property-pages.md)<br/>
演示如何指定和实现 COM 属性页。

[ATL 支持 DHTML 控件](atl-support-for-dhtml-controls.md)<br/>
提供创建 DHTML 控件的分步说明。

[ATL 连接点](atl-connection-points.md)<br/>
介绍什么是连接点以及 ATL 如何实现它们。

[事件处理和 ATL](event-handling-and-atl.md)<br/>
介绍使用 ATL 的 [IDispEventImpl](reference/idispeventimpl-class.md) 和 [IDispEventSimpleImpl](reference/idispeventsimpleimpl-class.md) 类处理 COM 事件所需执行的步骤。

[ATL 和自由线程封送拆收器](atl-and-the-free-threaded-marshaler.md)<br/>
提供关于 ATL 简单对象向导的允许类聚合自由线程封送拆收器 (FTM) 的选项的详细信息。

[指定项目的线程模型](specifying-the-threading-model-for-a-project-atl.md)<br/>
介绍可用于控制与项目中的线程相关的运行时性能的宏。

[ATL Module 类](atl-module-classes.md)<br/>
讨论 ATL 7.0 的全新模块类。 模块类实现 ATL 要求的基本功能。

[ATL 服务](atl-services.md)<br/>
介绍实现服务时发生的事件的序列。 此外，还讨论一些与开发服务相关的概念。

[ATL 窗口类](atl-window-classes.md)<br/>
介绍如何在 ATL 中创建窗口并对窗口进行超分类和子分类。 ATL 窗口类不是 COM 类。

[ATL 集合类](atl-collection-classes.md)<br/>
介绍如何在 ATL 中使用数组和映射。

[ATL 注册表组件（注册器）](atl-registry-component-registrar.md)<br/>
讨论 ATL 脚本语法和可替换参数。 它还介绍了如何设置指向注册机构的静态链接。

[使用 ATL 和 C 运行时代码进行编程](programming-with-atl-and-c-run-time-code.md)<br/>
讨论静态或动态链接到 C 运行时库 (CRT) 的优势。

[使用 CComBSTR 进行编程](programming-with-ccombstr-atl.md)<br/>
讨论使用 `CComBSTR` 进行编程时需要注意的几种情况。

[编码引用](atl-encoding-reference.md)<br/>
提供支持在 atlenc.h 中以一系列常见 Internet 标准（如 uuencode、十六进制和 UTF8）进行编码的函数和宏。

[实用程序引用](atl-utilities-reference.md)<br/>
提供以 [CPathT](reference/cpatht-class.md) 和 [CUrl](reference/curl-class.md) 格式处理路径和 URL 的代码。 线程池 [CThreadPool](reference/cthreadpool-class.md) 可在自己的应用程序中使用。 可在 atlpath.h 和 atlutil.h 中找到此代码。

## <a name="related-sections"></a>相关章节

[ATL 教程](active-template-library-atl-tutorial.md)<br/>
可指导你完成控件的创建并在此过程中展示一些 ATL 基础知识。

[ATL 示例](../overview/visual-cpp-samples.md)<br/>
提供 ATL 示例程序的说明和相关链接。

[创建 ATL 项目](reference/creating-an-atl-project.md)<br/>
包含关于 ATL 项目向导的信息。

[ATL 控件向导](reference/atl-control-wizard.md)<br/>
讨论如何添加类。

[属性化编程](../windows/attributed-programming-concepts.md)<br/>
提供关于使用属性简化 COM 编程的概述，以及指向更详细主题的链接列表。

[ATL 类概述](atl-class-overview.md)<br/>
提供 ATL 类的参考信息和相关链接。
