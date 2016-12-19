---
title: "处理应用按钮 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "属性表中的应用按钮"
  - "属性表，“应用”按钮"
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 处理应用按钮
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

属性表不存在标准对话框的功能：它们允许用户关闭应用更改。属性表之前完成。  使用应用按钮，这样做。  本文讨论可以使用适当实现此功能的方法。  
  
 当用户单击"确定"以关闭对话框时，模式对话框通常应用设置到外部对象。  上述情况同样适用于属性表：当用户单击"确定"则在属性表中的新设置生效。  
  
 但是，您可能要让用户保存设置，而不必关闭属性表对话框。  这是应用按钮的功能。  应用按钮应用所有的当前设置属性页对外部对象，而应用当前有效的页面仅当前设置相对。  
  
 默认情况下，应用按钮始终禁用。  必须编写代码使应用按钮在适当的时间，因此，您必须编写代码实现功能的效果，如下所述。  
  
 如果不希望向用户提供功能应用，移除应用按钮并不是必需的。  可以将其禁用，在使用标准属性表支持有窗口的未来版本的应用程序中常见。  
  
 报告页面根据修改和启用应用按钮，请调用 **CPropertyPage::SetModified\( TRUE \)**。  如果任何一页修改报告，应用按钮都保持启用，不管 \+ 是否修改了当前活动的页。  
  
 应调用 [CPropertyPage::SetModified](../Topic/CPropertyPage::SetModified.md)，只要用户更改中的任何设置。  一种方式是检测用户何时更改页中的设置要实施更改每个通知的处理程序在属性页的控件，例如 **EN\_CHANGE** 或 **BN\_CLICKED**。  
  
 若要实现应用按钮效果，属性表必须调用其所有者，或其他外部对象在应用程序，当前设置应用在属性页。  同时，属性表应当通过调用将其应用于对象的外部修改的所有页来禁用应用的 **CPropertyPage::SetModified\( FALSE \)** 按钮。  
  
 有关此过程的示例，请参见 MFC 泛型示例 [PROPDLG](../top/visual-cpp-samples.md)。  
  
## 请参阅  
 [属性表](../mfc/property-sheets-mfc.md)