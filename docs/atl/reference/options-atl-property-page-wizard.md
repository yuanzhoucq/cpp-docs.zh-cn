---
title: "选项，ATL 属性页向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.ppg.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 属性页向导，选项"
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 选项，ATL 属性页向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用此向导页定义正在创建的属性页的线程模型和聚合级别。  
  
 **线程模型**  
 指定属性页使用的线程模型。  
  
 有关更多信息，请参见[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。  
  
|选项|说明|  
|--------|--------|  
|`Single`|属性页仅在主 COM 线程内运行。|  
|**单元**|可以在任何单线程单元内创建属性页。  默认值。|  
  
 **Aggregation**  
 为正在创建的属性页添加聚合支持。  有关更多信息，请参见[聚合](../../atl/aggregation.md)。  
  
|选项|说明|  
|--------|--------|  
|**是**|创建可聚合的属性页。|  
|**否**|创建不能聚合的属性页。|  
|**只能创建为聚合**|创建只能通过聚合实例化的属性页。|  
  
## 请参阅  
 [ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)   
 [字符串，ATL 属性页向导](../../atl/reference/strings-atl-property-page-wizard.md)