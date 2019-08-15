---
title: 销毁列表控件
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: 5004026da6bb309cc2c966384724b7b98e254e1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508709"
---
# <a name="destroying-the-list-control"></a>销毁列表控件

如果将[CListCtrl](../mfc/reference/clistctrl-class.md)对象作为视图或对话框类的数据成员嵌入, 则在销毁其所有者时将销毁该对象。 如果使用[CListView](../mfc/reference/clistview-class.md), 框架将在销毁视图时销毁控件。

如果您安排将某些列表数据存储在应用程序中而不是列表控件中，则需要安排释放。 有关详细信息, 请参阅 Windows SDK 中的[回调项和回调掩码](/windows/win32/Controls/using-list-view-controls)。

此外，您还要负责释放由您创建并与列表控件对象关联的任何图像列表。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
