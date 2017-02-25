---
title: "Aggregation and Class Factory Macros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregation [C++], ATL macros"
  - "class factories, ATL macros"
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# Aggregation and Class Factory Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些宏提供控件的摘要方式和声明选件类工厂。  
  
|||  
|-|-|  
|[DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md)|声明您的对象可以聚合\(默认值）。|  
|[DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)|声明选件类工厂是 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，ATL默认选件类工厂。|  
|[DECLARE\_CLASSFACTORY\_EX](../Topic/DECLARE_CLASSFACTORY_EX.md)|声明您的选件类工厂对象是选件类工厂。|  
|[DECLARE\_CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md)|声明 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) 是选件类工厂。|  
|[DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md)|声明 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 是选件类工厂。|  
|[DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md)|声明 [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) 是选件类工厂。|  
|[DECLARE\_GET\_CONTROLLING\_UNKNOWN](../Topic/DECLARE_GET_CONTROLLING_UNKNOWN.md)|声明虚拟 `GetControllingUnknown` 功能。|  
|[DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)|声明您的对象不能聚合。|  
|[DECLARE\_ONLY\_AGGREGATABLE](../Topic/DECLARE_ONLY_AGGREGATABLE.md)|声明必须复合您的对象。|  
|[DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md)|检查值的外部未知并声明您的对象可聚集的或不可聚集的，根据。|  
|[DECLARE\_PROTECT\_FINAL\_CONSTRUCT](../Topic/DECLARE_PROTECT_FINAL_CONSTRUCT.md)|在内部对象的构造时防止删除的外部对象。|  
|[DECLARE\_VIEW\_STATUS](../Topic/DECLARE_VIEW_STATUS.md)|指定 **VIEWSTATUS** 标志向容器。|  
  
## 请参阅  
 [Macros](../../atl/reference/atl-macros.md)