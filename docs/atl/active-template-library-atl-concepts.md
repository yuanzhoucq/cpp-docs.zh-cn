---
title: 活动模板库 (ATL) 概念 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5636f92df42116b838c24c21d81f0b320f7d69c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358109"
---
# <a name="active-template-library-atl-concepts"></a>活动模板库 (ATL) 概念
活动模板库 (ATL) 是一组基于模板的 c + + 类，可用于创建小型、 快速组件对象模型 (COM) 对象。 它提供了有关密钥的 COM 功能，包括股票实现、 双重接口、 标准 COM 枚举器接口、 连接点、 分离式接口和 ActiveX 控件的特殊支持。  
  
 如果执行大量 ATL 编程，你需要更多地了解属性，用于简化 COM 编程的 Visual c + +.NET 中的新功能。 有关详细信息，请参阅[特性化编程](../windows/attributed-programming-concepts.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [ATL 教程](../atl/active-template-library-atl-tutorial.md)  
 将引导你完成创建控件并演示了在过程中的一些 ATL 基础知识。  
  
 [COM 和 ATL 介绍](../atl/introduction-to-com-and-atl.md)  
 介绍主要概念后面组件对象模型 (COM)。 此文章还简要介绍了 ATL 的是，当您应使用它。  
  
 [ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)  
 讨论各种 ATL 类和如何实现这些类之间的关系。  
  
 [双重接口和 ATL](../atl/dual-interfaces-and-atl.md)  
 描述从 ATL 的角度的双重接口。  
  
 [ATL 集合和枚举数](../atl/atl-collections-and-enumerators.md)  
 描述实现和创建集合和枚举数在 atl。  
  
 [复合控件基础知识](../atl/atl-composite-control-fundamentals.md)  
 提供有关创建复合控件的分步说明。 复合控件是一种可以包含其他 ActiveX 控件或 Windows 控件的 ActiveX 控件。  
  
 [ATL 控件包含常见问题解答](../atl/atl-control-containment-faq.md)  
 介绍与承载与 atl。 控件相关的基本问题  
  
 [ATL COM 属性页](../atl/atl-com-property-pages.md)  
 演示如何指定并实现 COM 属性页。  
  
 [ATL 支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)  
 提供有关创建 DHTML 控件的分步说明。  
  
 [ATL 连接点](../atl/atl-connection-points.md)  
 解释什么是连接点以及 ATL 如何实现它们。  
  
 [事件处理和 ATL](../atl/event-handling-and-atl.md)  
 描述需要采取以处理使用 ATL 的 COM 事件的步骤[IDispEventImpl](../atl/reference/idispeventimpl-class.md)和[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)类。  
  
 [ATL 和自由线程封送拆收器](../atl/atl-and-the-free-threaded-marshaler.md)  
 提供允许你的类以聚合自由线程封送处理程序 (FTM) 的 ATL 简单对象向导的选项的详细信息。  
  
 [指定项目的线程处理模型](../atl/specifying-the-threading-model-for-a-project-atl.md)  
 介绍可用于控制运行时性能与你的项目中的线程处理相关的宏。  
  
 [ATL Module 类](../atl/atl-module-classes.md)  
 ATL 7.0 讨论新的模块类。 Module 类实现的基本功能所需的 atl。  
  
 [ATL 服务](../atl/atl-services.md)  
 介绍一的系列事件发生在实现服务时。 此外讨论一些与开发服务相关的概念。  
  
 [ATL 窗口类](../atl/atl-window-classes.md)  
 描述如何创建、 超类和子类 windows 在 atl。 ATL 窗口类不是 COM 类。  
  
 [ATL 集合类](../atl/atl-collection-classes.md)  
 介绍如何使用数组和映射中 atl。  
  
 [ATL 注册表组件 （注册器）](../atl/atl-registry-component-registrar.md)  
 讨论 ATL 脚本语法和可替换参数。 它还说明了如何设置注册机构的静态链接。  
  
 [使用 ATL 和 C 运行时代码进行编程](../atl/programming-with-atl-and-c-run-time-code.md)  
 讨论将静态还是动态链接到 C 运行时库 (CRT) 的优势。  
  
 [使用 ccombstr 进行编程](../atl/programming-with-ccombstr-atl.md)  
 讨论几种情况下进行编程时需要小心`CComBSTR`。  
  
 [编码引用](../atl/atl-encoding-reference.md)  
 提供了函数和宏支持编码中的公共 Internet 标准，如进行 uuencode 十六进制、 范围和 UTF8 atlenc.h 中。  
  
 [实用程序引用](../atl/atl-utilities-reference.md)  
 提供有关操作的窗体中的路径和 Url 的代码[CPathT](../atl/reference/cpatht-class.md)和[CUrl](../atl/reference/curl-class.md)。 线程池， [CThreadPool](../atl/reference/cthreadpool-class.md)，可在自己的应用程序。 此代码可以 atlpath.h 和 atlutil.h 中找到。  
  
## <a name="related-sections"></a>相关章节  
 [ATL 示例](../visual-cpp-samples.md)  
 提供的说明和链接到 ATL 示例程序。  
  
 [创建 ATL 项目](../atl/reference/creating-an-atl-project.md)  
 包含 ATL 项目向导的信息。  
  
 [ATL 控件向导](../atl/reference/atl-control-wizard.md)  
 讨论如何添加类。  
  
 [特性化的编程](../windows/attributed-programming-concepts.md)  
 提供有关使用属性简化 COM 编程以及指向更详细主题的链接列表的概述。  
  
 [ATL 类概述](../atl/atl-class-overview.md)  
 提供参考信息以及指向 ATL 类。

