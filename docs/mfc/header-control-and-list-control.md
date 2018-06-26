---
title: 标头控件和列表控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acee0508243f468f41c645a0cde825ca7c828657
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931589"
---
# <a name="header-control-and-list-control"></a>标题控件和列表控件
在大多数情况下，你将使用的标头控件嵌入在[CListCtrl](../mfc/reference/clistctrl-class.md)或[CListView](../mfc/reference/clistview-class.md)对象。 但是，有必要，如操作数据，排列在行或列，单独标头控件对象的情况[CView](../mfc/reference/cview-class.md)-派生对象。 在这些情况下，你需要更多控制力的外观和嵌入的标头控件的默认行为。  
  
 在想要提供标准标头控件常见的情况下，默认行为，你可能想要使用[CListCtrl](../mfc/reference/clistctrl-class.md)或[CListView](../mfc/reference/clistview-class.md)相反。 使用`CListCtrl`时所需的默认标头控件，嵌入在列表视图公共控件的功能。 使用[CListView](../mfc/reference/clistview-class.md)如果想在视图对象中嵌入的默认标头控件的功能。  
  
> [!NOTE]
>  如果使用创建列表视图控件后，这些控件将只包含一个内置的标头控件**LVS_REPORT**样式。  
  
 在大多数情况下，可以通过更改包含列表视图控件的样式修改嵌入的标头控件的外观。 此外，可以通过父列表视图控件的成员函数获取标头控件有关的信息。 但是，用于完全控制和访问的特性和样式的内嵌的标题控件中，建议获取指向标头控件对象的指针。  
  
 可以从访问嵌入的标头控件对象`CListCtrl`或`CListView`通过各自类调用`GetHeaderCtrl`成员函数。 下面的代码演示此：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [标头控件使用图像列表](../mfc/using-image-lists-with-header-controls.md)  
  
## <a name="see-also"></a>请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)

