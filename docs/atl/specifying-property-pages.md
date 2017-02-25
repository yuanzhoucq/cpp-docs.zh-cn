---
title: "Specifying Property Pages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ISpecifyPropertyPages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISpecifyPropertyPages method"
  - "属性页, 指定"
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Specifying Property Pages
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您创建一个ActiveX控件，通常需要将其与可用于设置控件属性的属性页。  控件容器使用属性页可以用于设置控件的属性 **ISpecifyPropertyPages** 接口发现。  您需要实现在控件中此接口。  
  
 使用ATL，若要实现 **ISpecifyPropertyPages**，请执行以下步骤:  
  
1.  从 [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)派生您的选件类。  
  
2.  添加 **ISpecifyPropertyPages** 的项添加到您的选件类的COM映射。  
  
3.  添加 [PROP\_PAGE](../Topic/PROP_PAGE.md) 项添加到每页的属性映射与您的控件。  
  
> [!NOTE]
>  当生成一个标准控件使用 [ATL控件向导](../atl/reference/atl-control-wizard.md)，只需要添加时将属性的 `PROP_PAGE` 项映射。  向导生成其他步骤的需的代码。  
  
 功能良好的容器将显示指定的属性页按与在属性中 `PROP_PAGE` 项映射的序列。  通常，应在自己的自定义页的项后放置标准属性页中的项属性映射，因此，用户首次显示页特定于您的控件。  
  
## 示例  
 日历控件的下列选件类使用 **ISpecifyPropertyPages** 接口调用容器使用自定义日期页和股票颜色页，其属性进行设置。  
  
 [!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/CPP/specifying-property-pages_1.h)]  
  
## 请参阅  
 [属性页](../atl/atl-com-property-pages.md)   
 [ATLPages示例](../top/visual-cpp-samples.md)