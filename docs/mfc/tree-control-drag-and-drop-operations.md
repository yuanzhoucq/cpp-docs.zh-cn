---
title: 树控件拖放操作 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73aa47a2d888c88dd58d114dd4f5ca9a3f086cd3
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956247"
---
# <a name="tree-control-drag-and-drop-operations"></a>树控件拖放操作
树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 发送通知，当用户开始拖动项。 控件将发送[TVN_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504)通知消息，当用户开始拖动项时鼠标左键和[TVN_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509)通知消息，当用户开始拖动与右侧的按钮。 你可以防止树控件发送这些通知通过为树控件提供 TVS_DISABLEDRAGDROP 样式。  
  
 获取该图像显示在拖动操作期间，通过调用[CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage)成员函数。 树控件将基于所拖动的项标签创建一个拖动位图。 然后树控件创建图像列表，将位图添加到其中，并返回一个指向[CImageList](../mfc/reference/cimagelist-class.md)对象。  
  
 必须提供实际拖动项的代码。 这通常涉及使用图像列表函数的拖动功能和处理[WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616)和[WM_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) (或[WM_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243))在拖动操作开始之后发送的消息。 有关图像列表函数的详细信息，请参阅[CImageList](../mfc/reference/cimagelist-class.md)中*MFC 参考*和[图像列表](http://msdn.microsoft.com/library/windows/desktop/bb761389)Windows SDK 中。 有关拖动树控件项的详细信息，请参阅[拖动树视图项](http://msdn.microsoft.com/library/windows/desktop/bb760017)，还在[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
 如果树控件中的项是拖放操作的目标，则需要了解鼠标光标何时指向了目标项。 你可以通过调用找出[HitTest](../mfc/reference/ctreectrl-class.md#hittest)成员函数。 指定一个点和整数或的地址[TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448)结构，它包含鼠标光标的当前坐标。 当函数返回时，该整数或结构包含一个指示与树控件相关的鼠标光标的位置的标志。 如果光标在树控件中的某个项的上方，则该结构还包含该项的句柄。  
  
 你可以指示某个项是拖放操作的目标，通过调用[SetItem](../mfc/reference/ctreectrl-class.md#setitem)成员函数以将状态设置为`TVIS_DROPHILITED`值。 使用用于指示拖放目标的样式绘制具有此状态的项。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

