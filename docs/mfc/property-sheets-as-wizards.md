---
title: 属性表作为向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73b6b0462012fc54b3bd6f2cb22422f5b1431288
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374205"
---
# <a name="property-sheets-as-wizards"></a>属性表作为向导

向导属性表的关键特征是，“下一步”或“完成”、“后退”和“取消”按钮而不是选项卡提供有导航。 您需要调用[CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode)之前，调用[cpropertysheet:: Domodal](../mfc/reference/cpropertysheet-class.md#domodal)上属性表对象才能利用此功能。

用户会收到相同[cpropertypage:: Onsetactive](../mfc/reference/cpropertypage-class.md#onsetactive)并[cpropertypage:: Onkillactive](../mfc/reference/cpropertypage-class.md#onkillactive)从一页移到另一个页面时的通知。 “下一步”和“完成”按钮是手动独占控件；即，这两个按钮一次只显示其中一个。 在第一页上，应启用“下一步”按钮。 如果用户位于最后一页，则应启用“完成”按钮。 这不是由框架自动完成的。 您必须调用[CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons)来实现此目的的最后一页。

若要显示所有默认按钮，则必须显示“完成”按钮并移动“下一步”按钮。 然后移动“后退”按钮，以便保留其与“下一步”按钮的相对位置。

## <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]

## <a name="see-also"></a>请参阅

[属性表](../mfc/property-sheets-mfc.md)

