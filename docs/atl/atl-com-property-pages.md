---
title: "ATL COM 属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "ATL COM 对象"
  - "ATL 属性页"
  - "COM 对象, ATL"
  - "COM 属性页"
  - "属性页, ATL"
  - "属性页, COM"
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL COM 属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM属性页设置了属性\(或调用方法\)提供用户界面一个或多个COM对象。  ActiveX控件广泛使用属性页提供允许控件属性设置在设计时的丰富的用户界面。  
  
 属性页是实现 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) 或 [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) 接口的COM对象。  这些接口提供允许页与 `site` 的方法\(表示页的容器\)的COM对象和一组 *对象* \(调用方法以响应属性页用户所做的更改\)的COM对象。  属性页容器何时调用在属性页中接口的方法来调用页显示或隐藏其用户界面和应用该用户所做的更改为基础对象。  
  
 每个属性页可以独立属性设置的对象将被完全生成。  属性页所需的任何是了解特定的接口\(或组接口\)以及调用方法提供用户界面该接口。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [属性表和属性页](http://msdn.microsoft.com/library/windows/desktop/ms686577)。  
  
## 本节内容  
 [指定属性页](../atl/specifying-property-pages.md)  
 列出指定的属性页步骤您的控件并显示示例选件类。  
  
 [实现属性页](../atl/implementing-property-pages.md)  
 列出实现的属性页步骤，包括重写的方法。  指导您通过基于ATLPages示例程序的完整示例。  
  
## 相关章节  
 [ATLPages示例](../top/visual-cpp-samples.md)  
 ATLPages示例的示例摘要，使用 `IPropertyPageImpl`，实现属性页。  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 使用活动模板库提供一些链接，指向有关概念性主题有关如何使用进行编程。  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)