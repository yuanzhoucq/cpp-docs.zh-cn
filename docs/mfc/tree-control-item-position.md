---
title: "树控件项位置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a69198834513362e87568f83f8c4f38b74a2b05d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="tree-control-item-position"></a>树控件项位置
向树控件添加项时设置某一项的初始位置 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 通过使用`InsertItem`成员函数。 成员函数调用指定的父项的句柄和句柄的新项之后要插入的项。 第二个句柄必须标识给定父的子项目或这些值之一： `TVI_FIRST`， `TVI_LAST`，或`TVI_SORT`。  
  
 当`TVI_FIRST`或`TVI_LAST`指定，则树控件将新项的开头或末尾给定的父项的子项列表。 当`TVI_SORT`指定，则树控件将新项插入到的项标签的文本所基于的按字母顺序的子项列表。  
  
 通过调用放入字母顺序的子项的父项的列表[SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren)成员函数。 此函数包括一个参数，指定是否所有级别的降序从给定的父项的子项还进行了按字母顺序都排序。  
  
 [SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb)成员函数使你可以根据你定义的条件的子项进行排序。 在调用此函数时，你指定一个应用程序定义的回调函数，可以调用树控件，每当需要确定的两个子项的相对顺序。 回调函数接收两个 32 位应用程序定义的值进行比较的项和一个第三个 32 位值，在调用时指定`SortChildrenCB`。  
  
## <a name="see-also"></a>另请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

