---
title: 进度控件的设置 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26afdcb58a64f2d2042596349acc4496aa530468
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="settings-for-the-progress-control"></a>进度控件的设置
进度控件的基本设置 ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) 的范围和当前的位置。 范围表示该操作的整个持续时间。 当前的位置表示你的应用程序已完成该操作的进度。 对该区域或位置的任何更改导致进度控件重绘自己。  
  
 默认情况下，此范围被设置为 0-100 和的初始位置设置为 0。 若要检索进度控件的当前区域设置，请使用[GetRange](../mfc/reference/cprogressctrl-class.md#getrange)成员函数。 若要更改范围，使用[SetRange](../mfc/reference/cprogressctrl-class.md#setrange)成员函数。  
  
 若要设置的位置，请使用[SetPos](../mfc/reference/cprogressctrl-class.md#setpos)。 若要检索当前的位置，而不指定新值，使用[GetPos](../mfc/reference/cprogressctrl-class.md#getpos)。 例如，你可能想要只是查询当前操作的状态。  
  
 若要单步执行进度控件的当前位置，使用[StepIt](../mfc/reference/cprogressctrl-class.md#stepit)。 若要设置的每个步骤量，请使用[SetStep](../mfc/reference/cprogressctrl-class.md#setstep)  
  
## <a name="see-also"></a>请参阅  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [控件](../mfc/controls-mfc.md)

