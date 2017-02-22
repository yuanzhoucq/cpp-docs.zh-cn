---
title: "在 Rich Edit 控件中打印 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCtrl 类, 打印"
  - "打印 [MFC], CRichEditCtrl"
  - "Rich Edit 控件, 打印"
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 在 Rich Edit 控件中打印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以了解一个丰富的编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 呈现它的指定设备的输出，如打印机。  也可以指定一 Rich Edit 控件设置其文本的输出设备。  
  
 若要设置一部分丰富的编辑控件内容的特定的设备，可以使用 [FormatRange](../Topic/CRichEditCtrl::FormatRange.md) 成员函数。  [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) 结构对该函数指定文本范围的格式以及目标设备的设备上下文 \(DC\)。  
  
 使用 [DisplayBand](../Topic/CRichEditCtrl::DisplayBand.md) 成员函数，在格式输出设备的文本后，可以将输出发送到设备。  使用 `FormatRange` 和 `DisplayBand`，通过重复，打印的应用程序的丰富的编辑控件的内容可以实现双层。分级 \(出于打印目的是输出的除法成更小的部件。\)  
  
 可以使用 [SetTargetDevice](../Topic/CRichEditCtrl::SetTargetDevice.md) 成员函数中指定了丰富的格式文本编辑控件其的目标设备。  此函数在 WYSIWYG \(所看到位于所捕获\) 格式设置非常有用，但应用程序确定文本使用默认打印机的字体规格而不是屏幕的。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)