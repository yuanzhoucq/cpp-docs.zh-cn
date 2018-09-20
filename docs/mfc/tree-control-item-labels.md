---
title: 树控件项标签 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f07032a203761e78bd44f40456093eae9a84d07
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399870"
---
# <a name="tree-control-item-labels"></a>树控件项标签

将项添加到树控件时通常指定项的标签的文本 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 `InsertItem`成员函数可以传递[TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema)结构，用于定义项的属性，包括包含标签的文本的字符串。 `InsertItem` 有若干重载，可以使用各种组合的参数调用。

树控件分配内存来存储每个项;项标签的文本将占用此内存的重要部分。 如果你的应用程序维护一份树控件中的字符串，可以通过指定降低控件的内存需求**LPSTR_TEXTCALLBACK**中的值*pszText* 成员`TV_ITEM`或*lpszItem*参数而不是将实际的字符串传递给树控件。 使用**LPSTR_TEXTCALLBACK**导致要从应用程序检索项的标签的文本，每当需要重绘的项的树控件。 若要检索文本，树控件将发送[TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo)通知消息，其中包括的地址[2&AMP;GT;NMTVDISPINFO&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa)结构。 必须通过设置包含结构的合适成员进行响应。

树控件使用的进程的创建树控件堆中分配的内存。 树控件中的最大项数根据堆中可用的内存量。 每个项目占 64 个字节。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

