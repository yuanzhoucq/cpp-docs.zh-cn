---
title: ATL 窗口特性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71fbf5b3c4c3f1aa95070cbc0d30beb9e1321348
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362363"
---
# <a name="understanding-window-traits"></a>了解窗口特性
窗口特性类提供标准化用于创建 ATL 窗口对象的样式的简单方法。 窗口特征接受作为模板参数[CWindowImpl](../atl/reference/cwindowimpl-class.md)和其他 ATL 窗口类作为一种方法提供默认在类级别的窗口样式。  
  
 如果窗口实例的创建者不提供对的调用中显式样式[创建](../atl/reference/cwindowimpl-class.md#create)，你可以使用的特征类以确保仍使用正确的样式创建窗口。 你可以甚至确保某些样式设置为该窗口类的所有实例同时允许其他样式设置基于每个实例。  
  
## <a name="atl-window-traits-templates"></a>ATL 窗口特征模板  
 ATL 提供了两个窗口特征模板允许你设置在编译时使用其模板参数的默认样式。  
  
|类|描述|  
|-----------|-----------------|  
|[CWinTraits](../atl/reference/cwintraits-class.md)|当你想要提供仅在不指定的调用中的任何其他样式时将使用的窗口样式的默认使用此模板**创建**。 提供在运行的时的优先级，通过在设置的样式的样式编译时间。|  
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|当你想要指定必须始终设置为窗口类样式时，请使用此类。 在使用按位 OR 运算符的编译时设置的样式与相结合，在运行时提供的样式。|  
  
 除了这些模板，ATL 提供了大量预定义专用化`CWinTraits`模板的常用组合的窗口样式。 请参阅[CWinTraits](../atl/reference/cwintraits-class.md)的完整详细信息，请参阅文档。  
  
## <a name="custom-window-traits"></a>自定义窗口特性  
 在可能的情况下不理想时该专用 ATL 所提供的模板之一并且你需要创建你自己的特征类，只需创建一个类以实现两个静态函数：`GetWndStyle`和**GetWndStyleEx**:  
  
 [!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]  
  
 其中每个函数将传递某个样式值在运行时它可以用于生成新的样式值。 如果你窗口的特征类用作 ATL 窗口类的模板自变量，则会传递给这些静态函数样式值，任何已作为样式参数传递给[创建](../atl/reference/cwindowimpl-class.md#create)。  
  
## <a name="see-also"></a>请参阅  
 [窗口类](../atl/atl-window-classes.md)

