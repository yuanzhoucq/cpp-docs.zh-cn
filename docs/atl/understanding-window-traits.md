---
title: "Understanding Window Traits | Microsoft Docs"
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
  - "window traits"
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Understanding Window Traits
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

窗口特征选件类出于标准化用于ATL窗口创建该对象的样式提供简单的方法。  窗口特征接受作为模板参数由 [CWindowImpl](../atl/reference/cwindowimpl-class.md) 和其他ATL窗口选件类作为提供默认值。选件类级别的窗口样式方式。  
  
 如果windows例程的创建者在调用不显式提供样式。[创建](../Topic/CWindowImpl::Create.md)，可以使用特征选件类窗口确保使用正确的样式仍然创建。  您甚至可以确保特定样式为该窗口选件类的所有实例设置，并允许其他样式设置基于每个实例的基类型。  
  
## ATL窗口特征模板  
 ATL提供使用自己的模板参数，允许您设置默认样式在编译时的两个窗口特征模板。  
  
|类|说明|  
|-------|--------|  
|[CWinTraits](../atl/reference/cwintraits-class.md)|请使用此模板，当您希望提供默认值将使用的windows样式时，只有当其他样式到 **Create**时的调用中指定。  样式提供在运行时优先于样式在编译时设置。|  
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|请使用此选件类，如果您希望指定必须为窗口选件类始终设置的样式时。  样式提供在运行时将与样式位在编译时设置使用或运算符。|  
  
 除了这些模板外，ATL为windows样式的常用的组合提供 `CWinTraits` 模板的许多预定义的专用化。  [CWinTraits](../atl/reference/cwintraits-class.md) 参见参考文档有关所有详细信息。  
  
## 自定义窗口特征  
 在专用ATL提供的某模板是不够的，并且需要创建自己的特征选件类的不太可能情况下，您需要创建一个选件类实现的两个静态函数: `GetWndStyle` 和 **GetWndStyleEx**:  
  
 [!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/CPP/understanding-window-traits_1.h)]  
  
 这些功能中的每一个都将传递它可以使用生成一个新的值的运行时的某些样式值。  如果窗口特征选件类用作ATL窗口选件类的模板参数，样式值传递给这些静态函数将什么是通过为样式的参数。[创建](../Topic/CWindowImpl::Create.md)。  
  
## 请参阅  
 [窗口类](../atl/atl-window-classes.md)