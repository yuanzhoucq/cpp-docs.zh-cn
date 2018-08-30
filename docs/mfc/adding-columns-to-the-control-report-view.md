---
title: 将列添加到控件 （报表视图） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3e81de52856d67760ffe58f29e4c39ac79213c4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221939"
---
# <a name="adding-columns-to-the-control-report-view"></a>向控件添加列（报表视图）
> [!NOTE]
>  以下过程适用于[CListView](../mfc/reference/clistview-class.md)或[CListCtrl](../mfc/reference/clistctrl-class.md)对象。  
  
 当列表控件位于报表视图中时，将显示列，提供组织每个列表控件项的各个子项的方式。 此组织是通过列表控件的列与列表控件项的关联子项之间的一一对应来实现的。 子项的详细信息，请参阅[将项添加到该控件](../mfc/adding-items-to-the-control.md)。 Windows 95 和 Windows 98 资源管理器的“细节”视图中提供了报表视图中列表控件的示例。 第一列将列出文件夹、文件图标和标签。 其他列将列出文件大小、文件类型、上次修改日期等。  
  
 即使列可以随时添加到列表控件，列也是仅当控件启用 `LVS_REPORT` 样式位时才可见。  
  
 每个列都有一个关联的标头项 (请参阅[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 标记列并允许用户调整列大小的对象。  
  
 如果列表控件支持报表视图，则需要为列表控件项的每个可能的子项添加一列。 准备添加一个列[LV_COLUMN](/windows/desktop/api/commctrl/ns-commctrl-taglvcolumna)结构，然后再进行调用[InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn)。 在添加必需的列（有时称为“标头项”）之后，您可使用属于标头控件的成员函数和样式对其进行重新排序。 有关详细信息，请参阅[标头控件中对项进行排序](../mfc/ordering-items-in-the-header-control.md)。  
  
> [!NOTE]
>  如果列表控件创建与**LVS_NOCOLUMNHEADER**样式，将列插入的任何尝试都将被忽略。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

