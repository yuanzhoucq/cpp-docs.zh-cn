---
title: 在窗体中显示和操作数据
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: 6b663fabd0c87d9a2773e6f5a2796bcc8f57ce29
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213247"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>在窗体中显示和操作数据

许多数据访问应用程序都选择数据并将其显示在窗体中的字段中。 数据库类[CRecordView](../../mfc/reference/crecordview-class.md)提供直接连接到 recordset 对象的[CFormView](../../mfc/reference/cformview-class.md)对象。 记录视图使用[对话框数据交换（DDX）](../../mfc/dialog-data-exchange-and-validation.md)将当前记录的字段值从记录集移动到窗体上的控件，并将更新后的信息移回记录集。 然后，记录集使用记录字段交换（RFX）在其字段数据成员和数据源的表中的相应列之间移动数据。

您可以使用 "MFC 应用程序向导" 或 "**添加类**" （如[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述）来创建视图类及其关联的记录集类。

关闭文档后，将销毁记录视图及其记录集。 有关记录视图的详细信息，请参阅[记录视图](../../data/record-views-mfc-data-access.md)。 有关 RFX 的详细信息，请参阅[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

## <a name="see-also"></a>另请参阅

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)
