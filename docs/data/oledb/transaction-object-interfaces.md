---
title: 事务对象接口 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 33aa2c3ec99db2c2581bce827425c2dfc25bb653
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216300"
---
# <a name="transaction-object-interfaces"></a>事务对象接口

事务对象上的数据源定义原子工作单元，并确定每个这些工作单元之间的关系。 OLE DB 提供程序模板不直接支持此对象 （即，必须创建你自己的对象）。

下表显示了由 OLE DB 定义的事务对象的必需和可选接口。

|接口|是否必需？|实现的 OLE DB 模板？|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|必需|否|
|[ITransaction](/previous-versions/windows/desktop/ms723053)|必需|否|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|可选|否|

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
