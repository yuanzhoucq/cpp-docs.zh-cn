---
title: "MFC ActiveX 控件：属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控件, 属性"
  - "属性 [MFC]"
  - "属性 [MFC], ActiveX 控件"
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC ActiveX 控件：属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控件激发事件及其控件容器通信。  容器，反过来，使用方法和属性与控件进行通信。  方法和属性非常相似在使用中并且打算，分别，指向成员函数，而 C. \+\+ 成员变量的类。  属性是公开给任何容器 ActiveX 控件的数据成员。  属性为所包含 ActiveX 控件的应用程序提供的接口，例如的自动化客户程序和 ActiveX 控件容器。  
  
 属性也称为特性。  
  
 有关方法 ActiveX 控件的更多信息，请参见知识库文章 [MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)。  
  
 ActiveX 控件可实现两个股票和自定义方法和属性。  `COleControl` 类为常用属性提供实现。\(有关常用属性的完整列表，请参见的文章 [MFC ActiveX 控件：添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)。\)自定义属性，定义由开发人员，添加专用功能到 ActiveX 控件。  有关更多信息，请参见 [MFC ActiveX 控件：添加自定义属性](../mfc/mfc-activex-controls-adding-custom-properties.md)。  
  
 自定义和常用属性，如方法，由包含计划映射处理的属性，方法和 `COleControl` 的现有成员函数类的机制。支持  此外，这些属性可以具有开发人员使用的信息传递附加到控件的参数。  
  
 下列文章更详细地讨论 ActiveX 控件属性：  
  
-   [MFC ActiveX 控件：添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [MFC ActiveX 控件：添加自定义属性](../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [MFC ActiveX 控件：高级属性实现](../mfc/mfc-activex-controls-advanced-property-implementation.md)  
  
-   [MFC ActiveX 控件：访问环境属性](../mfc/mfc-activex-controls-accessing-ambient-properties.md)  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)