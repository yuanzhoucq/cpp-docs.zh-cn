---
title: 属性表作为向导 |Microsoft 文档
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
ms.openlocfilehash: 634359763f24e02987664fe3de1094e3e7fec64c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="property-sheets-as-wizards"></a>属性表作为向导
向导属性表的关键特征是，“下一步”或“完成”、“后退”和“取消”按钮而不是选项卡提供有导航。 你需要调用[CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode)之前调用[CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal)上要充分利用此功能的属性表对象。  
  
 用户会收到相同[cpropertypage:: Onsetactive](../mfc/reference/cpropertypage-class.md#onsetactive)和[cpropertypage:: Onkillactive](../mfc/reference/cpropertypage-class.md#onkillactive)从一个页面移动到另一页时的通知。 “下一步”和“完成”按钮是手动独占控件；即，这两个按钮一次只显示其中一个。 在第一页上，应启用“下一步”按钮。 如果用户位于最后一页，则应启用“完成”按钮。 这不是由框架自动完成的。 你必须调用[CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons)来实现此目的的最后一页上。  
  
 若要显示所有默认按钮，则必须显示“完成”按钮并移动“下一步”按钮。 然后移动“后退”按钮，以便保留其与“下一步”按钮的相对位置。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [属性表](../mfc/property-sheets-mfc.md)

