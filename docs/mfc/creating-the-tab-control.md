---
title: "创建选项卡控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
dev_langs: C++
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: db477a8966e7a7ec5368e5ed9e783b466acbf103
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="creating-the-tab-control"></a>创建选项卡控件
选项卡控件的创建方式取决于您是使用控件在对话框中还是在非对话框窗口中创建它。  
  
### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>若要在对话框中直接使用 CTabCtrl  
  
1.  在对话框编辑器中，将选项卡控件添加到对话框模板资源。 指定其控件 ID。  
  
2.  使用[添加成员变量向导](../ide/adding-a-member-variable-visual-cpp.md)若要添加的类型的成员变量[CTabCtrl](../mfc/reference/ctabctrl-class.md)的控件属性。 您可以使用此成员调用 `CTabCtrl` 成员函数。  
  
3.  映射在需要以处理任何选项卡控件通知消息的对话框类的处理程序函数。 有关详细信息，请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。  
  
4.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，设置的样式`CTabCtrl`。  
  
### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>要在非对话框窗口中使用 CTabCtrl  
  
1.  在视图或窗口类中定义控件。  
  
2.  调用控件的[创建](../mfc/reference/ctabctrl-class.md#create)成员函数，可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)中进行，父窗口的[OnCreate](../mfc/reference/cwnd-class.md#oncreate)处理程序函数 （如果您是将控件子类化）。 设置控件的样式。  
  
 后`CTabCtrl`创建对象，你可以设置或清除以下扩展样式：  
  
-   **TCS_EX_FLATSEPARATORS**选项卡控件将绘制选项卡项之间的分隔符。 这仅影响选项卡控件具有扩展样式**TCS_BUTTONS**和**TCS_FLATBUTTONS**样式。 默认情况下，创建与选项卡控件**TCS_FLATBUTTONS**样式设置此扩展样式。  
  
-   **TCS_EX_REGISTERDROP**选项卡控件生成**TCN_GETOBJECT**通知消息来请求放置目标对象时对象拖到选项卡项控件中。  
  
    > [!NOTE]
    >  若要接收**TCN_GETOBJECT**通知，必须初始化 OLE 库通过调用[AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)。  
  
 可以检索和设置，该控件创建后，通过各自调用这些样式[GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle)和[SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle)成员函数。  
  
 例如，设置**TCS_EX_FLATSEPARATORS**与下面的代码行：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]  
  
 清除**TCS_EX_FLATSEPARATORS**样式从`CTabCtrl`对象与下面的代码行：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]  
  
 这将删除显示的按钮之间的分隔符你`CTabCtrl`对象。  
  
## <a name="see-also"></a>另请参阅  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控件](../mfc/controls-mfc.md)

