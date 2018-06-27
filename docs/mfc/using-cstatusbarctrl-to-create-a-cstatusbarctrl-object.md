---
title: 使用 CStatusBarCtrl 创建 CStatusBarCtrl 对象 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb378bba1505f8bbc3739c070d52abe9ef4f8afc
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953819"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>使用 CStatusBarCtrl 创建 CStatusBarCtrl 对象
下面是一个示例的一个典型用途[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### <a name="to-use-a-status-bar-control-with-parts"></a>若要使用的部件的状态栏控件  
  
1.  构造 `CStatusBarCtrl` 对象。  
  
2.  调用[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)如果你想要设置状态栏控件的最小高度的绘图区域。  
  
3.  调用[SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor)设置状态栏控件的背景色。  
  
4.  调用[SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts)在状态栏控件和每个部分的右边缘的坐标中设置的部分数。  
  
5.  调用[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)以设置状态栏控件给定部分中的文本。 消息将使已更改，从而导致该控件在下一步收到 WM_PAINT 消息时显示新的文本的控件部分失效。  
  
 在某些情况下，状态栏仅需要显示的文本行。 在这种情况下，请调用[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)。 这将状态栏控件放入"简单"模式下，显示单行文本。  
  
## <a name="see-also"></a>请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

