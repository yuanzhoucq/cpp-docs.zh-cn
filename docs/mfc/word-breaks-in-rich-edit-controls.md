---
title: Rich Edit 控件中的断 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 373a30ed4a327cff99cb3cfce873707314608b57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382955"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Rich Edit 控件中的断字
Rich edit 控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 调用一个名为"断词过程"函数查找单词之间的分页符并确定它可以在其中换行。 该控件在执行自动换行运算以及处理 Ctrl+向左键和 Ctrl+向右键组合键时使用此信息。 应用程序可将消息发送到 Rich Edit 控件，以便替换默认的断词过程、检索断词信息以及确定给定字符所在的行。  
  
## <a name="see-also"></a>请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)

