---
title: 为标题项提供拖放支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50cd19d4828269d0591afd0b46768e9917b96906
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>为标题项提供拖放支持
若要提供针对标题项的拖放支持，请指定 `HDS_DRAGDROP` 样式。 标题项的拖放支持使用户能够对标题控件的标题项进行重新排序。 默认行为将提供要拖动的标题项的半透明化拖动图像和新位置的可视指示器（如果已拖动标题项）。  
  
 利用常见的拖放功能，你可以通过处理来扩展默认的拖放行为**HDN_BEGINDRAG**和**HDN_ENDDRAG**通知。 此外可以自拖动图像的外观定义通过重写[cheaderctrl:: Createdragimage](../mfc/reference/cheaderctrl-class.md#createdragimage)成员函数。  
  
> [!NOTE]
>  如果将提供针对列表控件中的内嵌的标题控件的拖放支持，请参阅中的扩展样式部分[更改列表控件样式](../mfc/changing-list-control-styles.md)主题。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

