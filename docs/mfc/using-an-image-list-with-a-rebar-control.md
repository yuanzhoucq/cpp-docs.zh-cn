---
title: "Rebar 控件使用图像列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: acb4ed52982f7ab23dac044eeacf315f45aa1232
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-image-list-with-a-rebar-control"></a>对 Rebar 控件使用图像列表
每个 rebar 带区除了别的之外还可以包含关联图像列表的图像。 以下过程详述了在 rebar 带区显示图像的必需步骤。  
  
### <a name="to-display-images-in-a-rebar-band"></a>在 rebar 带区显示图像  
  
1.  通过调用将图像列表附加到 rebar 控件对象[SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist)，将指针传递给现有图像列表。  
  
2.  修改**REBARBANDINFO**结构以将图像分配到 rebar 带区：  
  
    -   设置**fMask**成员**RBBIM_IMAGE**，使用按位 OR 运算符来根据需要包含其他标志。  
  
    -   将 `iImage` 成员设置为要显示图像的图像列表索引。  
  
3.  使用必需信息初始化任何其余的数据成员，如包含子窗口的大小、文本和句柄。  
  
4.  插入新的带区 （带图像） 通过调用[CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband)，并传递**REBARBANDINFO**结构。  
  
 以下示例假定已将带两个图像的现有图像列表对象附加到 rebar 控件对象 (`m_wndReBar`)。 包含第一个图像的新的 rebar 带区（由 `rbi` 定义）是通过调用 `InsertBand` 添加的：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)

