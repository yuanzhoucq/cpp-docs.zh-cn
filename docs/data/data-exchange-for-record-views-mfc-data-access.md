---
title: 记录视图的数据交换（MFC 数据访问）
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: f9f460305b55a2313b64effdf4d1dbbfd9823def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213461"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>记录视图的数据交换（MFC 数据访问）

当您使用 "[添加类](../mfc/reference/adding-an-mfc-odbc-consumer.md)" 将记录视图的对话框模板资源中的控件映射到记录集的字段时，框架将在两个方向（从记录集到控件，从控件到记录集）管理数据交换。 使用 DDX 机制意味着你不必编写代码来回传输数据。

记录视图的 DDX 与 `CRecordset` （ODBC）类的记录集的[RFX](../data/odbc/record-field-exchange-rfx.md)一起工作。  RFX 在数据源的当前记录和记录集对象的字段数据成员之间移动数据。 DDX 可将数据从字段数据成员移动到窗体的控件中。 此组合在初始时和用户逐条移动记录时填充窗体控件。 它还可以将更新的数据移回记录集，然后再移到数据源。

下图显示了记录视图的 DDX 和 RFX 之间的关系。

![对话框&#45;数据交换和记录&#45;字段交换](../data/media/vc37xt1.gif "对话框&#45;数据交换和记录&#45;字段交换")<br/>
对话框数据交换和记录字段交换

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。 有关 RFX 的详细信息，请参阅[记录字段交换（RFX）](../data/odbc/record-field-exchange-rfx.md)。

## <a name="see-also"></a>另请参阅

[记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)
