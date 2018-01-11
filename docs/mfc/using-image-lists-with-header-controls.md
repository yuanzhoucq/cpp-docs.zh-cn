---
title: "标头控件使用图像列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a7a51aadc10a7722875597813e24ceb5960ab459
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-image-lists-with-header-controls"></a>对标题控件使用图像列表
标头项都具有显示标头项中的某个图像的功能。 存储在关联的图像列表中，此图像为 16 x 16 像素，并且具有相同的特性列表视图控件中使用的图标图像。 为了成功实现此行为，必须首先创建和初始化的图像列表，将列表与标头控件相关联，然后修改项的图像将显示的标题项的属性。  
  
 以下过程说明了使用指向标头控件的详细信息 (`m_pHdrCtrl`) 以及指向图像列表的指针 (`m_pHdrImages`)。  
  
### <a name="to-display-an-image-in-a-header-item"></a>标头项中显示图像  
  
1.  构造一个新的图像列表 （或使用现有的图像列表对象） 使用[CImageList](../mfc/reference/cimagelist-class.md)构造函数，存储结果的指针。  
  
2.  通过调用中初始化新的图像列表对象[CImageList::Create](../mfc/reference/cimagelist-class.md#create)。 下面的代码是此调用的一个示例。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]  
  
3.  添加为每个标头项的映像。 以下代码添加两个预定义的映像。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]  
  
4.  标头控件，通过调用相关联的图像列表[CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist)。  
  
5.  修改要显示的关联的图像列表中的映像的标头项。 下面的示例从分配的第一个图像， `m_phdrImages`，到第一个标头项， `m_pHdrCtrl`。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]  
  
 有关使用的参数值的详细信息，请查阅相关[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)。  
  
> [!NOTE]
>  很可能有多个使用相同的图像列表的控件。 例如，在标准列表视图控件中，可能有图像列表 （的 16 x 16 像素的图像） 的列表视图控件的小图标视图和列表视图控件的标题项使用。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

