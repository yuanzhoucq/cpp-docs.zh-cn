---
title: 图像图像列表中的覆盖 |Microsoft Docs
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
ms.openlocfilehash: 1c4052e06fe8aae1d149c3c09e88715d8270b361
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426557"
---
# <a name="image-overlays-in-image-lists"></a>图像列表中的图像覆盖

每个图像列表 ([CImageList](../mfc/reference/cimagelist-class.md)) 包括映像以用作覆盖掩码的列表。 “覆盖掩码”是在其他图像上透明绘制的图像。 任何图像都可用作覆盖掩码。 每个图像列表您最多可以指定 4 个覆盖掩码。

通过添加到覆盖掩码的列表的图像的索引[SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage)成员函数、 以图像的索引和覆盖掩码的索引。 请注意，覆盖掩码的索引是从 1 而不是 0 开始的。

使用调用一次图像上绘制覆盖掩码`Draw`。 参数包括要绘制图像的索引和覆盖掩码的索引。 必须使用[INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask)宏指定覆盖掩码的索引。 调用时，还可以指定覆盖图像[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)成员函数。

## <a name="see-also"></a>请参阅

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控件](../mfc/controls-mfc.md)

