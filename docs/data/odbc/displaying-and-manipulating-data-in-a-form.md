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
ms.openlocfilehash: e50c433e701fbae2e607d79d7abb34efe8eba5b5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033743"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>在窗体中显示和操作数据

许多数据访问应用程序选择的数据并将其显示在窗体中的字段中。 Database 类[CRecordView](../../mfc/reference/crecordview-class.md)为您提供了[CFormView](../../mfc/reference/cformview-class.md)直接连接到记录集对象的对象。 使用记录视图[对话框数据交换 (DDX)](../../mfc/dialog-data-exchange-and-validation.md)将当前记录的字段的值从记录集移到窗体上的控件，并将更新的信息移回记录集。 记录集，反过来，使用记录字段交换 (RFX) 上的数据源字段数据成员和表中相应的列之间移动数据。

可以使用 MFC 应用程序向导或**添加类**(如中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 来创建视图类及其关联的记录集类一起使用。

当文档关闭时销毁了记录视图和它的记录集。 关于记录视图的详细信息，请参阅[记录视图](../../data/record-views-mfc-data-access.md)。 有关 RFX 的详细信息，请参阅[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。

## <a name="see-also"></a>请参阅

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)