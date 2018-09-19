---
title: 使用记录视图 （MFC 数据访问） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4107b5e19020843fa50495153841ebcba64301ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077680"
---
# <a name="using-a-record-view--mfc-data-access"></a>使用记录视图（MFC 数据访问）

本主题介绍了自定义向导为你编写的记录视图的默认代码的常用方式。 通常情况下，你想要限制记录选择与[筛选器](../data/odbc/recordset-filtering-records-odbc.md)或[参数](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)，可能是[排序](../data/odbc/recordset-sorting-records-odbc.md)记录，自定义 SQL 语句。  
  
使用`CRecordView`是类似于使用[CFormView](../mfc/reference/cformview-class.md)。 基本的方法是使用记录视图显示或更新单个记录集的记录。 除此之外，你可能想要使用的其他记录集也，如中所述[记录视图： 填充列表框从第二个记录集](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。  
  
## <a name="see-also"></a>请参阅  

[记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)