---
title: 优化持久性和初始化 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e528ea7901518112c255eefbfb1e674fddee04e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355655"
---
# <a name="optimizing-persistence-and-initialization"></a>优化持久性和初始化
默认情况下，持久性和初始化的控件中处理通过`DoPropExchange`成员函数。 在典型的控件中，该函数包含到多个调用**PX_** 函数 (`PX_Color`， `PX_Font`，依次类推)，一个用于每个属性。  
  
 此方法具有优势，单个`DoPropExchange`可以用于实现，用于初始化、 持久性采用二进制格式，以及为采用由一些容器使用的所谓的"属性的包"格式的暂留。 此一个函数提供了有关的属性和及其默认值以一个方便的位置的所有信息。  
  
 但是，此一般性会降低效率。 **PX_** 函数获取通过本质上是不太多层实现其灵活性高效相比更直接，但不太灵活的方法。 此外，如果控件将传递到的默认值**PX_** 函数，每次，即使在环境下的默认值一定不能使用时必须提供默认值。 如果生成的默认值为普通的任务 （例如，从环境属性获取值时），则额外，在不使用默认值的位置的情况下进行不必要的工作。  
  
 你可以通过重写控件的提高控件的二进制暂留性能`Serialize`函数。 此成员函数的默认实现将调用你`DoPropExchange`函数。 通过重写它，你可以提供更直接为二进制持久性的实现。 例如，考虑这`DoPropExchange`函数：  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]  
  
 若要提高此控件的二进制持久性的性能，可以重写`Serialize`函数，如下所示：  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]  
  
 `dwVersion`局部变量可以用于检测正在加载或保存的控件的持久状态的版本。 你可以使用此变量，而不是调用[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)。  
  
 在的持久性格式中节省少量空间**BOOL**属性 (需要与生成的格式兼容和`PX_Bool`)，你可以存储属性作为**字节**、，如下所示：  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]  
  
 请注意，在负载情况下，使用临时变量，然后分配其值，而不是强制转换`m_boolProp`到**字节**引用。 强制转换方法将导致仅使用一个字节的`m_boolProp`被修改，使其余的字节未初始化的。  
  
 对于相同的控件，你可以通过重写优化控件的初始化[COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) ，如下所示：  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]  
  
 尽管`Serialize`和`OnResetState`已被重写，`DoPropExchange`函数应保持不变因为它仍将用于保留结果中的属性包格式。 请务必保留所有这三个函数以确保控件一致地管理其属性而不考虑哪种持久性机制容器使用。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)

