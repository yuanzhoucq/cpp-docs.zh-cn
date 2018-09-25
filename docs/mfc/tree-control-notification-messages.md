---
title: 树控件通知消息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07911dec25bf9d6b80f025e2f3738e3d98ffd2cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390742"
---
# <a name="tree-control-notification-messages"></a>树控件通知消息

树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 将作为 WM_NOTIFY 消息中发送以下通知消息：

|通知消息|描述|
|--------------------------|-----------------|
|TVN_BEGINDRAG|表示开始拖放操作|
|TVN_BEGINLABELEDIT|表示开始就地标签编辑|
|TVN_BEGINRDRAG|表示使用鼠标右键的拖放操作的开始|
|TVN_DELETEITEM|表示特定项目的删除|
|TVN_ENDLABELEDIT|表示结束标签编辑|
|TVN_GETDISPINFO|树控件显示项所需的请求信息|
|TVN_ITEMEXPANDED|父项的子项列表已展开或折叠的信号|
|TVN_ITEMEXPANDING|父项的子项列表是要展开或折叠的信号|
|TVN_KEYDOWN|表示键盘事件|
|TVN_SELCHANGED|所选内容已从一项更改为另一个的信号|
|TVN_SELCHANGING|所选内容即将从一项更改为另一个的信号|
|TVN_SETDISPINFO|若要维护的项的信息更新的通知|

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

