---
title: "将控件添加到属性表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2acbbed1a253a502aea8b19af6fd16ddb343e3ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-controls-to-a-property-sheet"></a>将控件添加到属性表
默认情况下，属性表将为属性页、选项卡索引和“确定”、“取消”和“应用”按钮分配窗口区域。 （无模式的属性表没有“确定”、“取消”和“应用”按钮。）您可以将其他控件添加到属性表中。 例如，您可以在属性页区域右侧添加预览窗口，以便为用户显示对外部对象应用当前设置的效果。  
  
 可以在 `OnCreate` 处理程序中向属性表对话框添加控件。 容纳附加控件通常需要扩展属性表对话框的大小。 调用基类后**cpropertysheet:: Oncreate**，调用[GetWindowRect](../mfc/reference/cwnd-class.md#getwindowrect)若要获取的宽度和当前分配的属性表窗口的高度，扩展矩形的尺寸，并调用[MoveWindow](../mfc/reference/cwnd-class.md#movewindow)若要更改的属性表窗口的大小。  
  
## <a name="see-also"></a>请参阅  
 [属性表](../mfc/property-sheets-mfc.md)   
 [CPropertyPage 类](../mfc/reference/cpropertypage-class.md)   
 [CPropertySheet 类](../mfc/reference/cpropertysheet-class.md)
