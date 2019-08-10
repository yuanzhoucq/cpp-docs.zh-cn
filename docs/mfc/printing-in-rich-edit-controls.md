---
title: 在 Rich Edit 控件中打印
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 6ae7212eaa8eed1088a507973c80311f169c7751
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916271"
---
# <a name="printing-in-rich-edit-controls"></a>在 Rich Edit 控件中打印

你可以通知 rich edit 控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 为指定的设备 (例如打印机) 呈现其输出。 你还可以指定富编辑控件为其设置文本格式的输出设备。

若要为特定设备设置丰富编辑控件部分内容的格式, 可以使用[FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange)成员函数。 与此函数一起使用的[FORMATRANGE](/windows/desktop/api/richedit/ns-richedit-formatrange)结构指定要设置格式的文本范围, 以及目标设备的设备上下文 (DC)。

格式化输出设备的文本后, 可以使用[DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband)成员函数将输出发送到设备。 通过重复使用`FormatRange`和`DisplayBand`, 打印丰富编辑控件的内容的应用程序可以实现分级。 (将输出划分为多个较小的部分, 用于打印。)

可以使用[SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice)成员函数指定富编辑控件为其文本设置格式的目标设备。 此函数适用于 WYSIWYG (所见即所得内容) 格式, 其中应用程序使用默认打印机的字体度量值而不是屏幕的来定位文本。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
