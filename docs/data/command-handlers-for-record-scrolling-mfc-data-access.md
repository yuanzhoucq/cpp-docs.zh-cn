---
title: 用于记录滚动的命令处理程序（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 14ef845c3029f1d9a30d257f91c1b33017b6ec8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336931"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>用于记录滚动的命令处理程序（MFC 数据访问）

[CRecordView](../mfc/reference/crecordview-class.md)类为以下标准命令提供默认命令处理：

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

成员`OnMove`函数为所有四个命令提供默认命令处理，这些命令从记录移动到记录。 发布这些命令后，RFX（或 DFX）将加载新记录到记录集字段，DDX 将移动值到记录窗体控件。 有关 RFX 的信息，请参阅[记录字段交换 （RFX）。](../data/odbc/record-field-exchange-rfx.md)

> [!NOTE]
> 确保将这些标准的命令 ID 用于任何与标准记录导航命令关联的用户界面对象。

## <a name="see-also"></a>另请参阅

[在记录视图中支持导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
