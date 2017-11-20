---
title: "属性表和 MFC 中的属性页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 93288308f78d719c4b2cad60ac4a95a607726f4f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>MFC 中的属性表和属性页
属性表，也称为选项卡对话框中，是一个包含属性页的对话框。 每个属性页基于对话框模板资源，并包含控件。 它被括在页面上在顶部的选项卡。 选项卡命名属性页，并指示其用途。 用户单击要选择一组控件的属性表中的选项卡。  
  
 使用页面的属性表中将控件分组到有意义的集。 包含的属性表通常具有其自己的多个控件。 这些应用于所有页面。  
  
 属性表基于类[CPropertySheet](../mfc/reference/cpropertysheet-class.md)。 属性页都基于类[CPropertyPage](../mfc/reference/cpropertypage-class.md)。  
  
 属性表是对话框的对象的一种特殊的通常用于修改某些外部对象，例如视图中的当前选择的属性。 属性表有三个主要部分： 包含的对话框中，一个或多个属性页，一次只显示的一个和在用户单击以选择该页面的每一页顶部的选项卡。 属性表可用于具有多个相似的组的设置或更改的选项的情况。 属性表中一种易于理解的方式的组信息。  
  
> [!NOTE]
>  当你尝试通过使用显示属性表`CPropertySheet::DoModal`，系统可能会产生首次异常。 由于系统尝试更改，则会发生此异常[窗口样式](../mfc/reference/styles-used-by-mfc.md#window-styles)之前创建对象的对象。 有关此异常，以及如何避免它或处理它的详细信息，请参阅[CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal)。  
  
## <a name="see-also"></a>另请参阅  
 [属性表](../mfc/property-sheets-mfc.md)

