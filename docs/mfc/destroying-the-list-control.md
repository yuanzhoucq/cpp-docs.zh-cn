---
title: 销毁列表控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25642357e3dd9117ae2817307ed5fa3c4a0921d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424530"
---
# <a name="destroying-the-list-control"></a>销毁列表控件

如果在嵌入你[CListCtrl](../mfc/reference/clistctrl-class.md)对象的视图或对话框类中，数据成员作为其所有者被销毁时销毁它。 如果您使用[CListView](../mfc/reference/clistview-class.md)，在销毁视图，框架将销毁控件。

如果您安排将某些列表数据存储在应用程序中而不是列表控件中，则需要安排释放。 有关详细信息，请参阅[回调项和回调掩码](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。

此外，您还要负责释放由您创建并与列表控件对象关联的任何图像列表。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

