---
title: "Changing the Default Class Factory and Aggregation Model | Microsoft Docs"
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
  - "aggregation [C++], aggregation models"
  - "aggregation [C++], 使用 ATL"
  - "CComClassFactory class, making the default"
  - "CComCoClass class, default class factory and aggregation model"
  - "class factories, 更改默认值"
  - "default class factory"
  - "default class factory, ATL"
  - "默认值 [C++], aggregation model in ATL"
  - "默认值 [C++], class factory"
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the Default Class Factory and Aggregation Model
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL使用 [CComCoClass](../atl/reference/ccomcoclass-class.md) 定义默认选件类工厂和摘要设计您的对象的。  `CComCoClass` 指定下面两个宏:  
  
-   [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md) 声明选件类工厂是 [CComClassFactory](../atl/reference/ccomclassfactory-class.md)。  
  
-   [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md) 声明您的对象可以聚合。  
  
 通过指定另一个宏重写这些默认之一在类定义中。  例如，使用 [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) 而不是 `CComClassFactory`，请指定 [DECLARE\_CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) 宏:  
  
 [!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/CPP/changing-the-default-class-factory-and-aggregation-model_1.h)]  
  
 定义选件类工厂的其他两宏是 [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 和 [DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md)。  
  
 ATL还使用 `typedef` framework实现默认行为。  例如，`DECLARE_AGGREGATABLE` 宏使用 `typedef` 定义调用 **\_CreatorClass**的类型，然后引用在ATL中。  请注意在派生类中，使用名称的 `typedef` 和在ATL的基类的 `typedef` 结果相同使用您的定义和重写默认行为。  
  
## 请参阅  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)   
 [Aggregation and Class Factory Macros](../atl/reference/aggregation-and-class-factory-macros.md)