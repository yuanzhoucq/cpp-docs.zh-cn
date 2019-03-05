---
title: 选项，ATL 简单对象向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.options
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
ms.openlocfilehash: 327c78b00cbe69fcce4f055b0ae63c4dc2e5a7d9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273384"
---
# <a name="options-atl-simple-object-wizard"></a>选项，ATL 简单对象向导

ATL 简单对象向导的此页用于更高的效率以及对该对象的错误支持设计。

ATL 项目和 ATL COM 类的详细信息，请参阅[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)。

- **线程处理模型**

   指示用于管理线程的方法。 默认情况下，使用项目**单元**线程处理。

   请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)有关详细信息。

   |选项|描述|
   |------------|-----------------|
   |**Single**|指定对象始终在主 COM 线程中运行。 请参阅[单线程单元](/windows/desktop/com/single-threaded-apartments)并[InprocServer32](/windows/desktop/com/inprocserver32)有关详细信息。|
   |**Apartment**|指定该对象使用单元线程处理。 等效于单线程单元。 单线程单元的组件的每个对象分配一个单元用于其线程的生存期内的对象;但是，多个线程可以用于多个对象。 每个单元绑定到特定线程，并具有 Windows 消息泵 （默认值）。<br /><br /> 请参阅[单线程单元](/windows/desktop/com/single-threaded-apartments)有关详细信息。|
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

- **Interface**

   指示该对象支持的接口的类型。 默认情况下，该对象支持双重接口。

   |选项|描述|
   |------------|-----------------|
   |**Dual**|指定对象支持双重接口 (其 vtable 具有自定义接口函数和后期绑定`IDispatch`方法)。 允许这两个 COM 客户端和[自动化控制器](../../mfc/automation-clients.md)若要访问的对象。 默认值。|
   |**自定义**|指定的对象支持自定义界面 （其 vtable 具有自定义接口函数）。 尤其是跨进程边界，可以快于双重接口自定义界面。<br /><br /> - **自动化兼容**允许自动化控制器，以访问具有自定义接口支持的对象。|

- **支持**

   指示对象的附加支持。

   |选项|描述|
   |------------|-----------------|
   |**ISupportErrorInfo**|创建支持[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)接口使对象可以将错误信息返回到客户端。|
   |**连接点**|派生的对象的类，从而使您的对象的连接点[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。|
   |**自由线程封送处理程序**|创建在同一进程中线程之间有效地封送接口指针的自由线程封送处理程序对象。 对象指定可供**同时**作为线程模型。|
   |**IObjectWithSite** （IE 对象支持）|实现[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)，简单的方式来支持在容器中的对象及其站点之间的通信。|

## <a name="see-also"></a>请参阅

[ATL 简单对象向导](../../atl/reference/atl-simple-object-wizard.md)<br/>
[ATL 简单对象](../../atl/reference/adding-an-atl-simple-object.md)<br/>
[进程内服务器线程处理问题](/windows/desktop/com/in-process-server-threading-issues)
