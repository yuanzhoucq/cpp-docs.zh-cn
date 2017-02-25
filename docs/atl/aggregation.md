---
title: "Aggregation | Microsoft Docs"
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
  - "aggregate objects [C++]"
  - "aggregation [C++]"
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Aggregation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有时，当对象的实现者希望利用另一个提供的服务，生成对象。  此外，所需第二个对象显示为自然部分的第一。  通过COM包容和摘要实现这两个目标。  
  
 摘要意味着包含的\(外部\)对象创建包含\(内部\)对象作为其创建过程的一部分，并且内部对象的接口由外部显示。  对象使自身可聚集的。  如果是，则它必须遵循摘要的某些规则正常工作。  
  
 首先，所有 **IUnknown** 方案中包含的对象调用必须委托给包含的对象。  
  
## 请参阅  
 [COM 介绍](../atl/introduction-to-com.md)   
 [Reusing Objects](http://msdn.microsoft.com/library/windows/desktop/ms678443)