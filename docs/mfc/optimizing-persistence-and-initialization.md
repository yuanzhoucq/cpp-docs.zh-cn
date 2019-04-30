---
title: 优化持久性和初始化
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 294d9c43f5f767329c04932c574485d7dca704e9
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342133"
---
# <a name="optimizing-persistence-and-initialization"></a>优化持久性和初始化

默认情况下，持久性和初始化的控件中处理通过`DoPropExchange`成员函数。 在典型的控件中，此函数包含对多个调用**PX_** 函数 (`PX_Color`， `PX_Font`，依此类推)，一个用于每个属性。

此方法具有优势，单个`DoPropExchange`初始化、 以二进制格式暂留和暂留中使用一些容器的所谓"属性的包"格式，可以使用实现。 此函数提供了有关的属性和其默认值在一个方便的位置中的所有信息。

但是，这种通用性的代价是效率。 **PX_** 函数可获取通过本质上是要少的多层实现其灵活性比更直接，但不太灵活方法有效。 此外，如果控件将传递到的默认值**PX_** 函数，每次，即使在有些情况下，默认值一定不能使用必须提供默认值。 如果生成的默认值是非常重要的任务 （例如，当从一个环境属性获取值），则额外，在不使用默认值的情况下进行不必要的工作。

可以通过重写控件的提高控件的二进制暂留性能`Serialize`函数。 此成员函数的默认实现将调用你`DoPropExchange`函数。 通过重写它，您可以为二进制持久性更直接的实现。 例如，考虑这`DoPropExchange`函数：

[!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

若要提高此控件的二进制暂留的性能，可以重写`Serialize`函数，如下所示：

[!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

`dwVersion`本地变量可用于检测待加载或保存的控件的持久状态的版本。 您可以使用此变量，而不是调用[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)。

若要保存小的空间中的持久性格式**BOOL**属性 (而将其与生成的格式兼容`PX_Bool`)，可以存储属性作为**字节**，按如下所示：

[!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

请注意，在负载情况下，使用临时变量，然后分配它的值，而不是强制转换*m_boolProp*到**字节**引用。 类型转换技术将导致仅使用一个字节的*m_boolProp*被修改，保留未初始化的剩余字节数。

对于同一个控件，可以通过重写优化控件的初始化[COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) ，如下所示：

[!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

尽管`Serialize`并`OnResetState`已重写`DoPropExchange`函数应保持不变因为仍用于持久性的属性包格式。 请务必维护所有这三个函数以确保该控件一致地管理其属性而不考虑哪种持久性机制容器使用。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)
