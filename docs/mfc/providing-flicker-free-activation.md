---
title: 提供无闪烁激活 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd9f780472b8256f6d8332ecbde08138d85c8ebd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378315"
---
# <a name="providing-flicker-free-activation"></a>提供无闪烁激活

如果控件绘制自身相同处于非活动和活动状态 （和不使用无窗口激活），则可以消除绘制操作和进行非活动状态之间转换时，通常会发生随附 visual 闪烁和活动状态。 若要执行此操作，包括**noFlickerActivate**标志的标志返回的集中[colecontrol:: Getcontrolflags](../mfc/reference/colecontrol-class.md#getcontrolflags)。 例如：

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

如果你选择自动生成代码以包括此标志**无闪烁激活**选项卡上[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)页面时使用 MFC ActiveX 控件向导创建您的控件。

如果使用无窗口激活，则此优化不起作用。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)

