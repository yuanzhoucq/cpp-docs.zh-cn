---
title: Rich Edit 控件中的断 |Microsoft Docs
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
ms.openlocfilehash: f012897d968d108cb366126fc38992ff1dd11d0a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424607"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Rich Edit 控件中的断字

Rich edit 控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 调用一个名为"断词过程"函数来查找单词之间的分页符并确定它可以换行的位置。 该控件在执行自动换行运算以及处理 Ctrl+向左键和 Ctrl+向右键组合键时使用此信息。 应用程序可将消息发送到 Rich Edit 控件，以便替换默认的断词过程、检索断词信息以及确定给定字符所在的行。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

