---
title: "树控件图像列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5015a001bf2c15f3144303ba5e19b2a9ea8c34f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-image-lists"></a>树控件图像列表
树控件中的每个项 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 可以具有与之关联的位图图像的对。 在左侧的项的标签上显示图像。 当选定了项，并显示其他时未选择项目时，会显示一个图像。 例如，某一项可能显示选中时打开的文件夹和关闭的文件夹，如果未选择。  
  
 若要使用项映像，必须创建图像列表通过构造[CImageList](../mfc/reference/cimagelist-class.md)对象，并使用[CImageList::Create](../mfc/reference/cimagelist-class.md#create)函数来创建关联的图像列表。 然后将所需的位图添加到列表中，并将列表与树控件相关联使用[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)成员函数。 默认情况下，所有项所选和未选中状态的图像列表中都显示的第一个图像。 你可以通过将项添加到树控件使用时指定的所选的和未选定映像的索引更改特定项的默认行为[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成员函数。 你可以通过使用添加一项后更改索引[SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage)成员函数。  
  
 树控件的图像列表还可以包含用于在项的图像叠加的覆盖图像。 中的树控件项状态的位 8 至 11，则为非 0 值指定覆盖图像的基于 1 的索引 （0 表示没有覆盖图像）。 由于使用 4 位、 基于 1 的索引，图像列表中的前 15 映像必须是覆盖图像。 有关树控件项状态的详细信息，请参阅[树控件项状态概述](../mfc/tree-control-item-states-overview.md)本主题前面的。  
  
 如果指定一个状态图像列表，则树控件将保留状态图像的每个项的图标左侧的空间。 应用程序可以使用状态图像，如选中和清除复选框，以指示应用程序定义的项状态。 以位为单位通过 15 12 一个非零值指定状态图像的基于 1 的索引 （0 表示没有状态图像）。  
  
 通过指定**I_IMAGECALLBACK**值而不是图像的索引，可以延迟到相应项来重绘指定所选的或未选中映像。 **I_IMAGECALLBACK**代码指示查询索引的应用程序通过发送该树控件[TVN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518)通知消息。  
  
 [GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist)成员函数将检索树控件的图像列表的句柄。 此函数很有用，如果你需要将更多的图像添加到列表。 有关图像列表的详细信息，请参阅[使用 CImageList](../mfc/using-cimagelist.md)， [CImageList](../mfc/reference/cimagelist-class.md)中*MFC 参考*，和[图像列表](http://msdn.microsoft.com/library/windows/desktop/bb761389)中Windows SDK。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

