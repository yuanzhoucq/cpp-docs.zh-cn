---
title: 使用记录视图（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: 9d64fc26e1c78bad0431bc9b10dd5117c4866159
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029351"
---
# <a name="using-a-record-view--mfc-data-access"></a>使用记录视图（MFC 数据访问）

本主题介绍了自定义向导为你编写的记录视图的默认代码的常用方式。 通常情况下，你想要限制记录选择与[筛选器](../data/odbc/recordset-filtering-records-odbc.md)或[参数](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)，可能是[排序](../data/odbc/recordset-sorting-records-odbc.md)记录，自定义 SQL 语句。

使用`CRecordView`是类似于使用[CFormView](../mfc/reference/cformview-class.md)。 基本的方法是使用记录视图显示或更新单个记录集的记录。 此外，你还可以使用其他记录集，如[记录视图：从另一个记录集填充列表框](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)所述。

## <a name="see-also"></a>请参阅

[记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)