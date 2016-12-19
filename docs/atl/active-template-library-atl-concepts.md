---
title: "活动模板库 (ATL) 概念 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 关于 ATL"
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
caps.latest.revision: 18
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 活动模板库 (ATL) 概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

活动模板库 \(ATL\) 是允许您创建小，快速组件对象模型\(COM\)对象的设置基于模板的C\+\+选件类。  它还提供对密钥COM函数特殊支持，包括常用实现，双绑定接口，标准COM枚举器接口，连接点，拖曳接口和ActiveX控件。  
  
 如果执行编程大量的ATL，您将希望详细了解属性，旨在简化COM编程在Visual C\+\+ .NET的新功能。  有关更多信息，请参见 [特性化编程](../windows/attributed-programming-concepts.md)。  
  
## 本节内容  
 [ATL教程](../atl/active-template-library-atl-tutorial.md)  
 带领您完成创建控件的过程，并在此过程中阐释一些 ATL 基础知识。  
  
 [COM和ATL简介](../atl/introduction-to-com-and-atl.md)  
 介绍组件对象模型\(COM\)后的主要概念。  本文简要还演示了当ATL为，并且，当您应使用它。  
  
 [ATL COM对象的基本知识](../atl/fundamentals-of-atl-com-objects.md)  
 讨论在各种ATL选件类之间的关系，这些选件类的实现方式。  
  
 [双重接口和ATL](../atl/dual-interfaces-and-atl.md)  
 描述双重接口从ATL方面。  
  
 [ATL 集合和枚举数](../atl/atl-collections-and-enumerators.md)  
 在ATL描述集合和枚举数的实现以及创建。  
  
 [复合控件的基本知识](../atl/atl-composite-control-fundamentals.md)  
 用于创建复合控件的分步说明。  复合控件是可以包含其他ActiveX控件或Windows控件ActiveX控件的类型。  
  
 [ATL控件包容常见问题](../atl/atl-control-containment-faq.md)  
 使用ATL报告根本问题与承载控件相关。  
  
 [ATL COM属性页](../atl/atl-com-property-pages.md)  
 演示如何指定和实现COM属性页。  
  
 [ATL为DHTML控件支持](../atl/atl-support-for-dhtml-controls.md)  
 用于创建DHTML控件的分步说明。  
  
 [ATL连接点](../atl/atl-connection-points.md)  
 解释什么连接点为，并且ATL如何实现它们。  
  
 [事件处理和ATL](../atl/event-handling-and-atl.md)  
 描述使用ATL的 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 和 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 选件类，您需要采取处理COM事件的步骤。  
  
 [ATL和自由线程封送拆收器](../atl/atl-and-the-free-threaded-marshaler.md)  
 在允许您的选件类复合自由线程封送拆收器\(FTM\)的ATL简单对象向导"的选项提供详细信息。  
  
 [指定项目的线程处理模型](../atl/specifying-the-threading-model-for-a-project-atl.md)  
 描述可用控件的运行时性能相关到项目中的线程处理的宏。  
  
 [ATL模块选件类](../atl/atl-module-classes.md)  
 讨论模块选件类为新ATL 7.0。  模块类的基本功能由ATL要求的实现。  
  
 [ATL服务](../atl/atl-services.md)  
 报告发生的事件的系列，当服务实现时。  并讨论一些概念与开发服务有关。  
  
 [ATL窗口选件类](../atl/atl-window-classes.md)  
 在ATL描述如何创建，创建超类时和子类窗口。  ATL窗口选件类不是COM选件类。  
  
 [ATL 集合类](../atl/atl-collection-classes.md)  
 在ATL描述如何使用数组和映射。  
  
 [ATL注册表元素\(管理员\)](../atl/atl-registry-component-registrar.md)  
 讨论脚本语法和可替换参数的ATL。  还说明如何设置静态链接到控制器。  
  
 [编程时ATL和C运行时代码](../atl/programming-with-atl-and-c-run-time-code.md)  
 讨论静态或动态链接的优点到C运行库\(crt）。  
  
 [编程时CComBSTR](../atl/programming-with-ccombstr-atl.md)  
 讨论需要小心，在编程时 `CComBSTR`时的几种情况。  
  
 [编码引用](../atl/atl-encoding-reference.md)  
 提供支持常规Internet标准大小的编码例如uuencode、十六进制和UTF8在atlenc.h的函数和宏。  
  
 [实用程序引用](../atl/atl-utilities-reference.md)  
 在 [CPathT](../atl/reference/cpatht-class.md) 和 [卷毛](../atl/reference/curl-class.md)的窗体中，为操作的路径提供代码和URL。  线程池，[CThreadPool](../atl/reference/cthreadpool-class.md)，可用于您的应用程序。  此代码可在atlpath.h和atlutil.h找到。  
  
## 相关章节  
 [ATL示例](../top/visual-cpp-samples.md)  
 提供说明和指向ATL示例程序。  
  
 [创建ATL项目](../atl/reference/creating-an-atl-project.md)  
 包含有关ATL项目向导的信息。  
  
 [ATL 控件向导](../atl/reference/atl-control-wizard.md)  
 讨论如何将选件类。  
  
 [特性化编程](../windows/attributed-programming-concepts.md)  
 在使用概述属性简化编程以及链接列表的COM更为详细的主题。  
  
 [ATL选件类概述](../atl/atl-class-overview.md)  
 提供参考信息以及指向ATL选件类。