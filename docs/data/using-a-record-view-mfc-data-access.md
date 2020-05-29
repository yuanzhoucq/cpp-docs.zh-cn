---
title: 使用记录视图（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: 611ddfd755eec84d4f2572a50c18802f988c5c3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209022"
---
# <a name="using-a-record-view--mfc-data-access"></a>使用记录视图（MFC 数据访问）

本主题介绍了自定义向导为你编写的记录视图的默认代码的常用方式。 通常，您需要使用[筛选器](../data/odbc/recordset-filtering-records-odbc.md)或[参数](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)约束记录选择，可能会[对记录进行排序](../data/odbc/recordset-sorting-records-odbc.md)，自定义 SQL 语句。

使用 `CRecordView` 与使用[CFormView](../mfc/reference/cformview-class.md)几乎相同。 基本的方法是使用记录视图显示或更新单个记录集的记录。 除此之外，你可能还希望使用其他记录集，如[记录视图：从另一个记录集填充列表框](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)中所述。

## <a name="see-also"></a>另请参阅

[记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)
