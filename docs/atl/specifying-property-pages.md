---
title: "指定属性页 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ISpecifyPropertyPages
dev_langs: C++
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a4519bee0d1f9c5e433114f12a6568bde6b8c4fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-property-pages"></a>指定属性页
在创建 ActiveX 控件时，通常想要将其与可以用来设置控件的属性的属性页关联。 控制容器使用**ISpecifyPropertyPages**接口以找出哪些属性页可以用于设置控件的属性。 你将需要对控件中实现此接口。  
  
 若要实现**ISpecifyPropertyPages**使用 ATL，执行以下步骤：  
  
1.  派生您的类从[ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)。  
  
2.  为添加一个条目**ISpecifyPropertyPages**到您的类的 COM 映射。  
  
3.  添加[PROP_PAGE](reference/property-map-macros.md#prop_page)与控件关联的每一页的属性映射到的条目。  
  
> [!NOTE]
>  生成标准控件使用时[ATL 控件向导](../atl/reference/atl-control-wizard.md)，你只需添加`PROP_PAGE`属性映射到的条目。 向导将生成所需的代码有关的其他步骤。  
  
 功能良好的容器将显示指定的属性页中的顺序相同`PROP_PAGE`属性映射中的条目。 通常情况下，你应该将置于标准属性页项条目后在属性映射中，你自定义页的以便用户先看到特定于控件的页面。  
  
## <a name="example"></a>示例  
 下面的类为日历控件使用**ISpecifyPropertyPages**接口来告诉可以使用自定义日期页和常用颜色页设置其属性的容器。  
  
 [!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]  
  
## <a name="see-also"></a>另请参阅  
 [属性页](../atl/atl-com-property-pages.md)   
 [ATLPages 示例](../visual-cpp-samples.md)

