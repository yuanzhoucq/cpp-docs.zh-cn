---
title: "选项卡和选项卡控件特性 | Microsoft Docs"
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
  - "特性 [C++], 参考主题"
  - "CTabCtrl 类, 选项卡控件特性"
  - "选项卡控件, 特性"
  - "选项卡"
  - "选项卡, 特性"
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 选项卡和选项卡控件特性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可对外观严重的组成选项卡控件的选项卡控件和行为 \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\)。  每个选项卡都可以具有标签、图标、项状态和应用程序定义的 32 位值与其关联。  对于每个选项卡，可以显示图标，标签或两个。  
  
 此外，所有选项卡项可以有三种可能的状态：按未压缩，或突出显示。  此状态能通过修改现有选项卡项只设置。  若要修改现有选项卡项，请检索它的调用。[GetItem](../Topic/CTabCtrl::GetItem.md)，修改 `TCITEM` 结构 \(具体而言 **dwState** 和一个 **dwStateMask** 数据成员\)，然后返回的调用中已修改的 `TCITEM` 结构设置为 [SetItem](../Topic/CTabCtrl::SetItem.md)。  如果需要清除项状态 `CTabCtrl` 中的所有选项卡项对象，调用 [DeselectAll](../Topic/CTabCtrl::DeselectAll.md)。  此函数仅重置所有选项卡项或全部项的状态，但当前选定的文件。  
  
 下面代码清除状态所有选项卡项来修改第三项的状态：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/CPP/tabs-and-tab-control-attributes_1.cpp)]  
  
 有关选项卡特性的更多信息，请参见" [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [选项卡以及选项卡特性](http://msdn.microsoft.com/library/windows/desktop/bb760550)。  有关向添加选项卡的更多信息向选项卡控件后，请参见 [添加选项卡向选项卡控件](../mfc/adding-tabs-to-a-tab-control.md) 本主题。  
  
## 请参阅  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控件](../mfc/controls-mfc.md)