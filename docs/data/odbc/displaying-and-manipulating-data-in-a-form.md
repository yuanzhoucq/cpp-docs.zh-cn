---
title: 显示和操作窗体中的数据 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3b86c58c8e5afb53cb02174beb3553378dd0efc8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089361"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>在窗体中显示和操作数据
许多数据访问应用程序选择数据，并将其显示在窗体中的字段中。 数据库类[CRecordView](../../mfc/reference/crecordview-class.md)为你提供[CFormView](../../mfc/reference/cformview-class.md)直接连接到记录集对象的对象。 记录视图使用[对话框数据交换 (DDX)](../../mfc/dialog-data-exchange-and-validation.md)从记录集的当前记录的字段的值移到窗体上的控件并将更新的信息移回记录集。 记录集，反过来，使用记录字段交换 (RFX) 对数据源字段数据成员和表中的相应列之间移动数据。  
  
 你可以使用 MFC 应用程序向导或**添加类**(中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 一起使用在创建视图类和其关联的记录集类。  
  
 在关闭文档时销毁了记录视图和它的记录集。 有关记录视图的详细信息，请参阅[记录视图](../../data/record-views-mfc-data-access.md)。 有关 RFX 的详细信息，请参阅[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
## <a name="see-also"></a>请参阅  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)