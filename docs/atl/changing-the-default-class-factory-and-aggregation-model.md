---
title: 更改默认类工厂和聚合模型 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory class, making the default
- aggregation [C++], using ATL
- aggregation [C++], aggregation models
- defaults [C++], aggregation model in ATL
- default class factory
- class factories, changing default
- CComCoClass class, default class factory and aggregation model
- default class factory, ATL
- defaults [C++], class factory
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce64f2162aa0d5cdf5bcf5e16b56b6989fcaf1ee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355234"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>更改默认类工厂和聚合模型
使用 ATL [CComCoClass](../atl/reference/ccomcoclass-class.md)来定义你的对象的默认类工厂和聚合模型。 `CComCoClass` 指定以下两个宏：  
  
-   [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory)声明类工厂为[CComClassFactory](../atl/reference/ccomclassfactory-class.md)。  
  
-   [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable)声明你的对象可以进行聚合。  
  
 你可以通过在类定义中指定的另一个宏覆盖这些默认值之一。 例如，若要使用[CComClassFactory2](../atl/reference/ccomclassfactory2-class.md)而不是`CComClassFactory`，指定[DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2)宏：  
  
 [!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]  
  
 定义类工厂的两个其他宏[DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)和[DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton)。  
  
 ATL 还使用`typedef`机制来实现默认行为。 例如，`DECLARE_AGGREGATABLE`宏使用`typedef`以定义调用类型 **_CreatorClass**，然后引用整个 atl。 请注意，在派生类中，`typedef`使用相同的名称作为基类的`typedef`导致 ATL 使用您的定义和重写默认行为。  
  
## <a name="see-also"></a>请参阅  
 [ATL COM 对象的基础知识](../atl/fundamentals-of-atl-com-objects.md)   
 [聚合和类工厂宏](../atl/reference/aggregation-and-class-factory-macros.md)

