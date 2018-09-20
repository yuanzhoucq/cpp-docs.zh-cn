---
title: 视图在打印中的角色 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], printing
- OnDraw method [MFC], and printing
- printing [MFC], OnDraw method [MFC]
- printing [MFC], views
- CView class [MFC], role in printing
- printing views [MFC]
ms.assetid: 8d4a3c8e-1fce-4edc-b608-94cb5f3e487e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c78756ea84df66b77f71d8f8ad8d0b9dfa1a6c9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377521"
---
# <a name="role-of-the-view-in-printing"></a>视图在打印中的作用

您的视图还将对其关联文档的打印具有两个重要影响。

视图：

- 使用相同[OnDraw](../mfc/reference/cview-class.md#ondraw)代码，以在屏幕上绘制打印机上绘制。

- 管理对要分页打印的文档的划分。

有关打印以及在打印中的视图的角色的详细信息，请参阅[打印和打印预览](../mfc/printing-and-print-preview.md)。

## <a name="see-also"></a>请参阅

[使用视图](../mfc/using-views.md)

