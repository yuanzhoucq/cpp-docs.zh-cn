---
title: MFC 中的属性表和属性页
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: 10fb34c79745e672d30dd2d3c3b97d457583f795
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371173"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>MFC 中的属性表和属性页

属性表（也称为选项卡对话框）是一个包含属性页的对话框。 每个属性页都基于对话框模板资源，并包含控件。 它包含在页面上，上面有一个选项卡。 选项卡命名页面并指示其用途。 用户单击属性表中的选项卡以选择一组控件。

使用页面将属性表中的控件分组到有意义的集中。 包含的属性表通常具有其自己的多个控件。 这些适用于所有页面。

属性表基于类[C 属性表](../mfc/reference/cpropertysheet-class.md)。 属性页基于[类 CPropertyPage](../mfc/reference/cpropertypage-class.md)。

属性表是一种特殊的对话框，通常用于修改某些外部对象的属性，例如视图中的当前选择。 属性表有三个主要部分：包含对话框、一个或多个属性页一次显示一个，以及用户单击以选择该页面的每个页面顶部的选项卡。 属性表可用于您有多个类似的设置组或要更改的选项的情况。 属性表以易于理解的方式对信息进行分组。

> [!NOTE]
> 当您尝试使用`CPropertySheet::DoModal`显示属性表时，系统可能会生成第一个异常。 出现此异常的原因是系统在创建对象之前尝试更改对象[的窗口样式](../mfc/reference/styles-used-by-mfc.md#window-styles)。 有关此异常的详细信息以及如何避免或处理它，请参阅[CPropertySheet：:DoModal](../mfc/reference/cpropertysheet-class.md#domodal)。

## <a name="see-also"></a>另请参阅

[属性表](../mfc/property-sheets-mfc.md)
