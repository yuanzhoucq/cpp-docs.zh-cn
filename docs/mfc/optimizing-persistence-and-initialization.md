---
title: 优化持久性和初始化
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 57b98f7e2e4f9e23175b8b01c2e37ff49c499949
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624000"
---
# <a name="optimizing-persistence-and-initialization"></a>优化持久性和初始化

默认情况下，控件中的持久性和初始化由 `DoPropExchange` 成员函数处理。 在典型的控件中，此函数包含对多个**PX_** 函数（ `PX_Color` 、 `PX_Font` 等）的调用，每个函数对应一个属性。

此方法的优点是 `DoPropExchange` ，单个实现可用于初始化、以二进制格式持久保留，以及用于某些容器使用的所谓的 "属性包" 格式的持久性。 此函数在一个方便的位置提供有关属性及其默认值的所有信息。

但是，这种通用性会降低效率。 **PX_** 函数可以通过多层实现获得灵活性，这些实现本质上比更直接但更灵活的方法更有效。 此外，如果控件将默认值传递到**PX_** 函数，则每次都必须提供默认值，即使在不一定使用默认值的情况下也是如此。 如果生成默认值是重要任务（例如，当从环境属性中获取值时），则在不使用默认值的情况下，会执行额外的不必要的工作。

可以通过重写控件的函数来改善控件的二进制持久性性能 `Serialize` 。 此成员函数的默认实现对函数进行调用 `DoPropExchange` 。 通过重写它，可以提供更直接的二进制持久性实现。 例如，请考虑以下 `DoPropExchange` 函数：

[!code-cpp[NVC_MFC_AxOpt#1](codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

若要提高此控件的二进制持久性的性能，可以重写函数，如下所示 `Serialize` ：

[!code-cpp[NVC_MFC_AxOpt#2](codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

`dwVersion`局部变量可用于检测正在加载或保存的控件持久状态的版本。 您可以使用此变量，而不是调用[CPropExchange：： GetVersion](reference/cpropexchange-class.md#getversion)。

若要以**布尔**值属性的持久格式保存少许空间（并使其与生成的格式兼容 `PX_Bool` ），可以将属性存储为**字节**，如下所示：

[!code-cpp[NVC_MFC_AxOpt#3](codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

请注意，在加载情况下，使用临时变量，然后分配其值，而不是将*m_boolProp*强制转换为**字节**引用。 转换方法只会导致修改一个*m_boolProp*的字节，使剩余的字节保持未初始化状态。

对于同一控件，可以通过重写[COleControl：： OnResetState](reference/colecontrol-class.md#onresetstate)来优化控件的初始化，如下所示：

[!code-cpp[NVC_MFC_AxOpt#4](codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

尽管 `Serialize` 和已被 `OnResetState` 重写，但 `DoPropExchange` 函数应保持不变，因为它仍用于持久保存在属性包格式中。 务必维护所有这三个函数，以确保控件按一致的方式管理其属性，而不考虑容器使用的持久性机制。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件：优化](mfc-activex-controls-optimization.md)
