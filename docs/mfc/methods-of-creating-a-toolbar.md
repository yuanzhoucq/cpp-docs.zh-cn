---
title: "创建工具栏的方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d93f8e43c933e9c8054e798c11754cc48bf54a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="methods-of-creating-a-toolbar"></a>创建工具栏的方法
MFC 提供用于创建工具栏的两个类： [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) （其包装 Windows 公共控件 API）。 `CToolBar`提供的所有功能的工具栏公共控件，并它为你; 处理许多必需的常用控制设置和结构但是，生成可执行文件通常将大于使用创建的`CToolBarCtrl`。  
  
 `CToolBarCtrl`通常产生较小的可执行文件，以及你可能希望使用`CToolBarCtrl`如果你不想要将工具栏集成到 MFC 体系结构。 如果你打算使用`CToolBarCtrl`和将工具栏集成到 MFC 体系结构，你必须采取额外注意将工具栏控制操作传送到 MFC。 此传送不难;但是，它是在使用时是不需要的额外工作`CToolBar`。  
  
 Visual c + + 提供两种方法以利用工具栏公共控件。  
  
-   创建工具栏使用`CToolBar`，然后调用[CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)才能访问`CToolBarCtrl`成员函数。  
  
-   创建工具栏使用[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)的构造函数。  
  
 任何一种方法将可使用工具栏控件的成员函数。 当您调用 `CToolBar::GetToolBarCtrl` 时，它将返回对 `CToolBarCtrl` 对象的引用，以便您可以使用成员函数集。 请参阅[CToolBar](../mfc/reference/ctoolbar-class.md)有关构造和创建工具栏使用信息`CToolBar`。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

