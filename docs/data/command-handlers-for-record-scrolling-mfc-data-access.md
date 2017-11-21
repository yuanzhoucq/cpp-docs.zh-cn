---
title: "命令处理程序用于记录滚动 （MFC 数据访问） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dc91c19661bb8902ff15919d89e745e9966c72c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
## <a name="see-also"></a>另请参阅  
 [支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)