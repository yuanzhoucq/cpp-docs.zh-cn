---
title: 记录视图类的功能（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 62597a3eb3f7a7e779ca57c9781565176df568d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213429"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>记录视图类的功能（MFC 数据访问）

您可以使用类[CFormView](../mfc/reference/cformview-class.md)执行基于窗体的数据访问编程，但[CRecordView](../mfc/reference/crecordview-class.md)通常是派生自的更好的类。 除了其 `CFormView` 功能外，`CRecordView`：

- 提供窗体控件和关联记录集对象之间的对话框数据交换（DDX）。

- 句柄先移动、移到下一步、移动上一条命令，然后移动最后一个命令，以便在关联记录集对象中的记录间导航。

- 当用户移到另一记录时，更新对当前记录所做的更改。

有关导航的详细信息，请参阅[记录视图：支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)。

## <a name="see-also"></a>另请参阅

[记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)
