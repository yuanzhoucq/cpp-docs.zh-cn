---
title: "在 CStatusBarCtrl 对象中使用工具提示 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf522d17d8abfc4b8dbf53baa24255ab23cfa621
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>在 CStatusBarCtrl 对象中使用工具提示
若要启用状态栏控件的工具提示，请创建`CStatusBarCtrl`对象**SBT_TOOLTIPS**样式。  
  
> [!NOTE]
>  如果要使用 `CStatusBar` 对象实现状态栏，请使用 `CStatusBar::CreateEx` 函数。 它允许你指定的嵌入其他样式**CStatusBarCtrl**对象。  
  
 一次`CStatusBarCtrl`成功创建对象，请使用[cstatusbarctrl:: Settiptext](../mfc/reference/cstatusbarctrl-class.md#settiptext)和[cstatusbarctrl:: Gettiptext](../mfc/reference/cstatusbarctrl-class.md#gettiptext)设置并检索特定窗格的提示文本。  
  
 设置工具提示后，仅当部件具有图标且没有文本，或所有文本无法在部件内显示时才显示工具提示。 简单模式中不支持工具提示。  
  
## <a name="see-also"></a>请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

