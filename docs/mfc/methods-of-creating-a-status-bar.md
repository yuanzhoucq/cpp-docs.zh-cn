---
title: 创建状态栏的方法 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0428bfc906ba6e8a1ecc7bd7c198327e8c31505
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="methods-of-creating-a-status-bar"></a>创建状态栏的方法
MFC 提供用于创建状态栏的两个类： [CStatusBar](../mfc/reference/cstatusbar-class.md)和[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) （其包装 Windows 公共控件 API）。 `CStatusBar` 提供的所有功能的公共控件状态栏，它会自动与交互菜单和工具栏，和它为你; 处理许多必需的常用控制设置和结构但是，生成可执行文件通常将大于使用创建的`CStatusBarCtrl`。  
  
 `CStatusBarCtrl` 通常产生较小的可执行文件，以及你可能希望使用`CStatusBarCtrl`如果你不想要将状态栏集成到 MFC 体系结构。 如果你打算使用`CStatusBarCtrl`和将状态栏集成到 MFC 体系结构，你必须采取额外注意将控制操作传送到 MFC 状态栏。 此传送不难;但是，它是在使用时是不需要的额外工作`CStatusBar`。  
  
 Visual c + + 提供两种方法以利用状态栏公共控件。  
  
-   创建状态栏使用`CStatusBar`，然后调用[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)才能访问`CStatusBarCtrl`成员函数。  
  
-   创建状态栏使用[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)的构造函数。  
  
 任何一种方法将授予你访问状态栏控件的成员函数。 当您调用 `CStatusBar::GetStatusBarCtrl` 时，它将返回对 `CStatusBarCtrl` 对象的引用，以便您可以使用成员函数集。 请参阅[CStatusBar](../mfc/reference/cstatusbar-class.md)有关构造和创建状态栏使用信息`CStatusBar`。  
  
## <a name="see-also"></a>请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

