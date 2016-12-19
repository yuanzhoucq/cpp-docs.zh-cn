---
title: "Design Principles for Collection and Enumerator Interfaces | Microsoft Docs"
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
  - "collection interfaces"
  - "enumerator interfaces"
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Design Principles for Collection and Enumerator Interfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在接口后的每种不同的设计原则:  
  
-   集合接口通过 **Item** 方法提供对单个项目的 *随机* 访问集合，它使客户端能够确定多少项集合中通过 **Count** 属性和通常允许客户端添加和移除项。  
  
-   枚举器接口提供 *序列化访问* 对于集合中的 *多个* 项目，它不允许客户端发现多少项集合\(直到枚举器停止返回项目\)，因此，它不提供添加或移除项任何方式。  
  
 接口的每种类型的提供对模拟不同的效果对于集合中的元素。  
  
## 请参阅  
 [集合和枚举数](../atl/atl-collections-and-enumerators.md)