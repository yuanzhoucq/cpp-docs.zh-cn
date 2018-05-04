---
title: 选项，ATL 简单对象向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffc38f5359b68b90f91a2643e1fbaa743a94e559
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="options-atl-simple-object-wizard"></a>选项，ATL 简单对象向导
ATL 简单对象向导的此页用于设计以便提高的效率和错误支持对象。  
  
 ATL 项目和 ATL COM 类的详细信息，请参阅[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)。  
  
 **线程处理模型**  
 指示用于管理线程的方法。 默认情况下，项目使用**单元**线程处理。  
  
 请参阅[指定项目的线程处理模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)有关详细信息。  
  
|选项|描述|  
|------------|-----------------|  
|`Single`|指定对象始终在主 COM 线程中运行。 请参阅[单线程单元](http://msdn.microsoft.com/library/windows/desktop/ms680112)和[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)有关详细信息。|  
|**单元**|指定该对象使用单元线程处理。 等效于单线程单元。 单元线程组件的每个对象分配一个单元用于其线程对象; 的整个生命周期但是，多个线程可以用于多个对象。 每个单元绑定到特定线程，并具有 Windows 消息泵 （默认值）。<br /><br /> 请参阅[单线程单元](http://msdn.microsoft.com/library/windows/desktop/ms680112)有关详细信息。|  
|**同时**|指定对象可使用单元或自由线程处理，具体取决于创建它的哪种类型的一个线程。|  
|**可用**|指定该对象使用自由线程处理。 自由线程处理相当于多线程单元模型。 请参阅[多线程单元](http://msdn.microsoft.com/library/windows/desktop/ms693421)有关详细信息。|  
|**Neutral**|指定对象后面的指南，多线程单元，但它可以在任何类型的线程上执行。|  
  
 **聚合**  
 指示对象是否使用[聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558)。 聚合对象选择要公开给客户端，将哪些接口和接口的公开方式就像是聚合对象实现它们。 聚合对象的客户端仅与聚合对象通信。  
  
|选项|描述|  
|------------|-----------------|  
|是|指定可聚合对象。 默认值。|  
|否|指定对象进行了不聚合。|  
|仅|指定必须聚合对象。|  
  
 **Interface**  
 指示对象支持的接口的类型。 默认情况下，该对象支持双重接口。  
  
|选项|描述|  
|------------|-----------------|  
|**双**|指定对象支持双重接口 (其 vtable 具有自定义接口函数和后期绑定`IDispatch`方法)。 允许这两个 COM 客户端和[自动化控制器](../../mfc/automation-clients.md)要访问的对象。 默认值。|  
|**自定义**|指定对象支持自定义接口 （其 vtable 具有自定义接口函数）。 自定义接口可以比双重接口，更快，尤其是跨进程边界。<br /><br /> -   **自动化兼容**允许自动化控制器访问具有自定义接口支持的对象。|  
  
 **支持**  
 指示对象的附加支持。  
  
|选项|描述|  
|------------|-----------------|  
|**ISupportErrorInfo**|创建支持[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)接口以便对象可以将错误信息返回到客户端。|  
|**连接点**|使对象的类派生来使你的对象的连接点[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。|  
|**自由线程封送处理程序**|创建在同一进程中线程之间有效地封送接口指针的自由线程封送处理程序对象。 可用于对象指定**同时**为线程模型。|  
|**IObjectWithSite （IE 对象支持）**|实现[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)，该属性提供一种简单的方法，以支持在容器中的对象及其站点之间的通信。|  
  
## <a name="see-also"></a>请参阅  
 [ATL 简单对象向导](../../atl/reference/atl-simple-object-wizard.md)   
 [ATL 简单对象](../../atl/reference/adding-an-atl-simple-object.md)   
 [进程内服务器线程处理问题](http://msdn.microsoft.com/library/windows/desktop/ms687205)

