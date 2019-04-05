---
title: 用于记录滚动的命令处理程序（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 66944221910dbd23d78a78fc951030efbee86bd0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038508"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>用于记录滚动的命令处理程序（MFC 数据访问）

[CRecordView](../mfc/reference/crecordview-class.md)类提供了处理以下标准命令的默认命令：

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

`OnMove`成员函数提供了默认命令处理的所有四个命令，记录之间移动。 发布这些命令后，RFX（或 DFX）将加载新记录到记录集字段，DDX 将移动值到记录窗体控件。 有关 RFX 的信息，请参阅[记录字段交换 (RFX)](../data/odbc/record-field-exchange-rfx.md)。

> [!NOTE]
>  确保将这些标准的命令 ID 用于任何与标准记录导航命令关联的用户界面对象。

## <a name="see-also"></a>请参阅

[支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)