---
title: "选项，ATL Active Server Page 组件向导 | Microsoft Docs"
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
  - "vc.codewiz.class.atl.asp.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL Active Server Page 组件向导，选项"
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 选项，ATL Active Server Page 组件向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用此“ATL Active Server Page 组件向导”页旨在提高对象的效率和错误支持。  
  
 有关 ATL 项目和 ATL COM 类的更多信息，请参见 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)。  
  
 **线程模型**  
 指示线程管理方法。  默认情况下，项目使用“单元”线程。  
  
 有关更多信息，请参见[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。  
  
|选项|说明|  
|--------|--------|  
|`Single`|指定对象使用单线程模型。  在单线程模型中，对象始终在主 COM 线程中运行。  有关更多信息，请参见[单线程单元](http://msdn.microsoft.com/library/windows/desktop/ms680112)和 [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)。|  
|**单元**|指定对象使用单元线程。  等效于单线程单元。  对于单元线程组件的每个对象，在该对象的生存期内为它分配一个单元用于其线程，但是，多个线程可用于多个对象。  每个单元绑定到一个特定的线程，而且具有 Windows 消息泵（默认）。<br /><br /> 有关更多信息，请参见[单线程单元](http://msdn.microsoft.com/library/windows/desktop/ms680112)。|  
|**高度和宽度**|指定对象可使用单元线程或自由线程，具体取决于创建它的线程类型。|  
|**自由**|指定对象使用自由线程。  自由线程等效于多线程单元模型。  有关更多信息，请参见[多线程单元](http://msdn.microsoft.com/library/windows/desktop/ms693421)。|  
|**中性**（仅适用于 Windows 2000）|指定对象遵守多线程单元的指南，但它可以在任何线程类型上执行。|  
  
 **Aggregation**  
 指示对象是否使用[聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558)。  聚集对象选择要将哪些接口公开给客户端，接口的公开方式就像是聚集对象实现它们一样。  聚集对象的客户端只与该聚集对象通信。  
  
|选项|说明|  
|--------|--------|  
|**是**|指定可聚合对象。  默认值。|  
|**否**|指定不聚合对象。|  
|**只能创建为聚合**|指定必须聚合对象。|  
  
 **支持**  
 （要添加的元素说明）  
  
|选项|说明|  
|--------|--------|  
|**ISupportErrorInfo**|创建 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 接口支持，以便对象可将错误信息返回到客户端。|  
|**连接点**|通过使对象的类从 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 导出来启用对象的连接点。|  
|**自由线程封送拆收器**|创建自由线程封送拆收器对象，以有效地在同一进程中的两个线程之间封送接口指针。  对指定“两者”或“自由”作为线程模型的对象可用。|  
  
## 请参阅  
 [ATL Active Server Page 组件向导](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [ATL Active Server Page Component](../../atl/reference/adding-an-atl-active-server-page-component.md)