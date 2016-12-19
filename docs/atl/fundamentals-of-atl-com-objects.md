---
title: "Fundamentals of ATL COM Objects | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL COM objects"
  - "ATL, COM"
  - "COM 对象, ATL"
  - "COM, 和 ATL"
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
caps.latest.revision: 25
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Fundamentals of ATL COM Objects
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于定义ATL COM对象的下图演示对选件类之间的关系和接口。  
  
 ![ATL 结构](../atl/media/vc307y1.png "vc307Y1")  
  
> [!NOTE]
>  此关系图表示，`CComObject` 从 `CYourClass` 派生，而 `CComAggObject` 和 `CComPolyObject` 包括 `CYourClass` 作为成员变量。  
  
 有三种定义ATL COM对象。  标准选项是使用从 `CYourClass`派生的 `CComObject` 选件类。  第二个选项是创建聚合的对象使用 `CComAggObject` 选件类。  第三种方法是使用 `CComPolyObject` 选件类。  `CComPolyObject` 为混合:它可以作为 `CComObject` 选件类或作为 `CComAggObject` 选件类，根据如何首次创建。  有关如何使用 `CComPolyObject` 类的更多信息，请参见 [CComPolyObject Class](../atl/reference/ccompolyobject-class.md)。  
  
 当您使用标准ATL COM时，可以使用两个对象:一个外部对象和内部对象。  外部客户端访问内部对象的函数通过在外部对象定义的包装函数。  外部对象是类型 `CComObject`。  
  
 在将聚合的对象时，外部对象为内部对象的函数不提供包装。  相反，外部对象提供由外部客户端直接访问的指针。  在此方案中，外部对象是类型 `CComAggObject`。  内部对象是外部对象的成员变量，因此，为类型 `CYourClass`。  
  
 由于客户端不必通过外部对象与内部对象进行交互，合成对象通常更高效。  此外，外部对象不需要知道合成对象的功能，假定合成对象的接口直接客户端可使用。  但是，并非所有对象都可以聚合。  对于要聚合的对象，它需要设计记住摘要。  
  
 在两个阶段的ATL实现 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) :  
  
-   [CComObject](../atl/reference/ccomobject-class.md)、 [CComAggObject](../atl/reference/ccomaggobject-class.md)或 [CComPolyObject](../atl/reference/ccompolyobject-class.md) 实现 **IUnknown** 方法。  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 管理 **IUnknown**引用计数和外部指针。  
  
 您的ATL COM对象的其他方面由其他选件类处理:  
  
-   [CComCoClass](../atl/reference/ccomcoclass-class.md) 定义对象的默认选件类工厂和摘要模型。  
  
-   [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 在对象提供所有双重接口的 `IDispatch Interface` 部分的默认实现。  
  
-   [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) 实现相应的接口 **ISupportErrorInfo** 错误信息能准确传播调用链。  
  
## 本节内容  
 [实现CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)  
 演示COM实现的 `CComObjectRootEx`映射项。  
  
 [实现CComObject、CComAggObject和CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)  
 讨论 **DECLARE\_\*\_AGGREGATABLE** 宏如何影响使用 `CComObject`、 `CComAggObject`和 `CComPolyObject`。  
  
 [支持IDispatch和IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)  
 列出ATL实现选件类支持 `IDispatch` 和 **IErrorInfo** 接口使用。  
  
 [支持IDispEventImpl](../atl/supporting-idispeventimpl.md)  
 讨论步骤实现自己的选件类连接点。  
  
 [更改默认选件类工厂和摘要模型](../atl/changing-the-default-class-factory-and-aggregation-model.md)  
 显示使用的哪些宏更改默认选件类工厂和汇总了建模。  
  
 [创建聚合的对象](../atl/creating-an-aggregated-object.md)  
 列出创建的聚合的对象步骤。  
  
## 相关章节  
 [创建ATL项目](../atl/reference/creating-an-atl-project.md)  
 提供有关创建ATL COM对象的信息。  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 使用活动模板库提供一些链接，指向有关概念性主题有关如何使用进行编程。  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)