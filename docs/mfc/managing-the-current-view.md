---
title: 管理当前视图 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 323903d2e1285a4ee697bbd9d0c3a29c2e1248d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="managing-the-current-view"></a>管理当前视图
作为框架窗口默认实现的一部分，框架窗口将记录当前活动视图。 如果框架窗口包含多个视图，例如在拆分器窗口中，则当前视图是正在使用中的最新视图。 活动视图独立于 Windows 中的活动窗口或当前输入焦点。  
  
 活动视图发生更改时，框架将通过调用来通知当前视图其[OnActivateView](../mfc/reference/cview-class.md#onactivateview)成员函数。 您可以通过检查 `OnActivateView` 的 `bActivate` 参数来分辨视图处于激活还是停用状态。 默认情况下，`OnActivateView` 会将焦点设置为处于激活状态的当前视图。 您可以重写 `OnActivateView`，以在停用或重新激活视图时执行任何特殊处理。 例如，您可能需要提供特殊可视提示来区分活动视图与其他非活动视图。  
  
 框架窗口将命令转发给其当前 （活动） 视图中, 所述[命令路由](../mfc/command-routing.md)，作为标准命令路由的一部分。  
  
## <a name="see-also"></a>请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)

