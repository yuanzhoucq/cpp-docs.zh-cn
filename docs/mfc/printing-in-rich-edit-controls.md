---
title: 在 Rich Edit 控件中打印
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: f275078fbef9026363305bb714da3a2af333c91f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619823"
---
# <a name="printing-in-rich-edit-controls"></a>在 Rich Edit 控件中打印

你可以通知 rich edit 控件（[CRichEditCtrl](reference/cricheditctrl-class.md)）为指定的设备（例如打印机）呈现其输出。 你还可以指定富编辑控件为其设置文本格式的输出设备。

若要为特定设备设置丰富编辑控件部分内容的格式，可以使用[FormatRange](reference/cricheditctrl-class.md#formatrange)成员函数。 与此函数一起使用的[FORMATRANGE](/windows/win32/api/richedit/ns-richedit-formatrange)结构指定要设置格式的文本范围，以及目标设备的设备上下文（DC）。

格式化输出设备的文本后，可以使用[DisplayBand](reference/cricheditctrl-class.md#displayband)成员函数将输出发送到设备。 通过重复使用 `FormatRange` 和 `DisplayBand` ，打印丰富编辑控件的内容的应用程序可以实现分级。 （将输出划分为多个较小的部分，用于打印。）

可以使用[SetTargetDevice](reference/cricheditctrl-class.md#settargetdevice)成员函数指定富编辑控件为其文本设置格式的目标设备。 此函数适用于 WYSIWYG （所见即所得内容）格式，其中应用程序使用默认打印机的字体度量值而不是屏幕的来定位文本。

## <a name="see-also"></a>另请参阅

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控件](controls-mfc.md)
