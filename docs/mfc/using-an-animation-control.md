---
title: "使用动画控件 | Microsoft Docs"
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
  - "动画控件 [C++]"
  - "CAnimateCtrl 类, 动画控件"
  - "控件 [MFC], 动画"
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用动画控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

animation 控件的典型用法遵循以下模式：  
  
-   创建控件。  如果控件在对话框模板指定的，则该控件在对话框创建时自动创建。\(您应具有对话框类的一个 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) 成员对应于相应的animation控件。\) 或者，可以使用 [创建](../Topic/CAnimateCtrl::Create.md) 成员函数来创建控件作为所有窗口的一个子窗口。  
  
-   加载一 AVI 剪辑到动画控件通过调用成员函数。[打开](../Topic/CAnimateCtrl::Open.md) 如果动画控件对话框中，为此的适合放置在对话框类的函数 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)。  
  
-   通过调用 [播放](../Topic/CAnimateCtrl::Play.md) 成员函数播放剪辑。  如果动画控件对话框中，为此的适合放置在对话框类的函数 **OnInitDialog**。  调用 **播放** 不需要动画的控件是否将 `ACS_AUTOPLAY` 样式。  
  
-   如果要剪辑显示的部分或由帧播放该帧，请使用 `Seek` 成员函数。  若要停止播放的剪辑，请使用 `Stop` 成员函数。  
  
-   如果不立即销毁控件，从内存中移除。通过调用 **关闭** 成员函数。  
  
-   如果animation控件在对话框中，它和 `CAnimateCtrl` 对象将被自动销毁。  否则，您需要确保正确销毁控件和 `CAnimateCtrl` 对象。  销毁控件自动关闭 AVI 剪辑。  
  
## 请参阅  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控件](../mfc/controls-mfc.md)