---
title: ATL 窗口特征
ms.date: 11/04/2016
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
ms.openlocfilehash: 29549e54051405fc3dd4d5d7ae70a382ad7a62ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196178"
---
# <a name="understanding-window-traits"></a>了解窗口特征

窗口特征类提供简单的方法来标准化用创建 ATL 窗口对象的样式。 窗口特征会接受作为模板参数[CWindowImpl](../atl/reference/cwindowimpl-class.md)和作为一种方法提供默认窗口样式类级别的其它 ATL 窗口类。

如果窗口实例的创建者不提供对的调用中显式样式[创建](../atl/reference/cwindowimpl-class.md#create)，可以使用一个特征类以确保仍以正确样式创建窗口。 您甚至可以确保，设置特定的样式的窗口类的所有实例的同时允许其他样式设置根据每个实例。

## <a name="atl-window-traits-templates"></a>ATL 窗口特征模板

ATL 提供了两个窗口特征模板，可用于设置在编译时使用它们的模板参数的默认样式。

|类|描述|
|-----------|-----------------|
|[CWinTraits](../atl/reference/cwintraits-class.md)|当你想要提供默认值，仅当没有其他样式指定在调用时将使用的窗口样式时使用此模板`Create`。 提供在运行的时的优先级在设置的样式的样式编译时间。|
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|当你想要指定必须始终设置为窗口类样式时，请使用此类。 在运行时提供的样式设置在编译时使用按位 OR 运算符的样式相结合。|

除了这些模板，ATL 提供了大量预定义的专用化`CWinTraits`常用组合的窗口样式的模板。 请参阅[CWinTraits](../atl/reference/cwintraits-class.md)参考文档的完整详细信息。

## <a name="custom-window-traits"></a>自定义窗口特征

在不太可能的情况下由 ATL 提供的模板专用之一并不足够并需要创建您自己的特征类，只需创建实现两个静态函数的类：`GetWndStyle`和`GetWndStyleEx`:

[!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]

每个函数将传递某些样式值在运行时它可以用于生成新的样式值。 如果窗口特性类用作 ATL 窗口类的模板参数，传递给这些静态函数的样式值将为任何已作为样式参数传递给[创建](../atl/reference/cwindowimpl-class.md#create)。

## <a name="see-also"></a>请参阅

[窗口类](../atl/atl-window-classes.md)
