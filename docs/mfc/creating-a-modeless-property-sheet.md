---
title: 创建无模式属性表 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16b0a558dcae7d2bf35cf530abfea15ef6f8138a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378093"
---
# <a name="creating-a-modeless-property-sheet"></a>创建无模式属性表

通常情况下，创建属性表将为模式对话框。 当使用模式属性表时，用户必须使用应用程序的任何其他部分之前关闭属性表。 本文介绍可用于创建允许用户属性表保持处于打开状态时使用的应用程序的其他部分无模式属性表的方法。

若要显示属性表作为无模式对话框而不是为模式对话框，请调用[CPropertySheet::Create](../mfc/reference/cpropertysheet-class.md#create)而不是[DoModal](../mfc/reference/cpropertysheet-class.md#domodal)。 此外必须实现一些额外的任务，以支持无模式属性表。

其他任务之一之间交换数据的属性表和它修改的属性表处于打开状态时的外部对象。 这通常是相同的任务与标准的无模式对话框。 此任务的一部分实现无模式属性表和外部对象的属性设置将应用之间的通信的通道。 此实现是容易得多，如果派生的类从[CPropertySheet](../mfc/reference/cpropertysheet-class.md)为无模式属性表。 本文假定你这样做。

无模式属性表和外部之间进行通信的一种方法是定义从属性表为外部对象的指针对象 （在视图中，例如当前的选择）。 定义函数 (名为类似`SetMyExternalObject`) 中`CPropertySheet`-派生的类将指针更改时将焦点从一个外部对象更改为另一个。 `SetMyExternalObject`函数需要重置每个属性页的设置以反映新选择的外部对象。 若要完成此操作，请`SetMyExternalObject`函数必须能够访问[CPropertyPage](../mfc/reference/cpropertypage-class.md)属于对象`CPropertySheet`类。

提供对属性表中的属性页的访问的最简便方法是将嵌入`CPropertyPage`中的对象`CPropertySheet`-派生的对象。 嵌入`CPropertyPage`中的对象`CPropertySheet`-派生的对象不同于模式对话框，其中属性表的所有者创建的典型设计`CPropertyPage`对象，并将其传递到属性表通过[Cpropertysheet:: Addpage](../mfc/reference/cpropertysheet-class.md#addpage)。

有许多可用于确定何时应无模式属性表的设置应用于外部对象的用户界面选项。 一种替代方法是将当前的属性页的设置应用在用户更改任何值。 另一种方法是提供应用按钮，这样用户就可以将它们提交给外部对象之前积累的属性页中的更改。 有关处理应用按钮的方法的信息，请参阅文章[处理应用按钮](../mfc/handling-the-apply-button.md)。

## <a name="see-also"></a>请参阅

[属性表](../mfc/property-sheets-mfc.md)<br/>
[交换数据](../mfc/exchanging-data.md)<br/>
[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

