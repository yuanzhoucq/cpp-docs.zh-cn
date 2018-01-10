---
title: "与树控件通信 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ef1188c9519e57c8132a2b20fc3b272d6c0ac51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="communicating-with-a-tree-control"></a>与树控件通信
为调用成员函数使用不同的方法[CTreeCtrl](../mfc/reference/ctreectrl-class.md)对象取决于对象的创建方式：  
  
-   如果树控件位于对话框中，请使用您在对话框类中创建的 `CTreeCtrl` 类型的成员变量。  
  
-   如果树控件是子窗口，请使用用于构造对象的 `CTreeCtrl` 对象（或指针）。  
  
-   如果你使用`CTreeView`对象，请使用函数[ctreeview:: Gettreectrl](../mfc/reference/ctreeview-class.md#gettreectrl)若要获取对树控件的引用。 您可以使用此值初始化其他引用或将引用的地址分配给 `CTreeCtrl` 指针。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

