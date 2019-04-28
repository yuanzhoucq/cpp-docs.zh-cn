---
title: Rich Edit 控件中的段落格式设置
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: baee4863bee9b96e7a850e70b8f13388f69b41cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218827"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Rich Edit 控件中的段落格式设置

可以使用格式文本编辑控件的成员函数 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 设置段落格式和检索格式设置信息。 段落格式设置特性包括对齐、选项卡、缩进和编号。

您可以应用段落格式设置通过使用[SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat)成员函数。 若要确定设置所选文本的格式将当前段落，请使用[GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat)成员函数。 [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-_paraformat)结构使用与这些成员函数，用于指定段落特性。 重要成员之一**PARAFORMAT**是*dwMask*。 在中`SetParaFormat`， *dwMask*指定将由此函数调用设置的段落特性。 `GetParaFormat` 报告中所选内容; 第一个段落的属性*dwMask*指定选择中一致的属性。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
