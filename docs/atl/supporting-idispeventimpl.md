---
title: 支持 IDispEventImpl
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: 31beff30a067416f71029c18051f214c8d4429de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329314"
---
# <a name="supporting-idispeventimpl"></a>支持 IDispEventImpl

模板类[IDispEventImpl](../atl/reference/idispeventimpl-class.md)可用于为 ATL 类中的连接点接收器提供支持。 连接点接收器允许类处理从外部 COM 对象触发的事件。 这些连接点接收器使用事件接收器映射映射，由类提供。

要正确实现类的连接点接收器，必须完成以下步骤：

- 导入每个外部对象的类型库

- 声明`IDispEventImpl`接口

- 声明事件接收器映射

- 建议并取消建议连接点

实现连接点接收器所涉及的步骤都通过仅修改类的标头文件 （.h） 来完成。

## <a name="importing-the-type-libraries"></a>导入类型库

对于要处理的事件的每个外部对象，必须导入类型库。 此步骤定义可处理的事件，并提供声明事件接收器映射时使用的信息。 [#import](../preprocessor/hash-import-directive-cpp.md)指令可用于实现此目的。 为将支持的`#import`每个调度接口添加所需的指令行到类的标头文件 （.h）。

以下示例导入外部 COM 服务器的类型库 （`MSCAL.Calendar.7`）：

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
> 对于将支持的每个外部`#import`类型库，必须具有单独的语句。

## <a name="declaring-the-idispeventimpl-interfaces"></a>声明 IDispEventImpl 接口

现在，您已经导入了每个调度接口的类型库，您需要为每个外部调度接口声明单独的`IDispEventImpl`接口。 通过为每个外部对象添加`IDispEventImpl`接口声明来修改类的声明。 有关参数的详细信息，请参阅[IDispEventImpl](../atl/reference/idispeventimpl-class.md)。

以下代码声明两个连接点接收器，对于`DCalendarEvents`接口，对于由类`CMyCompositCtrl2`实现的 COM 对象：

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>声明事件接收器映射

为了使事件通知由正确的函数处理，类必须将每个事件路由到其正确的处理程序。 这是通过声明事件接收器映射来实现的。

ATL 提供了多个宏[，BEGIN_SINK_MAP、END_SINK_MAP](reference/composite-control-macros.md#begin_sink_map)[END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)和[SINK_ENTRY_EX，](reference/composite-control-macros.md#sink_entry_ex)使此映射更容易。 标准格式如下：

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

以下示例声明具有两个事件处理程序的事件接收器映射：

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

实现已接近完成。 最后一步是建议和取消通知外部接口。

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>为 IDispEventImpl 接口提供咨询和取消建议

最后一步是实现一种方法，该方法将在适当的时候通知（或不建议）所有连接点。 在外部客户端和对象之间发生通信之前，必须执行此建议。 在对象变得可见之前，对象支持的每个外部调度接口都会查询出发接口。 建立连接，并使用对传出接口的引用来处理来自对象的事件。 此过程称为"建议"。

在对象完成外部接口后，应通知传出接口它们不再被类使用。 此过程称为"不建议"。

由于 COM 对象的独特性质，此过程在细节和执行之间因实现而异。 这些详细信息超出了本主题的范围，并且未涉及。

## <a name="see-also"></a>另请参阅

[ATL COM 对象的基础知识](../atl/fundamentals-of-atl-com-objects.md)
