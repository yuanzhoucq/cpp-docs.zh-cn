---
title: 使用树控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bd7210f2f63d55fc4244a6b88456ede1265c8e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384864"
---
# <a name="using-tree-controls"></a>使用树控件
树控件的典型用法 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 遵循以下模式：  
  
-   创建滑块控件。 如果控件对话框模板中指定，或者如果你使用`CTreeView`，则在创建对话框或视图时自动创建。 如果你想要用作子窗口的某些其他窗口中创建树控件，使用[创建](../mfc/reference/ctreectrl-class.md#create)成员函数。  
  
-   如果你想要使用映像树控件，通过调用设置图像列表[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)。 你还可以通过调用更改缩进[SetIndent](../mfc/reference/ctreectrl-class.md#setindent)。 执行此操作的好时机是在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) （对于在对话框中的控件） 或[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) （适用于视图）。  
  
-   将数据放入控件，通过调用`CTreeCtrl`的[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)一次为每个数据项的函数。 `InsertItem` 返回一个句柄到项可以使用来引用它更高版本，例如，当添加子项。 初始化的数据的好时机是在`OnInitDialog`（对于在对话框中的控件） 或`OnInitialUpdate`（适用于视图）。  
  
-   当用户与该控件交互时，将发送各种通知消息。 你可以指定函数来处理每个你想要通过添加处理的消息**ON_NOTIFY_REFLECT**宏控件窗口的消息映射中或通过添加`ON_NOTIFY`宏为父窗口的消息映射。 请参阅[树控件通知消息](../mfc/tree-control-notification-messages.md)本主题中有关的可能的通知列表更高版本。  
  
-   调用各种 Set 成员函数来设置滑块控件的值。 可以进行的更改包括设置缩进和更改文本、 图像或与项目关联的数据。  
  
-   使用各种获取函数检查控件的内容。 你可以遍历的函数，使您得以检索父级、 子级和同级的指定项的句柄树控件的内容。 甚至可以对特定节点的子级进行排序。  
  
-   完成该控件后，请确保正确地销毁。 如果树控件位于对话框中，或如果它是视图，它与`CTreeCtrl`将自动销毁对象。 否则，您需要确保正确地销毁控件和 `CTreeCtrl` 对象。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

