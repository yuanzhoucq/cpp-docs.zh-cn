---
title: "创建无模式属性表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4686caf6c414952cd86dfe0c69fcc3be8ee09af9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-modeless-property-sheet"></a>创建无模式属性表
通常情况下，你创建属性表将模式。 如果使用模式属性表，用户必须使用的应用程序的任何其他部分之前关闭属性表。 本文介绍可用于创建无模式属性表，用户可以保持打开属性表，同时使用的应用程序其他部分的方法。  
  
 若要显示属性表为无模式对话框而不是为模式对话框，请调用[CPropertySheet::Create](../mfc/reference/cpropertysheet-class.md#create)而不是[DoModal](../mfc/reference/cpropertysheet-class.md#domodal)。 你还必须实现一些额外的任务，以支持无模式属性表。  
  
 其他任务之一之间交换数据的属性表和打开属性表时，它修改的外部对象。 这通常是与标准的无模式对话框的相同任务。 此任务的一部分正在实现无模式属性表和外部对象的属性设置将应用之间的通信的通道。 此实现是容易得多，如果派生的类从[CPropertySheet](../mfc/reference/cpropertysheet-class.md)为无模式属性表。 本文假定你这样做。  
  
 无模式属性表和外部之间进行通信所需的一种方法是定义属性表中指向外部对象的指针对象 （在视图中，例如当前的选择）。 定义的函数 (称为类似`SetMyExternalObject`) 中`CPropertySheet`-派生类来更改焦点从一个外部对象更改为另一个指针。 `SetMyExternalObject`函数需要重置为每个属性页的设置，以反映新选择的外部对象。 若要实现此目的，`SetMyExternalObject`函数必须能够访问[CPropertyPage](../mfc/reference/cpropertypage-class.md)属于对象`CPropertySheet`类。  
  
 若要提供对属性表中的属性页的访问，最方便的方法是将嵌入`CPropertyPage`中的对象`CPropertySheet`-派生对象。 嵌入`CPropertyPage`中的对象`CPropertySheet`-派生的对象不同于有模式对话框，其中属性表的所有者创建的典型设计`CPropertyPage`对象，并将其传递给属性表通过[Cpropertysheet:: Addpage](../mfc/reference/cpropertysheet-class.md#addpage)。  
  
 有许多可用于确定何时应无模式属性表的设置应用于外部对象的用户界面选项。 一种替代方法，将应用当前的属性页的设置，每当用户更改的任何值。 另一种方法是提供应用按钮，这样用户就可以将它们提交给外部对象之前累积在属性页中的更改。 有关如何处理应用按钮的信息，请参阅文章[处理应用按钮](../mfc/handling-the-apply-button.md)。  
  
## <a name="see-also"></a>请参阅  
 [属性表](../mfc/property-sheets-mfc.md)   
 [交换数据](../mfc/exchanging-data.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

