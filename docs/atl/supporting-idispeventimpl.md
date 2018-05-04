---
title: 支持 IDispEventImpl |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 680396ae912cca5f19e87697e7de0033213cc963
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="supporting-idispeventimpl"></a>支持 IDispEventImpl
此模板类[IDispEventImpl](../atl/reference/idispeventimpl-class.md)可以用于为 ATL 类中的连接点接收器提供支持。 连接点接收器允许你的类以处理从外部 COM 对象触发的事件。 这些连接点接收器使用事件接收器映射，你的类所提供的映射。  
  
 若要正确实现连接点接收器来用于您的类，必须完成以下步骤：  
  
-   导入每个外部对象的类型库  
  
-   声明`IDispEventImpl`接口  
  
-   声明事件接收器映射  
  
-   通知和取消通知的连接点  
  
 所有完成通过修改仅标头文件 (.h) 的您的类中实现连接点接收器所涉及的步骤。  
  
## <a name="importing-the-type-libraries"></a>导入的类型库  
 对于每个外部对象你想要处理其事件，你必须导入类型库。 此步骤定义可以处理的事件，并提供在声明事件接收器映射时使用的信息。 [#Import](../preprocessor/hash-import-directive-cpp.md)指令可以用于实现此目的。 添加所需`#import`指令的行，以便将到你的类的标头文件 (.h) 支持每个调度接口。  
  
 下面的示例将外部 COM 服务器的类型库导入 (`MSCAL.Calendar.7`):  
  
 [!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]  
  
> [!NOTE]
>  你必须有一个单独`#import`将支持每个外部类型库的语句。  
  
## <a name="declaring-the-idispeventimpl-interfaces"></a>声明 IDispEventImpl 接口  
 现在，你已导入的每个调度接口的类型库，则需要声明单独`IDispEventImpl`为每个外部调度接口的接口。 通过添加修改您的类的声明`IDispEventImpl`接口对于每个外部对象的声明。 有关参数的详细信息，请参阅[IDispEventImpl](../atl/reference/idispeventimpl-class.md)。  
  
 下面的代码的声明两个连接点接收器， `DCalendarEvents` COM 对象由类实现的接口， `CMyCompositCtrl2`:  
  
 [!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]  
  
## <a name="declaring-an-event-sink-map"></a>声明事件接收器映射  
 为了使由正确的函数处理的事件通知，你的类必须将每个事件路由到其正确的处理程序。 这被通过声明事件接收器映射。  
  
 ATL 提供几个宏[BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map)， [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)，和[SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)，，这使此映射更容易。 标准的格式如下所示：  
  
 `BEGIN_SINK_MAP(comClass)`  
  
 `SINK_ENTRY_EX(id, iid, dispid, func)`  
  
 `. . . //additional external event entries`  
  
 `END_SINK_MAP()`  
  
 下面的示例声明两个事件处理程序使用事件接收器映射：  
  
 [!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]  
  
 实现已接近完成。 最后一步涉及通知和外部接口的取消通知。  
  
## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>通知和取消通知 IDispEventImpl 接口  
 最后一步是实现将建议 （或不建议） 的所有连接点的方法在适当的时间。 外部客户端和你的对象之间的通信进行之前，必须完成这种通知。 你的对象将变得可见之前，向对象支持的每个外部调度接口将查询输出接口。 建立的连接并对传出的接口的引用用于处理来自对象的事件。 此过程称为"通知"。  
  
 使用外部接口完成你的对象后，应通知的传出接口，它们不再使用通过您的类。 此过程称为"取消通知。"  
  
 由于 COM 对象的唯一性质，此过程会有所不同，在详细信息和执行，实现之间。 这些详细信息超出了本主题的范围，并且未得到解决。  
  
## <a name="see-also"></a>请参阅  
 [ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)

