---
title: "属性表作为向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 65aedc5dbeb8a740d5713983f66eefe693864937
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="property-sheets-as-wizards"></a>属性表作为向导
向导属性表的关键特征是，“下一步”或“完成”、“后退”和“取消”按钮而不是选项卡提供有导航。 你需要调用[CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode)之前调用[CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal)上要充分利用此功能的属性表对象。  
  
 用户会收到相同[cpropertypage:: Onsetactive](../mfc/reference/cpropertypage-class.md#onsetactive)和[cpropertypage:: Onkillactive](../mfc/reference/cpropertypage-class.md#onkillactive)从一个页面移动到另一页时的通知。 “下一步”和“完成”按钮是手动独占控件；即，这两个按钮一次只显示其中一个。 在第一页上，应启用“下一步”按钮。 如果用户位于最后一页，则应启用“完成”按钮。 这不是由框架自动完成的。 你必须调用[CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons)来实现此目的的最后一页上。  
  
 若要显示所有默认按钮，则必须显示“完成”按钮并移动“下一步”按钮。 然后移动“后退”按钮，以便保留其与“下一步”按钮的相对位置。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [属性表](../mfc/property-sheets-mfc.md)

