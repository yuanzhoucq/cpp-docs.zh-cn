---
title: 图像图像列表中的覆盖 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93d37b49a949ab29e0ae888d9c961da086ee4ca4
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928591"
---
# <a name="image-overlays-in-image-lists"></a>图像列表中的图像覆盖
每个图像列表 ([CImageList](../mfc/reference/cimagelist-class.md)) 包括映像以用作覆盖掩码的列表。 “覆盖掩码”是在其他图像上透明绘制的图像。 任何图像都可用作覆盖掩码。 每个图像列表您最多可以指定 4 个覆盖掩码。  
  
 你将图像的索引添加到覆盖掩码的列表的使用[SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage)成员函数、 映像的索引和覆盖掩码的索引。 请注意，覆盖掩码的索引是从 1 而不是 0 开始的。  
  
 在使用一次对图像上绘制覆盖掩码`Draw`。 参数包括要绘制图像的索引和覆盖掩码的索引。 必须使用[INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408)宏指定覆盖掩码的索引。 在调用时，还可以指定覆盖图像[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)

