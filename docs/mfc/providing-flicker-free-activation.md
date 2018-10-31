---
title: 提供无闪烁激活
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
ms.openlocfilehash: d979a6f633926bed1ad59de86829b9ac27b0d0cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438137"
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

