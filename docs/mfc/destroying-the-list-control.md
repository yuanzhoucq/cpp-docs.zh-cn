---
title: 销毁列表控件
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: d128a613a2a4cb595f362f843a5ae2eba830e538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621897"
---
# <a name="destroying-the-list-control"></a>销毁列表控件

如果将[CListCtrl](reference/clistctrl-class.md)对象作为视图或对话框类的数据成员嵌入，则在销毁其所有者时将销毁该对象。 如果使用[CListView](reference/clistview-class.md)，框架将在销毁视图时销毁控件。

如果您安排将某些列表数据存储在应用程序中而不是列表控件中，则需要安排释放。 有关详细信息，请参阅 Windows SDK 中的[回调项和回调掩码](/windows/win32/Controls/using-list-view-controls)。

此外，您还要负责释放由您创建并与列表控件对象关联的任何图像列表。

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](using-clistctrl.md)<br/>
[控件](controls-mfc.md)
