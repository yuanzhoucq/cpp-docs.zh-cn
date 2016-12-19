---
title: "使用树控件 | Microsoft Docs"
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
  - "CTreeCtrl 类, using"
  - "树控件, 关于树控件"
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用树控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 的典型用法遵循以下模式：  
  
-   创建控件。  如果控件在对话框模板指定或，如果您使用 `CTreeView`，则用于创建自动，则对话框或视图时创建。  如果想要创建树控件用作子窗口其他窗口，请使用 [创建](../Topic/CTreeCtrl::Create.md) 成员函数。  
  
-   如果希望控件树使用图像，通过调用 [SetImageList](../Topic/CTreeCtrl::SetImageList.md)设置图像列表。  通过调用 [SetIndent](../Topic/CTreeCtrl::SetIndent.md)还更改缩进。  优秀时执行此操作，[OnInitDialog](../Topic/CDialog::OnInitDialog.md) \(用于在对话框的控件\) 或 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) \(对于视图\)。  
  
-   将数据放入控件通过调用一次 `CTreeCtrl` [InsertItem](../Topic/CTreeCtrl::InsertItem.md) 函数的每个数据项。  `InsertItem` 返回一个句柄到可以使用后面引用它的项，例如，在添加子项时。  一个好时机初始化数据在 `OnInitDialog` \(用于在对话框的控件\) 或 `OnInitialUpdate` \(对于视图\)。  
  
-   当用户与控件交互，将发送的不同通知消息。  可以函数指定处理要处理通过将控制窗口的消息映射的 **ON\_NOTIFY\_REFLECT** 宏或通过添加 `ON_NOTIFY` 宏。父窗口的消息映射的每一条消息。  列表后的通知。可以参见 [树控件通知消息](../mfc/tree-control-notification-messages.md) 本主题。  
  
-   调用的各种集合成员函数设置控件的值。  更改可包括将缩进并更改文本、图像或数据相关的项。  
  
-   使用捕获各函数检查控件的内容。  还可以遍历控件树的内容与允许检索句柄到父、指定项的子项和同级的函数。  甚至可以排序特定节点的子级。  
  
-   当您用控件时，请确保正确销毁它。  如果该树控件在对话框或，则为视图，将自动销毁它和 `CTreeCtrl` 对象。  否则，您需要确保正确销毁控件和 `CTreeCtrl` 对象。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)