---
title: 创建无模式属性表
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 7a44d96adf0a25a401fbc2e561bd7d32758a37d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617173"
---
# <a name="creating-a-modeless-property-sheet"></a>创建无模式属性表

通常，您创建的属性表将是模式的。 使用模式属性表时，用户必须先关闭属性表，然后才能使用应用程序的任何其他部分。 本文介绍可用于创建无模式属性表的方法，使用该属性表，用户可以在使用应用程序的其他部分时使属性表保持打开状态。

若要将属性表显示为无模式对话框而不是模式对话框，请调用[CPropertySheet：： Create](reference/cpropertysheet-class.md#create)而不是[DoModal](reference/cpropertysheet-class.md#domodal)。 还必须实现一些额外的任务来支持无模式属性表。

其中一项任务是在属性表打开时，在属性表与它正在修改的外部对象之间交换数据。 这通常是与标准无模式对话框相同的任务。 此任务的一部分是在无模式属性表和将属性设置应用到的外部对象之间实现通信通道。 如果从[CPropertySheet](reference/cpropertysheet-class.md)为无模式属性表派生类，则此实现会更容易。 本文假设已完成此操作。

在无模式属性表与外部对象（例如，视图中的当前选定内容）之间进行通信的一种方法是定义从属性表到外部对象的指针。 在派生类中定义一个函数（称为 `SetMyExternalObject` ）， `CPropertySheet` 以便在焦点从一个外部对象变为另一个时更改指针。 `SetMyExternalObject`函数需要重置每个属性页的设置以反映新选定的外部对象。 若要实现此目的，该 `SetMyExternalObject` 函数必须能够访问属于类的[CPropertyPage](reference/cpropertypage-class.md)对象 `CPropertySheet` 。

提供对属性表中的属性页访问的最便捷方法是将 `CPropertyPage` 对象嵌入 `CPropertySheet` 派生对象。 `CPropertyPage`在派生对象中嵌入对象 `CPropertySheet` 不同于模式对话框的典型设计，其中属性表的所有者创建 `CPropertyPage` 对象并通过[CPropertySheet：： AddPage](reference/cpropertysheet-class.md#addpage)将这些对象传递给属性表。

有许多用户界面替代方法可用于确定何时应将无模式属性表的设置应用于外部对象。 一种替代方法是在用户更改任何值时应用当前属性页的设置。 另一种方法是提供 "应用" 按钮，该按钮允许用户在将更改提交到外部对象之前，在属性页中累积更改。 有关处理 "应用" 按钮的方法的信息，请参阅[处理应用按钮](handling-the-apply-button.md)一文。

## <a name="see-also"></a>另请参阅

[属性表](property-sheets-mfc.md)<br/>
[交换数据](exchanging-data.md)<br/>
[在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)
