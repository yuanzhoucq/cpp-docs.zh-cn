---
title: 选项，ATL Active Server Page 组件向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.options
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
ms.openlocfilehash: c76ab7730256b007b66d54ca6753409926f7ae89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495304"
---
# <a name="options-atl-active-server-page-component-wizard"></a>选项，ATL Active Server Page 组件向导

使用 ATL Active Server Page 组件向导的此页可为对象提供更高的效率和错误支持。

有关 ATL 项目和 ATL COM 类的详细信息，请参阅 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)。

- **线程模型**

   指示用于管理线程的方法。 默认情况下, 该项目使用**单元**线程。

   有关详细信息，请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。

   |选项|描述|
   |------------|-----------------|
   |**单精度**|指定对象使用单线程模型。 在单线程模型中, 对象始终在主 COM 线程中运行。 有关详细信息, 请参阅[单线程单元](/windows/win32/com/single-threaded-apartments)和[InprocServer32](/windows/win32/com/inprocserver32) 。|
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

- **支持**

   其他支持选项:

   |选项|描述|
   |------------|-----------------|
   |**ISupportErrorInfo**|创建对 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 接口的支持，使对象可以将错误信息返回到客户端。|
   |**连接点**|通过使对象的类派生自[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md), 为对象启用连接点。|
   |**自由线程封送拆收器**|创建自由线程封送拆收器对象, 以便在同一进程中的线程之间有效地封送接口指针。 可用于将或**自由**指定为线程模型的对象。|

## <a name="see-also"></a>请参阅

[ATL Active Server Page 组件向导](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[ATL Active Server Page 组件](../../atl/reference/adding-an-atl-active-server-page-component.md)
