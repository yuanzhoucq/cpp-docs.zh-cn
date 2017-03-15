---
title: "属性表作为向导 | Microsoft Docs"
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
  - "属性表, 作为向导"
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 属性表作为向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

键通常向导属性表是接下来提供导航或完成、返回和取消按钮而非选项卡。  需要在调用对象的属性表 [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md) 利用此功能称为 [CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)。  
  
 用户收到相同和 [CPropertyPage::OnSetActive](../Topic/CPropertyPage::OnSetActive.md) [CPropertyPage::OnKillActive](../Topic/CPropertyPage::OnKillActive.md) 通知，当焦点从一个页面到另一页。  然后和完成该按钮是互斥的控件；即它们中只有一个一次将显示。  在第一页，应启用下按钮。  如果用户是在一页，应启用按钮完成。  这不由框架自动完成。  必须对的 [CPropertySheet::SetWizardButton](../Topic/CPropertySheet::SetWizardButtons.md) 一页来实现这一点。  
  
 显示所有默认按钮，则糊状 food 软显示完成按钮并移动下按钮。  然后移动"后退"按钮，以便为下按钮的相对位置保持。  对于更多说明，为 Q143210 请搜索知识库文章。  可以在 MSDN Library 中查找知识库文章。  
  
## 示例  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/CPP/property-sheets-as-wizards_1.cpp)]  
  
## 请参阅  
 [属性表](../mfc/property-sheets-mfc.md)