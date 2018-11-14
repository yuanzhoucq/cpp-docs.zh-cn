---
title: 事务对象接口
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
ms.openlocfilehash: 177f66222a054c3305418ffcd0acdda5c82ccf43
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556174"
---
# <a name="transaction-object-interfaces"></a>事务对象接口

事务对象上的数据源定义原子工作单元，并确定每个这些工作单元之间的关系。 OLE DB 提供程序模板不直接支持此对象 （即，必须创建你自己的对象）。

下表显示了由 OLE DB 定义的事务对象的必需和可选接口。

|接口|是否必需？|实现的 OLE DB 模板？|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|强制|否|
|[ITransaction](https://docs.microsoft.com/previous-versions/windows/desktop/ms723053(v=vs.85))|强制|否|
|[ISupportErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|否|

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
