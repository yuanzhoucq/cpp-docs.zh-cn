---
title: "创建选项卡控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TCS_EX_REGISTERDROP"
  - "TCS_EX_FLATSEPARATORS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabCtrl 类, 创建"
  - "选项卡控件, 创建"
  - "TCS_EX_FLATSEPARATORS 扩展样式"
  - "TCS_EX_REGISTERDROP 扩展样式"
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建选项卡控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如何创建选项卡控件是根据您在对话框中使用控件还是在无对话框窗口中创建它。。  
  
### 在对话框直接使用 CTabCtrl  
  
1.  在对话框编辑器中，将添加选项卡控件添加到对话框模板资源。  指定其控件的ID .  
  
2.  使用 [添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)添加带有控件属性[CTabCtrl](../mfc/reference/ctabctrl-class.md) 类型的成员变量。  可以使用此成员调用 `CTabCtrl` 成员函数。  
  
3.  需要处理任何选项卡控件通知消息的对话框类的映射处理函数。  有关更多信息，请参见[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。  
  
4.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)，设置 `CTabCtrl`的样式。  
  
### 在非对话框窗口使用 CTabCtrl  
  
1.  在视图或窗口类中定义控件。  
  
2.  \(如果要把控件子类化\)，请在父窗口[OnCreate](../Topic/CWnd::OnCreate.md) 处理程序函数调用时，调用控件的[Create](../Topic/CTabCtrl::Create.md) 成员函数，在 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)中。  设置控件的样式。  
  
 在创建 `CTabCtrl` 对象之后，可以设置或清除以下扩展样式：  
  
-   **TCS\_EX\_FLATSEPARATORS** 选项卡控件绘制选项卡项之间的分隔符。  此扩展样式仅影响具有 **TCS\_BUTTONS** 和 **TCS\_FLATBUTTONS** 样式的选项卡控件。  默认情况下，创建 **TCS\_FLATBUTTONS** 样式的选项卡控件来设置此扩展样式。  
  
-   **TCS\_EX\_REGISTERDROP** 选项卡控件生成 **TCN\_GETOBJECT**通知消息，当一个对象被拖在选项卡中的项目控件时，请求放置目标对象。  
  
    > [!NOTE]
    >  希望接收 **TCN\_GETOBJECT** 通知，必须初始化调用[AfxOleInit](../Topic/AfxOleInit.md)的 OLE 库。  
  
 创建控件后，这些样式可以被检索和设置，调用[GetExtendedStyle](../Topic/CTabCtrl::GetExtendedStyle.md) [SetExtendedStyle](../Topic/CTabCtrl::SetExtendedStyle.md) 成员函数。  
  
 例如，按下列代码行的样式设置**TCS\_EX\_FLATSEPARATORS**：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/CPP/creating-the-tab-control_1.cpp)]  
  
 从下列代码行的 `CTabCtrl`对象中清除**TCS\_EX\_FLATSEPARATORS** 样式：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/CPP/creating-the-tab-control_2.cpp)]  
  
 这将删除位于 `CTabCtrl` 对象的按钮之间的分隔符。  
  
## 请参阅  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控件](../mfc/controls-mfc.md)