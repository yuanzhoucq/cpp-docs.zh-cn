---
title: 树控件项选择
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: 07c7b673e0f9029f8ece928b0ab17760b3863cc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513338"
---
# <a name="tree-control-item-selection"></a>树控件项选择

当所选内容从一项更改为另一项时, 树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 将发送[TVN_SELCHANGING](/windows/win32/Controls/tvn-selchanging)和[TVN_SELCHANGED](/windows/win32/Controls/tvn-selchanged)通知消息。 这两个通知包括指定更改是鼠标单击还是击键的结果的值。 通知还包括有关将获取选择的项和将失去选择的项的信息。 您可以使用此信息设置依赖项的选择状态的项特性。 在响应中返回 TRUE `TVN_SELCHANGING`以阻止选择更改; 如果返回**FALSE** , 则允许更改。

应用程序可以通过调用[SelectItem](../mfc/reference/ctreectrl-class.md#selectitem)成员函数来更改选择。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
