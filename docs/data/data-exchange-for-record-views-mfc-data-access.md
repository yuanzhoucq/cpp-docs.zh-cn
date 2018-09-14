---
title: 记录视图 （MFC 数据访问） 的数据交换 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 58bda2d9a712e38951b8201c08e5bbbe369537eb
ms.sourcegitcommit: 6e479e33e8fd8e30ea32801edbff2e3415f31bf7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2018
ms.locfileid: "33089406"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>记录视图的数据交换（MFC 数据访问）
当你使用[添加类](../mfc/reference/adding-an-mfc-odbc-consumer.md)将映射到记录集的字段的记录视图的对话框模板资源中的控件，框架会管理两个方向中的数据交换 — 从记录集到控件和控件到记录集。 使用 DDX 机制意味着你不必编写代码来回传输数据。  
  
 通过结合使用记录视图的 DDX [RFX](../data/odbc/record-field-exchange-rfx.md)的记录集的类`CRecordset`(ODBC)。  RFX 数据源的当前记录和记录集对象的字段数据成员之间移动数据。 DDX 可将数据从字段数据成员移动到窗体的控件中。 此组合在初始时和用户逐条移动记录时填充窗体控件。 它还可以将更新的数据移回记录集，然后再移到数据源。  
  
 下图显示了记录视图的 DDX 和 RFX 之间的关系。  
  
 ![对话框&#45;数据交换和记录&#45;字段 exchange](../data/media/vc37xt1.gif "vc37xt1")  
对话框数据交换和记录字段交换  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。 有关 RFX 的详细信息，请参阅[记录字段交换 (RFX)](../data/odbc/record-field-exchange-rfx.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录视图 （MFC 数据访问）](../data/record-views-mfc-data-access.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)