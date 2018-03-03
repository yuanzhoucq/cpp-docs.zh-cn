---
title: "设置 CStatusBarCtrl 对象的模式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7c954354321d814952ec3ac5ea148cc9177cd0fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>设置 CStatusBarCtrl 对象的模式
有两种模式`CStatusBarCtrl`对象： 简单和非简单。 在大多数情况下，你状态栏控件将具有一个或多个部件，以及文本和可能的图标或图标。 这被称为非简单模式。 有关此模式的详细信息，请参阅[初始化 CStatusBarCtrl 对象的组成部分](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。  
  
 但是，在其中你只需显示单个文本行的情况下。 在这种情况下，简单的模式足以满足你的需求。 若要更改的模式`CStatusBarCtrl`对象为 simple 时，请调用[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)成员函数。 简单模式状态栏控件后，通过调用设置的文本**SetText**成员函数，传递的值为 255 **nPane**参数。  
  
 你可以使用[IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple)函数来确定哪种模式`CStatusBarCtrl`对象处于。  
  
> [!NOTE]
>  如果状态栏对象将从不简单更改为简单、 或，反之亦然，这样，立即重绘窗口并且，如果适用，任何定义的部件将自动恢复。  
  
## <a name="see-also"></a>请参阅  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

