---
title: 选项，ATL Active Server Page 组件向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45824065a4ef190f509f003656b9d232ae287ca2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718024"
---
# <a name="options-atl-active-server-page-component-wizard"></a>选项，ATL Active Server Page 组件向导

使用 ATL Active Server Page 组件向导此页设计更高的效率以及对该对象的错误支持。

ATL 项目和 ATL COM 类的详细信息，请参阅[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)。

- **线程处理模型**

   指示用于管理线程的方法。 默认情况下，使用项目**单元**线程处理。

   请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)有关详细信息。

   |选项|描述|
   |------------|-----------------|
   |**单精度**|指定该对象使用单线程模型。 在单线程处理模型中，对象始终在主 COM 线程中运行。 请参阅[单线程单元](/windows/desktop/com/single-threaded-apartments)并[InprocServer32](/windows/desktop/com/inprocserver32)有关详细信息。|
   |**单元**|指定该对象使用单元线程处理。 等效于单线程单元。 单线程单元的组件的每个对象分配一个单元用于其线程的生存期内的对象;但是，多个线程可以用于多个对象。 每个单元绑定到特定线程，并具有 Windows 消息泵 （默认值）。<br /><br /> 请参阅[单线程单元](/windows/desktop/com/single-threaded-apartments)有关详细信息。|
   |**两者**|指定该对象可以使用单元或自由线程处理，具体取决于创建它的线程的类型。|
   |**免费**|指定该对象使用自由线程处理。 自由线程处理相当于多线程单元模型。 请参阅[多线程单元](/windows/desktop/com/multithreaded-apartments)有关详细信息。|
   |**Neutral**|指定对象后面的多线程单元的准则，但它可以在任何类型的线程上执行。|

- **聚合**

   指示对象是否使用[聚合](/windows/desktop/com/aggregation)。 聚合对象选择要向客户端，公开的接口和接口的公开方式像聚合对象实现它们。 聚合对象的客户端仅与聚合对象通信。

   |选项|描述|
   |------------|-----------------|
   |**是**|指定可聚合对象。 默认值。|
   |**否**|指定对象不聚合。|
   |**仅**|指定必须聚合对象。|

- **支持**

   其他支持选项：

   |选项|描述|
   |------------|-----------------|
   |**ISupportErrorInfo**|创建支持[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)接口使对象可以将错误信息返回到客户端。|
   |**连接点**|派生的对象的类，从而使您的对象的连接点[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。|
   |**自由线程封送处理程序**|创建在同一进程中线程之间有效地封送接口指针的自由线程封送处理程序对象。 对指定的对象可用**两者**或**免费**作为线程模型。|

## <a name="see-also"></a>请参阅

[ATL Active Server Page 组件向导](../../atl/reference/atl-active-server-page-component-wizard.md)   
[ATL Active Server Page 组件](../../atl/reference/adding-an-atl-active-server-page-component.md)

