---
title: "ATL COM 对象的基础知识 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a5a43af31a88420c154d7a57d27d2b69787d11d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fundamentals-of-atl-com-objects"></a>ATL COM 对象的基础知识
下图描绘了的类和接口，用于定义 ATL COM 对象之间的关系。  
  
 ![ATL 结构](../atl/media/vc307y1.gif "vc307y1")  
  
> [!NOTE]
>  此图演示`CComObject`派生自`CYourClass`而`CComAggObject`和`CComPolyObject`包括`CYourClass`作为成员变量。  
  
 有三种方法来定义 ATL COM 对象。 标准选项是使用`CComObject`类，该类派生自`CYourClass`。 第二个选项是通过使用创建聚合的对象`CComAggObject`类。 第三个选项是使用`CComPolyObject`类。 `CComPolyObject`充当混合： 它可以用作`CComObject`类或`CComAggObject`类，具体取决于如何首次创建。 有关如何使用`CComPolyObject`类，请参阅[CComPolyObject 类](../atl/reference/ccompolyobject-class.md)。  
  
 当使用标准的 ATL COM 时，使用两个对象： 外部对象和内部对象。 外部客户端通过外部对象中定义的包装函数访问内部对象的功能。 在外部对象属于类型`CComObject`。  
  
 当使用聚合的对象时，在外部对象不提供的功能的内部对象的包装器。 相反，在外部对象提供的外部的客户端直接访问的指针。 在此方案中，在外部对象属于类型`CComAggObject`。 内部对象是在外部对象的成员变量，并且它是类型`CYourClass`。  
  
 因为客户端不需要经历与内部对象进行交互的外部对象，则聚合的对象是通常更高效。 此外，在外部对象不必知道的聚合对象的功能的聚合对象的接口是供客户端直接访问。 但是，并非所有对象可都聚合。 要聚合的对象，它需要记住的聚合设计。  
  
 ATL 实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)中两个阶段：  
  
-   [CComObject](../atl/reference/ccomobject-class.md)， [CComAggObject](../atl/reference/ccomaggobject-class.md)，或[CComPolyObject](../atl/reference/ccompolyobject-class.md)实现**IUnknown**方法。  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)管理的引用计数和的外部指针**IUnknown**。  
  
 ATL COM 对象的其他方面由其他类处理：  
  
-   [CComCoClass](../atl/reference/ccomcoclass-class.md)定义对象的默认类工厂和聚合模型。  
  
-   [IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供的默认实现`IDispatch Interface`的任何对象上的双重接口的部分。  
  
-   [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)实现**ISupportErrorInfo**接口，以确保错误信息可以将会向上传播的调用链正确。  
  
## <a name="in-this-section"></a>本节内容  
 [实现 CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)  
 显示用于实现的 COM 映射项的示例`CComObjectRootEx`。  
  
 [实现 CComObject、CComAggObject 和 CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)  
 讨论如何**DECLARE_\*_AGGREGATABLE**宏会影响使用`CComObject`， `CComAggObject`，和`CComPolyObject`。  
  
 [支持 IDispatch 和 IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)  
 列出用于支持的 ATL 实现类`IDispatch`和**IErrorInfo**接口。  
  
 [支持 IDispEventImpl](../atl/supporting-idispeventimpl.md)  
 讨论实现你的类的连接点的步骤。  
  
 [更改默认类工厂和聚合模型](../atl/changing-the-default-class-factory-and-aggregation-model.md)  
 显示哪些宏，以用于更改默认类工厂和聚合模型。  
  
 [创建聚合对象](../atl/creating-an-aggregated-object.md)  
 列出用于创建聚合的对象的步骤。  
  
## <a name="related-sections"></a>相关章节  
 [创建 ATL 项目](../atl/reference/creating-an-atl-project.md)  
 提供有关创建 ATL COM 对象的信息。  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)

