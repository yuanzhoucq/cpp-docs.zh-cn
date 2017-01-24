---
title: "MFC ActiveX 控件：访问环境属性 | Microsoft Docs"
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
  - "MFC ActiveX 控件, 访问环境属性"
  - "属性 [MFC], 访问环境"
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：访问环境属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文讨论 ActiveX 控件如何访问其控件容器环境属性。  
  
 控件可以通过访问容器的环境属性获取有关其容器的信息。  这些属性所公开的可视化特性，例如容器的背景色、容器当前使用的字体和运行属性，例如容器当前是否处于用户模式或设计器模式。  控件可以使用环境属性为其外观和行为。例如生成它嵌入特定的容器。  但是，控件不应当假定其容器，将支持所有特定环境属性。  事实上，某些容器可能不支持任何环境属性。  如果没有一环境属性时，控件应假定一个合理的默认值。  
  
 若要访问本地环境属性，请调用 [COleControl::GetAmbientProperty](../Topic/COleControl::GetAmbientProperty.md)。  此函数需要环境属性的调度 ID 作为第一个参数 \(OLECTL.H 文件定义的标准的调度 ID 的环境属性\)。  
  
 `GetAmbientProperty` 函数中参数是计划、ID 不同的标记和特性指示预期的类型的指针。应返回值的内存。  该指针引用数据的类型根据不同标记将有所不同。  函数返回 **TRUE**，则容器支持属性，否则返回 **FALSE**。  
  
 下面的代码示例获取“UserMode 调用环境的属性的值”。如果属性不是容器支持，假定默认值：**TRUE**  
  
 [!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/CPP/mfc-activex-controls-accessing-ambient-properties_1.cpp)]  
  
 为了方便起见，提供 `COleControl` 访问许多常用的环境属性并返回合适的默认 Helper 函数，当属性不可用时。  这些帮助程序函数如下：  
  
-   [COleControl::AmbientBackColor](../Topic/COleControl::AmbientBackColor.md)  
  
-   [AmbientDisplayName](../Topic/COleControl::AmbientDisplayName.md)  
  
-   [AmbientFont](../Topic/COleControl::AmbientFont.md)  
  
    > [!NOTE]
    >  调用方必须调用所返回的字体的 **Release\( \)**。  
  
-   [AmbientForeColor](../Topic/COleControl::AmbientForeColor.md)  
  
-   [AmbientLocaleID](../Topic/COleControl::AmbientLocaleID.md)  
  
-   [AmbientScaleUnits](../Topic/COleControl::AmbientScaleUnits.md)  
  
-   [AmbientTextAlign](../Topic/COleControl::AmbientTextAlign.md)  
  
-   [AmbientUserMode](../Topic/COleControl::AmbientUserMode.md)  
  
-   [AmbientUIDead](../Topic/COleControl::AmbientUIDead.md)  
  
-   [AmbientShowHatching](../Topic/COleControl::AmbientShowHatching.md)  
  
-   [AmbientShowGrabHandles](../Topic/COleControl::AmbientShowGrabHandles.md)  
  
 如果一环境属性更改 \(通过容器执行某些操作\)，控件的 **OnAmbientPropertyChanged** 成员函数。  重写该成员函数处理这些通知。  **OnAmbientPropertyChanged** 的参数是受影响的属性的方式安排 ID。  此计划 ID 值可以是 **DISPID\_UNKNOWN**，指示一个或多个环境属性更改，属性受影响，但信息不可用。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)