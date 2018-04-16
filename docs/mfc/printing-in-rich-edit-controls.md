---
title: "在 Rich Edit 控件中打印 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab8e15e25e2d419bb7c3ac67fc2c6f3453fb03c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="printing-in-rich-edit-controls"></a>在 Rich Edit 控件中打印
你可以判断 rich edit 控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 来呈现为指定的设备，例如打印机其输出。 你还可以指定为其 rich edit 控件输出设备设置其文本的格式。  
  
 若要设置格式的特定设备的 rich edit 控件内容的一部分，你可以使用[FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange)成员函数。 [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911)结构使用此函数使用指定的目标设备的设备上下文 (DC) 以及设置格式的文本范围。  
  
 在设置格式的输出设备的文本之后, 你可以将输出发送到设备使用[DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband)成员函数。 通过重复使用`FormatRange`和`DisplayBand`，应用程序打印 rich edit 控件的内容可以实现条带。 （条带是输出划分为较小的部分以供打印。）  
  
 你可以使用[SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice)成员函数来指定为其 rich edit 控件的目标设备设置其文本的格式。 此函数可用于所见即所得 （所见即所得） 格式，在其中的应用程序中定位文本而不屏幕的使用默认打印机字体规格。  
  
## <a name="see-also"></a>请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)

