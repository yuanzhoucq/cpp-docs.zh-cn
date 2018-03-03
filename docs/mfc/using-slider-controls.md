---
title: "使用滑块控件 |Microsoft 文档"
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
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4fdab6a7fae25845da81ee7263e045e50951f557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-slider-controls"></a>使用滑块控件
滑块控件的典型用法遵循以下模式：  
  
-   创建滑块控件。 如果滑块控件是在对话框模板中指定的，则在创建对话框时自动进行创建。 (你应具有[CSliderCtrl](../mfc/reference/csliderctrl-class.md)对应于滑块控件的对话框类中的成员。)或者，可以使用[创建](../mfc/reference/csliderctrl-class.md#create)成员函数来创建控件用作子窗口的任何窗口。  
  
-   调用各种 Set 成员函数来设置滑块控件的值。 可进行的更改包括设置滑块的最小和最大位置、绘制刻度线、设置选择范围以及重新定位滑块。 有关控件在对话框中，执行此操作的好时机是在对话框的[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函数。  
  
-   当用户与该控件交互时，将发送各种通知消息。 通过调用提取该控件中的滑块值[GetPos](../mfc/reference/csliderctrl-class.md#getpos)成员函数。  
  
-   在使用完该控件之后，您需要确保将其正确地销毁。 如果滑块控件在对话框中，将自动销毁该控件和 `CSliderCtrl` 对象。 否则，您需要确保正确地销毁控件和 `CSliderCtrl` 对象。  
  
## <a name="see-also"></a>请参阅  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控件](../mfc/controls-mfc.md)

