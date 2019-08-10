---
title: Rich Edit 控件中的段落格式设置
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: 0988e7940c8d8947b86e97a35d71586f8f5c316a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916372"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Rich Edit 控件中的段落格式设置

您可以使用 rich edit 控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 的成员函数设置段落格式, 并检索格式设置信息。 段落格式设置特性包括对齐、选项卡、缩进和编号。

您可以使用[SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat)成员函数应用段落格式设置。 若要确定所选文本的当前段落格式, 请使用[GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat)成员函数。 [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-paraformat)结构与这些成员函数结合使用来指定段落属性。 **PARAFORMAT**的一个重要成员是*dwMask*。 在`SetParaFormat`中, *dwMask*指定将通过此函数调用设置的段落属性。 `GetParaFormat`报告所选内容中第一个段落的属性;*dwMask*指定在整个选定内容中一致的属性。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
