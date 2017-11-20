---
title: "在 Rich Edit 控件中设置格式的段落 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e65611c915bfdaf5b8a0e03e2fb44804e65f904f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Rich Edit 控件中的段落格式设置
你可以使用 rich edit 控件的成员函数 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 设置段落格式和检索格式设置信息。 段落格式设置特性包括对齐、选项卡、缩进和编号。  
  
 你可以将应用段落格式设置通过使用[SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat)成员函数。 若要确定所选文本格式设置的当前段落，请使用[GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat)成员函数。 [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940)结构使用与这些成员函数，用于指定段落特性。 重要成员之一**PARAFORMAT**是**dwMask**。 在`SetParaFormat`， **dwMask**指定将由此函数调用设置的段落特性。 `GetParaFormat`报告所选内容; 中的第一个段落的特性**dwMask**指定选择中一致的属性。  
  
## <a name="see-also"></a>另请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)

