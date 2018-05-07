---
title: 列表控件和列表视图 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3279ae5edc02ec52ded065c4a45d18e3236802f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="list-control-and-list-view"></a>列表控件和列表视图
为方便起见，MFC 将通过两种方式封装列表控件。 您可使用列表控件：  
  
-   直接使用，方式嵌入[CListCtrl](../mfc/reference/clistctrl-class.md)对话框类中的对象。  
  
-   间接方法，通过使用类[CListView](../mfc/reference/clistview-class.md)。  
  
 `CListView` 可以轻松地将与封装控件的 MFC 文档/视图体系结构集成列表控件数量为[CEditView](../mfc/reference/ceditview-class.md)封装编辑控件： 控件将填充 MFC 视图的整个图面区域。 (视图*是*控件，强制转换为`CListView`。)  
  
 A`CListView`对象继承自[CCtrlView](../mfc/reference/cctrlview-class.md)和其基类并添加成员函数以检索基础列表控件。 使用视图成员以将此视图作为视图使用。 使用[GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl)成员函数获取对列表控件的成员函数的访问权限。 使用这些成员  
  
-   添加、删除或操作列表中的“项”。  
  
-   设置或获取列表控件特性。  
  
 若要获取对作为 `CListCtrl` 的基础的 `CListView` 的引用，请通过列表视图类调用 `GetListCtrl`：  
  
 [!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]  
  
 本主题介绍了使用列表控件的两种方式。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

