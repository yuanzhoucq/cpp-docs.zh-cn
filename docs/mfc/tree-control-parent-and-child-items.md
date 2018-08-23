---
title: 树控件父项和子项 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7937ef604d14c464141c6e432a4d20a9d06e172
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954502"
---
# <a name="tree-control-parent-and-child-items"></a>树控件父项和子项
树控件中的任意项 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 都具有子项，称为子项目，与之关联的列表。 具有一个或多个子项的项称为“父项”。 子项显示在其父项下，可能指示其是父级的下属。 没有父级的项位于层次结构顶部，称为“根项”。  
  
 在任何给定时间，子项的父项列表的状态都可以为展开或折叠。 在状态为展开时，子项将显示在父项下。 当状态为折叠时，子项不会显示。 列表自动在状态之间切换展开和折叠当用户双击父项，或如果父任务具有**TVS_HASBUTTONS**样式，当用户单击与父项关联的按钮。 应用程序可以展开或折叠子项使用[展开](../mfc/reference/ctreectrl-class.md#expand)成员函数。  
  
 通过调用中的向树控件添加项[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成员函数。 此函数将返回的句柄**HTREEITEM**唯一标识项的类型。 添加项时，您必须为新项的父项指定句柄。 如果指定**NULL**或**TVI_ROOT**值而不是中的父项句柄[TVINSERTSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb773452)结构或*hParent*参数，该项目将添加为根项。  
  
 树控件将发送[TVN_ITEMEXPANDING](http://msdn.microsoft.com/library/windows/desktop/bb773537)将要可展开或折叠父项的子项列表时的通知消息。 此通知为您提供了阻止更改或设置依赖于子项列表状态的父项的任何特性。 更改列表的状态之后, 树控件将发送[TVN_ITEMEXPANDED](http://msdn.microsoft.com/library/windows/desktop/bb773533)通知消息。  
  
 子项列表展开后，则将相对于父项缩进。 你可以通过使用设置缩进量[SetIndent](../mfc/reference/ctreectrl-class.md#setindent)成员函数或检索当前量使用[GetIndent](../mfc/reference/ctreectrl-class.md#getindent)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

