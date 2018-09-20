---
title: 树控件项选择 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9aa9c82a57ff8504c8e3eba7becff1e1cdccaae2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431562"
---
# <a name="tree-control-item-selection"></a>树控件项选择

当所选内容从一个项更改到另一个树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 将发送[TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging)并[TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged)通知消息。 这两个通知包括指定更改是鼠标单击还是击键的结果的值。 通知还包括有关将获取选择的项和将失去选择的项的信息。 您可以使用此信息设置依赖项的选择状态的项特性。 返回 **，则返回 TRUE**响应`TVN_SELCHANGING`阻止所选内容更改; 返回**FALSE**允许更改。

应用程序可以通过调用更改所选内容[SelectItem](../mfc/reference/ctreectrl-class.md#selectitem)成员函数。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

