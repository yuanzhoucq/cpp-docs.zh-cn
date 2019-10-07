---
title: 选项，ATL 简单对象向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.options
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
ms.openlocfilehash: e92f4909907645fc317590fbcc3601887346c642
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495162"
---
# <a name="options-atl-simple-object-wizard"></a>选项，ATL 简单对象向导

使用 ATL 简单对象向导的此页可为对象提供更高的效率和错误支持。

有关 ATL 项目和 ATL COM 类的详细信息，请参阅 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)。

- **线程模型**

   指示用于管理线程的方法。 默认情况下, 该项目使用**单元**线程。

   有关详细信息，请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。

   |选项|描述|
   |------------|-----------------|
   |**单精度**|指定对象始终在主 COM 线程中运行。 有关详细信息, 请参阅[单线程单元](/windows/win32/com/single-threaded-apartments)和[InprocServer32](/windows/win32/com/inprocserver32) 。|
   |**单元**|指定对象使用单元线程。 等效于单线程单元。 在对象的整个生存期内, 单元线程组件的每个对象都为其线程分配一个单元;但是, 多个线程可用于多个对象。 每个单元都绑定到特定的线程, 并且具有 Windows 消息泵 (默认值)。<br /><br /> 有关详细信息, 请参阅[单线程单元](/windows/win32/com/single-threaded-apartments)。|
   |**全部**|指定对象可以使用单元线程或自由线程, 具体取决于创建它的线程类型。|
   |**忙**|指定对象使用自由线程处理。 自由线程处理等效于多线程单元模型。 有关详细信息, 请参阅[多线程单元](/windows/win32/com/multithreaded-apartments)。|
   |**Neutral**|指定对象遵循多线程单元的准则, 但它可以在任何类型的线程上执行。|

- **聚合**

   指示对象是否使用[聚合](/windows/win32/com/aggregation)。 聚合对象选择要向客户端公开的接口, 并公开接口, 就像聚合对象实现它们一样。 聚合对象的客户端仅与聚合对象通信。

   |选项|描述|
   |------------|-----------------|
   |**是**|指定可以聚合对象。 默认值。|
   |**否**|指定不聚合对象。|
   |**仅限**|指定必须聚合对象。|

- **Interface**

   指示对象支持的接口类型。 默认情况下，对象支持双重接口。

   |选项|描述|
   |------------|-----------------|
   |**双重**|指定对象支持双重接口 (其 vtable 具有自定义接口函数和后期绑定`IDispatch`方法)。 允许 COM 客户端和[自动化控制器](../../mfc/automation-clients.md)访问对象。 默认值。|
   |**自定义**|指定对象支持自定义接口（其 vtable 具有自定义接口函数）。 自定义接口的速度比双重接口更快，尤其对于跨进程边界而言。<br /><br /> - **自动化兼容**允许自动化控制器访问具有自定义接口支持的对象。|

- **支持**

   指示对对象的其他支持。

   |选项|描述|
   |------------|-----------------|
   |**ISupportErrorInfo**|创建对 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 接口的支持，使对象可以将错误信息返回到客户端。|
   |**连接点**|通过使对象的类派生自[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md), 为对象启用连接点。|
   |**自由线程封送拆收器**|创建自由线程封送拆收器对象, 以便在同一进程中的线程之间有效地封送接口指针。 可用于指定作为线程模型的对象。|
   |**IObjectWithSite**(IE 对象支持)|实现[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), 它提供了一种简单的方法来支持在容器中的对象与其站点之间进行通信。|

## <a name="see-also"></a>请参阅

[ATL 简单对象向导](../../atl/reference/atl-simple-object-wizard.md)<br/>
[ATL 简单对象](../../atl/reference/adding-an-atl-simple-object.md)<br/>
[进程内服务器线程问题](/windows/win32/com/in-process-server-threading-issues)
