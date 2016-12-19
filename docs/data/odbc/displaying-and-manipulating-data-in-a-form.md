---
title: "在窗体中显示和操作数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据 [MFC]"
  - "数据 [MFC], 在窗体中显示"
  - "显示数据 [C++], 窗体"
  - "窗体 [C++], 显示数据"
  - "ODBC [C++], 窗体"
  - "记录视图 [C++], 显示数据"
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在窗体中显示和操作数据
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

许多数据访问应用程序可选择数据，然后在窗体的字段中显示该数据。  数据库类 [CRecordView](../../mfc/reference/crecordview-class.md) 提供给您直接连接到某记录集对象的 [CFormView](../../mfc/reference/cformview-class.md) 对象。  记录视图使用 [对话框数据交换 \(DDX\)](../../mfc/dialog-data-exchange-and-validation.md) 将当前记录的字段值从记录集移到窗体的控件上，并将更新的信息移回到记录集。  反过来，记录集使用记录字段交换 \(RFX\) 在它的字段数据成员和数据源上表中相应的列之间移动数据。  
  
 您可以使用 MFC 应用程序向导或者“添加类”（如[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述）来一同创建视图类及其关联的记录集类。  
  
 当关闭文档时，也就销毁了记录视图和它的记录集。  有关记录视图的更多信息，请参见[记录视图](../../data/record-views-mfc-data-access.md)。  有关 RFX 的更多信息，请参见 [记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)。  
  
## 请参阅  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)