---
title: 命令处理程序用于记录滚动 （MFC 数据访问） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03dec2e3eff0f61db5f4c8b7573400a589615b02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>用于记录滚动的命令处理程序（MFC 数据访问）
[CRecordView](../mfc/reference/crecordview-class.md)类提供了处理以下标准命令的默认命令：  
  
-   **ID_RECORD_MOVE_FIRST**  
  
-   **ID_RECORD_MOVE_LAST**  
  
-   **ID_RECORD_MOVE_NEXT**  
  
-   **ID_RECORD_MOVE_PREV**  
  
 `OnMove`成员函数提供了默认命令处理所有四个命令，记录之间移动。 发布这些命令后，RFX（或 DFX）将加载新记录到记录集字段，DDX 将移动值到记录窗体控件。 有关 RFX 的信息，请参阅[记录字段交换 (RFX)](../data/odbc/record-field-exchange-rfx.md)。  
  
> [!NOTE]
>  确保将这些标准的命令 ID 用于任何与标准记录导航命令关联的用户界面对象。  
  
## <a name="see-also"></a>请参阅  
 [支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)