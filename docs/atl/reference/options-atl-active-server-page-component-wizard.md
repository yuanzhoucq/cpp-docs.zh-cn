---
title: "选项，ATL Active Server Page 组件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 199092acf4d26303a0d83d4885c3c7e3999bf0c4
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="options-atl-active-server-page-component-wizard"></a>选项，ATL Active Server Page 组件向导
使用 ATL Active Server Page 组件向导的此页为提高的效率和对象的错误支持设计。  
  
 ATL 项目和 ATL COM 类的详细信息，请参阅[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)。  
  
 **线程处理模型**  
 指示用于管理线程的方法。 默认情况下，项目使用**单元**线程处理。  
  
 请参阅[指定项目的线程处理模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)有关详细信息。  
  
|选项|描述|  
|------------|-----------------|  
|`Single`|指定该对象使用单个线程处理模型。 在单个线程处理模型中，对象始终在主 COM 线程中运行。 请参阅[单线程单元](http://msdn.microsoft.com/library/windows/desktop/ms680112)和[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)有关详细信息。|  
|**Apartment**|指定该对象使用单元线程处理。 等效于单线程单元。 单元线程组件的每个对象分配一个单元用于其线程对象; 的整个生命周期但是，多个线程可以用于多个对象。 每个单元绑定到特定线程，并具有 Windows 消息泵 （默认值）。<br /><br /> 请参阅[单线程单元](http://msdn.microsoft.com/library/windows/desktop/ms680112)有关详细信息。|  
|**同时**|指定对象可使用单元或自由线程处理，具体取决于创建它的哪种类型的一个线程。|  
|**可用**|指定该对象使用自由线程处理。 自由线程处理相当于多线程单元模型。 请参阅[多线程单元](http://msdn.microsoft.com/library/windows/desktop/ms693421)有关详细信息。|  
|**Neutral**|指定对象后面的指南，多线程单元，但它可以在任何类型的线程上执行。|  
  
 **聚合**  
 指示对象是否使用[聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558)。 聚合对象选择要公开给客户端，将哪些接口和接口的公开方式就像是聚合对象实现它们。 聚合对象的客户端仅与聚合对象通信。  
  
|选项|描述|  
|------------|-----------------|  
|**是**|指定可聚合对象。 默认值。|  
|**否**|指定对象进行了不聚合。|  
|**仅**|指定必须聚合对象。|  
  
 **支持**  
 （元素描述要添加）  
  
|选项|描述|  
|------------|-----------------|  
|**ISupportErrorInfo**|创建支持[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)接口以便对象可以将错误信息返回到客户端。|  
|**连接点**|使对象的类派生来使你的对象的连接点[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。|  
|**自由线程封送处理程序**|创建在同一进程中线程之间有效地封送接口指针的自由线程封送处理程序对象。 对指定的对象可用**同时**或**免费**为线程模型。|  
  
## <a name="see-also"></a>请参阅  
 [ATL Active Server Page 组件向导](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [ATL Active Server Page 组件](../../atl/reference/adding-an-atl-active-server-page-component.md)

