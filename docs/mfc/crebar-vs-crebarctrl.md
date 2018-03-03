---
title: "CReBar vs。CReBarCtrl |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 68cd21e21c14a34122f1b26345fab767728ac6a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crebar-vs-crebarctrl"></a>CReBar vs。CReBarCtrl
MFC 提供了两个类来创建 rebar: [CReBar](../mfc/reference/crebar-class.md)和[CReBarCtrl](../mfc/reference/crebarctrl-class.md) （其包装 Windows 公共控件 API）。 **CReBar**提供所有 rebar 公共控件的功能，和它为你处理的许多所需的常用控制设置和结构。  
  
 `CReBarCtrl` 是 Win32 rebar 控制的包装器类，因此如果您不打算将 rebar 集成到 MFC 体系结构中，则这可能更易于实现。 如果您计划使用 `CReBarCtrl` 并计划将 rebar 集成到 MFC 体系结构中，则必须额外注意将 rebar 控制操作传送到 MFC。 此传送不难;但是，它是在使用时是不需要的额外工作**CReBar**。  
  
 Visual C++ 提供了两种利用 rebar 常用控制的方式。  
  
-   创建 rebar 使用**CReBar**，然后调用[crebar:: Getrebarctrl](../mfc/reference/crebar-class.md#getrebarctrl)才能访问`CReBarCtrl`成员函数。  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl`是一个内联成员函数，将强制转换**这**rebar 对象的指针。 这意味着，函数调用在运行时没有开销。  
  
-   创建 rebar 使用[CReBarCtrl](../mfc/reference/crebarctrl-class.md)的构造函数。  
  
 任一方法都将为您提供对 rebar 控制的成员函数的访问权限。 当您调用 `CReBar::GetReBarCtrl` 时，它将返回对 `CReBarCtrl` 对象的引用，以便您可以使用成员函数集。 请参阅[CReBar](../mfc/reference/crebar-class.md)有关构造和创建 rebar 使用信息**CReBar**。  
  
## <a name="see-also"></a>请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)

