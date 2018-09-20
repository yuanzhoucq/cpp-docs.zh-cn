---
title: Rebar 控件和带区 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 988b16bb58462b42b8d4412a821cfc3fac5b4878
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443977"
---
# <a name="rebar-controls-and-bands"></a>Rebar 控件和带区

Rebar 控件的主要用途是作为子窗口、 通用对话框控件、 菜单、 工具栏和等等的容器。 此包含支持的概念"带区"。 每个 rebar 带区可以包含一个手柄栏、 位图、 文本标签和子窗口的任意组合。

类`CReBarCtrl`具有许多成员函数，可以使用来检索，并且操作，为特定 rebar 带区的信息：

- [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount)检索 rebar 控件中的当前带区数。

- [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo)初始化**REBARBANDINFO**结构中指定的带区的信息。 具有对应[SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo)成员函数。

- [GetRect](../mfc/reference/crebarctrl-class.md#getrect)检索指定的带区的边框。

- [GetRowCount](../mfc/reference/crebarctrl-class.md#getrowcount)检索外 rebar 控件中的行数。

- [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex)检索指定的带区的索引。

- [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders)检索的外边框。

除了操作、 多个成员函数都是提供，使用户能够对特定 rebar 带区。

[InsertBand](../mfc/reference/crebarctrl-class.md#insertband)并[DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband)添加和删除 rebar 带区。 [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband)并[MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband)影响特定 rebar 带区的当前大小。 [MoveBand](../mfc/reference/crebarctrl-class.md#moveband)更改特定 rebar 带区的索引。 [ShowBand](../mfc/reference/crebarctrl-class.md#showband)显示或隐藏从用户 rebar 带区。

下面的示例演示如何添加工具栏区 (*m_wndToolBar*) 到现有 rebar 控件 (*m_wndReBar*)。 初始化描述外`rbi`结构，然后再调用`InsertBand`成员函数：

[!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]

## <a name="see-also"></a>请参阅

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

