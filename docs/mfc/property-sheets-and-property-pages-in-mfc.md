---
title: 属性表和 MFC 中的属性页 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f35282ce46aff3a3f0fba5fca505653cd892a392
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430029"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>MFC 中的属性表和属性页

属性表，也称为选项卡对话框中是一个包含属性页的对话框。 每个属性页对话框模板资源为基础，并包含控件。 它被括在上一个页面顶部的选项卡。 选项卡命名属性页，并指示其用途。 用户单击要选择一组控件的属性表中的选项卡。

使用页可以在属性表中的将控件分组为有意义的集。 包含的属性表通常具有其自己的多个控件。 这些数字适用于所有页面。

属性表基于类[CPropertySheet](../mfc/reference/cpropertysheet-class.md)。 属性页基于类[CPropertyPage](../mfc/reference/cpropertypage-class.md)。

属性表是对象的对话框的一种特殊中，通常用于修改某些外部对象，如在视图中当前所选内容的属性。 属性表具有三个主要部分: 包含对话框中，一个或多个属性页显示了一次，并在用户单击以选择该页面每个页面顶部的选项卡。 属性表可用于有多个相似的组的设置或更改选项的情况。 属性表中一种易于理解的方式的组的信息。

> [!NOTE]
>  当您尝试使用显示属性表`CPropertySheet::DoModal`，系统可能会生成最可能的异常。 发生此异常的原因尝试更改系统[的窗口样式](../mfc/reference/styles-used-by-mfc.md#window-styles)之前创建对象的对象。 有关此异常，以及如何避免它或对其进行处理的详细信息，请参阅[cpropertysheet:: Domodal](../mfc/reference/cpropertysheet-class.md#domodal)。

## <a name="see-also"></a>请参阅

[属性表](../mfc/property-sheets-mfc.md)

